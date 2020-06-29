# How to build a Flink project

## Create Flink Maven package
```bash
mvn archetype:generate \
    -DarchetypeGroupId=org.apache.flink \
    -DarchetypeArtifactId=flink-quickstart-java \
    -DarchetypeVersion=1.9.1 \
    -DgroupId=Chilseasai \
    -DartifactId=FlinkProject \
    -Dversion=0.1 \
    -Dpackage=flink \
    -DinteractiveMode=false
```

## Build package
```bash
mvn clean package
mvn exec:java -Dexec.mainClass=flink.SocketWindowWordCount
```

## Run Flink in Intellij directly

### Replace 'provided' with 'compile'.
```xml
<dependency>
    <groupId>org.apache.flink</groupId>
    <artifactId>flink-java</artifactId>
    <version>${flink.version}</version>
    <scope>compile</scope> <!-- Replace 'provided' with 'compile' for running in Intellij-->
</dependency>
<dependency>
    <groupId>org.apache.flink</groupId>
    <artifactId>flink-streaming-java_${scala.binary.version}</artifactId>
    <version>${flink.version}</version>
    <scope>compile</scope> <!-- Replace 'provided' with 'compile' for running in Intellij-->
</dependency>
```

### Run command below to test if the change above has taken effect.
```bash
mvn clean package
mvn exec:java -Dexec.mainClass=flink.SocketWindowWordCount
```

### Restart Intellij