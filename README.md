# HID Remapper

_For user documentation please see the project's website at [remapper.org](https://www.remapper.org/)._

A configurable USB dongle that remaps inputs from mice, keyboards, and other devices in hardware. No software required on the host computer.

## Features

- **Input Remapping**: Reassign buttons, change keyboard layouts, map mouse to keyboard and vice versa
- **Polling Rate Overclocking**: Up to 1000 Hz
- **Web Configuration**: Browser-based setup via [remapper.org/config](https://www.remapper.org/config/) (Chrome/Chromium required)
- **Multi-Device Support**: USB hub compatible with per-device mappings
- **Wireless Receivers**: Full support for wireless input devices
- **Serial & Bluetooth Variants**: See [SERIAL.md](SERIAL.md) and [BLUETOOTH.md](BLUETOOTH.md)

## Recent Updates

### Gaming Features (v2.x)

**SOCD Implementation** - Last Input Priority for conflicting inputs
- Prevents unwanted key combinations (A+D, W+S)
- Configurable delay for different playstyles
- Independent tracking for movement keys

**Mouse Button + WASD Freeze**
- Freezes WASD input when left mouse button is pressed
- Enables precise aiming without movement
- Configurable timing for different games

**Counter-Strafe System**
- Automatic counter-movement taps after mouse button release
- Improves precision movement in competitive shooters
- Ultra-responsive for natural feel

## Getting Started

### Setup Options

1. **Adafruit Feather RP2040**: Buy [pre-configured board](https://www.adafruit.com/product/5723) and flash firmware
2. **DIY Raspberry Pi Pico**: See [HARDWARE.md](HARDWARE.md) for assembly
3. **Custom Boards**: Refer to [custom-boards/](custom-boards/) directory

### Firmware Installation

Download firmware from [releases](https://github.com/blubtxt/hid-remapper/releases/latest) and flash to your device.

| Board | Firmware |
|-------|----------|
| Pico | `remapper.uf2` |
| Dual Pico | `remapper_dual_a.uf2` + `remapper_dual_b.uf2` |
| Feather RP2040 | `remapper_feather.uf2` |
| nRF52840 | `remapper_adafruit_feather_nrf52840.uf2` |

See [releases page](https://github.com/blubtxt/hid-remapper/releases/latest) for complete firmware list.

### Configuration

- **Web Tool**: [remapper.org/config](https://www.remapper.org/config/) (recommended)
- **Command-line**: `config-tool` with JSON input (Linux)
- **Manual**: Export/import JSON configs for backup

## Development

### Compile Firmware

**RP2040 (Pico)**:
```bash
sudo apt install gcc-arm-none-eabi libnewlib-arm-none-eabi libstdc++-arm-none-eabi-newlib srecord
git clone https://github.com/blubtxt/hid-remapper.git
cd hid-remapper/firmware
mkdir build && cd build
cmake ..
make
```

**nRF52840 with Docker**:
```bash
docker run --rm -v $(pwd):/workdir/project -w /workdir/project/firmware-bluetooth \
  nordicplayground/nrfconnect-sdk:v2.2-branch west build -b seeed_xiao_nrf52840
```

## License

The software is licensed under the [MIT License](LICENSE).

Hardware designs are licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
