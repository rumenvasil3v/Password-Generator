# Password-Generator

> A beginner exercise. Don't use the passwords it makes for anything that matters.

Give it a length and it returns a string of that many random characters. A second class keeps a username-to-password map so you can generate for several people at once.

```
cd PasswordGenerator/src
javac *.java
java Test
```

`Test` makes three 21-character passwords and prints them:

```
Username: Dudu; Password: JbpFOaPIJ|)#AR`)6a"[a
Username: Rumen; Password: :yb6UOnsL0@.UKDMFiDVv
Username: Koko; Password: X}z+j^?Io[GwEa"<#i^?Ey>
```

`GeneratePass` picks character codes from 33 up to 127. Two reasons that isn't good enough for real use: it uses `java.util.Random`, which isn't built to be unpredictable (`SecureRandom` is the right tool), and code 127 is the invisible DEL control character, so now and then a generated password has a character you can't see or type. The range should stop at 126.

`StorePasswords` just holds plain text in a `HashMap` while the program runs. Nothing is saved to disk, and adding a username twice overwrites the first password.
