# ossrh-parent
[![Build Status](https://travis-ci.org/jinahya/ossrh-parent.svg)](https://travis-ci.org/jinahya/ossrh-parent)
[![Dependency Status](https://www.versioneye.com/user/projects/5652ef1dff016c00330005b0/badge.svg)](https://www.versioneye.com/user/projects/5652ef1dff016c00330005b0)
[![Maven Central](https://img.shields.io/maven-central/v/com.github.jinahya/id-codec.svg)](http://search.maven.org/#search%7Cgav%7C1%7Cg%3A%22com.github.jinahya%22%20AND%20a%3A%22id-codec%22)

A parent pom project for deploying artifacts to `oss.sonatype.org`. See [OSSRH Guide](http://central.sonatype.org/pages/ossrh-guide.html) (or [Apache Maven specific](http://central.sonatype.org/pages/apache-maven.html)).

## `pom.xml`
Just set this artifact as parent.
```xml
<parent>
  <groupId>com.github.jinahya</groupId>
  <artifactId>ossrh-parent</artifactId>
  <version>x.y.z</version>
</parent>
```
## `settings.xml`
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
## deploy
Now you can release artifact as following.
```
$ mvn checkout x.y.z
$ mvn -Possrh clean deploy
```
