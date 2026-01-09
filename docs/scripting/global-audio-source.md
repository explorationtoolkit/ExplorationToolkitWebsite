icon: material/volume-high

# :material-volume-high: Global Audio Source

On many components, down in their sounds section, you'll notice a **Use Global Audio Source** property. When enabled, the sounds won't play via a referenced AudioSource component, but through the **GlobalAudioSource**, which is included by default with the ExplorationToolkitManager prefab.

## Why?

The purpose of the global audio source is to cut down on the number of AudioSource components created for all of the toolkit's systems. Instead of having an AudioSource for every object the player can inspect, there are none. The audio clip that is to play when inspecting begins is instead sent to the GlobalAudioSource, where the sound will be played via a **PlayOneShot** wrapper method, playing the sound in 2D in the player's ears.

!!! success "Pros"

    Sounds don't require an AudioSource reference, less component/GameObject clutter.

!!! failure "Cons"

    Sounds are 2D, meaning they are not directional or position based. This may change in the future though!

## Cached Audio Sources

There is another feature of the global audio source, and that is the ability to play a cached sound. Typically, all sounds will be played via a single AudioSource, which is good if it's for a single shot sound effect.

But if you want to play a sound and have it loop or cancel it mid play, that must be done on a separate, sole audio source.

When the `PlayCached(AudioClip clip, bool loop)` function is called:

1. Check to see if an AudioSource has already been created and it's available.
2. If not, create a new one.
3. Set the clip and other properties, then play the sound.

If you want to stop the clip for any reason, you can call `StopCached(AudioClip clip)`, sending over the clip you wish to stop. The associated audio source will be found, then the sound will be stopped.

!!! question "Where is this used?"

    Cached audio sources are not used commonly in the toolkit. One place you'll find it being used though, is in the TensionLockpicking script. The sound that plays when the lockpick is strained loops and cuts off once the pick breaks or the player cancels the unlock.