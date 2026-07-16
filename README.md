# Guillaume Paris — Home Assistant Add-ons

## Installation

1. In Home Assistant, go to **Settings → Add-ons → Add-on Store**
2. Click the three-dot menu (⋮) → **Repositories**
3. Add `https://github.com/guillaumejparis/hassio-addons`
4. Find **Teleinfo2MQTT** in the store and install it

## Add-ons

### Teleinfo2MQTT

Publishes Linky/TIC teleinfo meter data to MQTT with Home Assistant auto-discovery.

This fork adds **TIC checksum validation** (fix for [issue #103](https://github.com/fmartinou/teleinfo2mqtt/issues/103)):
corrupt frames from the serial link are now rejected before they can corrupt
energy statistics in Home Assistant.

- Supports Standard TIC (Linky) and Historical TIC modes
- Multi-arch: `amd64`, `aarch64`, `armv7`, `armhf`
- Built from [`ghcr.io/guillaumejparis/teleinfo2mqtt`](https://github.com/guillaumejparis/teleinfo2mqtt/pkgs/container/teleinfo2mqtt)
