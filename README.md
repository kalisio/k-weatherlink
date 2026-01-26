# k-weatherlink

[![Latest Release](https://img.shields.io/github/v/tag/kalisio/k-weatherlink?sort=semver&label=latest)](https://github.com/kalisio/k-weatherlink/releases)
[![CI](https://github.com/kalisio/k-weatherlink/actions/workflows/main.yaml/badge.svg)](https://github.com/kalisio/k-weatherlink/actions/workflows/main.yaml)
[![Quality Gate Status](https://sonar.portal.kalisio.com/api/project_badges/measure?project=kalisio-k-weatherlink&metric=alert_status&token=sqb_0652a45b522deb182462b29d17031dedca1de12e)](https://sonar.portal.kalisio.com/dashboard?id=kalisio-k-weatherlink)
[![Maintainability Issues](https://sonar.portal.kalisio.com/api/project_badges/measure?project=kalisio-k-weatherlink&metric=software_quality_maintainability_issues&token=sqb_0652a45b522deb182462b29d17031dedca1de12e)](https://sonar.portal.kalisio.com/dashboard?id=kalisio-k-weatherlink)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A [Krawler](https://kalisio.github.io/krawler/) based service to download data from [WeatherLink V2 API](https://https://weatherlink.github.io/)

The **k-weatherlink** jobs allow to scrape all sort of data from sensors connected to stations. The data are stored in a [MongoDB](https://www.mongodb.com/) database and more precisely in 2 collections:
* the `observations` collection stores the observed data from the sensors, more information [here](https://weatherlink.github.io/v2-api/data-structure-types)
* the `stations` collection stores the data of the stations

> [!CAUTION]
>This service only supports **Data Structure [Type 23](https://weatherlink.github.io/v2-api/data-structure-types)**. Using other data types result in storage issues.

The project consists in 2 jobs:
* the `stations` job scrapes the stations data associated to your account, according a specific cron expression. By default every day at midnight.
* the `observations` job scrapes the last (current) observation of the stations above according a specific cron expression. By default every 5 minutes.


## Disclaimer
The data retrieved and frequence at wich they are retrieved are limited by your relationship with the station and subscription, see more [here](https://weatherlink.github.io/v2-api/data-permissions).
### Stations

| Variable | Description |
|--- | --- |
| `DB_URL` | The database URL. The default value is `mongodb://127.0.0.1:27017/weatherlink` |
| `STN_COLLECTION` | The collection name to store the stations data. The default value is `weatherlink-stations`. |
| `API_KEY` | The WeatherLink API key for authentication. |
| `API_SECRET` | The WeatherLink API secret to sign requests. |
| `DEBUG` | Enables debug output. Set it to `krawler*` to enable full output. By default it is undefined. |

### Observations

| Variable | Description |
|--- | --- |
| `DB_URL` | The database URL. The default value is `mongodb://127.0.0.1:27017/weatherlink` |
| `STN_COLLECTION` | The collection name from which to retrieve the stations data. The default value is `weatherlink-stations`. |
| `OBS_COLLECTION` | The collection name to store the observations data. The default value is `weatherlink-observations`. |
| `TTL` | The observations data time to live. It must be expressed in seconds and the default value is `604 800` (7 days) |
| `API_KEY` | The WeatherLink API key for authentication. |
| `API_SECRET` | The WeatherLink API secret to sign requests. |
| `DATA_TYPE` | The [data types](https://weatherlink.github.io/v2-api/data-structure-types) to retrieve (e.g `1,11,13,4,15`). The default value is `everything (1 to 27)`. |
| `TIMEOUT` | The maximum duration of the job. It must be in milliseconds and the default value is `1 800 000` (30 minutes). |
| `DEBUG` | Enables debug output. Set it to `krawler*` to enable full output. By default it is undefined. |


## Deployment

We personally use [Kargo](https://kalisio.github.io/kargo/) to deploy the service.

## Contributing

Please refer to [contribution section](./CONTRIBUTING.md) for more details.

## License

Licensed under the [MIT license](LICENSE).

Copyright (c) 2017-20xx [Kalisio](https://kalisio.com)

[![Kalisio](https://kalisio.github.io/kalisioscope/kalisio/kalisio-logo-black-256x84.png)](https://kalisio.com)



