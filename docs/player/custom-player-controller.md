icon: material/hammer-wrench

# :material-hammer-wrench: Custom Player Controller

You may not want to use the provided player controller, opting instead for your own solution, or a 3rd party one. Since the toolkit uses a custom input system, you'll need to connect your player controller to it. 

!!! note
    Exploration Toolkit uses a custom input manager. This doesn't mean you can't use 3rd party input systems such as Rewired — you can! [Click here](input-manager.md#creating-a-module) if you're not using Unity's built-in input system.

In the player script, we first need to create a read-only property which will fetch the InputManager from the [ETSystemRegistry](../scripting/etsystemregistry.md).

```csharp
private InputManager inputManager => ETSystemRegistry.Instance.Get<InputManager>();
```

Then we can connect to the input events we require.

```csharp
void OnEnable ()
{
    inputManager.OnMove += OnMoveInput;
    inputManager.OnRun += OnRunInput;
    inputManager.OnCrouch += OnCrouchInput;
}
        
void OnDisable ()
{
    inputManager.OnMove -= OnMoveInput;
    inputManager.OnRun -= OnRunInput;
    inputManager.OnCrouch -= OnCrouchInput;
}
```

In their respective methods, do what you will with those inputs.

```csharp
void OnMoveInput (Vector2 input)
{
    moveInput = input;
}

void OnRunInput (InputManager.InputPhase inputPhase)
{
    if(inputPhase == InputManager.InputPhase.Pressed)
        runInput = true;
    else
        runInput = false;
}

void OnCrouchInput (InputManager.InputPhase inputPhase)
{
    if(inputPhase == InputManager.InputPhase.Pressed)
        crouchInput = true;
    else
        crouchInput = false;
}
```






