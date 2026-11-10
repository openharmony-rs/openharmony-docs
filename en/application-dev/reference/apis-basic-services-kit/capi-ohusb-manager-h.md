# ohusb_manager.h

<!--Kit: Basic Services Kit-->
<!--Subsystem: USB-->
<!--Owner: @hwymlgitcode-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=c96dc24f73db98316afa940d428e0b50eda355cb translatedAt=2026-11-09T10:21:30.303Z pushedAt=2026-11-09T10:54:20.117Z nl=1 -->

## Overview

Declares the C APIs for USB device management.

**File to include:** <BasicServicesKit/ohusb_manager.h>

**Library:** libohusb_manager.so

**System capability**: SystemCapability.USB.USBManager

**Since:** 26.0.1

**Related module:** [UsbManager](capi-usbmanager.md)

## Summary

### Structs

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [OH_UsbManager_UsbEndpoint](capi-usbmanager-oh-usbmanager-usbendpoint.md) | OH_UsbManager_UsbEndpoint | Defines a USB endpoint used to send or receive data. The endpoint is obtained from [OH_UsbManager_UsbInterface](capi-usbmanager-oh-usbmanager-usbinterface.md). |
| [OH_UsbManager_UsbInterface](capi-usbmanager-oh-usbmanager-usbinterface.md) | OH_UsbManager_UsbInterface | Defines a USB interface. An [OH_UsbManager_UsbConfig](capi-usbmanager-oh-usbmanager-usbconfig.md) can contain multiple **OH_UsbManager_UsbInterface** instances, each providing a specific function. |
| [OH_UsbManager_UsbConfig](capi-usbmanager-oh-usbmanager-usbconfig.md) | OH_UsbManager_UsbConfig | Defines a USB configuration. An [OH_UsbManager_UsbDevice](capi-usbmanager-oh-usbmanager-usbdevice.md) can contain multiple **OH_UsbManager_UsbConfig** instances. |
| [OH_UsbManager_UsbDevice](capi-usbmanager-oh-usbmanager-usbdevice.md) | OH_UsbManager_UsbDevice | Defines a flattened representation of a USB device. |
| [OH_UsbManager_UsbPipe](capi-usbmanager-oh-usbmanager-usbpipe.md) | OH_UsbManager_UsbPipe | Defines a USB device pipe used to communicate with an opened device. |

