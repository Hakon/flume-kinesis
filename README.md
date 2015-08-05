# Amazon Kinesis Source and Sink for Apache Flume

## Installation

To get started, clone the repository and build the package (Requires Maven)

```
git clone https://github.com/Hakon/flume-kinesis.git
cd flume-kinesis
mvn package
```

Copy the resulting jar to a plugin specific lib directory:
```
sudo mkdir -p /usr/lib/flume-ng/plugins.d/flume-kinesis-sink/lib
sudo cp target/flume-kinesis-sink-0.0.1-SNAPSHOT.jar /usr/lib/flume-ng/plugins.d/flume-kinesis-sink/lib/
```

And copy the AWS Java SDK dependencies to the plugin specific libext directory:
```
mvn org.apache.maven.plugins:maven-dependency-plugin:2.8:get \
     -Dartifact=com.amazonaws:aws-java-sdk-core:1.9.6:jar \
     -Ddest=aws-java-sdk-core-1.9.6.jar \
     -Dtransitive=false
mvn org.apache.maven.plugins:maven-dependency-plugin:2.8:get \
     -Dartifact=com.amazonaws:aws-java-sdk-kinesis:1.9.6:jar \
     -Ddest=aws-java-sdk-kinesis-1.9.6.jar \
     -Dtransitive=false
mvn org.apache.maven.plugins:maven-dependency-plugin:2.8:get \
     -Dartifact=com.amazonaws:amazon-kinesis-client:1.2.0:jar \
     -Ddest=amazon-kinesis-client-1.2.0.jar \
     -Dtransitive=false
sudo mkdir -p /usr/lib/flume-ng/plugins.d/flume-kinesis-sink/libext
sudo cp aws-java-sdk-core-1.9.6.jar aws-java-sdk-kinesis-1.9.6.jar amazon-kinesis-client-1.2.0.jar /usr/lib/flume-ng/plugins.d/flume-kinesis-sink/libext/
```