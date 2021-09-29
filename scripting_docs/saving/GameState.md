# Game State

The Transform State is based off the [`State`](State.md) class and it tracks the following information.

- The current scene of the game

This is essentially used to track the last scene the Player was on when they left the game, this is important because only after loading them into the correct scene can we load all the states within that scene.

If this information does not exist we default to the starting scene specified in the GameManager.

## Additional State Information

On Load, if the current scene is not the current active scene then it will redirect to that scene.

The most important property of this State is that `ShouldLoad()` is set to false, so when all states are loaded this is not included in that.

This state is manually loaded by the GameManager through the public `LoadPlayerCurrentLevel()` function when it is needed.

This is mainly used in the Main menu when trying to load the last player level, once the last player level is loaded then we can trust the GameManager to load the states within that level.
