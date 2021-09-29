# UI Manager

The UI Manager is nothing but a collection of references to the UI. It keeps all the UI Elements in one contained location to be accessed throughout the pack.

This can be found in the root Canvas object inside the Player Controller.

It is split into 3 Sections:

1. PlayerUI

   - crosshair (Image)
   - ammoText (Text)
   - weaponImage (Image)
   - healthText (Text)
   - coinText (Text)

2. UIScripts

   - keyUI (Reference to KeyUI Script)
   - DialogueProcessor (Reference to DialogueProcessor script)

3. DialogueUI
   - optionA (Button)
   - optionB (Button)
   - optionAText (Text)
   - optionBText (Text)
   - speakerText (Text)
   - text (Text)

You can access these through the following:

```C#
UIManager.Player; //PlayerUI
UIManager.Scripts; //UIScripts
UIManager.Dialogue; //DialogueUI
```

## Public Variable

There is only one public variable:

1. **enableLoadingScreenByDefault**: This is set to `true` by default; this refers to whether or not the loading screen for the Player Controller should be displayed by default.
