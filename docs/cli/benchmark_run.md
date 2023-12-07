# benchmark run

## help

```sh
tedge-benchmark.py run --help
```

```sh
usage: benchmark run [-h] [-v] [--debug] [--host HOST] [--port PORT] [--iterations ITERATIONS] [--mqtt-device-topic-id TOPIC_ID] [--mqtt-topic-root TOPIC_ROOT]
                     [--type_name TYPE_NAME] [--clients CLIENTS] [--qos QOS] [--datapoints DATAPOINTS] [--count COUNT] [--period PERIOD] [--beats BEATS]
                     [--beats-delay BEATS_DELAY] [--telemetry-type {measurement,alarm,event}] [--restart-service] [--pretty] [--out-metric OUT_METRIC]

options:
  -h, --help            show this help message and exit
  -v, --verbose         Include verbose logging
  --debug               Include debug logging
  --host HOST           MQTT broker host
  --port PORT           MQTT broker port
  --iterations ITERATIONS
                        Number of times/iterations to run the benchmark
  --mqtt-device-topic-id TOPIC_ID
                        The device MQTT topic identifier
  --mqtt-topic-root TOPIC_ROOT
                        MQTT root prefix
  --type_name TYPE_NAME
                        MQTT type name to use when publishing, e.g. environment
  --clients CLIENTS     Number of concurrent MQTT clients which will publish the same amount of data
  --qos QOS             Quality of Service used to publish the MQTT messages
  --datapoints DATAPOINTS
                        Number of datapoints to include in a single telemetry message
  --count COUNT         Number of messages to send in one iteration (across multiple bursts)
  --period PERIOD       Period in milliseconds between the start of the bursts. This will be ignored if the duration of the bursts is longer than the period
  --beats BEATS         Number of beats/messages to publish in a burst
  --beats-delay BEATS_DELAY
                        Delay in milliseconds between beats in a burst
  --telemetry-type {measurement,alarm,event}
                        Telemetry data type to use when benchmarking
  --restart-service     Restart tedge-mapper-c8y service after an iteration which dropped message were detected
  --pretty              Pretty print the JSON results
  --out-metric OUT_METRIC
                        Path to write the prometheus textfile

Examples:

  ./tedge-benchmark.py run --count 1000 --beats 100 --period 500
  # Run benchmarks by sending 1000 messages in bursts of 100 messages as quick as possible, and repeat every 500 milliseconds

  ./tedge-benchmark.py run --count 1000:500:2000 --beats 100 --period 500
  # Run multiple benchmarks increasing the amount of messages sent each time starting from 1000 messages to 2000 in increments of 500

  ./tedge-benchmark.py run --count 1000:500:2000 --beats 100 --period 500 --out-metric=/var/lib/prometheus/node-exporter/tedge-benchmark.prom
  # Run benchmarks and store the metrics to a file which can be read by the prometheus node-exporter
```
