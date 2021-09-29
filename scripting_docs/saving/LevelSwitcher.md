# Level Switcher

This is a trigger that the Player will stand on to move to the next level. When the Player enters the trigger the following things will happen:

1. Checks if the Player entered the trigger
2. Unequips the current weapon of the Player
3. Depending on the save options, it will clear the saves of the current level or all saves
4. It will also reset the Player's health to max depending on the options
5. Finally, the next scene will be loaded

There is a good explanation about Scene Switching here: https://youtu.be/-r8kb0DSpSM

## Public Variables

1. **sceneToSwitchTo**: Name of the scene to switch to, ensure it is in the Build Settings

2. **resetPlayerHealthToMax**: Whether or not to reset the Player's health to max

3. **requiresLoading**: Does the next level require any loading (for normal playable scenes yes, if it is an UI screen then no).

4. **resetAll**: Should destroy all saves in game.

5. **clearCurrentSceneSaves**: Should wipe all the saves of the current scene (so if you go a level back then this scene will start from scratch).
