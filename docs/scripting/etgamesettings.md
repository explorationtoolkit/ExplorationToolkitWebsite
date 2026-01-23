icon: material/hub-outline

# :material-hub-outline: ETGameSettings

This is a persistent (DontDestroyOnLoad) object which sets, loads and manages the game settings. This includes: volume levels, fov, key bindings, etc.

At the start of the game (ideally the menu scene), the component will load each setting in from the PlayerPrefs. These settings can then be accessed by components (e.g. the camera will read the FOV setting and assign it upon initialization, as well as whenever that value changes).

For a full list of settings, check out the **ETGameSettings** script.

## Scripting

Accessing a setting value can be done like so:

```csharp
ETGameSettings.Instance.MusicVolume.Value;
```

To change a setting (in a settings screen for example), call the setting's `ChangeValue(T)` function.

```csharp
ETGameSettings.Instance.MasterVolume.ChangeValue(0.5f);
```

Each setting is represented by a generic **Setting** class. There are 4 supported data types for these settings: int, float, bool, string. Each setting also has a default value and PlayerPrefs key, which is assigned upon its initialization, as well as an `OnUpdatedValue(T)` event, which you can connect to in order to apply changes made.

For example, if you wanted the camera's field of view to update whenever the setting is changed, you could implement the following:

```csharp
void OnEnable ()
{
    inputManager.OnRightMouseButton += OnRightMouseButtonInput;
    ETGameSettings.Instance.FieldOfView.OnUpdatedValue += OnFieldOfViewSettingChanged;
}

void OnDisable ()
{
    inputManager.OnRightMouseButton -= OnRightMouseButtonInput;
    ETGameSettings.Instance.FieldOfView.OnUpdatedValue -= OnFieldOfViewSettingChanged;
}

void OnFieldOfViewSettingChanged (float newFOV)
{
    cam.fieldOfView = newFOV;
}
```

To get a full understanding on how the settings work, I recommend checking out the settings screen scripts.