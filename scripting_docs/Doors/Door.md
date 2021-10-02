# Door

The Door script is attached to any object that can be triggered with a Key object, you can even use it for treasure chests and padlocks.

The Door is derived from State so its tracked by the SaveManager.

## Public Variables

1. **saveDoorState**: Whether or not to save the state of the door.

2. **keyReference**: A drop down where you can select or type the ID of the key you want to use to unlock this door. You can select anything from the `KeyManager`.

3. **requiresKey**: Do you need a key to open this door?

4. **doorOpen**: SFX to play On Door Open.

5. **dialogueRunner**: A reference to the `DialogueRunner` component on the GameObject that will play dialogue.

6. **executeDialogue**: Reference to the actual Dialogue object to run when the door doesn't open.

7. **openDoor**: The Input Action to use when opening the door (you can change this in inspector).

## Functionality

The Door will contain an animator with the boolean parameter `opened`; when this is set to true the Door's open animation will play.

When the player enters the trigger and then presses the `openDoor` input action, the door will check if the Player has the key needed and open the door.

If not then it will play the 'no key' dialogue. You can extend this to play dialogue when the door opens.

## Tracked State

The only tracked state is `opened`, so if the Player opens the door they will not have to keep reopening it after they die; it can remain open.
