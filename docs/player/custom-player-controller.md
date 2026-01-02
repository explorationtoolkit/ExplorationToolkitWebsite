# :material-hammer-wrench: Custom Player Controller

You may not want to use the provided player controller, opting instead for your own solution, or a 3rd party one. The process has been made as smooth as possible, so simply follow these steps:

## 1. Prefab Setup

First, we need to create the player controller prefab, or modify an existing one.

1. Go to the `Core > Prefabs > Managers` folder, and drag the **PlayerComponents** prefab in as a child of your controller.
    * This acts as a middle man/manager for all your Exploration Toolkit controllers.

2. Go to the `Core > Prefabs > Controllers` folder, and drag in all the controllers you want to use as a child of your prefab.
    * Connect them as a reference to PlayerComponents.
    * Refer to their individual pages to learn how to set them up individually.

## 2. Detecting Inputs

Exploration Toolkit uses a custom input manager. This doesn't mean you can't use 3rd party input systems such as Rewired — you can! Click here if you're not using Unity's built-in input system.

In your player script, you need to listen to the InputManager's events. Connect to whatever input events are needed by your player controller.

```csharp
void OnEnable ()
{
    InputManager.Instance.OnMove += OnMoveInput;
    InputManager.Instance.OnRun += OnRunInput;
    InputManager.Instance.OnCrouch += OnCrouchInput;
}
        
void OnDisable ()
{
    InputManager.Instance.OnMove -= OnMoveInput;
    InputManager.Instance.OnRun -= OnRunInput;
    InputManager.Instance.OnCrouch -= OnCrouchInput;
}
```

Then, in their respective methods, do what you will with those inputs.

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






