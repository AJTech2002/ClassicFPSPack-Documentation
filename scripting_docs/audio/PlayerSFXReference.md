# Player SFX Reference

This is only used when attached to the weapon's animators. It exposes a public function to call the footsteps of the player through the animation.

It's a very simple script that is used just to expose 1 function.

1. **PlayGroundSFX()**: Finds PlayerSFX then calls [`PlayFootstepSound()`](PlayerSFX.md).

   You can call this function through an [Animation Event](https://docs.unity3d.com/540/Documentation/Manual/animeditor-AnimationEvents.html) in an animation.
