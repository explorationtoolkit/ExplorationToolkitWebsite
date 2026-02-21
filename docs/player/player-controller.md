icon: material/camera-control

# :material-camera-control: Player Controller

The toolkit comes with a kinematic player controller. You can find the prefab in the `Core > Prefabs > Player Controllers` folder.

**Controls**:

* Move `WASD`
* Run `Left Shift`
* Camera look `Mouse`
* Crouching `Left Ctrl`
* Zoom the camera `Middle Mouse`

## How it Works

At it's core, the controller uses Unity's built in [CharacterController](https://docs.unity3d.com/6000.3/Documentation/ScriptReference/CharacterController.html) component, with heavy modifications to improve upon it.

This is all controlled via one component: **ETPlayerController**.

## States

There are **3** states the controller can be in.

| State | About |
|-|-|
| Grounded | When on solid, stable ground. |
| Falling | When in the air, both falling down and jumping. |
| Sliding | When grounded, but on a surface too steep to walk on. The player will slide down the slope. |

!!! tip "Tip"
    For medium to large scale games you may find it limiting and wish to implement your own solution.