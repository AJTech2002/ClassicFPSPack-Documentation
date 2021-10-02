# Dialogue

The Dialogue is a Scriptable Object that holds all of your Dialogue data. You can create a new Dialogue by right clicking on your Project folder and `Create > Classic FPS > Dialogue`.

In this Dialogue object you can fill out all the Dialogue you need and serialize it and deserialize it into a text file.

Here is a good tutorial on how to create new Dialogue: [Creating New Dialogue](https://youtu.be/p87XN8AVCOU)

The Dialogue is just a holder of Dialogue Interactions, when you use a Dialogue Scriptable Object, in the Inspector a custom editor will be used to allow you to create/delete/edit the Dialogue Interactions.

The Dialogue object once you have a reference to it can be queried about different information.

## Public Variables

1. **interactionName**: Name of the interaction between Player and NPC to store as Text File.

2. **PlayerName**: The name of the player, default "Player"

3. **NPCName**: The name of the NPC, default "NPC"

4. **interactions**: A List of `DialogueInteraction` which make up this Dialogue

## Public Functions

1. **ValidIndex (int index)**: Is there an interaction at this Dialogue Index

2. **CurrentDialogueChild (bool a, int interactionIndex)**: Get the a or b child of the interactionIndex.

3. **bool CurrentDialogueHasOptions (bool a, bool b, int interactionIndex)**: Get whether or not a, b, or both exist for interactionIndex index.

4. **List<DialogueInteractoin> Next (currentIndex)**: Provide list of Dialogue Interactions given current index.

## Functionality

Most of the time you will not need to interface directly with the Dialogue object, there are other classes that will handle this information.
