icon: material/hub-outline

# :material-hub-outline: ETSystemRegistry

The toolkit implements the [service locator pattern](https://en.wikipedia.org/wiki/Service_locator_pattern) in its framework, using concrete MonoBehaviours instead of service interfaces.

This is done to prevent the over-reliance on singletons, which as a toolkit with many manager/controller components, it can be an issue. ETSystemRegistry acts as the single point of access when trying to reference a manager or controller.

The ETSystemRegistry component is attached to the **ExplorationToolkitManager** GameObject, which must be present in all scenes you wish to implement the toolkit's systems.

If you've dug through the code, you've likely seen lines such as this:

```csharp
ETSystemRegistry.Instance.Get<UIManager>();
```

This returns a reference to the UI Manager that's currently in the scene.

!!! question "What is a system?"

    The term *system* in the ETSystemRegistry encapsulates management components such as the UIManager and InputManager, as well as player-centric controllers such as the InspectController and PickupController.

## Working with the ETSystemRegistry

If you are looking to add your own code to the toolkit or implement your own custom management scripts, I recommend integrating it within the current system. This will make your systems accessable without the need for its own direct dependancy or singleton.

### Registering a new system

In this example, let's say we've created a **ScoreManager** component.

1. In the `OnEnable` function, register the system with ETSystemRegistry.

    ```csharp
    void OnEnable ()
    {
        ETSystemRegistry.Instance.Register(this);
    }
    ```

2. In the `OnDisable` function, unregister the system. This helps to prevent any errors later on if the component gets destroyed.

    ```csharp
    void OnDisable ()
    {
        ETSystemRegistry.Instance.Unregister(this);
    }
    ```

3. Now the ScoreManager can be accessed from anywhere with the following:

    ```csharp
    ETSystemRegistry.Instance.Get<ScoreManager>();
    ```

### Referencing a system

Convention in the toolkit is to not reference the system registry directly when needed, but rather create a read-only property in the script where it will be needed.

```csharp
private InputManager inputManager => ETSystemRegistry.Instance.Get<InputManager>();
private UIManager uiManager => ETSystemRegistry.Instance.Get<UIManager>();
```

This allows you to write cleaner looking code, going from something like this:

```csharp
ETSystemRegistry.Instance.Get<UIManager>().CloseCurrentWindow();
```

To this:

```csharp
uiManager.CloseCurrentWindow();
```

## Existing Systems

Many of the toolkit's managers and controllers are automatically registered with the ETSystemRegistry upon initialization.

* `InputManager`
* `UIManager`
* `GlobalAudioSource`
* `InteractionController`
* `PickupController`
* `InspectController`
* `CrosshairController`
* `CameraFocusController`
* `Inventory`
* `NavigationMarkerManager`
* `PauseMenu` *