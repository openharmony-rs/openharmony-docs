# FAQs
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=3ef7f69a75e36b1756789f3b838cf0a1fdcb6208 translatedAt=2026-09-01T02:12:45.029Z pushedAt=2026-09-01T11:57:34.168Z -->

## Failed to Find the Header File During Compilation or Running

### Symptom

The message "usb/usb_ddk_api.h not found" or "hid/hid_ddk_api.h not found" is displayed during compilation or running.

### Solution

- If an error is reported during compilation, check whether the OpenHarmony version is the latest.
<!--RP1-->
- If an error is reported during running, check whether the device version is 4.1 Release or later.<!--RP1End-->

## Version Mismatch Displayed During HAP Installation

### Symptom

The message "compileSdkVersion and releaseType of the app do not match the apiVersion and releaseType on the device" is displayed during HAP installation.

### Solution

<!--RP2-->Check whether the system version of the device is correct<!--RP2End--> according to the mapping provided in [Version Mapping](#version-mapping).

### Version Mapping
<!--RP3-->
| API Type| Minimum API Version| OpenHarmony Version|
| --------- | --------- | --------- |
| Application development APIs (ArkTS APIs)| API10 | 4.0 Release or later|
| UsbDdk APIs| API10 | 4.0 Release or later|
| HidDdk APIs| API11 | 4.1 Release or later|
| USBSerialDDK APIs| API18 | 5.1 Release or later|
| ScsiPeripheralDDK APIs| API18 | 5.1 Release or later|
<!--RP3End-->

## Failed to Parse the Local .so File During HAP Installation

### Symptom

The message "code:9568347 error: install parse native so failed" is displayed during HAP installation.

### Solution

According to the solution provided in [What should I do if "code:9568347 error: install parse native so failed" is displayed during HAP installation or error message "TypeError: Cannot read property xxx of undefined" is displayed during HAP running?](https://developer.huawei.com/consumer/en/doc/harmonyos-faqs-V5/faqs-app-debugging-14-V5) in application debugging, manually set **abiFilters** in **buildOption/externalNativeOptions** in the **build-profile.json5** file.

## When Using a DDK API That Sends Data Based on a Buffer, Data Is Not Sent According to the Specified offset and bufferLength

### Symptom

Take [OH_Usb_SendPipeRequest](../../reference/apis-driverdevelopment-kit/capi-usb-ddk-api-h.md#oh_usb_sendpiperequest) as an example. When using this type of buffer-based data transfer API, even if the `offset` and `bufferLength` fields of [UsbDeviceMemMap](../../reference/apis-driverdevelopment-kit/capi-usbddk-usbdevicememmap.md) are set, the API actually sends the entire buffer based on the `size` value.

### Solution

The implementation of such APIs uses the entire buffer for transmission according to `size`. Therefore, when sending a specific portion of data, apply for a buffer of the required size and fill it with the corresponding data to initiate the transmission. Refer to the implementation in the following code block. Note:
- Such APIs are planned to be optimized and refactored. In later versions, the capability to transmit data based on `offset` and `bufferLength` will be provided.
- Performance overhead: The performance overhead of creating and destroying a buffer is minimal, usually within 0.1 ms and negligible.

```cpp
/**
 * Assume that data has been filled with valid data, deviceId is the ID of the corresponding peripheral, and pipe is the pipe information to be transferred.
 * Preset scenario: transfer the 32-byte data starting from index 0x10 in data.*/
uint8_t *data = new uint8_t [128];

/** Create a data buffer. */
UsbDeviceMemMap *devMmap;
OH_Usb_CreateDeviceMemMap(deviceId, 32, &devMmap);

/** Copy only the data to be transferred to the buffer. */
memcpy(devMmap->address, data + 0x10, 32);

/** Initiate the data transfer. */
OH_Usb_SendPipeRequest(pipe, devMmap);

/** After use, destroy the data buffer to reclaim resources. */
OH_Usb_DestroyDeviceMemMap(devMmap);
```

## Calling DDK C-APIs in a Child Process or a Non-Driver Ability Fails

### Symptom

Calling the Driver Development Kit C-APIs in a child process created by a driver Ability or in a non-driver Ability process returns an abnormal error.

### Solution

The C-APIs provided by the Driver Development Kit can be used only in the DriverExtension process. To manage and communicate with peripherals in other processes, use the APIs provided by [@ohos.usbManager (USB Management)](../../reference/apis-basic-services-kit/js-apis-usbManager.md), the libusb third-party library, and so on.

## When Multiple Driver Abilities Are Configured for the Same Peripheral Device Model, Inserting the Device Starts Only One Driver Ability

### Symptom

A peripheral device of a certain model is configured in the "vids" and "pids" lists of multiple driver Abilities, but when the device is connected, only one driver Ability can be bound and started.

### Solution

The driver Ability is designed to allow vendors to develop a single driver application for one or more peripheral device models. The specification does not support deploying multiple driver Abilities for the same peripheral device simultaneously. If such a requirement does exist (for example, an upstream party needs to encapsulate USB functionality and distribute it to multiple downstream applications), you can use the [@ohos.usbManager (USB Management)](../../reference/apis-basic-services-kit/js-apis-usbManager.md) API provided by the USB system service, a third-party library such as libusb, or other similar solutions.