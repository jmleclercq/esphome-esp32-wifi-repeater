# ESP32-C6 WiFi Router (NAT) – Installation Guide

![ESP32-C6](https://img.shields.io/badge/Platform-ESP32--C6-blue) ![NAT
Router](https://img.shields.io/badge/Mode-NAT%20Router-orange)
![Guide](https://img.shields.io/badge/Type-Installation%20Guide-lightgrey)

This repository provides a **step-by-step installation guide** to
transform an **ESP32-C6** into a lightweight WiFi NAT router.

⚠️ This project does **not** contain the router firmware itself.  
It documents how to install and flash the official firmware:

👉 https://github.com/dchristl/esp32_nat_router_extended

------------------------------------------------------------------------

# Table of Contents

-   Overview  
-   Hardware Requirements  
-   Software Prerequisites  
-   Identify Serial Port  
-   Test Communication  
-   Firmware Installation  
-   Flash Firmware  
-   Expected Result  
-   Troubleshooting  
-   License  
-   Contribution

------------------------------------------------------------------------

# Overview

This guide explains how to configure an **ESP32-C6** as:

-   WiFi Access Point  
-   NAT Router  
-   Lightweight Network Extender  
-   Embedded low-power routing solution

Firmware used:

👉 https://github.com/dchristl/esp32_nat_router_extended

------------------------------------------------------------------------

# Hardware Requirements

-   ESP32-C6 development board  
-   USB-C data cable (must support data, not power-only)  
-   Stable 5V / 2A power supply  
-   Linux computer (or compatible with esptool)

------------------------------------------------------------------------

# Software Prerequisites

-   Python 3  
-   esptool

Install esptool if needed:

``` bash
pip install esptool
```

------------------------------------------------------------------------

# Identify Serial Port

### 1️⃣ List available ports (ESP disconnected)

``` bash
ls /dev/ttyACM*
```

### 2️⃣ Connect the ESP32-C6

Run again:

``` bash
ls /dev/ttyACM*
```

👉 The newly detected port corresponds to your ESP32  
Example: `/dev/ttyACM0`

------------------------------------------------------------------------

# Test Communication

``` bash
esptool.py --port /dev/ttyACM0 chip_id
```

Replace the port with yours.

If a **Chip ID** is returned, communication is working correctly.

------------------------------------------------------------------------

# Firmware Installation

Download the latest release:

👉 https://github.com/dchristl/esp32_nat_router_extended/releases/latest

Choose the appropriate file:

-   `esp32nat_extended_full_vX.X.X.zip` → Full installation  
-   `esp32nat_extended_update_vX.X.X.zip` → Update

Extract the `.bin` file before flashing.

------------------------------------------------------------------------

# Flash the Firmware

``` bash
esptool --chip esp32c6 --port /dev/ttyACM0 write_flash 0x0 esp32nat_extended_full_vX.X.X.bin
```

Adapt:

-   Serial port  
-   Exact `.bin` filename

------------------------------------------------------------------------

# Expected Result

After reboot:

-   The ESP32-C6 creates a WiFi access point  
-   You can connect to the generated network  
-   The administration interface becomes accessible according to
    firmware defaults

------------------------------------------------------------------------

# Troubleshooting

## Permission denied on serial port

``` bash
sudo usermod -a -G dialout $USER
```

Then log out and log back in.

------------------------------------------------------------------------

## No serial port detected

-   Ensure the USB cable supports data  
-   Try another USB port  
-   Verify power supply

------------------------------------------------------------------------

# Important Notice

This repository is only an installation guide.

All routing functionality is provided by:

https://github.com/dchristl/esp32_nat_router_extended

Please refer to the official repository for:

-   Firmware source code  
-   Advanced configuration  
-   Licensing details

------------------------------------------------------------------------

# License

This repository contains documentation only.

The NAT router firmware is developed by **dchristl**.  
Please refer to the official project for licensing terms.

------------------------------------------------------------------------

# Contribution

Contributions are welcome:

-   Issues  
-   Pull Requests  
-   Improvements to documentation
