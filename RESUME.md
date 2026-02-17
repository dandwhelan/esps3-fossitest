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

## To Resume

1. **Clone the repo**:

    ```bash
    git clone https://github.com/dandwhelan/esp32-fossitest.git
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
