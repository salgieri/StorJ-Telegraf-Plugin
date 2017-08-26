# StorJ Telegraf Plugin

The following script, when used through an [[input:exec]] block will provide StorJ information to the relevant storage location

Based on the awesome CollectD script by Olivier : [storj-collectd-plugin](https://github.com/bobey/storj-collectd-plugin)

## Install

Clone the repository locally.

	npm install

You can run the script directly to confirm that the results are being generated directly. When you run you should see something similar to

```bash
./storjstats.js

storj,host=<your_host_name>,shareid=<share_id_1> peers=188,restarts=0,shared=190084937031,contracts=82855,delta=8,used_percentage=2
storj,host=<your_host_name>,shareid=<share_id_2> peers=174,restarts=0,shared=248917529152,contracts=47173,delta=11,used_percentage=3
storj,host=<your_host_name>,shareid=<share_id_3> peers=160,restarts=0,shared=124914324005,contracts=36168,delta=3,used_percentage=1
```
You see one line for each node you're running on the local machine.


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
