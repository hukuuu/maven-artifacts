maven-artifacts
===============

# Hosting Maven Repos on Github


1. Set up/identify your Maven repo project on Github

You need to figure out where you’re going to deploy (and then host) your project artifacts.  I’ve created a new repo, and checked it out at the root of my dev directory.

    ```git clone https://github.com/hukuuu/maven-artifacts.git maven-artifacts

Because Maven namespaces artifacts based on their group and artifact IDs, you should probably have only one Github-hosted Maven repository for all of your projects and other miscellaneous artifact storage.  I can’t see any reason to have a repository-per-project.

2. Set up separate snapshots and releases directories.

    ```
        mkdir snapshots
        kdir releases
    ```
    
3. Deploy your project’s artifacts to your Maven repo
    
    A properly-useful pom.xml contains a <distributionManagement> configuration that specifies the repositories to which     one’s project artifacts should be deployed.  If you’re only going to use Github-hosted Maven repositories, then we       just need to stub this configuration out (doing this will not be necessary in the future1):

    ```
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

    Now let’s run the clutch build and deploy our artifacts (which handily implies running all of the project’s tests),      providing a path to our repo’s clone directory using the altDeploymentRepository system property:

    ```  
        mvn -DaltDeploymentRepository=snapshot-repo::default::file:../../cemerick-mvn-repo/snapshots clean deploy
    ```


4. Push to Github

    


5. Use your new Maven repository

    add this to the depending project:

    ```xml
        <repositories>
            <repository>
                <id>cemerick-snapshots</id>
                <url>https://github.com/cemerick/cemerick-mvn-repo/raw/master/snapshots</url>
            </repository>
        </repositories>
    ```

