---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/virtual-reality/vr-plugins/vr-unreal-engine/unreal-engine-optitrack-live-link-plugin/ue5.1-live-link-retarget-external-workaround
---

# UE5.1 Live Link Retarget External Workaround

{% hint style="info" %}
While a development bug fix is underway, there is a external workaround plugin in order to accommodate stick skeletons exported into Unreal Engine 5.1. This is not a perfect solution, but will offer a way to use a properly scaled skeletal mesh to use in retargeting an animation.&#x20;
{% endhint %}

The Live Link Skeletal Mesh Generator is a third-party plugin and is **not supported** by OptiTrack. More details of this plugin can be found here: [Live Link Skeletal Mesh Generator Plugin](https://github.com/Mystfit/LiveLinkSkeletalMeshGeneratorPlugin).&#x20;

<figure><img src="../../../../.gitbook/assets/image (835).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/image (780).png" alt=""><figcaption></figcaption></figure>

## Required Components

* [Live Link Skeletal Mesh Generator Plugin](https://github.com/Mystfit/LiveLinkSkeletalMeshGeneratorPlugin)
* Unreal Engine 5.1
* Motive 3.0
* Visual Studio 2019+&#x20;

## Visual Studio Setup

1. Install Visual Studio 2019 or higher
2. During installation, from the Workloads tab make sure to select 'Game Development with C++'

<figure><img src="../../../../.gitbook/assets/image (801).png" alt=""><figcaption></figcaption></figure>

## Unreal Engine Skeletal Mesh Generator Installation

1. Disable any OptiTrack plugins in UE5.1
2. From your project navigate to Tools > New C++ Class
3. Select 'None' from the Add C++ Class window
4. Name your class (i.e. 'StarterClass')
5. In order for this to be applied, you'll need to save and close Unreal
6. Find your project in the file directory you chose to save it in
7. Open the generated solution file and verify that you can select the green play button from top toolbar
8. This will open the Unreal Editor, close the Unreal Editor and the solution
9. Move the Skeletal Mesh Generator Plugin into the Plugins folder of your project files.&#x20;
10. Restart the solution/editor and enable: The 'Skeletal Mesh Generator Plugin', 'Geometry script', and 'Skeletal Mesh Modeling tools'.
11. Re-enabled OptiTrack LiveLink Plugin.&#x20;
12. You should now be able to use the Skeletal Mesh Generator Plugin under Plugins > SkeletonGenerator Content > Widgets.&#x20;
13. To view the Skeletal Mesh Generator widget, right click on the BLU\_SkelmeshFromLiveLink and select Run Editor Utility Widget.&#x20;

<figure><img src="../../../../.gitbook/assets/image (799).png" alt=""><figcaption></figcaption></figure>

## Additional Notes

{% hint style="warning" %}
Please note you'll need to bind the mesh to the skeleton in order for your skeletal mesh asset to properly work. &#x20;
{% endhint %}

<figure><img src="../../../../.gitbook/assets/image (771).png" alt=""><figcaption></figcaption></figure>
