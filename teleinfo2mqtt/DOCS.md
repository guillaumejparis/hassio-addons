# Teleinfo2MQTT - Configuration

## Options

| Option | Default | Description |
|---|---|---|
| `SERIAL` | `/dev/ttyACM0` | Serial device connected to your meter |
| `TIC_MODE` | `standard` | `standard` (Linky) or `history` (legacy meter) |
| `MQTT_URL` | `mqtt://core-mosquitto:1883` | MQTT broker URL |
| `MQTT_USER` | _(empty)_ | MQTT username |
| `MQTT_PASSWORD` | _(empty)_ | MQTT password |
| `MQTT_BASE_TOPIC` | `teleinfo` | Root MQTT topic |
| `HASS_DISCOVERY` | `true` | Enable Home Assistant MQTT discovery |
| `HASS_DISCOVERY_PREFIX` | `homeassistant` | Discovery prefix |
| `LOG_LEVEL` | `info` | `trace`, `debug`, `info`, `warn`, `error`, `fatal` |
| `EMIT_INTERVAL` | `10` | Minimum seconds between publishes (0 = every frame) |
| `TEMPO_ENABLED` | `false` | Enable EDF Tempo API integration |
| `TEMPO_INTERVAL_MINUTE` | `5` | Tempo refresh interval in minutes |

## Serial permissions

This add-on requests serial access using both:
- `udev: true` / `uart: true`
- explicit common serial devices (`/dev/ttyUSB*`, `/dev/ttyACM*`, `/dev/ttyAMA0`)

If needed, set `SERIAL` to the exact path shown by your Home Assistant host.

## Note about this fork

This build includes the checksum validation fix for upstream issue #103 to reject
corrupted TIC frames before publication.
