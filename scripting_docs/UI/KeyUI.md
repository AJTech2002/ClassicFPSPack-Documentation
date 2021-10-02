# Key UI

The Key UI is responsible for displaying all the keys you have picked up, this is is on the Canvas.

## Public Variables

1. **keyPanel**: This is the panel which represents the starting point of the keys on the Canvas.

2. **keyElementPrefab**: Prefab of the key element, simply an Image UI (the image is filled out by the KeyManager).

3. **horizontalPadding**: Padding of new keys that are added.

4. **horizontalLength**: Length of the UI image (ex. default 40px).

## Public Functions

1. **UpdateUI (List<string> keys)**: Update UI given a list of keys, the strings are the IDs of the keys which allow the UI to pull images from the Key Manager.
