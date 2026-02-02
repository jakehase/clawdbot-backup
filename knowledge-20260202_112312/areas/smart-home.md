# Smart Home

Running Home Assistant at 10.0.0.7

## Devices

### Lights
- **Hallway:** `light.hallway_2` (Hue group, 3 ambiance lamps)
- **Kitchen:** `light.kitchen`
- **Living room:** `switch.living_room_lamp` (it's a switch, not light!)

### Sensors
- Aqara FP2 presence sensors (indoor lux affected by room lights)

### Voice
- ESP32-S3-Box-3 with touchscreen
- Lights page: 2 big bulbs (hallway yellow, all lights cyan)
- Config: `/config/esphome/esp32-s3box-3.yaml`

## Access
- SSH: `ssh -i ~/.ssh/ha_esphome root@10.0.0.7`
- ESPHome configs: `/config/esphome/`
- MCP: ha-mcp connected

## Notes
- Indoor lux readings unreliable when lights are on (Aqara FP2 quirk)
