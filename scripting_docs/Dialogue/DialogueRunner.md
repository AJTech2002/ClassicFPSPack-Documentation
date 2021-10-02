# Dialogue Runner

The Dialogue Runner is a MonoBehaviour that can be attached to Game Objects and can execute Dialogue; it is the interface between the Player Input and the running of dialogue on UI.

It also has a list of public functions that you can use to control how Dialogue is executed and actions to run during and after the execution of Dialogue.

In order for this to work you will need any sort of Trigger attached to the same object.

Here is a good tutorial on how to use the Dialogue System: [Dialogue System](https://youtu.be/p87XN8AVCOU)

The References to the UI itself is now held in the `UIManager` script, which should also be on the Canvas.

## Public Variables

1. **triggerEnabled**: Is the trigger for this object enabled

2. **source**: AudioSource from which to play the SFX on the Dialogue

3. **autoRunWhenPlayerEnters**: Auto-run the Dialogue when the Player enters the trigger

4. **diableAfterLeavingTrigger**: Auto-disable the Dialogue when the Player leaves the trigger

5. **runOnce**: Ensure that the Dialogue only runs once through

6. **playPlayerReplies**: Should you play the Player's options once they have selected it or just move to the next NPC dialogue

7. **DialogueCompletedEvent**: This is an UnityEvent meaning you can attach any function on other scripts to this callback, that function will be called when the Dialogue is completed.

8. **DialogueRunEvent**: This is also an UnityEvent meaning you can attach any function on other scripts to this callback, that function will be called everytime a new DialogueInteraction is shown on screen and it will also pass the DialogueInteraction to the parameters of that function.

   This can be used to check the commands at every interaction to execute some functionality.

9. **runnableDialogues**: The list of Dialogues that can be executed, you can attach the scriptable objects you created in the project to this list.

10. **defaultRunDialogue**: This is the index of the dialogue in `runnableDialogues` to execute by default when the player enters the trigger or uses the input.

11. **dialogueRunInput**: The input to use to execute this Dialogue, this is another way to begin the Dialogue; the player still has to be within the trigger.

12. **overrideDialogueInputExecution**: Prevents input from working so that another script can take over the execution of the Dialogue Runner.

## Public Functions

1. **ExecuteDialogue (int index, bool requirePlayerToBeInTrigger)**: From another script you can execute a Dialogue at a certain `runnableDialogues` index, you can also ensure the player is in the trigger when this is executed.

2. **ExecuteDialogue (Dialogue interaction, bool requirePlayerToBeInTrigger)**: Here you can pass a Dialogue directly into the runner and ensure the player is within the trigger.

3. **StopCurrentDialogue()**: This will stop the currently executing dialogue.
