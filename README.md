# ossrh-parent



**REPLACED BY [central-parent](https://github.com/jinahya/central-parent).**

**REPLACED BY [central-parent](https://github.com/jinahya/central-parent).**

**REPLACED BY [central-parent](https://github.com/jinahya/central-parent).**

**REPLACED BY [central-parent](https://github.com/jinahya/central-parent).**



[![Maven Central](https://img.shields.io/maven-central/v/com.github.jinahya/ossrh-parent.svg)](http://search.maven.org/#search%7Cga%7C1%7Cg%3A%22com.github.jinahya%22%20AND%20a%3A%22ossrh-parent%22)

A parent pom for deploying artifacts to `oss.sonatype.org`. see [OSSRH Guide](http://central.sonatype.org/pages/ossrh-guide.html) (or [Apache Maven specific](http://central.sonatype.org/pages/apache-maven.html)). You might also want to see [Working with PGP Signatures](http://central.sonatype.org/pages/working-with-pgp-signatures.html).

## Configure
### `pom.xml`
Just set this artifact as parent.
```xml
<parent>
  <groupId>com.github.jinahya</groupId>
  <artifactId>ossrh-parent</artifactId>
</parent>
```
### `settings.xml`
We need two credentials. One for `nexus-staging-maven-plugin` and the other for `maven-gpg-plugin`.
```xml
<!-- for nexus-staging-maven-plugin -->
<server>
  <id>ossrh</id>
  <username>username</username>
  <password>{...}</password>
</server>

<!-- for maven-gpg-plugin -->
<server>
  <id>gpg.passphrase</id>
  <passphrase>{...}</passphrase>
</server>
```

## Deploy

### Snapshots

Snapshots can be deployed as it is.

```
$ mvn deploy
```

### Releases

Releases can be deployed like this.

```
$ git switch -d x.y.z
$ mvn -Possrh clean deploy
```

If your project provisioned on https://s01.oss.sonatype.org/

```shell
$ git switch -d x.y.z
$ mvn -Possrh,s01 clean deploy
```

## Caveats

Note that, by invoking the `deploy` goal with the `-Possrh` profile (or `-Possrh,s01`), you're intending to deploy the artifact to the OSSRH (snapshot|release) repository. When the `${project.version}` doesn't have a `SNAPSHOT`, the deployed artifact will also be automatically synchronized to the Maven Central Repository.
