# MyMavenLibSample
Maven deployment using Sonatype Nexus 2
--

To create a project with Maven we can run the following command:

> **Command:**

> - mvn archetype:generate -DarchetypeArtifactId=maven-archetype-quickstart

Now we can open the project with a preferred IDE, like Netbeans.

Put lines below into Pom.xml.

> **Pom.xml**
```xml 
<distributionManagement>
	<repository>
        	<id>releases</id>
	 	<url>http://localhost:8081/nexus/content/repositories/releases</url>
<!--            <url>http://localhost:8081/nexus/content/repositories/vheineck/</url>-->
        </repository>
 
        <snapshotRepository>
            	<id>snapshots</id>
            	<name>Internal Snapshots</name>
            	<url>http://localhost:8081/nexus/content/repositories/snapshots</url>
<!--            <url>http://localhost:8081/nexus/content/repositories/vheineck/</url>-->
        </snapshotRepository>
</distributionManagement>
```

Same for **settings.xml**

```xml
<servers>
	<server>
                <id>snapshots</id>
                <username>deployment</username>
                <password>deployment123</password>
        </server>
        <server>
        	<id>releases</id>
        	<username>deployment</username>
        	<password>deployment123</password>
        </server>
        <server>
            	<id>thirdparty</id>
            	<username>deployment</username>
            	<password>deployment123</password>
        </server>
</servers>
```

Finnaly, to deploy to server run de following command:

>**command:**
>mvn clean deploy
