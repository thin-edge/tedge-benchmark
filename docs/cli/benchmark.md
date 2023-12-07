# benchmark

## Usage

```sh
tedge-benchmark.py --help
```

```sh
usage: benchmark [-h] {run,configure} ...

thin-edge.io benchmark script to validate the message throughput

positional arguments:
  {run,configure}
    run            Run benchmark
    configure      Configure device in preparation for running the benchmark (e.g. update mosquitto bridge settings)

options:
  -h, --help       show this help message and exit
```

## Sub commands

* [tedge-benchmark.py configure](./benchmark_configure.md)
* [tedge-benchmark.py run](./benchmark_run.md)
