# weather-api
A Tinybird Data Project that defines and implements a weather data API. This project's Tinybird Data product is synced with this Git repositoy.




### Landing Data Source


```
DESCRIPTION >
    Weather data from OpenWeatherMap, pushed via the Events API by a Python script.

The script below is hosted on Heroku and scheduled to run every 10 minutes.

https://github.com/jimmoffitt/get_and_send_weather_data/blob/main/get_and_send_weather_data_cron.py

SCHEMA >
    `clouds` Int16 `json:$.clouds`,
    `description` String `json:$.description`,
    `humidity` Int16 `json:$.humidity`,
    `precip` Float32 `json:$.precip`,
    `pressure` Int32 `json:$.pressure`,
    `site_name` String `json:$.site_name`,
    `temp_f` Float32 `json:$.temp_f`,
    `timestamp` DateTime `json:$.timestamp`,
    `wind_dir` Int16 `json:$.wind_dir`,
    `wind_speed` Float32 `json:$.wind_speed`

ENGINE "MergeTree"
ENGINE_PARTITION_KEY "toYear(timestamp)"
ENGINE_SORTING_KEY "timestamp, pressure, site_name, wind_dir"
```

### GET Reports endpoint

`/reports.json?order=desc&max_results=1000&sensor_type=all`

```
DESCRIPTION >
    Weather data from OpenWeatherMap, pushed via the Events API by a Python script.

The script below is hosted on Heroku and scheduled to run every 10 minutes.

https://github.com/jimmoffitt/get_and_send_weather_data/blob/main/get_and_send_weather_data_cron.py

SCHEMA >
    `clouds` Int16 `json:$.clouds`,
    `description` String `json:$.description`,
    `humidity` Int16 `json:$.humidity`,
    `precip` Float32 `json:$.precip`,
    `pressure` Int32 `json:$.pressure`,
    `site_name` String `json:$.site_name`,
    `temp_f` Float32 `json:$.temp_f`,
    `timestamp` DateTime `json:$.timestamp`,
    `wind_dir` Int16 `json:$.wind_dir`,
    `wind_speed` Float32 `json:$.wind_speed`

ENGINE "MergeTree"
ENGINE_PARTITION_KEY "toYear(timestamp)"
ENGINE_SORTING_KEY "timestamp, site_name, temp_f"
```
