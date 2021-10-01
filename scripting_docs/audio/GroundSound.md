# Ground Sound

A Ground Sound is used in the `SFXManager` to represent the different ground types the player can walk on and the footsteps to play on that surface.

## Public Variables

1. **TerrainLayerNameOrTag**: The name of the [terrain layer](https://docs.unity3d.com/Manual/class-TerrainLayer.html) or the tag that you have attached to the surface.

2. **isTerrainLayer**: Here you tell the system whether the name you provided above was a terrain layer or not.

3. **footsteps**: A list of AudioClips to play at random when walking on this surface.

The logic to play these sounds are found in the [`PlayerSFX`](PlayerSFX.md).

