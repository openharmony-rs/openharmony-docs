# FAQs

<!--Kit: Basic Services Kit-->
<!--Subsystem: USB-->
<!--Owner: @hwymlgitcode-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=124940311872fe2d4490632d55584ec442983b8a translatedAt=2026-11-06T12:11:54.923Z pushedAt=2026-11-09T12:40:13.017Z nl=1 -->

## What should I do if the device list obtained by using usbManager.getDevices is empty when the device is connected to a PC using a USB cable?

### Symptom

After a device is connected to a PC using a USB cable, the device list obtained by **usbManager.getDevices** is empty, and the PC is not identified as a USB device.

### Possible Causes

USB devices are classified into two types: host and device. The USB host takes charge of data transmission and USB port management, and USB devices are managed by the USB host.

If the current device functions as the USB host, the **usbManager.getDevices** API can be used to obtain the list of connected USB devices.

Based on the preceding description:

- When a device, for example, a phone, is connected to a PC using a USB cable, the PC is the USB host by default, and the phone is a USB device. It is normal if the device list obtained by calling **usbManager.getDevices** on the phone is empty.
- When a device, for example, a phone, is connected to a mouse or keyboard using a USB cable, the phone is the USB host by default, and the mouse or keyboard is the USB device. In this case, you can call the **usbManager.getDevices** API on the phone to obtain the device list.

### Solution

Ensure that the current device is the USB host and the connected device is the USB device. (Some devices can serve both as the USB host and USB device. In this case, you need to set such devices as USB devices so that the device list can be obtained by the USB host.)

## What should I do if garbled characters are displayed when data is transferred through the USB?

### Symptom

Garbled characters are displayed during data transfer.

### Possible Causes

The baud rate does not match.

### Solution

Check whether the baud rates at both ends are the same. If not, reconfigure the baud rates.

## What should I do if communication fails when data is transferred through the USB?

### Symptom

The connection cannot be set up between the two ends. No data is transferred or received, or the transferred data frames are incomplete (for example, only some bytes are received).

### Possible Causes

The parity bit or stop bit is incorrectly configured.

### Solution

Check whether the settings of the parity bit or stop bit at both ends are the same as those required by the device.

## What should I do if packet loss occurs when data is transferred through the USB?


### Symptom

Occasional packet loss occurs during data transfer.

### Possible Causes

Noise interference or insufficient stop bit.

### Solution

Check whether interference exists. Modify the stop bit to improve the anti-interference capability (for example, change the stop bit from 1 to 2).

## Peripherals Cannot Be Used After ClaimInterface Is Called

### Problem Symptom

Peripherals cannot be used, for example, a mouse or keyboard.

### Possible Cause

After an application calls the ClaimInterface API, the USB interface is released from the kernel driver and controlled by a user-space program. As a result, the kernel cannot control the corresponding device.

### Solution Measure

1. When calling the API, you can pass false to the optional parameter to avoid forcibly claiming the interface.
2. After this problem occurs, replug the device to restore it.
