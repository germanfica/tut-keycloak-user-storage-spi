# User Storage SPI Example

This repository provides a maven project to connect to external user in-memory database.

| [:sparkles: Getting Started](#getting-started) | [:rocket: Download](#download) |
| --------------- | -------- |

## Getting Started

Follow the below instructions to get started with the source code:
- [Make sure you have all Requirements](#requirements)
- [Download Source Code](#download)
- Open Project in your favourite Java IDE
- [Build the app](#maven-commands)
- [Deploy the .jar file](#deploy-app-in-keycloak-amazon-lightsail-server)
- [Setup your Keycloak Server SPI](#keycloak-server-spi-getting-started)
- And finally, enjoy it!

## Requirements

Make sure you have the below requirements before starting:
- [OpenJDK 11 (LTS)](https://adoptium.net/?variant=openjdk11)
- [IntelliJ IDEA](https://www.jetbrains.com/idea/)
- [Keycloak 16.1.0](https://www.keycloak.org/downloads)

## Download
You can get access to the source code by using one of the following ways:
- :sparkles: Download Source Code
- :fire: Clone the repository locally:
```bash
git clone https://github.com/germanfica/user-storage-spi-example.git
```

## Keycloak Server SPI Getting Started

You can use the User Storage SPI to write extensions to Keycloak to connect to external user databases and credential stores. The built-in LDAP and ActiveDirectory support is an implementation of this SPI in action.

If you want to know more, see below the official Keycloak documentation.

- [User Storage SPI](https://www.keycloak.org/docs/latest/server_development/index.html#_user-storage-spi)

### Add user federation provider

Let’s add our first provider.

1. Open the [Keycloak Admin Console](http://localhost:8180/auth/admin)

2. Hover the mouse over the dropdown in the top-left corner where it says `Master`, then click on `Myrealm`

3. Click `User Federation`

4. Fill in the form with the following values:
   - Add provider: `hashmap-user-store`

![step_1](https://user-images.githubusercontent.com/15948693/156259407-3433abfd-f518-4d89-b298-627e9eb138d5.png)

Done, now let's save the provider. To do this:

1. Click `Save`

![step_2](https://user-images.githubusercontent.com/15948693/156260402-2f9f2d2c-8e36-4518-9afb-f3de1eb8dbdf.png)

That's it, we now have our user federation available.

![user-federation](https://user-images.githubusercontent.com/15948693/156261450-aa07c395-139b-476c-b40e-1f51f7fc8d8b.png)

### Add default roles to users

If you want you can add default roles.

![default-roles](https://user-images.githubusercontent.com/15948693/156261220-dbdbc575-50a6-46b8-9b99-d36109519557.png)

## Install maven

Follow the official maven guide below:

- [Maven in 5 Minutes](https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html)

pom.xml

```xml
 <properties>
     <maven.compiler.release>11</maven.compiler.release>
 </properties>

 <build>
     <pluginManagement>
         <plugins>
             <plugin>
                 <groupId>org.apache.maven.plugins</groupId>
                 <artifactId>maven-compiler-plugin</artifactId>
                 <version>3.10.0</version>
             </plugin>
         </plugins>
     </pluginManagement>
 </build>
```

## Maven commands

- `mvn clean`
- `mvn clean install`

## Configuration

Open `org.keycloak.storage.UserStorageProviderFactory`

```
com.hexadefence.userstoragespi.HashMapStorageProviderFactory
```

## Maven dependencies

Apache Maven Compiler Plugin
```xml
<!-- https://mvnrepository.com/artifact/org.apache.maven.plugins/maven-compiler-plugin -->
<dependency>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-compiler-plugin</artifactId>
    <version>3.10.0</version>
</dependency>
```

Keycloak Server SPI
```xml
<!-- https://mvnrepository.com/artifact/org.keycloak/keycloak-server-spi -->
<dependency>
    <groupId>org.keycloak</groupId>
    <artifactId>keycloak-server-spi</artifactId>
    <version>17.0.0</version>
    <scope>provided</scope>
</dependency>
```

## Deploy app in Keycloak Amazon Lightsail server

```bash
scp -i YourLightsailDefaultKey.pem "D:\workspace\user-storage-spi-example\target\user-storage-spi.jar" ubuntu@xxx.xxx.xxx.xxx:"/home/ubuntu/keycloak-myrealm/standalone/deployments/user-storage-spi.jar"
```

## Credits
- [German Fica](https://germanfica.com/)
- [hexaDefence](https://www.youtube.com/channel/UCuVoQAkifLvxej36w357vEA)
