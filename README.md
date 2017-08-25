# StorJ Telegraf Plugin

The following script, when used through an [[input:exec]] block will provide StorJ information to the relevant storage location

## Config Example

```toml
[[inputs.exec]]
  # Shell/commands array
  # Full command line to executable with parameters, or a glob pattern to run all matching files.
  commands = ["<absolute_path_to_script>/storjstats.js"]
  
  ## Timeout for each command to complete.
  timeout = "10s"

  # Data format to consume.
  # NOTE json only reads numerical measurements, strings and booleans are ignored.
  data_format = "influx"

  # measurement name suffix (for separating different commands)
  name_suffix = "_storj"

```
## Grafana

In Grafana, once you've selected your data source, you should find new selection called (in my case at least) storj_storj.

You can then select node (for aggregate results) or shareid for specific node stats.

![Grafana Query Screenshot](https://raw.githubusercontent.com/salgieri/StorJ-Telegraf-Plugin/master/images/grafana_query.png)


## Screenshot

![Grafana Storj Screenshot](https://raw.githubusercontent.com/salgieri/StorJ-Telegraf-Plugin/master/images/screenshot.png)
