# ohusb_manager.h

## Overview

Declares the C APIs for USB device management.

**Include**: <BasicServicesKit/ohusb_manager.h>

**Library**: libohusb_manager.so

**System capability**: SystemCapability.USB.USBManager

**Since**: 26.1.0

**Related module**: [UsbManager](capi-usbmanager.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_UsbManager_UsbEndpoint](capi-usbmanager-oh-usbmanager-usbendpoint.md) | OH_UsbManager_UsbEndpoint | Defines the USB endpoint from which data is sent or received. An endpoint <br>is obtained from [OH_UsbManager_UsbInterface](capi-usbmanager-oh-usbmanager-usbinterface.md). |
| [OH_UsbManager_UsbInterface](capi-usbmanager-oh-usbmanager-usbinterface.md) | OH_UsbManager_UsbInterface | Defines a USB interface. One [OH_UsbManager_UsbConfig](capi-usbmanager-oh-usbmanager-usbconfig.md) can contain <br>multiple OH_UsbManager_UsbInterface instances, each providing a specific function. |
| [OH_UsbManager_UsbConfig](capi-usbmanager-oh-usbmanager-usbconfig.md) | OH_UsbManager_UsbConfig | Defines a USB configuration. One [OH_UsbManager_UsbDevice](capi-usbmanager-oh-usbmanager-usbdevice.md) can contain multiple <br>**OH_UsbManager_UsbConfig** instances. |
| [OH_UsbManager_UsbDevice](capi-usbmanager-oh-usbmanager-usbdevice.md) | OH_UsbManager_UsbDevice | Defines a flat representation of a USB device. |
| [OH_UsbManager_UsbPipe](capi-usbmanager-oh-usbmanager-usbpipe.md) | OH_UsbManager_UsbPipe | Defines the USB device pipe used to communicate with an opened device. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_UsbManager_ErrorCode](#oh_usbmanager_errorcode) | OH_UsbManager_ErrorCode | Enumerates the USB Manager error codes. |
| [OH_UsbManager_RequestDirection](#oh_usbmanager_requestdirection) | OH_UsbManager_RequestDirection | Enumerates USB request directions. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_UsbManager_ErrorCode OH_UsbManager_GetUsbDeviceList(OH_UsbManager_UsbDevice **devices, uint32_t *deviceCount)](#oh_usbmanager_getusbdevicelist) | - | Obtains the list of all connected USB devices. The caller must release the <br>returned array by calling [OH_UsbManager_FreeUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_freeusbdevicelist). |
| [void OH_UsbManager_FreeUsbDeviceList(OH_UsbManager_UsbDevice *devices, uint32_t deviceCount)](#oh_usbmanager_freeusbdevicelist) | - | Frees a device array previously returned by [OH_UsbManager_GetUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_getusbdevicelist).<br> <br>After this call, the pointer is invalid and must not be used. Passing null or a <br>count of 0 is a safe no-op. |
| [OH_UsbManager_ErrorCode OH_UsbManager_ConnectDevice(const OH_UsbManager_UsbDevice *device, OH_UsbManager_UsbPipe *pipe)](#oh_usbmanager_connectdevice) | - | Connects to a USB device and opens a pipe for communication. The returned pipe must be closed by calling <br>[OH_UsbManager_ClosePipe](capi-ohusb-manager-h.md#oh_usbmanager_closepipe) to avoid resource leaks.<br> <br>Only the **busNum** and **devAddress** fields in the device structure are required. Other fields are ignored. |
| [OH_UsbManager_ErrorCode OH_UsbManager_HasPermission(const char *deviceName, bool *result)](#oh_usbmanager_haspermission) | - | Checks whether the application has permission to access the specified device. |
| [typedef void (\*OH_UsbManager_PermissionCallback)(OH_UsbManager_ErrorCode errorCode, bool result, void *userContext)](#oh_usbmanager_permissioncallback) | OH_UsbManager_PermissionCallback | Defines the callback type used to return the result of <br>[OH_UsbManager_RequestPermission](capi-ohusb-manager-h.md#oh_usbmanager_requestpermission). |
| [OH_UsbManager_ErrorCode OH_UsbManager_RequestPermission(const char *deviceName, OH_UsbManager_PermissionCallback callback, void *userContext)](#oh_usbmanager_requestpermission) | - | Requests permission to access the specified USB device asynchronously. <br>This may trigger a system dialog asking the user for permission. The function <br>returns immediately and the result is delivered via the callback. |
| [OH_UsbManager_ErrorCode OH_UsbManager_GetFileDescriptor(const OH_UsbManager_UsbPipe *pipe, int32_t *fd)](#oh_usbmanager_getfiledescriptor) | - | Obtains the file descriptor for the opened USB device pipe. The fd can be <br>used for low-level ioctl-based USB transfers. |
| [OH_UsbManager_ErrorCode OH_UsbManager_ClosePipe(const OH_UsbManager_UsbPipe *pipe)](#oh_usbmanager_closepipe) | - | Closes the USB device pipe and releases the underlying resources. <br>The pipe must be obtained from [OH_UsbManager_ConnectDevice](capi-ohusb-manager-h.md#oh_usbmanager_connectdevice). |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_UsbManager_PermissionCallback)(OH_UsbManager_ErrorCode errorCode, bool result, void *userContext) | Defines the callback type used to return the result of <br>[OH_UsbManager_RequestPermission](capi-ohusb-manager-h.md#oh_usbmanager_requestpermission).<br>**Since**: 26.1.0 |

## Enum type description

### OH_UsbManager_ErrorCode

```c
enum OH_UsbManager_ErrorCode
```

**Description**

Enumerates the USB Manager error codes.

**Since**: 26.1.0

| Enum item | Description |
| -- | -- |
| OH_USBMANAGER_SUCCESS = 0 | Operation successful.<br>**Since**: 26.1.0 |
| OH_USBMANAGER_ERROR_PERMISSION_DENIED = 14400001 | Permission denied.<br>**Since**: 26.1.0 |
| OH_USBMANAGER_ERROR_SERVICE_EXCEPTION = 14400004 | Service exception.<br>**Since**: 26.1.0 |
| OH_USBMANAGER_ERROR_NO_DEVICE = 14400008 | No such device (it may have been disconnected).<br>**Since**: 26.1.0 |
| OH_USBMANAGER_ERROR_NO_MEMORY = 14400009 | Insufficient memory.<br>**Since**: 26.1.0 |
| OH_USBMANAGER_ERROR_IO_ERROR = 14400012 | Transmission I/O error.<br>**Since**: 26.1.0 |
| OH_USBMANAGER_ERROR_INVALID_PARAMETER = 14400014 | Invalid parameter. A null pointer is passed for a parameter that must not be null.<br>**Since**: 26.1.0 |

### OH_UsbManager_RequestDirection

```c
enum OH_UsbManager_RequestDirection
```

**Description**

Enumerates USB request directions.

**Since**: 26.1.0

| Enum item | Description |
| -- | -- |
| OH_USBMANAGER_REQUEST_DIR_TO_DEVICE = 0 | Request for writing data from the host to the device.<br>**Since**: 26.1.0 |
| OH_USBMANAGER_REQUEST_DIR_FROM_DEVICE = 0x80 | Request for reading data from the device to the host.<br>**Since**: 26.1.0 |


## Function description

### OH_UsbManager_GetUsbDeviceList()

```c
OH_UsbManager_ErrorCode OH_UsbManager_GetUsbDeviceList(OH_UsbManager_UsbDevice **devices, uint32_t *deviceCount)
```

**Description**

Obtains the list of all connected USB devices. The caller must release the <br>returned array by calling [OH_UsbManager_FreeUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_freeusbdevicelist).

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UsbManager_UsbDevice](capi-usbmanager-oh-usbmanager-usbdevice.md) **devices | [out] Double pointer to the array of [OH_UsbManager_UsbDevice](capi-usbmanager-oh-usbmanager-usbdevice.md). On success, <br>the function allocates the array and all internal string buffers. The caller <br>must NOT free individual fields; use [OH_UsbManager_FreeUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_freeusbdevicelist) instead. <br>Must not be null. |
| uint32_t *deviceCount | [out] Pointer to the number of devices returned. On success, this is <br>set to the number of elements in the array. Zero indicates no devices present. <br>Must not be null. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UsbManager_ErrorCode](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) | [OH_USBMANAGER_SUCCESS](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) if the operation is successful.      <br>[OH_USBMANAGER_ERROR_SERVICE_EXCEPTION](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) if the USB service is unavailable. Possible cause:      <br>a USB service fault, for example the service is not running or has stopped unexpectedly.      <br>[OH_USBMANAGER_ERROR_NO_MEMORY](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) if memory allocation for the device array or strings fails.      <br>Possible causes: insufficient system memory or too many connected devices. Suggested action: release      <br>unused memory and retry.      <br>[OH_USBMANAGER_ERROR_INVALID_PARAMETER](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) if devices or deviceCount is NULL. Possible cause:      <br>a required parameter is not provided. Suggested action: pass valid non-null pointers. |

### OH_UsbManager_FreeUsbDeviceList()

```c
void OH_UsbManager_FreeUsbDeviceList(OH_UsbManager_UsbDevice *devices, uint32_t deviceCount)
```

**Description**

Frees a device array previously returned by [OH_UsbManager_GetUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_getusbdevicelist).<br> <br>After this call, the pointer is invalid and must not be used. Passing null or a <br>count of 0 is a safe no-op.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UsbManager_UsbDevice](capi-usbmanager-oh-usbmanager-usbdevice.md) *devices | [in] Pointer to the array returned by [OH_UsbManager_GetUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_getusbdevicelist). |
| uint32_t deviceCount | [in] Number of elements in the array, as returned by <br>[OH_UsbManager_GetUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_getusbdevicelist). |

### OH_UsbManager_ConnectDevice()

```c
OH_UsbManager_ErrorCode OH_UsbManager_ConnectDevice(const OH_UsbManager_UsbDevice *device, OH_UsbManager_UsbPipe *pipe)
```

**Description**

Connects to a USB device and opens a pipe for communication. The returned pipe must be closed by calling <br>[OH_UsbManager_ClosePipe](capi-ohusb-manager-h.md#oh_usbmanager_closepipe) to avoid resource leaks.<br> <br>Only the **busNum** and **devAddress** fields in the device structure are required. Other fields are ignored.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_UsbManager_UsbDevice](capi-usbmanager-oh-usbmanager-usbdevice.md) *device | [in] Pointer to the [OH_UsbManager_UsbDevice](capi-usbmanager-oh-usbmanager-usbdevice.md) to connect. This is an input <br>parameter. This parameter cannot be left empty. |
| [OH_UsbManager_UsbPipe](capi-usbmanager-oh-usbmanager-usbpipe.md) *pipe | [out] Pointer to the [OH_UsbManager_UsbPipe](capi-usbmanager-oh-usbmanager-usbpipe.md), which is used to receive the handle <br>upon successful operation. <br>This is an output parameter. This parameter cannot be left empty. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UsbManager_ErrorCode](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) | [OH_USBMANAGER_SUCCESS](capi-ohusb-manager-h.md#oh_usbmanager_errorcode): The connection is successful.      <br>[OH_USBMANAGER_ERROR_PERMISSION_DENIED](capi-ohusb-manager-h.md#oh_usbmanager_errorcode): The app does not have the permission to access the device.      <br>Possible causes: The access permission has not been requested, the permission has been revoked, or the user      <br>has rejected the request. Suggestion: Call [OH_UsbManager_RequestPermission](capi-ohusb-manager-h.md#oh_usbmanager_requestpermission) to request the access      <br>permission.  <br>[OH_USBMANAGER_ERROR_SERVICE_EXCEPTION](capi-ohusb-manager-h.md#oh_usbmanager_errorcode): The USB service fails to open the device. Possible causes: The  <br>USB service is abnormal (for example, the service is not running or has stopped unexpectedly), or the input  <br>device is invalid. Suggestion: If device is invalid, call [OH_UsbManager_GetUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_getusbdevicelist) to  <br>obtain valid device data and try again.      <br>[OH_USBMANAGER_ERROR_IO_ERROR](capi-ohusb-manager-h.md#oh_usbmanager_errorcode): The device cannot be opened. For example, the device is disconnected      <br>or an I/O error occurs. Possible causes: The device is disconnected or an I/O error occurs on the USB bus.      <br>Suggestion: Check the physical connection and device status, and try again.      <br>[OH_USBMANAGER_ERROR_INVALID_PARAMETER](capi-ohusb-manager-h.md#oh_usbmanager_errorcode): device or pipe is null. Possible cause: Mandatory      <br>parameters are not provided. Suggestion: Pass a valid non-null pointer. |

### OH_UsbManager_HasPermission()

```c
OH_UsbManager_ErrorCode OH_UsbManager_HasPermission(const char *deviceName, bool *result)
```

**Description**

Checks whether the application has permission to access the specified device.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *deviceName | [in] Device name, in the format of <bus number>-<device address>. Must not be null. |
| bool *result | [out] Pointer to receive the result. true if the application has been <br>granted permission to access the device; false if permission has not been <br>granted or has not been requested. Must not be null. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UsbManager_ErrorCode](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) | [OH_USBMANAGER_SUCCESS](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) if the operation is successful.      <br>[OH_USBMANAGER_ERROR_SERVICE_EXCEPTION](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) if the USB service is unavailable. Possible causes:      <br>a USB service fault (for example, the service is not running or has stopped unexpectedly), or the      <br>passed deviceName is invalid. Suggested action: if deviceName is invalid, call      <br>[OH_UsbManager_GetUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_getusbdevicelist) to obtain a valid device name and retry.      <br>[OH_USBMANAGER_ERROR_INVALID_PARAMETER](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) if deviceName or result is NULL. Possible cause:      <br>a required parameter is not provided. Suggested action: pass valid non-null pointers. |

### OH_UsbManager_PermissionCallback()

```c
typedef void (*OH_UsbManager_PermissionCallback)(OH_UsbManager_ErrorCode errorCode, bool result, void *userContext)
```

**Description**

Defines the callback type used to return the result of <br>[OH_UsbManager_RequestPermission](capi-ohusb-manager-h.md#oh_usbmanager_requestpermission).

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_UsbManager_ErrorCode](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) errorCode | [out] Error code of the request. [OH_USBMANAGER_SUCCESS](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) means the <br>request completed normally; other values indicate a service exception. |
| bool result | [out] true if the permission is granted; false if the user denied the request. <br>This parameter is meaningful only when errorCode is [OH_USBMANAGER_SUCCESS](capi-ohusb-manager-h.md#oh_usbmanager_errorcode). |
| void \*userContext | [out] User context passed through from [OH_UsbManager_RequestPermission](capi-ohusb-manager-h.md#oh_usbmanager_requestpermission). |

### OH_UsbManager_RequestPermission()

```c
OH_UsbManager_ErrorCode OH_UsbManager_RequestPermission(const char *deviceName, OH_UsbManager_PermissionCallback callback, void *userContext)
```

**Description**

Requests permission to access the specified USB device asynchronously. <br>This may trigger a system dialog asking the user for permission. The function <br>returns immediately and the result is delivered via the callback.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *deviceName | [in] Device name, in the format of <bus number>-<device address>. Must not be null. |
| [OH_UsbManager_PermissionCallback](capi-ohusb-manager-h.md#oh_usbmanager_permissioncallback) callback | [in] [OH_UsbManager_PermissionCallback](capi-ohusb-manager-h.md#oh_usbmanager_permissioncallback) invoked when the request completes. <br>Must not be null. |
| void *userContext | [in] User context pointer passed to the callback. May be null. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UsbManager_ErrorCode](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) | [OH_USBMANAGER_SUCCESS](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) if the request is successfully initiated.      <br>[OH_USBMANAGER_ERROR_SERVICE_EXCEPTION](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) if the service fails to start the request. Possible      <br>causes: a USB service fault (for example, the service is not running or has stopped unexpectedly), or      <br>the passed deviceName is invalid. Suggested action: if deviceName is invalid, call      <br>[OH_UsbManager_GetUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_getusbdevicelist) to obtain a valid device name and retry.      <br>[OH_USBMANAGER_ERROR_INVALID_PARAMETER](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) if deviceName or callback is NULL. Possible cause:      <br>a required parameter is not provided. Suggested action: pass valid non-null pointers. |

### OH_UsbManager_GetFileDescriptor()

```c
OH_UsbManager_ErrorCode OH_UsbManager_GetFileDescriptor(const OH_UsbManager_UsbPipe *pipe, int32_t *fd)
```

**Description**

Obtains the file descriptor for the opened USB device pipe. The fd can be <br>used for low-level ioctl-based USB transfers.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_UsbManager_UsbPipe](capi-usbmanager-oh-usbmanager-usbpipe.md) *pipe | [in] Pointer to the [OH_UsbManager_UsbPipe](capi-usbmanager-oh-usbmanager-usbpipe.md) obtained from <br>[OH_UsbManager_ConnectDevice](capi-ohusb-manager-h.md#oh_usbmanager_connectdevice). Must not be null. |
| int32_t *fd | [out] Pointer to receive the file descriptor on success. Must not be null. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UsbManager_ErrorCode](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) | [OH_USBMANAGER_SUCCESS](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) if the operation is successful.      <br>[OH_USBMANAGER_ERROR_PERMISSION_DENIED](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) if the app lacks device access permission. Possible causes:      <br>the access permission has not been requested, has been revoked, or the user denied the request. Suggested      <br>action: call [OH_UsbManager_RequestPermission](capi-ohusb-manager-h.md#oh_usbmanager_requestpermission) to request the access permission.      <br>[OH_USBMANAGER_ERROR_SERVICE_EXCEPTION](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) if the pipe is invalid or the service fails. Possible      <br>causes: a USB service fault, or the pipe was not obtained from [OH_UsbManager_ConnectDevice](capi-ohusb-manager-h.md#oh_usbmanager_connectdevice) or      <br>has been closed. Suggested action: if the pipe is invalid or closed, obtain a valid open pipe from      <br>[OH_UsbManager_ConnectDevice](capi-ohusb-manager-h.md#oh_usbmanager_connectdevice) and retry.      <br>[OH_USBMANAGER_ERROR_NO_DEVICE](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) if the device is not present or has been disconnected. Possible      <br>cause: the device has been unplugged. Suggested action: enumerate devices again with      <br>[OH_UsbManager_GetUsbDeviceList](capi-ohusb-manager-h.md#oh_usbmanager_getusbdevicelist) and reconnect.      <br>[OH_USBMANAGER_ERROR_INVALID_PARAMETER](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) if pipe or fd is NULL. Possible cause: a required      <br>parameter is not provided. Suggested action: pass valid non-null pointers. |

### OH_UsbManager_ClosePipe()

```c
OH_UsbManager_ErrorCode OH_UsbManager_ClosePipe(const OH_UsbManager_UsbPipe *pipe)
```

**Description**

Closes the USB device pipe and releases the underlying resources. <br>The pipe must be obtained from [OH_UsbManager_ConnectDevice](capi-ohusb-manager-h.md#oh_usbmanager_connectdevice).

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_UsbManager_UsbPipe](capi-usbmanager-oh-usbmanager-usbpipe.md) *pipe | [in] Pointer to the [OH_UsbManager_UsbPipe](capi-usbmanager-oh-usbmanager-usbpipe.md) obtained from <br>[OH_UsbManager_ConnectDevice](capi-ohusb-manager-h.md#oh_usbmanager_connectdevice) to close. Must not be null. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_UsbManager_ErrorCode](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) | [OH_USBMANAGER_SUCCESS](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) if the pipe is closed successfully.      <br>[OH_USBMANAGER_ERROR_PERMISSION_DENIED](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) if the app lacks device access permission. Possible causes:      <br>the access permission has not been requested, has been revoked, or the user denied the request. Suggested      <br>action: call [OH_UsbManager_RequestPermission](capi-ohusb-manager-h.md#oh_usbmanager_requestpermission) to request the access permission.      <br>[OH_USBMANAGER_ERROR_SERVICE_EXCEPTION](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) if the close operation fails. Possible causes: a USB      <br>service fault, or the pipe is invalid or has already been closed. Suggested action: if the pipe is      <br>invalid or closed, obtain a valid open pipe from [OH_UsbManager_ConnectDevice](capi-ohusb-manager-h.md#oh_usbmanager_connectdevice) and retry.      <br>[OH_USBMANAGER_ERROR_INVALID_PARAMETER](capi-ohusb-manager-h.md#oh_usbmanager_errorcode) if pipe is NULL. Possible cause: a required parameter      <br>is not provided. Suggested action: pass valid non-null pointers. |


