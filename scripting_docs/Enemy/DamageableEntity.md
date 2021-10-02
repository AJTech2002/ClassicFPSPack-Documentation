# Damageable Entity

The Damageable Entity is a base class that is extended to other objects in this pack such as the Breakable Object and Enemy.

It is based on the `State` class so it will be tracked by the `SaveManager`.

The Damageable Entity contains a few functions that can be overriden by children classes that mainly cover taking damage and dying.

## Public Variables

1. **health**: Initial health of the entity.

2. **respawnOnLoad**: Ensure that the death of this entity is not permenant.

3. **hitParticles**: Emit hit particles when the entity takes damage.

4. **droppablePrefabs**: List of prefabs that can be dropped when the entity dies.

5. **chanceOfDrop**: The chance that this entity drops something when it dies.

6. **alwaysDrop**: Always drop some prefabs on the death of the entity.

7. **dropAllItems**: Drop all items in **droppablePrefabs** on death.

8. **spawnOffset**: Offset of the droppable prefab spawn on death.

9. **onTakeDamage**: Sound effect to play on take damage.

10. **onDeath**: Sound effect to play when the entity dies.

## Override Functions

The override functions are used by any scripts that inherit this script.

1. **TakeDamage (float damage, float delay)**: What functionality to execute when the entity takes damage, the default behaviour is to emit hit particles, take away the health, check for death and play the sound effects.

2. **Die (bool spawnDrops)**: What to execute when the entity dies, the default behaviour is to spawn the drops and then set the GameObject to disabled.

## Tracked State

The only property tracked in this state is the health of the entity, if the health is <= 0 after it is loaded in then it will be killed automatically; however no drops will spawn.

Basically, the system will ensure the entity remains dead or destroyed until saves are cleared.
