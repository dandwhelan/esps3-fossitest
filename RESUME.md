# Project Resume: Fossibot Remote V2

## Current State

- **Device**: ESP32-S3 (esp32-s3-devkitc-1) with ILI9341 display.
- **Functionality**:
  - Connects to Fossibot via BLE (`dandwhelan/esp-fbot` component).
  - Displays status (Voltage, Battery %, Input/Output Power).
  - **Visuals**: Draws a dashboard with "AC", "USB", "DC" buttons and a pulse animation on press.
  - **Controls**: Defines switches for AC, USB, DC.
- **Pending/In-Progress**:
  - **Touch Controls**: The `touchscreen` platform and `binary_sensor` definitions for touch buttons are currently **commented out** in `fossibot-remote-v2.yaml` (lines 311-367).
  - The pulse animation logic references `id(ac_press_time)`, etc., which are updated by the lambda in the commented-out touch sensors. Currently, these won't trigger via touch.

## Hardware Configuration

### Board Specifications

- **Model**: ESP32-S3 DevKitC-1
- **Chip**: ESP32-S3
- **Flash**: 16MB (Quad SPI)
- **PSRAM**: 8MB (Octal SPI) - *Required for display buffer*

### Display Specifications

- **Model**: ILI9341 TFT LCD
- **Resolution**: 320x240 (Landscape)
- **Interface**: SPI (4-wire)
- **Touch Controller**: XPT2046 (Resistive Touch)

### Wiring Diagram & GPIO Map

| Pin Name | ESP32-S3 GPIO | Connected Device | Function |
| :--- | :--- | :--- | :--- |
| **Power** | 5V | Display VCC | Main Power |
| | GND | Display GND | Ground |
| | GPIO 15 | Display LED | Backlight (PWM Control) |
| **SPI Bus** | GPIO 12 | Display & Touch | CLK (SCK) |
| | GPIO 11 | Display & Touch | MOSI (SDI) |
| | GPIO 13 | Display & Touch | MISO (SDO) |
| **Display** | GPIO 10 | ILI9341 | CS (Chip Select) |
| | GPIO 9 | ILI9341 | DC (Data/Command) |
| | GPIO 14 | ILI9341 | RST (Reset) |
| **Touch** | GPIO 6 | XPT2046 | CS (Chip Select) |
| | GPIO 7 | XPT2046 | IRQ (Interrupt) |

> **Note**: Touch functionality (GPIO 6 & 7) is currently defined but commented out in the YAML configuration.

## To Resume

1. **Clone the repo**:

    ```bash
    git clone https://github.com/dandwhelan/esps3-fossitest.git
    ```

2. **Restore Secrets**:
    - Create a `secrets.yaml` file in the root directory.
    - Populate it with:

        ```yaml
        wifi_ssid: "YOUR_SSID"
        wifi_password: "YOUR_PASSWORD"
        ```

3. **Install Dependencies**: Use ESPHome to compile/run. It will pull `dandwhelan/esp-fbot` from GitHub.
4. **Next Steps**:
    - Uncomment and verify the `touchscreen` platform and button binary sensors to enable touch interaction.
    - Verify BLE connection and control.

## File Manifest

- `fossibot-remote-v2.yaml`: Main ESPHome configuration.
- `.gitignore`: Git configuration (excl. secrets).
