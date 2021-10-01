# Terrain Surface

The Terrain Surface is a helper class with some static functions to help identify the texture the player is standing on.

## Public Static Functions

You can access a public static function like so:

```C#
string surfaceName = TerrainSurface.GetMainTexture(new Vector3(0,0,0));
```

1. **GetMainTexture (Vector3 pos)**: Given world position it will return the name of the texture you are currently standing on; you can change behaviour based on this.
