# onstar2mqtt
A service that utilizes the [OnStarJS](https://github.com/samrum/OnStarJS) library to expose OnStar data to MQTT topics.

This fork is centered around the gasoline line of vehicles.

There is no affiliation with this project and GM, Chevrolet nor OnStar. In fact, it would be nice if they'd even respond to development requests so we wouldn't have to reverse engineer their API.

## Running
Collect the following information:
1. [Generate](https://www.uuidgenerator.net/version4) a v4 uuid for the device ID
2. OnStar login: username, password, PIN
3. Your car's VIN. Easily found in the monthly OnStar diagnostic emails.
4. MQTT server information: hostname, username, password
    4a. If using TLS, define `MQTT_PORT` and `MQTT_TLS=true`

Supply these values to the ENV vars below. The default data refresh interval is 30 minutes and can be overridden with ONSTAR_REFRESH with values in milliseconds.
### [Docker](https://hub.docker.com/r/michaelwoods/onstar2mqtt)

### Node.js
It's a typical node.js application, define the same environment values as described in the docker sections and run with:
`npm run start`. Currently, this is only tested with Node.js 18.x.

### Home Assistant configuration templates
MQTT auto discovery is enabled. For further integrations and screenshots see [HA-MQTT.md](HA-MQTT.md).

## Development
### Running
`npm run start`
### Testing
`npm run test`
### Coverage
`npm run coverage`
### Releases
`npm version [major|minor|patch] -m "Version %s" && git push --follow-tags`

Publish the release on GitHub to trigger a release build (ie, update 'latest' docker tag).
