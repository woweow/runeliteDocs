# Building RuneLite with Cursor

The RuneLite community only uses IntelliJ and they're super snippy if you suggest anything else. For those who want to build it elsewhere (like Cursor, VSCode, or the command line), you may find the following helpful

## Lombok Annotations
I found IntelliJ to work mostly out of the box with the [official documentation](https://github.com/runelite/wiki/blob/master/Building-with-IntelliJ-IDEA.md). Mapping this 1 to 1 to Cursor/VSCode mostly worked too. But I would still get annotation processing related issues (cannot find symbol). I found that adding the following to every pom.xml file in each package + the root:

```
<plugin>
  <groupId>org.apache.maven.plugins</groupId>
  <artifactId>maven-compiler-plugin</artifactId>
  <version>3.10.1</version>
  <configuration>
    <release>11</release>
    <annotationProcessorPaths>
      <path>
        <groupId>org.projectlombok</groupId>
        <artifactId>lombok</artifactId>
        <version>${lombok.version}</version>
      </path>
    </annotationProcessorPaths>
  </configuration>
</plugin>
```