# User Storage SPI Example

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

## Deploy .jar in Keycloak in Amazon Lightsail

```bash
scp -i YourLightsailDefaultKey.pem "D:\workspace\user-storage-spi-example\target\user-storage-spi.jar" ubuntu@xxx.xxx.xxx.xxx:"/home/ubuntu/keycloak-myrealm/standalone/deployments/user-storage-spi.jar"
```
