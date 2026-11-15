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

## How it's published

This repository is a static Maven 2 layout on `main`, served by GitHub Pages (`CNAME`; `.nojekyll`, so Pages serves
the files as they are). Nothing is added by hand: a plugin's release workflow calls the reusable workflow
`publish-maven.yml` of `RB-Games/RubyCore-Source`, which adds the version's files with their checksums, updates the
artifact's `maven-metadata.xml` and commits `Publish <groupId>:<artifactId>:<version>`. It refuses snapshots and
versions that are already published.

`be.rbgames:maven-smoke-test` (0.0.1 to 0.0.3) is the smoke test of that workflow: an empty library to check that
a Maven build without any `settings.xml` resolves from here, also with strict checksums (`mvn -C`).
