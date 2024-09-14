Actualizar aplicaciones Spring Boot puede sonar como una tarea tediosa, pero no tiene por qué serlo. La migración de versiones de Spring Boot puede ser muy sencilla usando [OpenRewrite](https://docs.openrewrite.org/)

## Migrating to Spring Boot 3.2.x

[GitHub repo](https://github.com/microgestion-software/innovation-hub/tree/main/openrewrite/spring-boot-rewrite/spring-boot-2-to-3#migrating-to-spring-boot-32x-using-openrewrite)

This project demonstrates the migration from Spring Boot 2.7.x to 3.2.x using OpenRewrite. OpenRewrite is an automated refactoring tool that can help streamline the migration process.

### Steps to Migrate

1. Add the OpenRewrite plugin to your `pom.xml`:

```xml title:pom.xml
<plugins>
  <plugin>
    <groupId>org.openrewrite.maven</groupId>
    <artifactId>rewrite-maven-plugin</artifactId>
    <version>5.39.2</version>
    <configuration>
      <exportDatatables>true</exportDatatables>
      <activeRecipes>
        <recipe>org.openrewrite.java.spring.boot3.UpgradeSpringBoot_3_2</recipe>
      </activeRecipes>
    </configuration>
    <dependencies>
      <dependency>
        <groupId>org.openrewrite.recipe</groupId>
        <artifactId>rewrite-spring</artifactId>
        <version>5.18.0</version>
      </dependency>
    </dependencies>
  </plugin>
</plugins>
```

2. Run the OpenRewrite migration:

```shell title:terminal
mvn rewrite:run
```

3. Review the changes made by OpenRewrite. The tool will update your dependencies, configuration files, and code to be compatible with Spring Boot 3.2.x.

4. Address any remaining issues or warnings. While OpenRewrite can handle many aspects of the migration, some changes may require manual intervention.

5. Test your application thoroughly to ensure everything works as expected with the new Spring Boot version.


For a detailed walkthrough of the changes made during migration, compare the code in the `start/` and `finish/` directories.