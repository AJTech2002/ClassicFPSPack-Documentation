# Default Player Walk Animator

Usually the walk animation & walk SFX are played through the actual Weapon's animator. However, there are cases where the Player does not have a weapon equipped; in this scenario the SFX still needs to continue playing.

On the `Update()` method of this script, if there is no active weapon then the Animator on the _Gun Mount_ GameObject is played.

It's a default animator that plays a default walk animation; the footsteps are determined based on the [Ground Type](../managers/SFXManager).
