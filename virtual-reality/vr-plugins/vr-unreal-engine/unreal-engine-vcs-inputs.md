---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/virtual-reality/vr-plugins/vr-unreal-engine/unreal-engine-vcs-inputs
---

# Unreal Engine VCS Inputs

This page provides instructions on how to configure VCS inputs in Unreal Engine. The basic configuration is similar to configuring any other input triggers in Unreal Engine. Please note that only one VCS controller can be connected and configured due to some limitations. Having two controllers connected at the same time is not supported.

## Setup Steps

#### **Create VCS Rigid Body in Motive**

Create a Rigid Body from your tracking controller’s markers using the Builder pane or by selecting the markers and using the keyboard hotkey CTRL + T. You'll want to orient the controller along the +Z axis during creation to define the 'neutral' or 'zero' orientation.

<figure><img src="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F5yEhrhQepNQfhsDzAh6n%2Fuploads%2FtTkXzJjSavEySfZbVifP%2Fimage.png?alt=media&#x26;token=c7aef439-ddb9-477a-8783-e29b6e06fc36" alt=""><figcaption><p>Orientation of VCS in the physical space.</p></figcaption></figure>

<figure><img src="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F5yEhrhQepNQfhsDzAh6n%2Fuploads%2Fr7LzM8ywqZvo3WtTAeg9%2Fimage.png?alt=media&#x26;token=2afc5e23-e40c-47ba-9c5f-aaad86e089a9" alt=""><figcaption><p>Line up the controller with the Z axis in Motive to mimic the orientation in the physical space.</p></figcaption></figure>

#### **Configure Data Streaming settings**

In Motive, configure the data streaming settings. Use the [Data Streaming](../../../motive/data-streaming.md) pane to configure streamed packets. Make sure Rigid Body data is streamed out in order to use VCS.

![](<../../../.gitbook/assets/image (741).png>)

#### **Create/load an UE Project**

Start up a project in Unreal Engine (UE).

#### **Enable Windows RawInput plugin**

Go to _Edit tab → Plugins_ to open the plugins panel. Enable the Windows RawInput plugin under the Input Devices group.

![](<../../../.gitbook/assets/image (1252).png>)

#### **Connect VCS plugin through the enabled plugin**

In _Edit tab → Project Settings_, scroll to the bottom on the left side panel until you see _Raw Input_ under the plugins group. Here you will let UE project know which input devices to use.

![](<../../../.gitbook/assets/image (1175).png>)

#### **Find Hardware ID and Product ID of the VCS controllers**

To find these IDs, you will need to look at the windows device properties. Go to _Windows Control Panel -> Devices and Printers_. Then right-click on the VCS controllers to access its properties. In the properties, go to the Hardware tab and click properties for “HID-compliant game controller”.

![](<../../../.gitbook/assets/image (1199).png>)

![](<../../../.gitbook/assets/image (1218).png>)

Once you access the controller properties, go to the details tab. Select _Hardware ID_ in the drop-down menu and the hardware ID (HID) and product ID (PID) will be shown under the highlighted section.

![](<../../../.gitbook/assets/image (1232).png>)

#### **Input the IDs in UE**

Under the project settings panel Raw Input plugin properties, input both the vendor ID (Hardware ID) and the product ID (PID) that was found under the controller properties.

![](<../../../.gitbook/assets/image (1251).png>)

**Register the Input Buttons**

Now the project has the IDs to look for the controllers, next step is to setup and register the input buttons. To do so, you will play the project scene, and trigger on the buttons to register them.

In UE, hit _Play_ and press (\~) to access the console. In the console, input command _ShowDebug INPUT". This will list out all of the input actions on the left side of the viewport._

![](<../../../.gitbook/assets/image (1202).png>)

#### **Use the keys to register**

Use all of the keys on the controller to register the inputs; total three axis and seven buttons. _Please note that these keys may not exactly match the keys on your controller_.

* Axis 1: Joystick left/right
* Axis 2: Joystick up/down
* Axis 3: Nob rotate
* Button 1: Blue
* Button 2: Black
* Button 3: White
* Button 4: Red
* Button 6: Joystick click
* Button 7: Nob click

![](<../../../.gitbook/assets/image (1160).png>)

**Map the Registered Inputs**

Now that the buttons have been registered, next step is to map the keys. They will be mapped under _Edit → Project Settings → Inputs_. Choose either the Axis mapping or the action mapping to map the controls to desired actions.

![](<../../../.gitbook/assets/image (1177).png>)

#### **Use the Registered Inputs**

Now that all of the buttons are set up, use them to control the VCS in UE.
