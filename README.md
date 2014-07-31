maven-artifacts
===============

Repo to host maven projects ( and be able to get them as maven dependencies )

command for build:
  mvn -DaltDeploymentRepository=snapshot-repo::default::file:../../cemerick-mvn-repo/snapshots clean deploy

add this to the depending project:
<repositories>
    <repository>
        <id>cemerick-snapshots</id>
        <url>https://github.com/cemerick/cemerick-mvn-repo/raw/master/snapshots</url>
    </repository>
</repositories>
