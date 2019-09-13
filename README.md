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

## Spark Streaming example

```
public class Streamrspark {

      public static void main(String[] args) {
      SparkConf conf = new SparkConf();
      conf.setAppName("Streamrspark");
      JavaStreamingContext jssc = 
        new JavaStreamingContext(conf, Durations.seconds(1));
      JavaDStream<String> streamrReceiverStream = jssc.receiverStream(
        new StreamrReceiver("STREAMR_API_KEY","STREAM_ID"));

      JavaDStream<String> filtered = streamrReceiverStream.filter(
          new Function<String, Boolean>() {
            @Override
            public Boolean call(String s) throws Exception {
                return s.contains("6T");
            }
        });
      filtered.count().print();

      jssc.start();
      try {
          jssc.awaitTermination();
      } catch (InterruptedException e) {
          e.printStackTrace();
      }
  }

}

```

For examples go to https://github.com/streamr-dev/streamr-spark-integrations