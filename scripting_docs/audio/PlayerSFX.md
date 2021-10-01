# Player SFX

The Player SFX stores all the Player's main sounds and also the audio source of the player. It also houses the logic for playing the footsteps depending on the surface type.

## Public Variables

1. **playerAudioSource**: Reference to the audio source of the player.

2. **controller**: Reference to the player controller, this will be imported automatically in future.

### Sounds

1. **onSpawnSound**: Sound to play when the player spawns.

2. **jumpSound**: Sound to play when the player jumps.

3. **landSound**: Sound to play when the player falls off a ledge/jumps and lands.

4. **onTakeDamage**: Sound to play when the player takes damage.

5. **onDeath**: Sound to play when the player dies.

All these are called from various different scripts, mainly the following:

1. `PlayerStatistics.cs`: On Take Damage, On Death, On Spawn Sound
2. `PlayerController.cs`: Jump Sound, Land Sound

## Public Functions

1. **PlayFootstepSound**: You can call this by finding the PlayerSFX, through `GameManager.PlayerSFX.instance.PlayFoostepSound()` or by using a [`PlayerSFXReference`](PlayerSFXReference.md).

   This first identifies if you are located on a terrain and the ground the player is standing on a terrain; then it checks the terrain layer you are currently on to figure out what sounds to play.

   Then it loops the sounds, randomly selecting from the list.
