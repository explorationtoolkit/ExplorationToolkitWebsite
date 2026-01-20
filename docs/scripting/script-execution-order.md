icon: material/script-text

# :material-script-text: Script Execution Order

Since the toolkit's systems are designed around modularity, it has a heavy reliance on events. You may notice that a few scripts modify their order of execution. This is to allow time to register with the [ETSystemRegistry](etsystemregistry.md) before their dependencies can make their own requests.

!!! note "Script Execution Order"

    The toolkit defines its scripts execution order not in the Project Settings, but with the `[DefaultExecutionOrder]` attribute. Go [here](https://docs.unity3d.com/Manual/class-MonoManager.html) if you want to learn more about script execution order in Unity.

## Scripts

Here's a list of all the scripts which modify their execution order: 

| Script                        | Order   | Why                                                           | Accessed Via              |
| -------------------------     | :-----------------: | -------------------------------------------------------------|---------------------------|
| `ETSystemRegistry`            | **-10**               | Dependency for most systems.                                  | Singleton
| `ETGameSettings`              | **-10**               | Dependency for many components and systems.                   | Singleton
| `InputManager`                | **-5**                | Dependency for many components.                               | ETSystemRegistry
| `UIManager`                   | **-2**                | Dependency for many components.                               | ETSystemRegistry
| `InteractionController`       | **-1**                | Many components subscribe the `OnInteract` event.             | ETSystemRegistry
| `NavigationMarkerManager`     | **-1**                | Navigation markers register themselves upon initialization.   | ETSystemRegistry