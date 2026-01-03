icon: material/star-shooting-outline

# :material-star-shooting-outline: Quick Setup

## Importing

When importing the asset, there are three main folders.

* **Core** [Required] - The core scripts and assets needed for the toolkit to function.
* **Implementation** - Models, textures, audio, and demo scenes. Good for learning the toolkit and implementing already built systems.
* **Documentation** - Links and files. You likely already get what this folder's about.

## Scene Setup

There are a few objects you need/may need in the scene for certain systems to work. Click on the respective links to learn more about what they do and how to implement them.

* [**Input Manager**](player/input-manager.md) [Required] - This detects inputs (customizable to fit your input system) and invokes events that the systems such as interaction, pickup/place down, inspect, etc, listen to.

* **UI Manager** - This is an event manager for UI related things, such as toggling the HUD. For example, when inspecting an object, by default we disable the HUD. All HUD elements (crosshair, inventory, etc) will be listening to that event.

* **Global Audio Source** - This is a singleton that allows you to play an audio clip without needing a reference to an AudioSource component.

## Player Setup

The individual controllers for each system are stored as children objects of the player.

* [**Player Components**](player/player-components.md) [Required] - This component stores a reference to all Exploration Toolkit related controllers that may be of use in the scene.

* [**Interaction Controller**](interaction/basic-setup.md) - Add this if you want the player to interact with objects. Required for pickup and inspect.

## Layer Setup (Required)

This toolkit requires an Inspect layer to be setup and assigned in order to use the inspect system. Follow the steps below, if you are importing the toolkit into a new Unity project, or an existing one.

### For a new Unity project

If you are importing the toolkit into a new Unity project, setting up the required Inspect layer is easy.

1. Go to the **Tags & Layers** window (select a GameObject, click on the Layers drop down, select Add Layer).

2. Click on the preset button.

<figure markdown="span">
![tags and layer window](images\quick-setup\quick-setup-0.png)
</figure>

3. In the **Select Preset** window, click on the ExplorationToolkit_LayersPreset.preset asset. This is located in the `Core > Presets` folder.

<figure markdown="span">
![select preset window](images\quick-setup\quick-setup-1.png)
</figure>

4. This will create the Inspect layer and you should be good to go.

### For an existing Unity project

If you are importing the toolkit into an existing Unity project with tags and layers already assigned, setting up the required Inspect layer is done like this.


1. Go to the **Tags & Layers** window and add a new layer called *Inspect*.

<figure markdown="span">
![create new layer](images\quick-setup\quick-setup-2.png)
</figure>

2. Open the **InspectController** prefab `Core > Prefabs > Controllers`. This manages the inspect system.

3. Go to the **Inspect Layer** property and change that to the *Inspect* layer. This is what inspected objects will set their layer to when inspecting.

<figure markdown="span">
![inspect controller layer set](images\quick-setup\quick-setup-3.png)
</figure>

4. Then select the **InspectOverlayCamera** child object and change its layer to `Inspect`. When prompted, also apply the layer to all children object.

<figure markdown="span">
![set inspect camera layer](images\quick-setup\quick-setup-4.png)
</figure>

5. Down in the Camera component, make sure that the **Culling Mask** is set to only the *Inspect* layer. This will make it so the inspect camera only renders GameObjects with that layer.

<figure markdown="span">
![set inspect camera culling mask](images\quick-setup\quick-setup-5.png)
</figure>

6. Now for your player camera. Go to its culling mask and disable the *Inspect* layer. We don't want the inspect layers to be rendered twice.

<figure markdown="span">
![set player camera culling mask](images\quick-setup\quick-setup-6.png)
</figure>

