# Save UI

The Save UI is used mainly on the Menu to coordinate the behaviour of the Menu.

## Public Variables

1. **startGameButton**: The button to start the game

2. **clearProgressButton**" Button to clear the progress of the game

## Public Functions

These public functions are usually hooked up to the buttons in the screen to execute different behaviour.

1. **DeleteSavedProgress()**: Clears the saves in the game and then refreshes the UI.

2. **LoadPlayerCurrentLEvel()**: Finds and loads the last level the player saved on.

3. **RefreshUI**: Refreshes the text on the buttons that are hooked up.
