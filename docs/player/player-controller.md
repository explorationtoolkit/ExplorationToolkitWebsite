icon: material/camera-control

# :material-camera-control: Player Controller

The toolkit comes with a basic player controller.

**Features**:

* Walk `WASD`
* Run `Left Shift`
* Camera look `Mouse`
* Crouching `Left Ctrl`
* Zoom the camera `Middle Mouse`

!!! tip "Tip"
    For medium to large scale games you may find it limiting and wish to implement your own solution.

There are 2 types of player controllers featured in the toolkit. You can find them in the `Core > Prefabs > Player Controllers` folder.

* **PlayerController_Blank** - Just the player controller and nothing else (apart from an empty PlayerComponents prefab). Feel free to add whatever systems you need for your game.

* **PlayerController_Complete** - The player controller with all of the toolkit's systems added (interaction, pickup, inspect, crosshair, etc).

!!! example "Coming in the future..."

    I'm planning to create a more advanced kinematic state-based controller in the future (climbing, swimming, etc).