# RB Games Maven repository

The public APIs of RB Games plugins, served at **https://repo.rbgames.be**, for developers who build on them.
Reading needs no account or token. Released versions never change, and snapshots aren't published here.

## Using it

Maven, in your `pom.xml`:

```xml
<repositories>
    <repository>
        <id>rbgames</id>
        <url>https://repo.rbgames.be</url>
    </repository>
</repositories>
```

Then depend on a plugin's API, with the coordinates from that plugin's documentation:

```xml
<dependency>
    <groupId>be.rbgames</groupId>
    <artifactId>PLUGIN-api</artifactId>
    <version>VERSION</version>
    <scope>provided</scope>
</dependency>
```

Gradle (Kotlin DSL):

```kotlin
repositories {
    maven("https://repo.rbgames.be")
}
```
