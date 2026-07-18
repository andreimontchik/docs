# [Etsy StatsD](https://github.com/statsd/statsd)

## Install

- Should be installed on the server running an application.

1. [Install Node.js](languages/JavaScript.md#nodejs)
1. Install StatsD: `npm install -g statsd`
1. Check the StatsD version: `npm info statsd version`

## Configure

- Update and use the [statsd_console.js](../../arb/config/statsd_console.js) or `statsd_graphite.js`. Refer to the [StatsD configuration example](https://github.com/statsd/statsd/blob/master/exampleConfig.js).

## Run

- Console backend: `statsd ~/src/research/config/statsd_console.js`

# [Graphite](statsd/Graphite.md)
