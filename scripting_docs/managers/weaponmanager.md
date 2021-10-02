# Weapon Manager

The Weapon Manager is a Scriptable Object meaning it is an item that lives in your Project. You can create a new Weapon Manager for your project by doing the following in the project window:

`Right Click > Classic FPS Pack > Weapon Manager`

Once you have a Weapon Manager you can assign that in the [Game Manager](gamemanager.md) object.

The Weapon Manager stores all the weapon references and manages the deployment of these weapons onto the player when the game is played. It also handles mapping the weapons to a keybind index for selection.

The Weapon Manager just stores a list of the Weapons in the game through the `WeaponReference` class.

So when you want to **create a new weapon** just add a new element to the list within the Weapon Manager and modify the properties inside to match your weapon.

A Weapon Reference contains the location of the prefab, the unique ID and keybind index. It is explained more in the Weapons namespace section.

The Weapon Manager is mainly invoked through the `PlayerWeaponController.cs` so you should interface through that most of the time. However, if you need to talk directly to the Weapon Manager here are the public functions:

## Important Information

The way the Weapons are handled within the game are in the following way:

1. You create the list of weapons in Weapon Manager

2. You create the corresponding Weapon prefabs

   - Weapon prefabs should have a root object which has a Component deriving from the Weapon class

3. In the Weapon Manager you point the Weapon Reference to the created prefab

4. On Awake, the PlayerWeaponController will call the WeaponManager Setup

5. WeaponManager will spawn all the Weapons onto the Player and initialise the properties on the Weapon class

6. The States are loaded into the weapon (remaining ammo etc.)

7. Input is handled in PlayerWeaponController and Equipping/Unequpping is handled through WeaponManager

Take a look at [this video](https://youtu.be/WYGxc-EifbM) for better understanding of Weapons.

## Public Functions / Variables

You can access a public function / variable in Weapon Manager through:

```C#
GameManager.instance.weaponManager.PublicFunction();
GameManager.instance.weaponManager.publicVariable;
```

### Methods

1. **GetWeaponReference (string UID)**: Get the properties of a weapon given the ID.

2. **Equip (string UID)**: Unequips currently spawned weapon and equips the weapon with UID. This also calls the `Equip()` function on the Weapon class.

3. **Unequip (string UID)**: Unequips the weapon with UID, also calls the `Unequip()` function on the Weapon class.

4. **Setup(PlayerWeaponController weaponController)**: Called from PlayerWeaponController to spawn all the weapons and initialise them.

### Variables

1. **spawnedWeaponInstance** : Get the currently spanwed Weapon class, you can access all the information about the weapon the player is holding (ex. ammo, UI, animations etc.)

If you want to get the spawned Weapon component in the scene based on UID you can do something like this:

`GameManager.instance.weaponManager.GetWeaponReference("Pistol").spawnedWeapon`

This is further explained in the `WeaponReference` documentation.

## Notes

You'll notice that the WeaponManager merely manages which weapon is spawned and loaded, the actual logic for equipping/unequipping weapons is done within the respective weapon's `Weapon` class.

Usually the `Weapon` class is extended to create classes such as the `DefaultClassicFPSWeapon`.
