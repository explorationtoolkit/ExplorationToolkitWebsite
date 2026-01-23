icon: material/knife-military

# :material-knife-military: Lockpicking

The toolkit features two lockpicking mini-games, which can be triggered upon interacting with a [Door](../mechanisms/doors.md) (or anything else if you wish), and when completed will unlock it. These mini-games are re-creations of existing systems in other games, so hopefully their mechanics are familiar to you.

## Tension Lockpicking

The goal here is to rotate the lockpick with the mouse in an attempt to find the sweet-spot. Press `D` to try and turn the lock. If the pick is in the sweet-spot, it will turn all the way and unlock. Otherwise, the lock may turn somewhat (the further it turns, the closer you are) then begin to wiggle. If you let the lock wiggle too much, the pick will break.

![](../images/locks-lockpicking/tension.png)

* Higher difficulties shrink the sweet-spot angle, the max tolerance angle, and the rate at which the lockpick is damaged.
* Similar to the lockpicking in *Skyrim*.

![](../images/locks-lockpicking/tension_component.png){align=left width="450"}

* As a child of the **LockpickingController_Tension** prefab is the **LockpickingTension** object. This is what's inspected when we enter the lockpicking.

* On the main component you can assign all the individual objects, angles, wiggle properties, etc.

* All four difficulties can also be tweaked, with a visual showing the sweet-spot size and max tolerance angle.

* There is also an Inspectable component attached to this object. That's because the lockpicking appears on-screen via the inspect system. Check out the Setup section below on what you need in your scene for the lockpicking to function.

</br></br></br></br>

## Pin Lockpicking

The goal here is to set all five pins. You do this by moving the mouse to select a pin, then holding down the `Left Mouse Button`, watch as the pin is pushed down. The moment it begins to wiggle, let go, and it will be set. If you let a pin wiggle too much, the pick will break.

![](../images/locks-lockpicking/pin.png)

* Higher difficulties shrink the time between the pin beginning to shake and breaking.
* Similar to the lockpicking in *The Elder Scrolls Online*.

## Setup

1. Add one of the **LockpickingController**'s to your scene, found in the `Core > Prefabs > Systems > Controllers` folder.
    * Choose between the *LockpickingController_Tension* and *LockpickingController_Pin*.
2. The lockpicking screen is built on the [Inspect System](../interaction/inspect-objects.md), so you also need to add an InspectController to your scene.

If you want to setup a door for lockpicking, do the following:

1. In your [Door](../mechanisms/doors.md) component, enable `Start Locked` and `Can Open With Lockpicking`.
2. Click on the **Create New** button next to `Lockpickable Component`.
3. A [Lockpickable](../locks-lockpicking/unlockables.md) component will be created. Configure it to your liking.

![](../images/locks-lockpicking/setup1.png){width=600}