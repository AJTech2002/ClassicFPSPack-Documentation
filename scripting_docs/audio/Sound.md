# Sound

This class is a simple holder for Audio, it is used throughout the pack to make it easier to play Audio.

A sound is usually included as a public variable in a script for the user to access and change:

```C#
public Sound hitSFX;
```

### Advantages

This gives you an easy way to attach sounds and play them with a volume that you define, also you can always play the sound without worrying that it might be null as that is checked within the functions.

## Public Variables

A Sound contains the following variables:

1. **sound**: The AudioClip to play
2. **defaultVolume**: The volume at which to play this audio (Slider)
   This can be overriden when the sound is played.

## Public Functions

A sounds public functions can be used to easily play it in different ways.

You can access a public function like the following:

```C#
hitSFX.PublicFunction (vars);
```

1. **PlayAt (Vector3 position, float volume = -1f)**: This plays this SFX at a certain position with a given volume, if you don't enter a volume it will use the `defaultVolume` provided.

2. **PlayFromSource (AudioSource source, float delay = 0f, float volume = -1f )**: This plays the SFX from a certain AudioSource with a delay and given volume; if no delay is inputted it will play instantly; if no volume is given then it will use `defaultVolume`.

It is encouraged to extend the functionality of this class found in `AudioClasses.cs` to incorporate more logic.
