# k-Weatherlink
<!---             
need edit
[![Latest Release](https://img.shields.io/github/v/tag/kalisio/k-hubeau?sort=semver&label=latest)](https://github.com/kalisio/k-hubeau/releases)
[![Build Status](https://app.travis-ci.com/kalisio/k-hubeau.svg?branch=master)](https://app.travis-ci.com/kalisio/k-hubeau)

A [Krawler](https://kalisio.github.io/krawler/) based service to download data from [WeatherLink V2 API](https://https://weatherlink.github.io/)

  -->


The **k-Weatherlink** jobs allow to scrape all sort of data from sensors connected to stations. The data are stored in a [MongoDB](https://www.mongodb.com/) database and more precisely in 2 collections:
* the `observations` collection stores the observed data from the sensors, more information [here](https://weatherlink.github.io/v2-api/data-structure-types)
* the `stations` collection stores the data of the stations

  
The project consists in 2 jobs:
* the `stations` job scrapes the stations data associated to your account, according a specific cron expression. By default every day at midnight.
* the `observations` job scrapes the last (current) observation of the stations above according a specific cron expression. By default every 5 minutes.


## Disclaimer
The data retrieved and frequence at wich they are retrieved are limited by your relationship with the station and subscription, see more [here](https://weatherlink.github.io/v2-api/data-permissions).
### Stations

| Variable | Description |
|--- | --- |
| `DB_URL` | The database URL. The default value is `mongodb://127.0.0.1:27017/weatherlink` |
| `API_KEY` | The WeatherLink API key for authentication. |
| `API_SECRET` | The WeatherLink API secret to sign requests. | 
| `DEBUG` | Enables debug output. Set it to `krawler*` to enable full output. By default it is undefined. |

### Observations

| Variable | Description |
|--- | --- |
| `DB_URL` | The database URL. The default value is `mongodb://127.0.0.1:27017/weatherlink` |
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

## Authors

This project is sponsored by 

![Kalisio](https://s3.eu-central-1.amazonaws.com/kalisioscope/kalisio/kalisio-logo-black-256x84.png)

## License

This project is licensed under the MIT License - see the [license file](./LICENSE) for details



