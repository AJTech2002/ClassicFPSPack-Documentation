# Key Dialogue

The Key Dialogue is a script that be attached to an NPC alongside a `DialogueRunner` to allow an NPC to gift the player a key depending on the choices they make.

Please watch this video understand how to attach actions to a dialogue : [Attaching Dialogue Interactions](https://www.youtube.com/watch?v=HEUePeZY-VM&list=PL9FeLoYIHiTyYr5zPLr2RtjX8T41PIArx&index=10&ab_channel=AJTech)

The Key Dialogue also derives from state so it is tracked by the SaveManager.

## Public Variables

1. **keyReference**: The Key ID that should be given to the player when the dialogue interaction reaches the key gifting.

2. **dialogue**: Dialogue Runner reference.

3. **onlyGiftOnce**: Prevent the NPC from gifting the key more than once.

## Functionality

When the player runs the dialogue, at every step of the dialogue the `GiftKey (DialogueInteraction interaction)` function in this script is called. This is done by attaching it as a callback on the `DialogueRunner`.

When the function is called it also returns the current interaction the dialogue is at, the interaction contains all the information about that dialogue point including all the commands attached to it.

The `GiftKey` function checks the following:

if `interaction.Commands.Contains("KEY")`, if this is true then it will gift the player the key. This is a command and they can be attached to any section of the dialogue in the following way.

`- Hello have this key [KEY]`

If the player has never recieved a key before the Key Dialogue will play the dialogue at the `1` index of the dialogues on the Dialogue Processor. Otherwise it will play the `2` index dialogue.

Please take a look at the prefabs in the Dialogue folder to understand how to set up this system fully.

## Tracked State

The tracked state ensures that the NPC only provides the player with the key once, so they can't restart the game and ask for another key.

## Sample Dialogue

This is a sample dialogue tree structure that can gift the player a key:

- Hello! Are you looking for an orange key?
  - No...
    - Okay, Bye!
  - Yes!
    - Okay, take this ORANGE key!! [KEY]
      - Thanks random NPC!
