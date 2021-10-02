# DialogueUtils

The Dialogue Utils are in charge of serializing and deserializing the Dialogue. At the moment Dialogue is serialized into a text file which usually looks something like this:

```
- Hello! Are you looking for an orange key?
    - No...
        - Okay, Bye!
    - Yes!
        - Okay, take this ORANGE key!! [KEY]
            - Thanks random NPC!

```

You can use the public static functions of the Dialogue Utils if you want to serialize and deserailize yourself.

## Static Functions

You can access these functions like so:

```C#
DialogueUtils.StaticFunction(parameter);
```

1. **string Serialize (List<DialogueInteraction> interactions)**: Returns a string which is the serialized text given a Dialogue Interaction list.

2. **List<DialogueInteraction> Deserialize(string s)**: Given a string it will return a list of Dialogue Interactions that you can attach to a Dialogue object.
