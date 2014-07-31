maven-artifacts
===============

Repo to host maven projects ( and be able to get them as maven dependencies )

1. command for build:

```  
mvn -DaltDeploymentRepository=snapshot-repo::default::file:../../cemerick-mvn-repo/snapshots clean deploy
```

2. add this to the depending project:

```xml
    <repositories>
        <repository>
            <id>cemerick-snapshots</id>
            <url>https://github.com/cemerick/cemerick-mvn-repo/raw/master/snapshots</url>
        </repository>
    </repositories>
```

3. add this to the dependency project:

```xml
    <distributionManagement>
         <repository>
                 <id>repo</id>
                 <url>https://github.com/hukuuu/maven-artifacts/tree/master/releases</url>
         </repository>
         <snapshotRepository>
                 <id>snapshot-repo</id>
                 <url>https://github.com/hukuuu/maven-artifacts/tree/master/snapshots</url>
         </snapshotRepository>
    </distributionManagement>
```
