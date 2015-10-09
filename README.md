# Maven - Notes, Tips & Snippets
Maven Tips &amp; Tricks

##Create Project Structure

1. Generates Folder Structure
2. Generates pom.xml

```
mvn archetype:generate
```
This helps in configuring

* Select ArcheType(e.g. Web Application, Spring, Hibernate etc.,) Choose based on project name.
* Group ID(Package Name) - com.thiru.maven
* Artificat ID(Project Name) - Output of the project
	* Web Applciaion - war
	* Enterprise Application - ear
	* Java Application -jar
* Version
	* Default - 1.0.SNAPSHOT
	* Release -  for final Release.
* Package - what package a class should belong to... ???

All these information goes in to ```pom.xml```

### Sample Snippets

####Snippet for generating WebApp

SYNTAX
```
mvn archetype:generate -DgroupId={GROUPID} -DartifactId={PROJECT NAME} -DarchetypeArtificatId=maven-archetype-webapp -DinteractiveMode=false
```
SAMPLE
````
mvn archetype:generate -DgroupId=xyz.thiru.webapp -DartifactId=MyWebApp -DarchetypeArtificatId=maven-archetype-webapp -DinteractiveMode=false
```



## Maven Build Process

Maven simplifies the process of packaging the code.

### Build Life Cycle

Build lifecycle consisists of different phases. Some fo the phases have default beahviours. Specify the build phase you need. Previous phase automatically runs.

####Commonly Used Phases

* validate - Validation checks on the projects.
* compile - Compiles the JAVA Code.
* test - Executes the test cases available in test folder.
* package - Creates jar/war/ear files based on the configuration.
* install - Installs the generated package into local repository(.m2 folder)
* deploy - Deploys the project to repository for other users to use. It doesn't deploy to App Server.
* clean - Deletes the target folder.

Compile Phase

```
mvn compile
```

Generates ```.class``` files inside ```target``` folder.


```
mvn test
```

Executes the Test Cases available in the ```test``` folder. Initial setup has dummy testcases generated by maven.


```
mvn package
```

Generates ```jar/war/ear``` based on the ```pom.xml``` configuration.

```
mvn install
```

Downloads the dependencies from the central repository & installs your project to the local repository.

```
mvn clean
```

Deletes the target folder. Usually ``` mvn clean install``` executed together.

## Adding Dependencies
Pull up the dependency from central repository. 

### Search for Dependencies

Search for Dependencies in [MVN Repository](www.mvnrepository.com)

```
<dependency>
	<groupId>org.slf4j</groupId>
	<artifactId>slf4j-api</artifactId>
	<version>1.7.12</version>
</dependency>
```

Add Scope based on your requirement

```
<scope>compile<scope>
````

## Scopes
* compile - Default Scope
* test
* provided

## Plugins
Dependencies are for code. Plugins are for running you pom.xml.
 * Compiler Plugin
 * Server & Servlet Container Plugin
 