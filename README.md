# Streamr - Apache Spark integration library

# How to use (maven):

Add this to your pom.xml file:
```
<dependency>
  <groupId>com.streamr.labs</groupId>
  <artifactId>streamr_spark</artifactId>
  <version>0.1</version>
</dependency>
```

Then import the library with:

```
import com.streamr.labs.StreamrReceiver;
```

Then add the receiver to your Spark executor with:

```
JavaDStream<String> streamrReceiverStream = jssc.receiverStream(new StreamrReceiver("YOUR_STREAMR_API_KEY","YOUR_STREAM_ID"));

```

For examples go to https://github.com/streamr-dev/streamr-spark-integrations