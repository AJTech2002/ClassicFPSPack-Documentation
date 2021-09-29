# Save Point

The Save Point is a MonoBehaviour that has been used on two prefabs that come with the pack:

1. **The Manual Save Point**: You walk up to the save box, and press E to save; this also contains a [`DialogueRunner`](../dialogue/dialoguerunner) which will provide prompts.

2. **Checkpoint**: You walk onto the checkpoint and it auto-saves, you can choose to make a checkpoint activate only once.

The Save Point derives from [`State`](State.md) meaning some variables within the Save Point are tracked by the SaveManager.

## Public Variables

1. **isCheckpoint**: Whether or not this Save Point is a Checkpoint.

2. **saveAction**: The Input Key to perform the Save operation.

3. **disableCheckpointOnUse**: Should disable checkpoint after standing on it.

4. **disabledMaterial**: Material to replace current one on disable.

5. **onSave**: SFX to play on save.

## Tracked State

The only state tracked within the Save Point is whether or not a checkpoint is disabled. This ensures even after a Player respawns or reloads into a level the checkpoint remains disabled preventing re-use.

This will only be tracked if `disableCheckpointOnUse` is `true`.
