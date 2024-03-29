# E3DC to Home Assistant

This is a custom configuration for Home Assistant to read data from an E3DC device via ModBus/TCP Version: V2.20 from 24.07.2023.

## Installation

Copy the folder `packages` with it's contents to your Home Assistant server at the same level as the `configuration.yaml` file. 

Be sure that you have activated Modbus in your storage.

## Configuration

Add the following line to your `configuration.yaml` file to make sure, the packages are loaded:

```
template:   !include_dir_merge_list  template/

homeassistant:
  packages: !include_dir_merge_named packages/
```

Edit the file `packages/e3dc/modbus.yaml` and add your E3DC device IP address.

## Extra Config

If you want to add utility_meter for creating daily/weekly/monthly sensors for better graphs or exporting to prometheus you can add the the file `extras/utility_meter.yaml` into the `packages` folder.

## Usage

Restart Home Assistant and you will find the sensors in the `e3dc` entity. Now you can use them in your automations or add the sensors to your dashboard.
If you added HACS to your Home Assistant, you can also add the card called [Power-Distribution-Card](https://github.com/JonahKr/power-distribution-card)

To add the sensor to your Energy Dashboard use the following Sensors:

<img src="https://github.com/MrIceman11/e3dc-homeassistant/raw/main/examples/Dashboard_Config_2.png"/>

It is normal that some sensors are not available. This is because the E3DC device has not yet sent all the values. This can take up to 2 days.

## Sensors

The following sensors are available:

  * `e3dc_modbus_id`                   - E3DC Modbus ID
  * `e3dc_modbus_firmware`             - E3DC Modbus Firmware
  * `e3dc_register_amount`             - E3DC amount of Register
  * `e3dc_manufacturer`                - E3DC Manufacturer
  * `e3dc_model`                       - E3DC Model
  * `e3dc_serial_number`               - E3DC Serial Number
  * `e3dc_firmware_release`            - E3DC Firmware Release
  * `e3dc_solar_power`                 - E3DC Solar Power [W]
  * `e3dc_battery_power              - E3DC Battery Power` [W]
  * `e3dc_house_consumption_power`   - E3DC Power Consumption House [W]
  * `e3dc_grid_power`                - E3DC Grid Power [W]
  * `e3dc_external_power`            - E3DC External Power [W]
  * `e3dc_wallbox_power`             - E3DC Wallbox Power [W]
  * tbd
  * `e3dc_grid_export_power`         - E3DC Grid Export Power [W]
  * `e3dc_grid_import_power`         - E3DC Grid Import Power [W]
  * `e3dc_battery_charge_power`      - Battery Charge Power [W]
  * `e3dc_battery_discharge_power`   - Battery Discharge Power [W]
  * `e3dc_autarky`                   - Autarky in % per day
  * `e3dc_external_power`            - Power of an additional source [W]
  * `e3dc_own_consumption`           - Own Consumption in % per day
  * `e3dc_emergency_power_state_text` - emergency power state in text
  * and many other, will be added asap

## Credits

This configuration Files are an extended version based on the work of Community-Contribution: [E3DC in Energy Dashboard](https://community.home-assistant.io/t/e3dc-in-energy-dashboard/379800)

Thanks to [Roman](https://github.com/Roemer) and [MrIceman11](https://github.com/MrIceman11) for sharing the work.

