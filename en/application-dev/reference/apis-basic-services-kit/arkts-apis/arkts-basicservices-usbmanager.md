# @ohos.usbManager(USB Manager)

This module provides APIs for managing USB devices, including USB device list query, bulk data transfer, control transfer, and permission control on the host side as well as port management, and function switch and query on the device side. This module can be used to exchange data with USB devices, manage USB device permissions, and dynamically switch the USB device mode.

## How to Use

Perform the following steps when using the APIs with the [USBDevicePipe](arkts-basicservices-usbmanager-usbdevicepipe-i.md) parameter:

**Before use**:

1. Call [usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md) to obtain the USB device list.
2. Call [usbManager.requestRight](arkts-basicservices-usbmanager-requestright-f.md) to request the temporary
device access permission.
3. Call [usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md) to obtain **USBDevicePipe**
as an input parameter.

**After use**:

Call [usbManager.closePipe](arkts-basicservices-usbmanager-closepipe-f.md) to disable the USB connection channel.

![usbManager](../../../reference/figures/usbManager.png)

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [bulkTransfer](arkts-basicservices-usbmanager-bulktransfer-f.md) | After the bulk transfer is complete, the size of the transferred or received data block is returned. This API uses a promise to return the result. Compared with **usbSubmitTransfer**, **bulkTransfer** is suitable for simple bulk transfer. It directly transfers data and endpoints through independent parameters and uses a promise to return the result. **usbSubmitTransfer** is suitable for scenarios that require more flexible control. It encapsulates parameters in the **UsbDataTransferParams** object, supports asynchronous callback, and allows you to cancel a transfer request using **usbCancelTransfer**. |
| [cancelAccessoryRight](arkts-basicservices-usbmanager-cancelaccessoryright-f.md) | Cancels the permission of the current app to access USB accessories. This API is called to cancel the accessory access permission requested using **requestAccessoryRight()**. This API must be used with **requestAccessoryRight()** in pairs. |
| [claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md) | Claims a USB device interface. After this API is called successfully, the app obtains exclusive control over the interface and can perform operations such as data transfer. Other apps cannot access the interface. After using the interface, call [releaseInterface](arkts-basicservices-usbmanager-releaseinterface-f.md) to release the control over the interface. |
| [claimInterfaceExclusive](arkts-basicservices-usbmanager-claiminterfaceexclusive-f.md) | Claims a USB device interface exclusively. When this API is called, the system checks whether the specified USB interface has been claimed by another process to avoid conflicts during declaration. If **force** is set to **true**, the operating system first releases the interface from the kernel driver and then grants control to the calling app. After the interface is claimed exclusively, other processes can still claim the same interface by calling [usbManager.claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md). You can use the **onConflict** callback to receive such conflict notifications. |
| [closeAccessory](arkts-basicservices-usbmanager-closeaccessory-f.md) | Closes the accessory file descriptor. |
| [closePipe](arkts-basicservices-usbmanager-closepipe-f.md) | Closes the USB device pipe. |
| [connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md) | Connects to the USB device based on the device information returned by **getDevices()**. After the API is called successfully, a device connection channel is established for subsequent data transmission and device control operations. After using the channel, you can call [usbManager.closePipe](arkts-basicservices-usbmanager-closepipe-f.md) to disable the USB connection channel. If the USB service is abnormal, **undefined** is returned. Check whether the return value of the API is empty. |
| [controlTransfer](arkts-basicservices-usbmanager-controltransfer-f.md) | Performs control transfer. This API uses a promise to return the result. |
| [getAccessoryList](arkts-basicservices-usbmanager-getaccessorylist-f.md) | Obtains the list of USB accessories connected to the host. |
| [getDevices](arkts-basicservices-usbmanager-getdevices-f.md) | Obtains the list of USB devices connected to the host. After the API is called successfully, a list of connected devices is returned, including the device name, manufacturer, and product information. |
| [getFileDescriptor](arkts-basicservices-usbmanager-getfiledescriptor-f.md) | Obtains a file descriptor. If the USB service is abnormal, an error code may be returned. Check whether the return value of the API is empty or check the error code. |
| [getRawDescriptor](arkts-basicservices-usbmanager-getrawdescriptor-f.md) | Obtains a raw USB descriptor. If the USB service is abnormal, **undefined** may be returned. Check whether the return value of the API is empty. |
| [hasAccessoryRight](arkts-basicservices-usbmanager-hasaccessoryright-f.md) | Checks whether the app has the permission to access USB accessories. |
| [hasRight](arkts-basicservices-usbmanager-hasright-f.md) | Checks whether the application has the permission to access the device. |
| [openAccessory](arkts-basicservices-usbmanager-openaccessory-f.md) | Obtains the accessory handle and opens the accessory file descriptor. Then, the host can communicate with the accessory through the **read** and **write** APIs provided by Core File Kit. After using the accessory, call [closeAccessory](arkts-basicservices-usbmanager-closeaccessory-f.md) to close the file descriptor. |
| [releaseInterface](arkts-basicservices-usbmanager-releaseinterface-f.md) | Releases the claimed communication interface. |
| [removeRight](arkts-basicservices-usbmanager-removeright-f.md) | Removes the permission for an app to access the device. System apps are granted the device access permission by default, and calling this API will not revoke the permission. |
| [requestAccessoryRight](arkts-basicservices-usbmanager-requestaccessoryright-f.md) | Requests the permission to access USB accessories for a specified app. This API uses a promise to return the result. |
| [requestRight](arkts-basicservices-usbmanager-requestright-f.md) | Requests the temporary permission for the app to access the device. This API uses a promise to return the result. System apps are granted the device access permission by default, and you do not need to call this API to request the permission. |
| [resetUsbDevice](arkts-basicservices-usbmanager-resetusbdevice-f.md) | Resets the USB device. This API is applicable to scenarios where the USB device needs to be restored due to communication exceptions. For example, the device needs to be reinitialized after a device firmware upgrade, the device status needs to be restored when it is abnormal, or the device status needs to be reset during debugging. After this API is successfully called, the device is reset to the initial state. The previously set configurations and interface settings are cleared, and the device needs to be reinitialized. |
| [setConfiguration](arkts-basicservices-usbmanager-setconfiguration-f.md) | Sets the device configuration. This API can be used to switch the working mode of a multi-functional USB device. For example, it can be used to switch to the printing mode or scanning mode for a device combining the printer and scanner functions, or switch a device from a low-power configuration to a high-power configuration to enable all functions. After the API is successfully called, the device configuration is switched to the specified configuration. Subsequent data transfer and device operations are performed based on the new configuration. |
| [setInterface](arkts-basicservices-usbmanager-setinterface-f.md) | Sets a USB interface. After the API is successfully called, the specified alternate setting is switched for the interfaces, and the endpoint configuration changes accordingly to match the transmission type. |
| [usbCancelTransfer](arkts-basicservices-usbmanager-usbcanceltransfer-f.md) | Cancels an asynchronous USB data transfer request. This API can be used to proactively terminate an ongoing USB data transfer, for example, when a user manually cancels a long-time data transfer, when an error occurs after a transfer times out, or when the current transfer needs to be terminated during an app switch. |
| [usbControlTransfer](arkts-basicservices-usbmanager-usbcontroltransfer-f.md) | Performs control transfer. After the control command is transferred successfully, the size of the transferred or received data block is returned. This API can be used to exchange control commands with a USB device, such as obtaining the device descriptor, setting the device address, sending vendor-defined commands, and configuring HID device features. This API uses a promise to return the result. |
| [usbSubmitTransfer](arkts-basicservices-usbmanager-usbsubmittransfer-f.md) | Submits an asynchronous transfer request. The result is returned immediately after this API is called. This API uses a callback to rerturn the actual read/write operation result. You can call [usbCancelTransfer](arkts-basicservices-usbmanager-usbcanceltransfer-f.md) to cancel an asynchronous transfer request. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [addAccessoryRight](arkts-basicservices-usbmanager-addaccessoryright-f-sys.md) | Adds the permission to apps for accessing USB accessories. This API can be used by system apps to grant third-party apps the permission to access USB accessories. **usbManager.requestAccessoryRight** triggers a dialog box to request user authorization. **addAccessoryRight** does not trigger a dialog box but directly adds the device accessory access permission for the app. The authorization takes effect immediately and is stored persistently. It remains valid even after the device is rebooted. The authorization applies to the specified USB device accessory instance. Multiple apps can obtain the access permission for the same accessory at the same time. Unlike **requestAccessoryRight**, **addAccessoryRight** does not require user interaction and is suitable for scenarios where the system app automatically grants authorization. |
| [addDeviceAccessRight](arkts-basicservices-usbmanager-adddeviceaccessright-f-sys.md) | Adds the authorization for the app to access the device. System applications are granted the device access permission by default, and calling this API will not revoke the permission. This API can be used by system settings apps or device management apps to grant third-party apps the permission to access USB devices. The authorization takes effect immediately and is stored persistently. It remains valid even after the device is rebooted. The authorization applies to the specified USB device instance. Multiple apps can obtain the access permission for the same device at the same time. |
| [getCurrentFunctions](arkts-basicservices-usbmanager-getcurrentfunctions-f-sys.md) | Obtains the numeric mask combination for the USB function list in Device mode. This API can be used to check the USB function state, confirm the function configuration, or compare the status before and after function switching. When the developer mode is disabled, **undefined** is returned if no device is connected. Check whether the return value of the API is empty. |
| [getDeviceFunctions](arkts-basicservices-usbmanager-getdevicefunctions-f-sys.md) | Obtains the numeric mask combination for the USB function list in Device mode. This API can be used to check the USB function state, confirm the function configuration, or compare the status before and after function switching. When the developer mode is disabled, **undefined** is returned if no device is connected. Check whether the return value of the API is empty. |
| [getFunctionsFromString](arkts-basicservices-usbmanager-getfunctionsfromstring-f-sys.md) | Converts the USB function list in the string format to a numeric mask in Device mode. This API can be used to convert the USB function list in the string format in the configuration file or input by the user to a numeric mask used internally by the system, so that USB functions can be set by calling APIs such as **setDeviceFunctions**. |
| [getPortList](arkts-basicservices-usbmanager-getportlist-f-sys.md) | Obtains the list of all physical USB ports. This API can be used to enumerate USB ports, perform port management, diagnose the device connection status, or query the port configuration information. When the developer mode is disabled, **undefined** is returned if no device is connected. Check whether the return value of the API is empty. |
| [getPorts](arkts-basicservices-usbmanager-getports-f-sys.md) | Obtains the list of all physical USB ports. This API can be used to enumerate USB ports, perform port management, diagnose the device connection status, or query the port configuration information. When the developer mode is disabled, **undefined** is returned if no device is connected. Check whether the return value of the API is empty. |
| [getPortSupportModes](arkts-basicservices-usbmanager-getportsupportmodes-f-sys.md) | Obtains the mask combination for the supported mode list of a given USB port. This method is applicable when the system app needs to query the USB-C port capabilities to determine whether a specific mode (such as UFP, DFP, or DRP) is supported. When the developer mode is disabled, **undefined** is returned if no device is connected. Check whether the return value of the API is empty. For details about the enumerated values, see [PortModeType](arkts-basicservices-usbmanager-portmodetype-e-sys.md). |
| [getStringFromFunctions](arkts-basicservices-usbmanager-getstringfromfunctions-f-sys.md) | Converts the USB function list in the numeric mask format to a string in Device mode. This API is applicable to scenarios where the USB function state needs to be displayed or saved as a string, for example, recording the current function configuration in logs or displaying the current function on the UI. |
| [getSupportedModes](arkts-basicservices-usbmanager-getsupportedmodes-f-sys.md) | Obtains the mask combination for the supported mode list of a given USB port. This method is applicable when the system app needs to query the USB-C port capabilities to determine whether a specific mode (such as UFP, DFP, or DRP) is supported. The return value is the mask combination of **PortModeType**. You can determine whether the port supports a specific mode using bitwise operations. The **PortModeType** values are as follows: **NONE (0)**: no mode; **UFP (1)**: upstream port mode, **dataRole** is **DEVICE**; **DFP (2)**: downstream port mode, **dataRole** is **HOST**; **DRP (3)**: dual-role mode, which can switch between **UFP** and **DFP**; **NUM_MODES (4)**: not supported currently. You can determine whether the port supports the combination of power roles and data transfer roles based on the return value. |
| [setCurrentFunctions](arkts-basicservices-usbmanager-setcurrentfunctions-f-sys.md) | Sets the current USB function list in Device mode. This API uses a promise to return the result. After this API is successfully called, the USB functions of the device will be switched to the specified function list. This API is applicable to scenarios where the system app needs to dynamically switch the USB functions of the device and configure the working mode of the device. |
| [setDeviceFunctions](arkts-basicservices-usbmanager-setdevicefunctions-f-sys.md) | Sets the current USB function list in Device mode. This API uses a promise to return the result. After this API is successfully called, the USB functions of the device will be switched to the specified function list. Some USB functions may not be supported by the current device. Before setting the USB functions, you are advised to query the list of functions supported by the device. When developer mode is disabled, the operation may fail if no device is connected. In this case, an exception is thrown. Function switching triggers re-enumeration of the USB devices, and the connected host may need to re-identify the device. Multiple functions can be set through bitwise operations. However, some functions may be mutually exclusive or have different priorities. For details about the restrictions, see the device specifications. The function setting may fail due to device incompatibility, insufficient permissions, or system restrictions. For details, see the error code description. |
| [setPortRoles](arkts-basicservices-usbmanager-setportroles-f-sys.md) | Sets the roles of a specified port, including **powerRole** (for charging) and **dataRole** (for data transfer). This API uses a promise to return the result. After this API is successfully called, the port role will be switched to the specified role. This API can be used to dynamically switch the role of a USB port. When developer mode is disabled, the operation may fail if no device is connected. In this case, an exception is thrown. |
| [setPortRoleTypes](arkts-basicservices-usbmanager-setportroletypes-f-sys.md) | Sets the role types of a specified port, including **powerRole** (for charging) and **dataRole** (for data transfer). This API uses a promise to return the result. After the API is successfully called, the power role and data transfer role of the port are switched to the specified roles. This API can be used to dynamically switch the role of a USB port. When developer mode is disabled, the operation may fail if no device is connected. In this case, an exception is thrown. For details about role constraints, see [USBPortStatus](arkts-basicservices-usbmanager-usbportstatus-i-sys.md). |
| [usbFunctionsFromString](arkts-basicservices-usbmanager-usbfunctionsfromstring-f-sys.md) | Converts the USB function list in the string format to a numeric mask in Device mode. This API can be used to convert the USB function list in the string format in the configuration file or input by the user to a numeric mask used internally by the system, so that USB functions can be set by calling APIs such as **setDeviceFunctions**. |
| [usbFunctionsToString](arkts-basicservices-usbmanager-usbfunctionstostring-f-sys.md) | Converts the USB function list in the numeric mask format to a string in Device mode. This API is applicable to scenarios where the USB function state needs to be displayed or saved as a string, for example, recording the current function configuration in logs or displaying the current function on the UI. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [InterfaceConflictInfo](arkts-basicservices-usbmanager-interfaceconflictinfo-i.md) | Describes the conflict information when the USB interface that has been exclusively claimed is claimed by another process in non-exclusive mode by calling [usbManager.claimInterfaceExclusive](arkts-basicservices-usbmanager-claiminterfaceexclusive-f.md). |
| [SubmitTransferCallback](arkts-basicservices-usbmanager-submittransfercallback-i.md) | Transfers USB data packets in an asynchronous manner. |
| [USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md) | Describes the USB accessory information. |
| [USBAccessoryHandle](arkts-basicservices-usbmanager-usbaccessoryhandle-i.md) | Defines a USB accessory handle, including the accessory file descriptor. This API is used to communicate with the accessory through the **read** or **write** API provided by Core File Kit. |
| [USBConfiguration](arkts-basicservices-usbmanager-usbconfiguration-i.md) | Represents the USB configuration. One [USBDevice](arkts-basicservices-usbmanager-usbdevice-i.md) can contain multiple **USBConfig** instances. |
| [USBControlParams](arkts-basicservices-usbmanager-usbcontrolparams-i.md) | Control transfer parameters. |
| [UsbDataTransferParams](arkts-basicservices-usbmanager-usbdatatransferparams-i.md) | Defines a USB data transfer parameter object, which contains all parameters required for USB data transfer. It is used by the **usbSubmitTransfer** and **usbCancelTransfer** APIs to initiate transfer requests. |
| [USBDevice](arkts-basicservices-usbmanager-usbdevice-i.md) | Represents the USB device information. |
| [USBDevicePipe](arkts-basicservices-usbmanager-usbdevicepipe-i.md) | Define a USB device pipe, which is used to determine the bus address and device address. |
| [USBDeviceRequestParams](arkts-basicservices-usbmanager-usbdevicerequestparams-i.md) | Describes control transfer parameters. |
| [USBEndpoint](arkts-basicservices-usbmanager-usbendpoint-i.md) | Defines a USB endpoint, which is used for data transfer between the host and the USB device. You can obtain the USB endpoint through [USBInterface](arkts-basicservices-usbmanager-usbinterface-i.md). |
| [USBInterface](arkts-basicservices-usbmanager-usbinterface-i.md) | Represents a USB interface. One [USBConfiguration](arkts-basicservices-usbmanager-usbconfiguration-i.md) object can contain multiple **USBInterface** instances, each providing a specific function. |
| [UsbIsoPacketDescriptor](arkts-basicservices-usbmanager-usbisopacketdescriptor-i.md) | Describes packet information returned in real time by the transfer callback. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [USBPort](arkts-basicservices-usbmanager-usbport-i-sys.md) | Represents a USB port. |
| [USBPortStatus](arkts-basicservices-usbmanager-usbportstatus-i-sys.md) | Enumerates USB port roles. **currentMode** indicates the current USB mode of the port. The value must be within the range of **supportedModes** of the USB port. **currentPowerRole** indicates the current power role, and **currentDataRole** indicates the current data transfer role. These fields are generally set as follows: In DFP mode, **dataRole** is **HOST**, and **powerRole** is **SOURCE**. In UFP mode, **dataRole** is **DEVICE**, and **powerRole** is **SINK**. The port status change is subject to hardware and system constraints. Some mode or role combinations may not be supported. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [USBControlRequestType](arkts-basicservices-usbmanager-usbcontrolrequesttype-e.md) | Enumerates control request types. Each type indicates a specific USB control request command such as obtaining the descriptor or setting the address. |
| [UsbEndpointTransferType](arkts-basicservices-usbmanager-usbendpointtransfertype-e.md) | Enumerates USB transfer types. |
| [USBRequestDirection](arkts-basicservices-usbmanager-usbrequestdirection-e.md) | Enumerates request directions. |
| [USBRequestTargetType](arkts-basicservices-usbmanager-usbrequesttargettype-e.md) | Enumerates request target types. |
| [UsbTransferFlags](arkts-basicservices-usbmanager-usbtransferflags-e.md) | Enumerates USB transfer flags. |
| [UsbTransferStatus](arkts-basicservices-usbmanager-usbtransferstatus-e.md) | Enumerates the status code returned after data processing is complete. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [DataRoleType](arkts-basicservices-usbmanager-dataroletype-e-sys.md) | Enumerates data role types. |
| [FunctionType](arkts-basicservices-usbmanager-functiontype-e-sys.md) | Enumerates USB device function types. |
| [PortModeType](arkts-basicservices-usbmanager-portmodetype-e-sys.md) | Enumerates USB port mode types. |
| [PowerRoleType](arkts-basicservices-usbmanager-powerroletype-e-sys.md) | Enumerates power role types. |
<!--DelEnd-->
