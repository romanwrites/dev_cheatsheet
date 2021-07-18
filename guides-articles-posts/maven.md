# Maven

## Effective and super pom

Info from [here](https://stackoverflow.com/a/67778609)
`Effective POM` is the merge between your POM (the `pom.xml` that you have in your project) and
the `super POM`.

Generate effective-pom and write it to file
`mvn help:effective-pom -Doutput=effective-pom.xml`

With this, you can see the default values that Maven uses.

The `super POM` file defines all the default configurations. Hence, even the simplest form of a POM
file will inherit all the configurations defined in the super POM file.

We can visualize it at ${M2_HOME}/lib, maven-model-builder-.jar file. If we open this JAR file,
we'll find it under the name org/apache/maven/model/pom-4.0.0.xml.

It contains information about:

1. Repository (from where maven download the dependencies)
2. PluginRepository (from where maven download plugins)
3. Build (directories, resources, pluginManagement)
4. Reporting (the output directory for reporting)
5. Profiles

## Effective settings

`mvn help:effective-settings -Doutput=effective-settings.xml`  
can see there: `<localReposytory>`

## Repository

Maven first go search in local repo, then in remote

## Build life cycle

```
validate
compile
test
package
integration test
verify
install
deploy
```

## JDK
```xml
<!-- use jdk 11 to compile our code -->
<plugin>
  <artifactId>maven-compiler-plugin</artifactId>
  <configuration>
    <source>11</source> <!-- specify the language level -->
    <target>11</target>
  </configuration>
</plugin>
```

## Dependency management
Specify all the versions of dependencies. And than you don't need to write versions in children poms
```xml
<dependencyManagement>
<dependencies>
  <dependency>
    <groupId>com.user.courses</groupId>
    <artifactId>data</artifactId>
    <version>${project.version}</version>
  </dependency>

  <dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-context</artifactId>
    <version>4.2.3.RELEASE</version>
  </dependency>
</dependencies>
</dependencyManagement>
```

## Some commands
`-X` for debug mode
```
mvn -X clean install
```

skip tests
```
mvn clean install -DskipTests
```

```
mvn dependency:tree
```

download sources for all dependencies
```
mvn dependency:tree
```
