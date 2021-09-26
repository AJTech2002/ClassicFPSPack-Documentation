# ISaver

The Save Manager can save to two different formats by default, **Plain Text** and **Binary Encrypted**. Plain Text is for testing and you can see what has been saved, Binary Encrypted is for production, it ensures no one tampers with the data.

The way multiple saving methods can be handled is through the `ISaver` interface.

An `ISaver` is defined by the following methods:

1. **WriteFile (string path, json)**: Given a path and the json to write, this method should write the file to disk.

2. **string ReadFile (string path)**: Given a file path it should be able to read that file and output a string.

3. **string ProcessUID (string uid)**: Given an input UID it would process it and output a new UID.

4. **string UnprocessedUID (string processed)**: Given a processed UID it would reverse the process.

These 4 methods are enough to create a general template for savers.

There are two existing savers, the **Binary Encrypted Saver** and **Simple Text Saver**.

## Binary Encrypted Server

This Saver should be used for production ready games, and it would be better to even create a more advanced version of this saver.

You can enable this Saver by setting **binary** to `true` on the `SaveManager`.

1. **WriteFile**: For writing files, the writer first encrypts the JSON then writes it to file.

2. **ProcessUID**: For processing UID, the saver turns the UID into Base 64 String and ensures it has no unallowed characters.

3. **ReadFile**: For read file, it first decrypts the test then reads the JSON.

4. **UnprocssedUID**: Simply converts Base 64 back into normal text.

The `EncryptorDecryptor` class is in charge of the Encryption & Decryption; it can be improved by including a better encryption algorithm.

## Simple Text Saver

The Simple Text Saver is easy to use and you can read the output of these files to Debug any issues both in the naming & contents of the files.

All Methods do no additional processing to the inputs/outputs.
