# Solace Spring Boot BOM (Bill of Materials)

## Contents

* [Overview](#overview)
* [Spring Boot Version Compatibility](#spring-boot-version-compatibility)
* [Including the BOM](#including-the-bom)

## Overview

The BOM (Bill of Materials) is a POM file which defines the versions of Solace Spring Boot projects that are compatible to a particular version of Spring Boot.

## Spring Boot Version Compatibility

Consult the table below to determine which version of the BOM you need to use:

|Spring Boot       | Solace Spring Boot BOM |
|----------------- |------------------------|
| 2.2.0            | 1.0.0                  |
| 2.2.1            |                        |
| 2.2.2            |                        |

## Including the BOM

In addition to showing how to include the BOM, the following snippets also shows how to use "versionless" Solace dependencies (`solace-spring-boot-starer` in this case) when using the BOM.

### Using it with Maven
```xml
<dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>com.solace.spring.boot</groupId>
            <artifactId>solace-spring-boot-bom</artifactId>
            <version>1.0.0</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>
    </dependencies>
</dependencyManagement>

<dependencies>
    <dependency>
        <groupId>com.solace.spring.boot</groupId>
        <artifactId>solace-spring-boot-starter</artifactId>
    </dependency>
</dependencies>
```

### Using it with Gradle 4
```groovy
buildscript {
    dependencies {
        classpath 'io.spring.gradle:dependency-management-plugin:1.0.8.RELEASE'
    }
}

/* Gradle 4 isn't natively compatible with Maven BOMs. Need to use the Spring's dependency management plugin. */
apply plugin: 'io.spring.dependency-management'

dependencyManagement {
    imports {
        mavenBom "com.solace.spring.boot:solace-spring-boot-bom:1.0.0"
    }
}

dependencies {
    compile("com.solace.spring.boot:solace-spring-boot-starter")
}
```

### Using it with Gradle 5
```groovy
dependencies {
    implementation(platform("com.solace.spring.boot:solace-spring-boot-bom:1.0.0"))
    implementation("com.solace.spring.boot:solace-spring-boot-starter")
}
```
