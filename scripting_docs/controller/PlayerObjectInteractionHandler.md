# Player Object Interaction Handler

The Player Object Interaction Handler script is used mainly to handle the pickup/throwing of objects. This is a way to pickup items without the Gravity Gun and through the player's 'hands'.

The Player can pickup items that have the `PushableObject` script with the **canPickup** variable set to true.

The Script ensures the following:

1. When an item is picked up the weapon that the player is holding is unequipped
2. The object that is picked up is centered and correctly positioned
3. Multiple objects are not picked up
4. Handles removing the collider/rigidbody on the item picked up

## Input Events

There are multiple events inside the script that are triggered through inputs:

1. **GetPickupRequest()**: Called when the user tries to pickup an item with the crosshair pointed over it.

   Default **E**

2. **GetDropRequest()**: Called when the user tries to drop the currently picked up weapon (simply drop it without throwing it)

   Default **Right Mouse Button**

3. **GetThrowRequest()**: Called when the user tries to throw away the object.

   Default **Left Mouse Button**

These are all triggered through the Player Input component on the Player Controller, they can be modified by changing the Player Input's bindings. This is explained more in the [Player Input Manager](PlayerInputManager.md) section.

## Public Variables

1. **pickup**: This is variable is based of a class called `PickupUtils`, this script manages all the pickup behaviour; and the variables within this class modify the pickup behaviour.

`PickupUtils` exists because the Gravity Gun exhibits the same behaviour as the Player Object Pickup, therefore it has been reused.

Go to [PickupUtils Scripting Reference](../utils/PickupUtils.md) to learn how to change all the pickup properties such as pickup distance, crosshair color etc.