### Enums

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [OH_UsbManager_ErrorCode](#oh_usbmanager_errorcode) | OH_UsbManager_ErrorCode | Enumerates the error codes of the USB manager. |
| [OH_UsbManager_RequestDirection](#oh_usbmanager_requestdirection) | OH_UsbManager_RequestDirection | Enumerates the USB request directions. |

### Functions

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [OH_UsbManager_ErrorCode OH_UsbManager_GetUsbDeviceList(OH_UsbManager_UsbDevice **devices, uint32_t *deviceCount)](#oh_usbmanager_getusbdevicelist) | - | Obtains the list of all connected USB devices. The caller must call [OH_UsbManager_FreeUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_freeusbdevicelist) to release the returned array. |
| [void OH_UsbManager_FreeUsbDeviceList(OH_UsbManager_UsbDevice *devices, uint32_t deviceCount)](#oh_usbmanager_freeusbdevicelist) | - | Releases the device array previously returned by [OH_UsbManager_GetUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_getusbdevicelist). After the call, the pointer becomes invalid and must not be used again. Passing null or **0** is a safe null operation. |
| [OH_UsbManager_ErrorCode OH_UsbManager_ConnectDevice(const OH_UsbManager_UsbDevice *device, OH_UsbManager_UsbPipe *pipe)](#oh_usbmanager_connectdevice) | - | Connects a USB device and opens a pipe for communication. The returned pipe must be closed by calling [OH_UsbManager_ClosePipe](capi-ohusb-manager-h.md#oh_usbmanager_closepipe) to avoid resource leaks. Only the **busNum** and **devAddress** fields in the device struct are required; other fields are ignored. |
| [OH_UsbManager_ErrorCode OH_UsbManager_HasPermission(const char *deviceName, bool *result)](#oh_usbmanager_haspermission) | - | Checks whether the app has permission to access the specified device. |
| [typedef void (\*OH_UsbManager_PermissionCallback)(OH_UsbManager_ErrorCode errorCode, bool result, void *userContext)](#oh_usbmanager_permissioncallback) | OH_UsbManager_PermissionCallback | Defines a pointer to the callback used to return the result of [OH_UsbManager_RequestPermission](capi-ohusb-manager-h.md#oh_usbmanager_requestpermission). |
| [OH_UsbManager_ErrorCode OH_UsbManager_RequestPermission(const char *deviceName, OH_UsbManager_PermissionCallback callback, void *userContext)](#oh_usbmanager_requestpermission) | - | Asynchronously requests the permission to access the specified USB device. This may trigger a system dialog box asking the user whether to grant authorization. The function returns a result immediately using the callback. |
| [OH_UsbManager_ErrorCode OH_UsbManager_GetFileDescriptor(const OH_UsbManager_UsbPipe *pipe, int32_t *fd)](#oh_usbmanager_getfiledescriptor) | - | Obtains the file descriptor of an opened USB device pipe. The FD can be used for low-level USB transfers based on ioctl. |
| [OH_UsbManager_ErrorCode OH_UsbManager_ClosePipe(const OH_UsbManager_UsbPipe *pipe)](#oh_usbmanager_closepipe) | - | Closes a USB device pipe and releases the underlying resources. The pipe must be obtained from [OH_UsbManager_ConnectDevice](capi-ohusb-manager-h.md#oh_usbmanager_connectdevice). |

## Enum Description

### OH_UsbManager_ErrorCode

```c
enum OH_UsbManager_ErrorCode
```

**Description**

Enumerates the error codes of the USB manager.

**Since:** 26.0.1

| Enum Item | Description |
| -- | -- |
| OH_USBMANAGER_SUCCESS = 0 | Operation succeeded.<br>**Since:** 26.0.1 |
| OH_USBMANAGER_ERROR_PERMISSION_DENIED = 14400001 | Permission denied.<br>**Since:** 26.0.1 |
| OH_USBMANAGER_ERROR_SERVICE_EXCEPTION = 14400004 | Service exception.<br>**Since:** 26.0.1 |
| OH_USBMANAGER_ERROR_NO_DEVICE = 14400008 | The device does not exist (it may have been disconnected).<br>**Since:** 26.0.1 |
| OH_USBMANAGER_ERROR_NO_MEMORY = 14400009 | Insufficient memory.<br>**Since:** 26.0.1 |
| OH_USBMANAGER_ERROR_IO_ERROR = 14400012 | I/O error during transmission.<br>**Since:** 26.0.1 |
| OH_USBMANAGER_ERROR_INVALID_PARAMETER = 14400014 | Invalid parameter. A null pointer is passed to a parameter that must not be null.<br>**Since:** 26.0.1 |

### OH_UsbManager_RequestDirection

```c
enum OH_UsbManager_RequestDirection
```

**Description**

Enumerates the USB request directions.

**Since:** 26.0.1

| Enum Item | Description |
| -- | -- |
| OH_USBMANAGER_REQUEST_DIR_TO_DEVICE = 0 | Request used to write data from the host to the device.<br>**Since:** 26.0.1 |
| OH_USBMANAGER_REQUEST_DIR_FROM_DEVICE = 0x80 | Request used to read data from the device to the host.<br>**Since:** 26.0.1 |


## Function Description

### OH_UsbManager_GetUsbDeviceList()

```c
OH_UsbManager_ErrorCode OH_UsbManager_GetUsbDeviceList(OH_UsbManager_UsbDevice **devices, uint32_t *deviceCount)
```

**Description**

Obtains the list of all connected USB devices. The caller must call [OH_UsbManager_FreeUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_freeusbdevicelist) to release the returned array.

**Since:** 26.0.1

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_UsbManager_UsbDevice](capi-usbmanager-oh-usbmanager-usbdevice.md) **devices | [out] Pointer to the second-level pointer to the array of [OH_UsbManager_UsbDevice](capi-usbmanager-oh-usbmanager-usbdevice.md). On success, the function allocates the array and all internal string buffers. The caller must not free individual fields; use [OH_UsbManager_FreeUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_freeusbdevicelist) instead. Must not be null. |
| uint32_t *deviceCount | [out] Pointer to the number of returned devices. On success, this value is set to the number of elements in the array. A value of 0 indicates that no device is currently available. Must not be null. |

**Resource release:** [OH_UsbManager_FreeUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_freeusbdevicelist)

**Return**

| Type | Description |
| -- | -- |
| [OH_UsbManager_ErrorCode](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) | [OH_USBMANAGER_SUCCESS](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) indicates that the operation is successful.      <br>[OH_USBMANAGER_ERROR_SERVICE_EXCEPTION](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) indicates that the USB service is unavailable. Possible cause: USB service fault, for example, the service is not running or stops unexpectedly.      <br>[OH_USBMANAGER_ERROR_NO_MEMORY](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) indicates that memory allocation for the device array or strings failed. Possible cause: insufficient system memory or too many connected devices. Handling suggestion: release unused memory and try again.      <br>[OH_USBMANAGER_ERROR_INVALID_PARAMETER](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) indicates that devices or deviceCount is NULL. Possible cause: required parameters are not provided. Handling suggestion: pass valid non-null pointers. |

### OH_UsbManager_FreeUsbDeviceList()

```c
void OH_UsbManager_FreeUsbDeviceList(OH_UsbManager_UsbDevice *devices, uint32_t deviceCount)
```

**Description**

Releases the device array previously returned by [OH_UsbManager_GetUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_getusbdevicelist). After the call, the pointer becomes invalid and must not be used again. Passing null or a count of 0 is a safe no-op.

**Since:** 26.0.1

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_UsbManager_UsbDevice](capi-usbmanager-oh-usbmanager-usbdevice.md) *devices | [in] Pointer to the array returned by [OH_UsbManager_GetUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_getusbdevicelist). |
| uint32_t deviceCount | [in] Number of elements in the array, returned by [OH_UsbManager_GetUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_getusbdevicelist). |

### OH_UsbManager_ConnectDevice()

```c
OH_UsbManager_ErrorCode OH_UsbManager_ConnectDevice(const OH_UsbManager_UsbDevice *device, OH_UsbManager_UsbPipe *pipe)
```

**Description**

Connects a USB device and opens a pipe for communication. The returned pipe must be closed by calling [OH_UsbManager_ClosePipe](capi-ohusb-manager-h.md#oh_usbmanager_closepipe) to avoid resource leaks. Only the **busNum** and **devAddress** fields in the device struct are required; other fields are ignored.

**Since:** 26.0.1

**Parameters**

| Parameter | Description |
| -- | -- |
| [const OH_UsbManager_UsbDevice](capi-usbmanager-oh-usbmanager-usbdevice.md) *device | [in] Pointer to the [OH_UsbManager_UsbDevice](capi-usbmanager-oh-usbmanager-usbdevice.md) to connect. Must not be null. |
| [OH_UsbManager_UsbPipe](capi-usbmanager-oh-usbmanager-usbpipe.md) *pipe | [out] Pointer to the [OH_UsbManager_UsbPipe](capi-usbmanager-oh-usbmanager-usbpipe.md) used to receive the handle on success. Must not be null. |

**Return**

| Type | Description |
| -- | -- |
| [OH_UsbManager_ErrorCode](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) | [OH_USBMANAGER_SUCCESS](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) indicates that the device is connected successfully.      <br>[OH_USBMANAGER_ERROR_PERMISSION_DENIED](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) indicates that the application lacks the device access permission.      <br>Possible cause: the access permission has not been requested, has been revoked, or the user has denied the request.      <br>Handling suggestion: call [OH_UsbManager_RequestPermission](capi-ohusb-manager-h.md#oh_usbmanager_requestpermission) to request the access permission.      <br>[OH_USBMANAGER_ERROR_SERVICE_EXCEPTION](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) indicates that the USB service fails to open the device.      <br>Possible cause: a USB service fault (for example, the service is not running or stops unexpectedly), or the passed device is invalid.      <br>Handling suggestion: if the device is invalid, obtain valid device data by calling [OH_UsbManager_GetUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_getusbdevicelist)      <br>and retry.      <br>[OH_USBMANAGER_ERROR_IO_ERROR](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) indicates that the device cannot be opened (for example, it has been disconnected or an I/O failure occurs).      <br>Possible cause: the device has been disconnected or an I/O error occurs on the USB bus.      <br>Handling suggestion: check the physical connection and device status, and retry.      <br>[OH_USBMANAGER_ERROR_INVALID_PARAMETER](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) indicates that device or pipe is NULL.      <br>Possible cause: the required parameter is not provided. Handling suggestion: pass a valid non-null pointer. |

### OH_UsbManager_HasPermission()

```c
OH_UsbManager_ErrorCode OH_UsbManager_HasPermission(const char *deviceName, bool *result)
```

**Description**

Checks whether the application has permission to access the specified device.

**Since:** 26.0.1

**Parameters**

| Parameter | Description |
| -- | -- |
| const char *deviceName | [in] Device name in the format of \< bus number \>-\< device address \>. It must not be null. |
| bool *result | [out] Pointer to the result. The value is true if the application has been granted permission to access the device; false if the permission is not granted or not requested. It must not be null. |

**Return**

| Type | Description |
| -- | -- |
| [OH_UsbManager_ErrorCode](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) | [OH_USBMANAGER_SUCCESS](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) indicates that the operation is successful.      <br>[OH_USBMANAGER_ERROR_SERVICE_EXCEPTION](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) indicates that the USB service is unavailable.      <br>Possible cause: a USB service fault (for example, the service is not running or stops unexpectedly), or the passed deviceName is invalid.      <br>Handling suggestion: if deviceName is invalid, call [OH_UsbManager_GetUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_getusbdevicelist) first to obtain a valid device name, and then retry.      <br>[OH_USBMANAGER_ERROR_INVALID_PARAMETER](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) indicates that deviceName or result is NULL.      <br>Possible cause: a required parameter is not provided. Handling suggestion: pass a valid non-null pointer. |

### OH_UsbManager_PermissionCallback()

```c
typedef void (*OH_UsbManager_PermissionCallback)(OH_UsbManager_ErrorCode errorCode, bool result, void *userContext)
```

**Description**

Defines a pointer to the callback used to return the result of [OH_UsbManager_RequestPermission](capi-ohusb-manager-h.md#oh_usbmanager_requestpermission).

**Since:** 26.0.1

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_UsbManager_ErrorCode](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) errorCode | [out] Error code of the request. [OH_USBMANAGER_SUCCESS](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) indicates that the request is completed successfully; other values indicate a service exception. |
| bool result | [out] true if the permission is granted; false if the user rejects the request. This parameter is meaningful only when errorCode is [OH_USBMANAGER_SUCCESS](capi-ohusb-manager-h.md#oh_usbmanager_errorcode). |
| void \*userContext | [out] User context passed through from [OH_UsbManager_RequestPermission](capi-ohusb-manager-h.md#oh_usbmanager_requestpermission). |

### OH_UsbManager_RequestPermission()

```c
OH_UsbManager_ErrorCode OH_UsbManager_RequestPermission(const char *deviceName, OH_UsbManager_PermissionCallback callback, void *userContext)
```

**Description**

Asynchronously requests permission to access the specified USB device. This may trigger a system dialog box asking the user whether to grant authorization. The function returns immediately, and the result is delivered through the callback.

**Since:** 26.0.1

**Parameters**

| Parameter | Description |
| -- | -- |
| const char *deviceName | [in] Device name in the format of \< bus number \>-\< device address \>. It must not be null. |
| [OH_UsbManager_PermissionCallback](capi-ohusb-manager-h.md#oh_usbmanager_permissioncallback) callback | [in] [OH_UsbManager_PermissionCallback](capi-ohusb-manager-h.md#oh_usbmanager_permissioncallback) invoked when the request is complete. Must not be null. |
| void *userContext | [in] Pointer to the user context passed to the callback. Can be null. |

**Return**

| Type | Description |
| -- | -- |
| [OH_UsbManager_ErrorCode](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) | [OH_USBMANAGER_SUCCESS](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) indicates that the request is successfully initiated.      <br>[OH_USBMANAGER_ERROR_SERVICE_EXCEPTION](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) indicates that the service fails to start the request.      <br>Possible cause: USB service fault (for example, the service is not running or stops unexpectedly), or the passed deviceName is invalid.      <br>Handling suggestion: If deviceName is invalid, obtain a valid device name through [OH_UsbManager_GetUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_getusbdevicelist)      <br>and try again.      <br>[OH_USBMANAGER_ERROR_INVALID_PARAMETER](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) indicates that deviceName or callback is NULL.      <br>Possible cause: required parameters are not provided. Handling suggestion: pass valid non-null pointers. |

### OH_UsbManager_GetFileDescriptor()

```c
OH_UsbManager_ErrorCode OH_UsbManager_GetFileDescriptor(const OH_UsbManager_UsbPipe *pipe, int32_t *fd)
```

**Description**

Obtains the file descriptor of an opened USB device pipe. The fd can be used for low-level USB transfers based on ioctl.

**Since:** 26.0.1

**Parameters**

| Parameter | Description |
| -- | -- |
| [const OH_UsbManager_UsbPipe](capi-usbmanager-oh-usbmanager-usbpipe.md) *pipe | [in] Pointer to the [OH_UsbManager_UsbPipe](capi-usbmanager-oh-usbmanager-usbpipe.md) obtained from [OH_UsbManager_ConnectDevice](capi-ohusb-manager-h.md#oh_usbmanager_connectdevice). It must not be null. |
| int32_t *fd | [out] Pointer used to receive the file descriptor on success. It must not be null. |

**Return**

| Type | Description |
| -- | -- |
| [OH_UsbManager_ErrorCode](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) | [OH_USBMANAGER_SUCCESS](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) indicates that the operation is successful.      <br>[OH_USBMANAGER_ERROR_PERMISSION_DENIED](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) indicates that the application lacks the device access permission.      <br>Possible cause: the access permission has not been requested, the permission has been revoked, or the user rejected the request.      <br>Handling suggestion: call [OH_UsbManager_RequestPermission](capi-ohusb-manager-h.md#oh_usbmanager_requestpermission) to request the access permission.      <br>[OH_USBMANAGER_ERROR_SERVICE_EXCEPTION](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) indicates that the pipe is invalid or the service fails.      <br>Possible cause: a USB service fault occurs, or the pipe is not obtained through [OH_UsbManager_ConnectDevice](capi-ohusb-manager-h.md#oh_usbmanager_connectdevice),      <br>or the pipe has been closed. Handling suggestion: if the pipe is invalid or has been closed, obtain a valid opened pipe through      <br>[OH_UsbManager_ConnectDevice](capi-ohusb-manager-h.md#oh_usbmanager_connectdevice) and try again.      <br>[OH_USBMANAGER_ERROR_NO_DEVICE](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) indicates that the device does not exist or has been disconnected.      <br>Possible cause: the device has been unplugged. Handling suggestion: use [OH_UsbManager_GetUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_getusbdevicelist)      <br>to re-enumerate the devices and reconnect.      <br>[OH_USBMANAGER_ERROR_INVALID_PARAMETER](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) indicates that pipe or fd is NULL.      <br>Possible cause: the required parameter is not provided. Handling suggestion: pass in a valid non-null pointer. |

### OH_UsbManager_ClosePipe()

```c
OH_UsbManager_ErrorCode OH_UsbManager_ClosePipe(const OH_UsbManager_UsbPipe *pipe)
```

**Description**

Closes a USB device pipe and releases the underlying resources. The pipe must be obtained from [OH_UsbManager_ConnectDevice](capi-ohusb-manager-h.md#oh_usbmanager_connectdevice).

**Since:** 26.0.1

**Parameters**

| Parameter | Description |
| -- | -- |
| [const OH_UsbManager_UsbPipe](capi-usbmanager-oh-usbmanager-usbpipe.md) *pipe | [in] Pointer to the [OH_UsbManager_UsbPipe](capi-usbmanager-oh-usbmanager-usbpipe.md) to close, which is obtained from [OH_UsbManager_ConnectDevice](capi-ohusb-manager-h.md#oh_usbmanager_connectdevice). It must not be null. |

**Return**

| Type | Description |
| -- | -- |
| [OH_UsbManager_ErrorCode](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) | [OH_USBMANAGER_SUCCESS](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) indicates that the pipe is closed successfully.      <br>[OH_USBMANAGER_ERROR_PERMISSION_DENIED](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) indicates that the application lacks the device access permission.      <br>Possible cause: the access permission has not been requested, the permission has been revoked, or the user rejected the request.      <br>Handling suggestion: call [OH_UsbManager_RequestPermission](capi-ohusb-manager-h.md#oh_usbmanager_requestpermission) to request the access permission.      <br>[OH_USBMANAGER_ERROR_SERVICE_EXCEPTION](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) indicates that the close operation failed.      <br>Possible cause: a USB service fault occurred, or the pipe is invalid or has been closed. Handling suggestion: if the pipe is invalid or has been closed,      <br>obtain a valid open pipe through [OH_UsbManager_ConnectDevice](capi-ohusb-manager-h.md#oh_usbmanager_connectdevice) and try again.      <br>[OH_USBMANAGER_ERROR_INVALID_PARAMETER](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) indicates that pipe is NULL.      <br>Possible cause: a required parameter is not provided. Handling suggestion: pass in a valid non-null pointer. |


