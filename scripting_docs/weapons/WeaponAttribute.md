# Weapon Attribute

If you want to reference a weapon anywhere in your game you will need to know the UID of the Weapon.

If you have 1 Weapon Manager in the project then you can use the Weapon Attribute to turn a string into a popup of available Weapon UIDs.

This will make it easier to reference weapons and change them in future.

This can be done by using the following:

```C#
using ClassicFPS.Weapons;

[WeaponID]
public string weaponReference;
```
