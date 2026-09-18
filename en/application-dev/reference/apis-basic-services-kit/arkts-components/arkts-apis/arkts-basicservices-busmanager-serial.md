# @ohos.busManager.serial(Serial Port Management)

This module provides APIs for serial port management, which are applicable to scenarios where data needs to be exchanged with serial port devices, such as industrial control, sensor data collection, and embedded device communication. This module provides functions such as obtaining the serial port list, opening and closing serial ports, reading and writing data, and managing hardware flow control signals. It helps you easily communicate with external serial port devices, improving device interconnection efficiency.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

## Modules to Import

```TypeScript
import { serial } from '@kit.BasicServicesKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getSerialPortList](arkts-basicservices-serial-getserialportlist-f.md) | Obtains the serial port list. This API uses a promise to return the result, which is a list of [SerialPort](arkts-basicservices-serial-serialport-i.md) objects. This API is used to identify available serial port devices in scenarios such as industrial device connection, IoT device management, and embedded system debugging. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [addPortAuthorization](arkts-basicservices-serial-addportauthorization-f-sys.md) | Adds the authorization for the app to access the serial port. This function associates the token ID of an app with the ID of a serial port device to enable the app to access the serial port. This function can be used by a system management app to grant serial port access permission to a third-party app. For example, a device management tool can use this function to grant serial port access permission to an industrial data collection app. This function is available only to system apps that display a dialog box for serial port authorization. After the user grants the permission, the permission information is persistently stored. This API uses a promise to return the result. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [SerialConfigs](arkts-basicservices-serial-serialconfigs-i.md) | Defines the communication parameters of the serial port. |
| [SerialPort](arkts-basicservices-serial-serialport-i.md) | Defines a serial port object, which provides information about the serial port device and the communication capability. |
| [SerialPortInfo](arkts-basicservices-serial-serialportinfo-i.md) | Describes the serial port information. |

### Enums

| Name | Description |
| --- | --- |
| [DataBits](arkts-basicservices-serial-databits-e.md) | Enumerates the number of data bits. |
| [Parity](arkts-basicservices-serial-parity-e.md) | Enumerates the number of parity bits. |
| [StopBits](arkts-basicservices-serial-stopbits-e.md) | Enumerates the number of stop bits. |
