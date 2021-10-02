# Dialogue Processor

The Dialogue Processor is found on the Canvas and controls all the UI elements of the Dialogue and also handles moving through a Dialogue and sending back callbacks.

This is directly executed by the `DialogueRunner` and most of the time you will not need to work with this script. However you can and should change the UI that is linked to this processor to change the visuals.

## Public Variables

These options are for the input & SFX of selection.

1. **OptionSelected**: The Sound Effect to play when an option is selected.

2. **OptionAInput**: The Input Action (key) to press to select the first option.

3. **OptionBInput**: The Input Action (key) to press to select the second option.

## Public Static Functions

These functions can be used to directly interfere with the UI of the Dialogue:

1. **Disable()**: Disables the current dialogue by force.

2. **BeginDialogue(Dialogue dialogue, string NPCName, string PlayerName, float waitTime, bool playPlayerReplies, System.Action<DialogueInteraction> OnDialogueStarted, System.Action OnInteractionCompleted)**:

   You can begin the dialogue manually by passing in all of these variables that are usually found on the `DialogueRunner`, please look at `DialogueRunner` to understand how to call this function.
