# Unreal bridge
![Final_setup.original.jpg](Final_setup.original.jpg){style=block}
_Image courtesy Shaun Lee Bishop_
## Introduction
Unreal Bridge is a real-time workflow link between the Unreal Engine and LightWave, focusing on LightWave driving Unreal changes. It can be limited to single-project use in Unreal or installed as a general plugin for use in all Unreal projects. The Unreal Bridge will transfer objects, materials, keyframe animation and instancing. Targeting and parenting can be baked using the Pro Tools baking tools and can be sent from LightWave to Unreal to create a powerful realtime system that can leverage Unreal's powerful capabilities for presentations, games and more.

## Installation

![Open_Unreal_Bridge.png](Open_Unreal_Bridge.png)

The Unreal Bridge is in two parts, with the LightWave part already installed - you can open it from the I/O tab in Layout. To install the Unreal Engine part of the plugin, download it from here or go to your LightWave install and select the lightwavebridge folder in support/3rdparty_support/UnrealEngine/[version] and:

*  copy the contents to your Unreal Engine install folder under YOUR_INSTALL_LOCATION\Engine\Plugins\Editor for system-wide access (Users/Shared/Epic Games/UE_5.xx/Engine/Plugins/Editor on the Mac), 
    OR
* create a folder called  Plugins in your Unreal project and copy the Lightwavebridge folder there for single-project use

Launch the Unreal editor. If you have installed lightwavebridge for single project use, the plugin will be automatically activated. If you have installed system-wide, you will first need to activate the Unreal-side lightwavebridge plugin:

![UE5_new_plugin.png](UE5_new_plugin.png){style=block}

![UE5_Activate_plugin.png](UE5_Activate_plugin.png){style=block}

When you restart Unreal after installing the LightWave Bridge plugin system-wide, you will get a message telling you "New plugins are available." Clicking "Manage Plugins..." you can activate the LightWave Bridge. You can also visit Edit > Plugins to activate. You will need to restart the Unreal engine once LightWave Bridge is activated.

## First Use

### Unreal
Once installed, and activated as necessary, visit the Unreal Engine preferences and in the General > Experimental group (or just type asy in the search bar) uncheck Enable async texture compilation and loading if you find Unreal Engine becoming unstable when sending elements from LightWave. You might also want to visit the General > Performance group and uncheck Use Less CPU When in Background - this is only necessary to allow the real-time updating between UE and LightWave. If real-time updates are not crucial for your project, you can leave this setting checked and simply Send from LightWave when necessary.

![UnrealEditor_prefs.gif](UnrealEditor_prefs.gif){style=block}

### LightWave 3D
In LightWave, change the colour space to sRGB to match with Unreal and go to the I/O tab to launch Unreal Bridge. Start by clicking the Connect button to link LightWave to the Unreal Editor.
![Unreal_bridge.png](Unreal_bridge.png){style=block}


Check the options required:

**Unreal**

Start by creating a new project with no Starter content. Once the editor window is open, remove everything from it apart from the PlayerStart item to start with a blank slate. Now change back to LightWave.

**LightWave 3D**

Add a polygonal object to your scene and add the Unreal material to the OpenGL input on the destination node. Now you can send it to Unreal. You can also create keyframe animation for your object and send that through as well, as a separate operation.

**Unreal**

Changes to animation or transforms will not carry back through to LightWave. Make those changes in Layout to avoid any confusion. In Unreal, make changes that will affect your game or presentation's code.

Suppose you have used the Send Animation Sequence in The Unreal Bridge plugin to transfer LightWave keyframe animation into Unreal. In that case, you will need to set the play range for the animation to playback. Do so by double-clicking on the animation icon in your Content Browser to bring up the Sequencer.

You need to set the playhead to 0, if not already there, and click the left square bracket icon to set the start of your range. Then, you need to go to the end of your animation and click the right square bracket to set the end of the animation range. Now, the animation will play in Unreal's editor.
Advanced Connection Settings

Clicking on the "Advanced Connection Settings" button on the Unreal Bridge panel will open the following dialogue:

In the "Unreal IP Address" input field you may enter the IP address of the Unreal instance to which you wish to connect. Alternatively, you can select one of the Unreal Instances discovered in your network. This allows you to work with an instance of the Unreal Editor that is not on your machine, but a colleague's.

The change is only applied after you press the "OK" button.

The Unreal Bridge plugin allows multiple connections to the same Unreal instance, enabling collaboration on the same scene by multiple artists if desired.
Preparing LightWave content for Unreal

There are always constraints when making content for a game engine, and Unreal is no exception. Right now, these are the main points for LightWave use.
Supported for transfer

* Meshes
  * Positions
  * Normals
  * UVs (maximum of seven UVs per object, not layer; no overlaps allowed)
  * Colour Maps
  * Nulls
  * Lights - Supports basic light settings like colour and intensity 
    * Point Light
    * Spherical Light
      *  Size
    * Linear Light
      * Length
    * Spot Light
      * Cone Angles
    * Distant Light
    * Cameras
      * Field of View
    * Materials
      * In principle, all Materials are supported, but only the Attributes with the same name as in Unreal are sent.
        They are:
        * Base Color or Color
        * Roughness
        * Specular
        * Metallic
        * Emissive Color
        * Opacity or Transparency
      * Unreal will use a material connected to the OpenGL surface input on your destination node if one exists (allowing for a rendered material and a realtime one simultaneously)
    * Transformations
      * Keyframe Animations can be sent optionally
      * Dynamic animations can be sent baked using the Pro Tools' Bakers
      * Parenting
        * If the parent of an object exists in the Unreal level/world, the sent object will be parented to it
        * If the parent of an object does not exist, it will be parented to the Unreal level/world root
          * Alternatively, if an Actor of the name LightWaveAnchor exists in the Unreal level/world, the new object will be parented to it
        * Parenting information is sent with every update, and parent relations will be updated in Unreal on incremental sends

When editing material properties in Modeler for a LightWave asset that is being sent to Unreal, it is important to remember that the LightWave Bridge is converting standard LightWave texture projections (Planar, Cylindrical, Cubic) to UV maps on the fly. This means that sending materials only is not sufficient, the mesh also needs to be sent. Note, that this is only for objects using standard texture projections. Objects using UV maps already will update fine without needing to resend meshes.
![Node_editor-trimaterial.png](Node_editor-trimaterial.png){style=block}
_Node editor showing a mterial for LightWave native, Octane and Unreal simultaneously_
