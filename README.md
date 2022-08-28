# speedtest-tracker-influxdbv2
Guide for using Influxdb v2 with Speedtest-Tracker Avalible Now at Grafana Dashboard 16428 (https://grafana.com/grafana/dashboards/16428-speedtest-tracker)


This dashboard shows data collected by Speedtest Tracker (https://github.com/henrywhitaker3/Speedtest-Tracker) and exported in an InfluxDBv1 database witch is connected to InfluxDBv2 bucket.


InfluxDBv1 client connect to InfluxDBv2

1. create bucket in InfluxDBv2
2.1 create or use exist API token (ALL ACCESS) for create dbv1 and auth .  
2.2 create API token (read/write) for this bucket to use with Grafana.
3. Enter in Console of InfluxDBv2

4. Make DB:

influx v1 dbrp create -t yourtokenALLACCESS
--bucket-id yourbucketid --db speedtest-tracker --rp v1-rp --default -o yourorg

5. Make User:

influx v1 auth create -t yourtokenALLACCESS 
--username speedtest --password speedtestpass --write-bucket yourbucketid -o yourorg


6. Config Client of InfluxDBv1(Speedtest-tracker) by entered data : db username, db pass , etc ...

7. Check in InfluxDBv2 in Data Explorer that data is exist in bucket

8. Then you can select all data needed and switch to Script Editor copy the script (already done)

9. Configure Grafana to use with data from InfluxDBv2 ( select datasource = InfluxDB , Query Language = Flux  ,Organization = yourorg , Bucket = speedtest , Token = yourtoken for bucket )

10. import this script in Grafana Dashboard .

11. Enjoy


Based on https://grafana.com/grafana/dashboards/16339


![speedtestsetup](https://user-images.githubusercontent.com/28630321/187088938-2b7c4492-89d8-433b-b66c-34de06cbb266.jpg)
![influxsetup](https://user-images.githubusercontent.com/28630321/187088939-492e8910-395b-4aef-b1f8-199ea98a2dc8.jpg)
![myspeedtest](https://user-images.githubusercontent.com/28630321/187088941-f2857cf1-0e2c-49ea-95b8-f9534460aff4.jpg)

