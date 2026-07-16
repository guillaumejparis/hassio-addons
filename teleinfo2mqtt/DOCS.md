# Teleinfo2MQTT — Configuration

## Options

| Option | Default | Description |
|---|---|---|
| `SERIAL` | `/dev/ttyUSB0` | Serial device connected to your Linky meter |
| `TIC_MODE` | `standard` | `standard` (Linky) or `history` (legacy meter) |
| `MQTT_URL` | `mqtt://homeassistant.local:1883` | MQTT broker URL |
| `MQTT_USER` | _(empty)_ | MQTT username (leave empty if not required) |
| `MQTT_PASSWORD` | _(empty)_ | MQTT password (leave empty if not required) |
| `MQTT_BASE_TOPIC` | `teleinfo` | Root MQTT topic |
| `HASS_DISCOVERY` | `true` | Enable Home Assistant MQTT auto-discovery |
| `HASS_DISCOVERY_PREFIX` | `homeassistant` | HA discovery prefix (change only if customised) |
| `LOG_LEVEL` | `info` | Log verbosity: `trace` `debug` `info` `warn` `error` `fatal` |
| `EMIT_INTERVAL` | `10` | Minimum seconds between MQTT publishes (0 = every frame) |
| `TEMPO_ENABLED` | `false` | Enable EDF Tempo tariff colour fetching |
| `TEMPO_INTERVAL_MINUTE` | `5` | How often (minutes) to refresh Tempo colour |

## Serial device

The add-on requests access to `/dev/ttyUSB0` and `/dev/ttyAMA0` by default.
If your adapter appears under a different path (e.g. `/dev/ttyACM0` or a
`/dev/serial/by-id/…` symlink) set `SERIAL` accordingly and make sure the
device is accessible to the Supervisor.

## MQTT

If you use the **Mosquitto broker** add-on, set `MQTT_URL` to:
```
mqtt://core-mosquitto:1883
```
and fill in `MQTT_USER` / `MQTT_PASSWORD` with the credentials you configured
in the Mosquitto add-on.

## Why this fork?

This build includes a fix for [upstream issue #103](https://github.com/fmartinou/teleinfo2mqtt/issues/103):
bad TIC checksum bytes are now validated before any value is accepted.
This prevents corrupt energy index values from being published to Home Assistant
and corrupting the energy dashboard statistics.
