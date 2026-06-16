---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/developer-tools/natnet-sdk/natnet-unicast-data-subscription-commands
---

# NatNet: Unicast Data Subscription Commands

This page provides instructions on how to use the subscribe commands in natNet. This feature is supported for Unicast streaming clients only.

## Overview

Starting from Motive 3.0, the size of the data packets that are streamed over Unicast can be configured from each NatNet client. More specifically, each client can now send commands to the Motive server and subscribe to only the data types that they need to receive. For situations where we must stream to multiple wireless clients through Unicast, this will greatly reduce the size of individual frame data packets, and help to ensure that each client continuously receives frame data packets streamed out from Motive.

**Notes**

* Supported for Unicast only.
* Supported for Motive versions 3.0 or above.
* This configuration is not necessary when streaming over a wired network since streaming packets are less likely to be dropped.
* To make sure the packet size is minimized, it is recommended to clear out the filter at the beginning.

## Use

In order to set which type of tracking data gets included in the streamed packets, a filter must be set by sending subscription commands to Motive. This filter will allow client applications to receive only the desired data over a wireless Unicast network. To setup the filter, each NatNet client application(s) needs to call the [SendMessageAndWait](natnet-remote-requests-commands.md#natnetclient-sendmessageandwait) method and send one of the following subscribe subscription command to the Motive server:

* “SubscribeToData, _\[Data Type]_, _\[Name of the Asset]_”
* “SubscribeByID, RigidBody, _\[StreamingID]_”
* “SubscribedDataOnly”

**Examples:**

```
NatNetClient natnetClient;

// Sets the filter so that the client receives only 6DOF data from RigidBody-1 tracking. 
natnetCient.SendMessageAndWait("SubscribeToData,RigidBody,RigidBody-1") 

// Sets the filter so that the client receives data from assets with specific streaming ID 
natnetClient.SendMessageAndWait("SubscribeByID,RigidBody,2")
```

### SubscribeToData

The SubscribeToData command allows you set up the filter so that NatNet client receives only the data types that it has subscribed to. Using this command, each client can subscribe to specific data types included in NatNet data packets. To set up the filter, the following string command must be sent to the Motive server using [SendMessageAndWait](natnet-remote-requests-commands.md#natnetclient-sendmessageandwait) method:

```
string command = "SubscribeToData,[Type],[Name]
```

**Type**

In the Type field, you will be specifying which data type to subscribe to. The following values are accepted:

* RigidBody
* Skeleton
* ForcePlate
* Device
* LabeledMarkers
* MarkersetMarkers
* LegacyUnlabeledMarkers
* AllTypes

**Name**

Once the type field is specified, you can also subscribe to a specific asset by inputting the name of the rigid body. You can also input "All" or leave the name field empty to subscribe to all of the assets in that data type.

**Examples**

If you wish to subscribe to a Rigid Bodynamed _Bat_, you will be sending the following string command:

```
string command = "SubscribeToData,RigidBody,Bat";
```

You can also subscribe to specific Skeleton also. The following command subscribes to _Player_ Skeleton only:

```
string command = "SubscribeToData,Skeleton,Player";
```

To subscribe to all rigid bodies in the data stream:

```
string command = "SubscribeToData,RigidBody,all";
```

{% hint style="danger" %}
Please note that Motive will not validate the presence of the requested asset, please make sure they are present on the server side.
{% endhint %}

### SubscribeByID

Another option for subscribing to a specific data is by providing the asset ID. This works only with rigid bodies that has [Streaming ID](../../motive/rigid-body-tracking/) values. This command may be easier to use when streaming to multiple clients with many rigid bodies.

**Examples**

For subscribing to a Rigid Bodywith streaming ID 3: \<source>string command = "SubscribeByID,RigidBody,3";\</source>

## Multiple Filters

Subscription filters are additive. When needed, you can send multiple subscription commands to set multiple filters. If a subscription filter contradicts one another, the order of precedence listed (high-to-low) below is followed:

**Filter Precedence Order:**

1. Specified asset, either by name or the streaming ID.
2. Specified data type, all
3. Specified data type, none
4. All types, all
5. All types, none
6. Unspecified – respects Motive settings.

## Unsubscribing / Clearing Filters

To clear the subscription filter, a client application can send an empty subscribe command OR disconnect and reconnect entirely. It’s suggested to clear the filter at the beginning to make sure the client application(s) is subscribing only to the data that’s necessary.

If you subscribe to a Rigid Bodywith a specific name or specific streaming ID, commands for unsubscribing to all will not unsubscribe to that specific object. To stop receiving data for a particular object, whether it's a Rigid Bodyor a Skeleton, the client will need to send an unsubscribe command for that specific object also.

```
// Clearing the filter
NatNetClient natnetClient;
```

```
//Clearing the subscription filter to all assets
natnetClient.SendMessageAndWait(“SubscribeToData”)
natnetClient.SendMessageAndWait(“SubscribeByID”)
```

```
//Clearing subscription filter for a Rigid Bodywith Streaming ID 3.
natnetClient.SendMessageAndWait("SubscribeByID,RigidBody,3");
```

```
//Unsubscribing to a Rigid Bodywith streaming ID 3 and a Skeleton named "Josh"
natnetClient.SendMessageAndWait("SubscribeByID,RigidBody,3,None");  
natnetClient.SendMessageAndWait("SubscribeToData,Skeleton,Josh,None");
```

## Testing Commands Using Sample Project

For quickly testing the NatNet commands, you can utilize the [WinFormSamples](natnet-sample-projects.md#running-the-.net-sample) program provided in the NatNet SDK package. This program has commands tab which can be used for calling the SendMessageAndWait method. Using this input field, you can test the command string to test out its results.

![Subscribing to shotgun Rigid Bodyfrom WinFormSamples app.](<../../.gitbook/assets/image (1021).png>)
