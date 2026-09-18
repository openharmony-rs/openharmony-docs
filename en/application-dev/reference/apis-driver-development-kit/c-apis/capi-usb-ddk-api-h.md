# usb_ddk_api.h

## Overview

Declares the USB DDK APIs used by the USB host to access USB devices.

**Library**: libusb_ndk.z.so

**System capability**: SystemCapability.Driver.USB.Extension

**Since**: 10

**Related module**: [UsbDdk](capi-usbddk.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [int32_t OH_Usb_Init(void)](#oh_usb_init) | Initializes the USB DDK. |
| [void OH_Usb_Release(void)](#oh_usb_release) | Releases the USB DDK. |
| [int32_t OH_Usb_ReleaseResource(void)](#oh_usb_releaseresource) | Releases the USB DDK. |
| [int32_t OH_Usb_GetDeviceDescriptor(uint64_t deviceId, struct UsbDeviceDescriptor *desc)](#oh_usb_getdevicedescriptor) | Obtains the device descriptor. |
| [int32_t OH_Usb_GetConfigDescriptor(uint64_t deviceId, uint8_t configIndex, struct UsbDdkConfigDescriptor ** const config)](#oh_usb_getconfigdescriptor) | Obtains the configuration descriptor. To avoid memory leakage, use [OH_Usb_FreeConfigDescriptor](capi-usb-ddk-api-h.md#oh_usb_freeconfigdescriptor) to release a descriptor after use. |
| [void OH_Usb_FreeConfigDescriptor(struct UsbDdkConfigDescriptor * const config)](#oh_usb_freeconfigdescriptor) | Releases a configuration descriptor after use to prevent memory leakage. |
| [int32_t OH_Usb_ClaimInterface(uint64_t deviceId, uint8_t interfaceIndex, uint64_t *interfaceHandle)](#oh_usb_claiminterface) | Claims a USB interface. |
| [int32_t OH_Usb_ReleaseInterface(uint64_t interfaceHandle)](#oh_usb_releaseinterface) | Releases a USB interface. |
| [int32_t OH_Usb_SelectInterfaceSetting(uint64_t interfaceHandle, uint8_t settingIndex)](#oh_usb_selectinterfacesetting) | Activates the alternate setting of a USB interface. |
| [int32_t OH_Usb_GetCurrentInterfaceSetting(uint64_t interfaceHandle, uint8_t *settingIndex)](#oh_usb_getcurrentinterfacesetting) | Obtains the activated alternate setting of a USB interface. |
| [int32_t OH_Usb_SendControlReadRequest(uint64_t interfaceHandle, const struct UsbControlRequestSetup *setup, uint32_t timeout, uint8_t *data, uint32_t *dataLen)](#oh_usb_sendcontrolreadrequest) | Sends a control read transfer request. This API works in a synchronous manner. |
| [int32_t OH_Usb_SendControlWriteRequest(uint64_t interfaceHandle, const struct UsbControlRequestSetup *setup, uint32_t timeout, const uint8_t *data, uint32_t dataLen)](#oh_usb_sendcontrolwriterequest) | Sends a control write transfer request. This API works in a synchronous manner. |
| [int32_t OH_Usb_SendPipeRequest(const struct UsbRequestPipe *pipe, UsbDeviceMemMap *devMmap)](#oh_usb_sendpiperequest) | Sends a pipe request. This API works in a synchronous manner. It applies to interrupt transfer and bulk transfer. |
| [int32_t OH_Usb_SendPipeRequestWithAshmem(const struct UsbRequestPipe *pipe, DDK_Ashmem *ashmem)](#oh_usb_sendpiperequestwithashmem) | Sends a pipe request based on the shared memory. This API returns the result synchronously. It applies to interrupt transfer and bulk transfer. |
| [int32_t OH_Usb_CreateDeviceMemMap(uint64_t deviceId, size_t size, UsbDeviceMemMap **devMmap)](#oh_usb_createdevicememmap) | Creates a buffer. To avoid resource leakage, use [OH_Usb_DestroyDeviceMemMap](capi-usb-ddk-api-h.md#oh_usb_destroydevicememmap) to destroy a buffer after use. |
| [void OH_Usb_DestroyDeviceMemMap(UsbDeviceMemMap *devMmap)](#oh_usb_destroydevicememmap) | Destroys a buffer. To prevent resource leakage, destroy a buffer in time after use. |
| [int32_t OH_Usb_GetDevices(struct Usb_DeviceArray *devices)](#oh_usb_getdevices) | Obtains the USB device ID list. Ensure that the pointer parameters passed in are valid. To avoid excessive memory usage, the size of the requested device ID array is recommended not to exceed 128. After using the struct, release the memory of its members; otherwise, resource leaks may occur. Besides, make sure that the obtained USB device ID has been filtered by **vid** in the driver configuration information. |
| [int32_t OH_Usb_ControlTransfer(uint64_t deviceID, const struct UsbControlRequestSetup *setupPacket, uint8_t *data, uint32_t timeout)](#oh_usb_controltransfer) | Performs a USB control transfer. This API works in a synchronous manner. |
| [int32_t OH_Usb_GetNonRootHubs(struct Usb_NonRootHubArray *nonRootHub)](#oh_usb_getnonroothubs) | Queries and returns the list of non-root hubs. Ensure that the pointer parameters passed in are valid. To avoid excessive memory usage, the size of the requested non-root hub ID array is recommended not to exceed 128. After using the struct, release the memory of its members; otherwise, resource leaks may occur. |

## Function description

### OH_Usb_Init()

```c
int32_t OH_Usb_Init(void)
```

**Description**

Initializes the USB DDK.

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link USB_DDK_SUCCESS}: The operation is successful.<br>    {@link USB_DDK_INVALID_OPERATION}: The USB DDK service connection fails, or an internal error occurs.<br>    {@link USB_DDK_NO_PERM}: The permission check fails.<br>    {@link USB_DDK_MEMORY_ERROR}: The memory allocation fails. |

### OH_Usb_Release()

```c
void OH_Usb_Release(void)
```

**Description**

Releases the USB DDK.

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 10

### OH_Usb_ReleaseResource()

```c
int32_t OH_Usb_ReleaseResource(void)
```

**Description**

Releases the USB DDK.

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 18

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link USB_DDK_SUCCESS}: The operation is successful.<br>    {@link USB_DDK_NO_PERM}: The permission check fails.<br>    {@link USB_DDK_INVALID_OPERATION}: The USB DDK service connection fails. |

### OH_Usb_GetDeviceDescriptor()

```c
int32_t OH_Usb_GetDeviceDescriptor(uint64_t deviceId, struct UsbDeviceDescriptor *desc)
```

**Description**

Obtains the device descriptor.

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t deviceId | Device ID. |
| struct UsbDeviceDescriptor *desc | Device descriptor. For details, see {@link UsbDeviceDescriptor}. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link USB_DDK_SUCCESS}: The operation is successful.<br>    {@link USB_DDK_NO_PERM}: The permission check fails.<br>    {@link USB_DDK_INVALID_OPERATION}: The USB DDK service connection fails.<br>    {@link USB_DDK_INVALID_PARAMETER}: The input desc is a null pointer. |

### OH_Usb_GetConfigDescriptor()

```c
int32_t OH_Usb_GetConfigDescriptor(uint64_t deviceId, uint8_t configIndex, struct UsbDdkConfigDescriptor ** const config)
```

**Description**

Obtains the configuration descriptor. To avoid memory leakage, use [OH_Usb_FreeConfigDescriptor](capi-usb-ddk-api-h.md#oh_usb_freeconfigdescriptor) to release a descriptor after use.

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t deviceId | Device ID. |
| uint8_t configIndex | Configuration index, which corresponds to the **bConfigurationValue** field in the USB configuration descriptor. |
| struct UsbDdkConfigDescriptor ** const config | Configuration descriptor, which includes the standard configuration descriptor defined in the USB protocol and the associated interface descriptor and endpoint descriptor. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link USB_DDK_SUCCESS}: The operation is successful.<br>    {@link USB_DDK_NO_PERM}: The permission check fails.<br>    {@link USB_DDK_INVALID_OPERATION}: The USB DDK service connection fails.<br>    {@link USB_DDK_INVALID_PARAMETER}: The input config is a null pointer.<br>    {@link USB_DDK_IO_FAILED}: An I/O exception occurs.<br>    {@link USB_DDK_MEMORY_ERROR}: The memory allocation fails. |

### OH_Usb_FreeConfigDescriptor()

```c
void OH_Usb_FreeConfigDescriptor(struct UsbDdkConfigDescriptor * const config)
```

**Description**

Releases a configuration descriptor after use to prevent memory leakage.

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct UsbDdkConfigDescriptor * const config | Configuration descriptor, which is obtained by calling [OH_Usb_GetConfigDescriptor](capi-usb-ddk-api-h.md#oh_usb_getconfigdescriptor). |

### OH_Usb_ClaimInterface()

```c
int32_t OH_Usb_ClaimInterface(uint64_t deviceId, uint8_t interfaceIndex, uint64_t *interfaceHandle)
```

**Description**

Claims a USB interface.

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t deviceId | Device ID. |
| uint8_t interfaceIndex | Interface index, which corresponds to {@link bInterfaceNumber} in the USB protocol. |
| uint64_t *interfaceHandle | Interface operation handle. After the interface is claimed successfully, a value will be assigned to this parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link USB_DDK_SUCCESS}: The operation is successful.<br>    {@link USB_DDK_NO_PERM}: The permission check fails.<br>    {@link USB_DDK_INVALID_OPERATION}: The USB DDK service connection fails.<br>    {@link USB_DDK_INVALID_PARAMETER}: The input interfaceHandle is a null pointer.<br>    {@link USB_DDK_MEMORY_ERROR}: The memory to be allocated exceeds the limit. |

### OH_Usb_ReleaseInterface()

```c
int32_t OH_Usb_ReleaseInterface(uint64_t interfaceHandle)
```

**Description**

Releases a USB interface.

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t interfaceHandle | Interface operation handle. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link USB_DDK_SUCCESS}: The operation is successful.<br>    {@link USB_DDK_NO_PERM}: The permission check fails.<br>    {@link USB_DDK_INVALID_OPERATION}: The USB DDK service connection fails.<br>    {@link USB_DDK_INVALID_PARAMETER}: One or more parameters are invalid. |

### OH_Usb_SelectInterfaceSetting()

```c
int32_t OH_Usb_SelectInterfaceSetting(uint64_t interfaceHandle, uint8_t settingIndex)
```

**Description**

Activates the alternate setting of a USB interface.

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t interfaceHandle | Interface operation handle. |
| uint8_t settingIndex | Alternate setting index, which corresponds to the **bAlternateSetting** field of the interface descriptor in the USB protocol. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link USB_DDK_SUCCESS}: The operation is successful.<br>    {@link USB_DDK_NO_PERM}: The permission check fails.<br>    {@link USB_DDK_INVALID_OPERATION}: The USB DDK service connection fails.<br>    {@link USB_DDK_INVALID_PARAMETER}: One or more parameters are invalid. |

### OH_Usb_GetCurrentInterfaceSetting()

```c
int32_t OH_Usb_GetCurrentInterfaceSetting(uint64_t interfaceHandle, uint8_t *settingIndex)
```

**Description**

Obtains the activated alternate setting of a USB interface.

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t interfaceHandle | Interface operation handle. |
| uint8_t *settingIndex | Alternate setting index, which corresponds to the **bAlternateSetting** field of the interface descriptor in the USB protocol. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link USB_DDK_SUCCESS}: The operation is successful.<br>    {@link USB_DDK_NO_PERM}: The permission check fails.<br>    {@link USB_DDK_INVALID_OPERATION}: The USB DDK service connection fails.<br>    {@link USB_DDK_INVALID_PARAMETER}: The input settingIndex is a null pointer. |

### OH_Usb_SendControlReadRequest()

```c
int32_t OH_Usb_SendControlReadRequest(uint64_t interfaceHandle, const struct UsbControlRequestSetup *setup, uint32_t timeout, uint8_t *data, uint32_t *dataLen)
```

**Description**

Sends a control read transfer request. This API works in a synchronous manner.

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t interfaceHandle | Interface operation handle. |
| const struct UsbControlRequestSetup *setup | Request parameters. For details, see {@link UsbControlRequestSetup}. |
| uint32_t timeout | Timeout duration, in ms. |
| uint8_t *data | Data to transfer. |
| uint32_t *dataLen | Data length. The return value indicates the length of the actually read data. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link USB_DDK_SUCCESS}: The operation is successful.<br>    {@link USB_DDK_NO_PERM}: The permission check fails.<br>    {@link USB_DDK_INVALID_OPERATION}: The USB DDK service connection fails.<br>    {@link USB_DDK_INVALID_PARAMETER}: The input setup, data, or dataLen is a null pointer, or the value<br>    of datalen is less than the length of the read data.<br>    {@link USB_DDK_MEMORY_ERROR}: The attempt to copy the memory that stores the read data fails.<br>    {@link USB_DDK_IO_FAILED}: An I/O exception occurs.<br>    {@link USB_DDK_TIMEOUT}: The operation times out. |

### OH_Usb_SendControlWriteRequest()

```c
int32_t OH_Usb_SendControlWriteRequest(uint64_t interfaceHandle, const struct UsbControlRequestSetup *setup, uint32_t timeout, const uint8_t *data, uint32_t dataLen)
```

**Description**

Sends a control write transfer request. This API works in a synchronous manner.

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t interfaceHandle | Interface operation handle. |
| const struct UsbControlRequestSetup *setup | Request parameters. For details, see {@link UsbControlRequestSetup}. |
| uint32_t timeout | Timeout duration, in ms. |
| const uint8_t *data | Data to transfer. |
| uint32_t dataLen | Data length. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link USB_DDK_SUCCESS}: The operation is successful.<br>    {@link USB_DDK_NO_PERM}: The permission check fails.<br>    {@link USB_DDK_INVALID_OPERATION}: The USB DDK service connection fails.<br>    {@link USB_DDK_INVALID_PARAMETER}: The input setup or data is a null pointer.<br>    {@link USB_DDK_MEMORY_ERROR}: The attempt to copy the memory that stores the read data fails.<br>    {@link USB_DDK_IO_FAILED}: An I/O exception occurs.<br>    {@link USB_DDK_TIMEOUT}: The operation times out. |

### OH_Usb_SendPipeRequest()

```c
int32_t OH_Usb_SendPipeRequest(const struct UsbRequestPipe *pipe, UsbDeviceMemMap *devMmap)
```

**Description**

Sends a pipe request. This API works in a synchronous manner. It applies to interrupt transfer and bulk transfer.

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| const struct UsbRequestPipe *pipe | Pipe used to transfer data. |
| UsbDeviceMemMap *devMmap | Data buffer, which can be obtained by calling [OH_Usb_CreateDeviceMemMap](capi-usb-ddk-api-h.md#oh_usb_createdevicememmap). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link USB_DDK_SUCCESS}: The operation is successful.<br>    {@link USB_DDK_NO_PERM}: The permission check fails.<br>    {@link USB_DDK_INVALID_OPERATION}: The USB DDK service connection fails.<br>    {@link USB_DDK_INVALID_PARAMETER}: The input pipe or devMmap is a null pointer, or the devMmap<br>    address is null.<br>    {@link USB_DDK_MEMORY_ERROR}: The attempt to copy the memory that stores the read data fails.<br>    {@link USB_DDK_IO_FAILED}: An I/O exception occurs.<br>    {@link USB_DDK_TIMEOUT}: The operation times out. |

### OH_Usb_SendPipeRequestWithAshmem()

```c
int32_t OH_Usb_SendPipeRequestWithAshmem(const struct UsbRequestPipe *pipe, DDK_Ashmem *ashmem)
```

**Description**

Sends a pipe request based on the shared memory. This API returns the result synchronously. It applies to interrupt transfer and bulk transfer.

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const struct UsbRequestPipe *pipe | Pipe used to transfer data. |
| DDK_Ashmem *ashmem | Shared memory, which can be obtained through {@link OH_DDK_CreateAshmem}. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link USB_DDK_SUCCESS}: The operation is successful.<br>    {@link USB_DDK_NO_PERM}: The permission check fails.<br>    {@link USB_DDK_INVALID_OPERATION}: The USB DDK service connection fails.<br>    {@link USB_DDK_INVALID_PARAMETER}: The input pipe or ashmem is a null pointer, or the ashmem address<br>    is null.<br>    {@link USB_DDK_MEMORY_ERROR}: The attempt to copy the memory that stores the read data fails.<br>    {@link USB_DDK_IO_FAILED}: An I/O exception occurs.<br>    {@link USB_DDK_TIMEOUT}: The operation times out. |

### OH_Usb_CreateDeviceMemMap()

```c
int32_t OH_Usb_CreateDeviceMemMap(uint64_t deviceId, size_t size, UsbDeviceMemMap **devMmap)
```

**Description**

Creates a buffer. To avoid resource leakage, use [OH_Usb_DestroyDeviceMemMap](capi-usb-ddk-api-h.md#oh_usb_destroydevicememmap) to destroy a buffer after use.

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t deviceId | Device ID. |
| size_t size | Buffer size. |
| UsbDeviceMemMap **devMmap | Data memory map, through which the created buffer is returned to the caller. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link USB_DDK_SUCCESS}: The operation is successful.<br>    {@link USB_DDK_NO_PERM}: The permission check fails.<br>    {@link USB_DDK_INVALID_PARAMETER}: The input parameter devMmap or devMmap is a null pointer.<br>    {@link USB_DDK_MEMORY_ERROR}: The memory mapping fails, or the memory allocation of devMmap fails. |

### OH_Usb_DestroyDeviceMemMap()

```c
void OH_Usb_DestroyDeviceMemMap(UsbDeviceMemMap *devMmap)
```

**Description**

Destroys a buffer. To prevent resource leakage, destroy a buffer in time after use.

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| UsbDeviceMemMap *devMmap | Destroys the buffer created by calling [OH_Usb_CreateDeviceMemMap](capi-usb-ddk-api-h.md#oh_usb_createdevicememmap). |

### OH_Usb_GetDevices()

```c
int32_t OH_Usb_GetDevices(struct Usb_DeviceArray *devices)
```

**Description**

Obtains the USB device ID list. Ensure that the pointer parameters passed in are valid. To avoid excessive memory usage, the size of the requested device ID array is recommended not to exceed 128. After using the struct, release the memory of its members; otherwise, resource leaks may occur. Besides, make sure that the obtained USB device ID has been filtered by **vid** in the driver configuration information.

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct Usb_DeviceArray *devices | Device memory address, which is used to store the obtained device ID list and quantity. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link USB_DDK_SUCCESS}: The operation is successful.<br>    {@link USB_DDK_NO_PERM}: The permission check fails.<br>    {@link USB_DDK_INVALID_OPERATION}: The USB DDK service connection fails.<br>    {@link USB_DDK_INVALID_PARAMETER}: The input devices is a null pointer. |

### OH_Usb_ControlTransfer()

```c
int32_t OH_Usb_ControlTransfer(uint64_t deviceID, const struct UsbControlRequestSetup *setupPacket, uint8_t *data, uint32_t timeout)
```

**Description**

Performs a USB control transfer. This API works in a synchronous manner.

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t deviceID | An ID for the device to communicate with |
| const struct UsbControlRequestSetup *setupPacket | Configuration parameters for the setup packet in control transfer requests |
| uint8_t *data | A suitably-sized data buffer for either input or output based on the direction bits within bmRequestType. |
| uint32_t timeout | Timeout (in milliseconds) that this function should wait before giving up due to no response being received. For an unlimited timeout, use value 0. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | on success, the number of bytes actually transferred.      {@link USB_DDK_NO_PERM} Permission authentication failed.<br>    {@link USB_DDK_INVALID_OPERATION} DDK Service not initialized. Please invoke [OH_Usb_Init](capi-usb-ddk-api-h.md#oh_usb_init) to complete the<br>    initialization process first.<br>    {@link USB_DDK_INVALID_PARAMETER} The setupPacket or data parameters are invalid.<br>    {@link USB_DDK_TIMEOUT} The control transfer timed out.<br>    {@link USB_DDK_IO_FAILED} Control transfer request I/O exception. |

### OH_Usb_GetNonRootHubs()

```c
int32_t OH_Usb_GetNonRootHubs(struct Usb_NonRootHubArray *nonRootHub)
```

**Description**

Queries and returns the list of non-root hubs. Ensure that the pointer parameters passed in are valid. To avoid excessive memory usage, the size of the requested non-root hub ID array is recommended not to exceed 128. After using the struct, release the memory of its members; otherwise, resource leaks may occur.

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct Usb_NonRootHubArray *nonRootHub | Returns the list of queried non-root hubs. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link USB_DDK_SUCCESS} Query operation successful.<br>    {@link USB_DDK_NO_PERM} Permission authentication failed.<br>    {@link USB_DDK_INVALID_OPERATION} DDK Service not initialized. Please invoke [OH_Usb_Init](capi-usb-ddk-api-h.md#oh_usb_init) to complete the<br>    initialization process first.<br>    {@link USB_DDK_INVALID_PARAMETER} The parameter nonRootHub is null. |


