# StorJ Telegraf Plugin

The following script, when used through an [[input:exec]] block will provide StorJ information to the relevant storage location

## Config Example

```toml
# Read flattened metrics from one or more commands that output JSON to stdout
[[inputs.exec]]
  # Shell/commands array
  # Full command line to executable with parameters, or a glob pattern to run all matching files.
  commands = ["/usr/bin/line_protocol_collector","/tmp/test2.sh"]
  ## Timeout for each command to complete.
  timeout = "10s"

  # Data format to consume.
  # NOTE json only reads numerical measurements, strings and booleans are ignored.
  data_format = "influx"

  # measurement name suffix (for separating different commands)
  name_suffix = "_storj"
```

