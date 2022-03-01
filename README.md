# User Storage SPI Example

## Keycloak Server SPI Getting Started

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

## Maven commands

- `mvn clean`
- `mvn clean install`

## Configuration

Open `org.keycloak.storage.UserStorageProviderFactory`

```
com.hexadefence.userstoragespi.HashMapStorageProviderFactory
```

## Dependencies

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

## Deploy .jar in Keycloak Amazon Lightsail server

```bash
scp -i YourLightsailDefaultKey.pem "D:\workspace\user-storage-spi-example\target\user-storage-spi.jar" ubuntu@xxx.xxx.xxx.xxx:"/home/ubuntu/keycloak-myrealm/standalone/deployments/user-storage-spi.jar"
```
