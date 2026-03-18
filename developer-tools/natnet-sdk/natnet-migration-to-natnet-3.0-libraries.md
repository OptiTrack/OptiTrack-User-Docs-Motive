# NatNet: Migration to NatNet 3.0 libraries

This page is created to guide help users migrating their NatNet projects onto NatNet 3.0 libraries.

## Statically Linked Libraries

NatNet 3.0 no longer allows static linking of the libraries. If a NatNet project was utilizing NatNetLibStatic.lib to accomplish static linking, you will need to make changes to the project configurations, so that it links dynamically instead.

{% hint style="info" %}
_This is only an example. Required configuration changes may be different depending on how the projects were setup._

**Visual Studio Example**

* **Project Settings → Configuration Properties → C/C++ → Preprocessor Definitions:** Add "NATNATLIB\_IMPORTS"
* **Project Settings → Configuration Properties → Linker → Input → Additional Dependencies:** Change "NatNetLibStatic.lib" to "NatNetLib.lib"
* **Project Settings → Configuration Properties → Linker → General:** Make sure the additional library directories includes the directory where the library files are locate.
{% endhint %}

## Rigid Body Marker Data

In NatNet 3.0, the structure of Rigid Body descriptions and Rigid Body frame data has been slightly modified. The sRigidBodyData:Markers member has been removed, and instead, the Rigid Body description (sRigidBodyDescription) now includes the expected Rigid Body marker positions in respect to the corresponding RB orientation axis.

Per-frame positions of Rigid Body markers have to be derived using the Rigid Body tracking data and the expected Rigid Body markers positions included in the description packet.
