# usb_ddk_api.h

## Overview

Declares the USB DDK APIs used by the host to access the device. These APIs provide functions such as USB device management, configuration, and data transmission, helping developers implement underlying interaction and data communication with the USB device.

**File to Include**: <usb/usb_ddk_api.h>

**Library**: libusb_ndk.z.so

**System capability**: SystemCapability.Driver.USB.Extension

**Since**: 10

**Related module**: [UsbDdk](capi-driver-development-kit-usbddk.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [int32_t OH_Usb_Init(void)](#oh_usb_init) | Initializes the USB DDK. This method must be called before all other USB DDK methods. After using the DDK, call [OH_Usb_Release](capi-usb-ddk-api-h.md#oh_usb_release) or [OH_Usb_ReleaseResource](capi-usb-ddk-api-h.md#oh_usb_releaseresource) to release resources. |
| [void OH_Usb_Release(void)](#oh_usb_release) | Releases the USB DDK. This method is used to correctly release resources when the USB DDK is no longer used. It can only be called after [OH_Usb_Init](capi-usb-ddk-api-h.md#oh_usb_init) is called to complete initialization. |
| [int32_t OH_Usb_ReleaseResource(void)](#oh_usb_releaseresource) | Releases the USB DDK. This method is used to correctly release resources when the USB DDK is no longer used. It can only be called after [OH_Usb_Init](capi-usb-ddk-api-h.md#oh_usb_init) is called to complete initialization. This method returns an integer value, which can be used to determine the execution result. |
| [int32_t OH_Usb_GetDeviceDescriptor(uint64_t deviceId, struct UsbDeviceDescriptor *desc)](#oh_usb_getdevicedescriptor) | Obtains the device descriptor. Ensure that the input pointer parameter is valid. |
| [int32_t OH_Usb_GetConfigDescriptor(uint64_t deviceId, uint8_t configIndex, struct UsbDdkConfigDescriptor ** const config)](#oh_usb_getconfigdescriptor) | Obtains the configuration descriptor. To prevent memory leak, use [OH_Usb_FreeConfigDescriptor()](capi-usb-ddk-api-h.md#oh_usb_freeconfigdescriptor()) to release a descriptor after use. |
| [void OH_Usb_FreeConfigDescriptor(struct UsbDdkConfigDescriptor * const config)](#oh_usb_freeconfigdescriptor) | Releases the configuration descriptor. To prevent memory leak, use this API to release the configuration descriptor after use. |
| [int32_t OH_Usb_ClaimInterface(uint64_t deviceId, uint8_t interfaceIndex, uint64_t *interfaceHandle)](#oh_usb_claiminterface) | Claims a USB interface exclusively. After calling this method, you must call [OH_Usb_ReleaseInterface](capi-usb-ddk-api-h.md#oh_usb_releaseinterface) to release the interface after use. Otherwise, the interface resources cannot be released. |
| [int32_t OH_Usb_ReleaseInterface(uint64_t interfaceHandle)](#oh_usb_releaseinterface) | Releases the USB interface that is claimed exclusively. Before calling this method, you must call [OH_Usb_ClaimInterface](capi-usb-ddk-api-h.md#oh_usb_claiminterface) to claim the interface and obtain the interface handle. |
| [int32_t OH_Usb_SelectInterfaceSetting(uint64_t interfaceHandle, uint8_t settingIndex)](#oh_usb_selectinterfacesetting) | Activates the alternate setting of a USB interface. Call this method when the interface working mode needs to be changed. |
| [int32_t OH_Usb_GetCurrentInterfaceSetting(uint64_t interfaceHandle, uint8_t *settingIndex)](#oh_usb_getcurrentinterfacesetting) | Obtains the activated alternate setting of a USB interface. |
| [int32_t OH_Usb_SendControlReadRequest(uint64_t interfaceHandle, const struct UsbControlRequestSetup *setup, uint32_t timeout, uint8_t *data, uint32_t *dataLen)](#oh_usb_sendcontrolreadrequest) | Sends a control read transfer request. This API works in a synchronous manner. |
| [int32_t OH_Usb_SendControlWriteRequest(uint64_t interfaceHandle, const struct UsbControlRequestSetup *setup, uint32_t timeout, const uint8_t *data, uint32_t dataLen)](#oh_usb_sendcontrolwriterequest) | Sends a control write transfer request. This API works in a synchronous manner. |
| [int32_t OH_Usb_SendPipeRequest(const struct UsbRequestPipe *pipe, UsbDeviceMemMap *devMmap)](#oh_usb_sendpiperequest) | Sends a pipe request. This API works in a synchronous manner. It applies to interrupt transfer and bulk transfer. |
| [int32_t OH_Usb_SendPipeRequestWithAshmem(const struct UsbRequestPipe *pipe, DDK_Ashmem *ashmem)](#oh_usb_sendpiperequestwithashmem) | Sends a pipe request based on the shared memory. This API returns the result synchronously. It applies to interrupt transfer and bulk transfer. |
| [int32_t OH_Usb_CreateDeviceMemMap(uint64_t deviceId, size_t size, UsbDeviceMemMap **devMmap)](#oh_usb_createdevicememmap) | Creates a buffer. To prevent resource leaks, use [OH_Usb_DestroyDeviceMemMap](capi-usb-ddk-api-h.md#oh_usb_destroydevicememmap) to destroy a buffer after use. |
| [void OH_Usb_DestroyDeviceMemMap(UsbDeviceMemMap *devMmap)](#oh_usb_destroydevicememmap) | Destroys a buffer. To prevent resource leaks, use this API to destroy a buffer after use. |
| [int32_t OH_Usb_GetDevices(struct Usb_DeviceArray *devices)](#oh_usb_getdevices) | Obtains the USB device ID list. Ensure that the pointer parameters passed in are valid. To avoid excessive memory usage, the size of the requested device ID array is recommended not to exceed 128. After using the struct, release the memory of its members; otherwise, resource leaks may occur. Besides, make sure that the obtained USB device ID has been filtered by **vid** in the driver configuration information. |
| [int32_t OH_Usb_ControlTransfer(uint64_t deviceID, const struct UsbControlRequestSetup *setupPacket, uint8_t *data, uint32_t timeout)](#oh_usb_controltransfer) | Performs USB control transfer. This API returns the result synchronously. |
| [int32_t OH_Usb_GetNonRootHubs(struct Usb_NonRootHubArray *nonRootHub)](#oh_usb_getnonroothubs) | Queries and returns the non-root hub list. Ensure that the input pointer is valid. It is recommended that the number of non-root hub IDs do not exceed 128 to prevent excessive memory usage. After using the struct, release the memory of its members; otherwise, resource leaks may occur. |
| [UsbDdkErrCode OH_Usb_CreateDeviceMemBuffer(uint64_t deviceId, uint32_t size, uint8_t **buffer)](#oh_usb_createdevicemembuffer) | Creates a device memory buffer. To avoid resource leakage, call [OH_Usb_DestroyDeviceMemBuffer](capi-usb-ddk-api-h.md#oh_usb_destroydevicemembuffer) to destroy the buffer after the buffer has been used. |
| [UsbDdkErrCode OH_Usb_DestroyDeviceMemBuffer(uint8_t **buffer)](#oh_usb_destroydevicemembuffer) | Destroy the device memory buffer. To prevent resource leakage, destroy the buffer immediately after using the buffer. |
| [UsbDdkErrCode OH_Usb_WritePipe(const struct UsbRequestPipe *pipe, uint8_t *buffer, uint32_t bufferSize, uint32_t offset, uint32_t writeLength, uint32_t *transferredLength)](#oh_usb_writepipe) | Send a pipe write request. This interface operates in synchronous mode and is suitable for interrupt transfers and bulk transfers. |
| [UsbDdkErrCode OH_Usb_ReadPipe(const struct UsbRequestPipe *pipe, uint8_t *buffer, uint32_t bufferSize, uint32_t offset, uint32_t readLength, uint32_t *transferredLength)](#oh_usb_readpipe) | Send a pipe read request. This interface operates in synchronous mode and is suitable for interrupt transfers and bulk transfers. |

## Function description

### OH_Usb_Init()

```c
int32_t OH_Usb_Init(void)
```

**Description**

Initializes the USB DDK. This method must be called before all other USB DDK methods. After using the DDK, call [OH_Usb_Release](capi-usb-ddk-api-h.md#oh_usb_release) or [OH_Usb_ReleaseResource](capi-usb-ddk-api-h.md#oh_usb_releaseresource) to release resources.

<!--Device-int32_t OH_Usb_Init(void)--><!--Device-int32_t OH_Usb_Init(void)-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode): The operation is successful. <br>[USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode): The USB DDK service connection fails, or an internal error occurs. <br>[USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails. Check whether the app has obtained the **ohos.permission.ACCESS_DDK_USB** permission. <br>[USB_DDK_MEMORY_ERROR](capi-usb-ddk-types-h.md#usbddkerrcode): The memory allocation fails. Check the memory size and validity. |

### OH_Usb_Release()

```c
void OH_Usb_Release(void)
```

**Description**

Releases the USB DDK. This method is used to correctly release resources when the USB DDK is no longer used. It can only be called after [OH_Usb_Init](capi-usb-ddk-api-h.md#oh_usb_init) is called to complete initialization.

<!--Device-void OH_Usb_Release(void)--><!--Device-void OH_Usb_Release(void)-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 10

### OH_Usb_ReleaseResource()

```c
int32_t OH_Usb_ReleaseResource(void)
```

**Description**

Releases the USB DDK. This method is used to correctly release resources when the USB DDK is no longer used. It can only be called after [OH_Usb_Init](capi-usb-ddk-api-h.md#oh_usb_init) is called to complete initialization. This method returns an integer value, which can be used to determine the execution result.

<!--Device-int32_t OH_Usb_ReleaseResource(void)--><!--Device-int32_t OH_Usb_ReleaseResource(void)-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 18

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode): The operation is successful. <br>[USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails. Check whether the app has obtained the **ohos.permission.ACCESS_DDK_USB** permission. <br>[USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode): The USB DDK service connection fails. Call [OH_Usb_Init](capi-usb-ddk-api-h.md#oh_usb_init) to complete initialization first. |

### OH_Usb_GetDeviceDescriptor()

```c
int32_t OH_Usb_GetDeviceDescriptor(uint64_t deviceId, struct UsbDeviceDescriptor *desc)
```

**Description**

Obtains the device descriptor. Ensure that the input pointer parameter is valid.

<!--Device-int32_t OH_Usb_GetDeviceDescriptor(uint64_t deviceId, struct UsbDeviceDescriptor *desc)--><!--Device-int32_t OH_Usb_GetDeviceDescriptor(uint64_t deviceId, struct UsbDeviceDescriptor *desc)-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t deviceId | Device ID, which can be obtained by calling [OH_Usb_GetDevices](capi-usb-ddk-api-h.md#oh_usb_getdevices). It identifies the device whose descriptor is to be obtained. |
| [struct UsbDeviceDescriptor](capi-usbddk-usbdevicedescriptor.md) *desc | Output parameter, which is used to receive the device descriptor. For details, see [UsbDeviceDescriptor](capi-usbddk-usbdevicedescriptor.md). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode): The operation is successful. <br>[USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails. Check whether the app has obtained the **ohos.permission.ACCESS_DDK_USB** permission. <br>[USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode): The USB DDK service connection fails. Call [OH_Usb_Init](capi-usb-ddk-api-h.md#oh_usb_init) to complete initialization first. <br>[USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode): The input **desc** is a null pointer. Check the parameter validity. |

### OH_Usb_GetConfigDescriptor()

```c
int32_t OH_Usb_GetConfigDescriptor(uint64_t deviceId, uint8_t configIndex, struct UsbDdkConfigDescriptor ** const config)
```

**Description**

Obtains the configuration descriptor. To prevent memory leak, use [OH_Usb_FreeConfigDescriptor()](capi-usb-ddk-api-h.md#oh_usb_freeconfigdescriptor()) to release a descriptor after use.

<!--Device-int32_t OH_Usb_GetConfigDescriptor(uint64_t deviceId, uint8_t configIndex, struct UsbDdkConfigDescriptor ** const config)--><!--Device-int32_t OH_Usb_GetConfigDescriptor(uint64_t deviceId, uint8_t configIndex, struct UsbDdkConfigDescriptor ** const config)-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t deviceId | Device ID, which can be obtained by calling [OH_Usb_GetDevices](capi-usb-ddk-api-h.md#oh_usb_getdevices). It identifies the device whose configuration descriptor is to be obtained. |
| uint8_t configIndex | Configuration index, which corresponds to the **bConfigurationValue** field in the USB configuration descriptor. |
| struct UsbDdkConfigDescriptor ** const config | Output parameter, which is used to receive the configuration descriptor, including the standard configuration descriptor defined in the USB protocol and the associated interface descriptor and endpoint descriptor. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode): The operation is successful. <br>[USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails. Check whether the app has obtained the **ohos.permission.ACCESS_DDK_USB** permission. <br>[USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode): The USB DDK service connection fails. Call [OH_Usb_Init](capi-usb-ddk-api-h.md#oh_usb_init) to complete initialization first. <br>[USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode): The input **config** is a null pointer. Check the parameter validity. <br>[USB_DDK_IO_FAILED](capi-usb-ddk-types-h.md#usbddkerrcode): An I/O exception occurs. Check the parameters and device specifications. <br>[USB_DDK_MEMORY_ERROR](capi-usb-ddk-types-h.md#usbddkerrcode): The memory allocation fails. Check the memory size and validity. |

### OH_Usb_FreeConfigDescriptor()

```c
void OH_Usb_FreeConfigDescriptor(struct UsbDdkConfigDescriptor * const config)
```

**Description**

Releases the configuration descriptor. To prevent memory leak, use this API to release the configuration descriptor after use.

<!--Device-void OH_Usb_FreeConfigDescriptor(struct UsbDdkConfigDescriptor * const config)--><!--Device-void OH_Usb_FreeConfigDescriptor(struct UsbDdkConfigDescriptor * const config)-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct UsbDdkConfigDescriptor * const config | Configuration descriptor obtained by calling [OH_Usb_GetConfigDescriptor](capi-usb-ddk-api-h.md#oh_usb_getconfigdescriptor). |

### OH_Usb_ClaimInterface()

```c
int32_t OH_Usb_ClaimInterface(uint64_t deviceId, uint8_t interfaceIndex, uint64_t *interfaceHandle)
```

**Description**

Claims a USB interface exclusively. After calling this method, you must call [OH_Usb_ReleaseInterface](capi-usb-ddk-api-h.md#oh_usb_releaseinterface) to release the interface after use. Otherwise, the interface resources cannot be released.

<!--Device-int32_t OH_Usb_ClaimInterface(uint64_t deviceId, uint8_t interfaceIndex, uint64_t *interfaceHandle)--><!--Device-int32_t OH_Usb_ClaimInterface(uint64_t deviceId, uint8_t interfaceIndex, uint64_t *interfaceHandle)-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t deviceId | Device ID, which can be obtained by calling [OH_Usb_GetDevices](capi-usb-ddk-api-h.md#oh_usb_getdevices). It identifies the device to be operated. |
| uint8_t interfaceIndex | Interface index, which corresponds to **bInterfaceNumber** in the USB protocol. |
| uint64_t *interfaceHandle | Output parameter, which is used to receive the declared interface operation handle. After the interface is claimed successfully, a value will be assigned to this parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode): The operation is successful. <br>[USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails. Check whether the app has obtained the **ohos.permission.ACCESS_DDK_USB** permission. <br>[USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode): The USB DDK service connection fails. Call [OH_Usb_Init](capi-usb-ddk-api-h.md#oh_usb_init) to complete initialization first. <br>[USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode): The input **interfaceHandle** is a null pointer. Check the parameter validity. <br>[USB_DDK_MEMORY_ERROR](capi-usb-ddk-types-h.md#usbddkerrcode): The memory to be allocated exceeds the limit. Check the memory size and validity. |

### OH_Usb_ReleaseInterface()

```c
int32_t OH_Usb_ReleaseInterface(uint64_t interfaceHandle)
```

**Description**

Releases the USB interface that is claimed exclusively. Before calling this method, you must call [OH_Usb_ClaimInterface](capi-usb-ddk-api-h.md#oh_usb_claiminterface) to claim the interface and obtain the interface handle.

<!--Device-int32_t OH_Usb_ReleaseInterface(uint64_t interfaceHandle)--><!--Device-int32_t OH_Usb_ReleaseInterface(uint64_t interfaceHandle)-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t interfaceHandle | Interface operation handle, which needs to be obtained through [OH_Usb_ClaimInterface](capi-usb-ddk-api-h.md#oh_usb_claiminterface). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode): The operation is successful. <br>[USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails. Check whether the app has obtained the **ohos.permission.ACCESS_DDK_USB** permission. <br>[USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode): The USB DDK service connection fails. Call [OH_Usb_Init](capi-usb-ddk-api-h.md#oh_usb_init) to complete initialization first. <br>[USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode): One or more parameters are invalid. Check the parameter validity. |

### OH_Usb_SelectInterfaceSetting()

```c
int32_t OH_Usb_SelectInterfaceSetting(uint64_t interfaceHandle, uint8_t settingIndex)
```

**Description**

Activates the alternate setting of a USB interface. Call this method when the interface working mode needs to be changed.

<!--Device-int32_t OH_Usb_SelectInterfaceSetting(uint64_t interfaceHandle, uint8_t settingIndex)--><!--Device-int32_t OH_Usb_SelectInterfaceSetting(uint64_t interfaceHandle, uint8_t settingIndex)-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t interfaceHandle | Interface operation handle, which needs to be obtained through [OH_Usb_ClaimInterface](capi-usb-ddk-api-h.md#oh_usb_claiminterface). |
| uint8_t settingIndex | Alternate setting index, which corresponds to the **bAlternateSetting** field of the interface descriptor in the USB protocol. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode): The operation is successful. <br>[USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails. Check whether the app has obtained the **ohos.permission.ACCESS_DDK_USB** permission. <br>[USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode): The USB DDK service connection fails. Call [OH_Usb_Init](capi-usb-ddk-api-h.md#oh_usb_init) to complete initialization first. <br>[USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode): One or more parameters are invalid. Check the parameter validity. |

### OH_Usb_GetCurrentInterfaceSetting()

```c
int32_t OH_Usb_GetCurrentInterfaceSetting(uint64_t interfaceHandle, uint8_t *settingIndex)
```

**Description**

Obtains the activated alternate setting of a USB interface.

<!--Device-int32_t OH_Usb_GetCurrentInterfaceSetting(uint64_t interfaceHandle, uint8_t *settingIndex)--><!--Device-int32_t OH_Usb_GetCurrentInterfaceSetting(uint64_t interfaceHandle, uint8_t *settingIndex)-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t interfaceHandle | Interface operation handle, which needs to be obtained through [OH_Usb_ClaimInterface](capi-usb-ddk-api-h.md#oh_usb_claiminterface). |
| uint8_t *settingIndex | Output parameter, which is used to receive the alternate setting index corresponding to the **bAlternateSetting** field of the interface descriptor in the USB protocol. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode): The operation is successful. <br>[USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails. Check whether the app has obtained the **ohos.permission.ACCESS_DDK_USB** permission. <br>[USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode): The USB DDK service connection fails. Call [OH_Usb_Init](capi-usb-ddk-api-h.md#oh_usb_init) to complete initialization first. <br>[USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode): The input **settingIndex** is a null pointer. Check the parameter validity. |

### OH_Usb_SendControlReadRequest()

```c
int32_t OH_Usb_SendControlReadRequest(uint64_t interfaceHandle, const struct UsbControlRequestSetup *setup, uint32_t timeout, uint8_t *data, uint32_t *dataLen)
```

**Description**

Sends a control read transfer request. This API works in a synchronous manner.

<!--Device-int32_t OH_Usb_SendControlReadRequest(uint64_t interfaceHandle, const struct UsbControlRequestSetup *setup, uint32_t timeout, uint8_t *data, uint32_t *dataLen)--><!--Device-int32_t OH_Usb_SendControlReadRequest(uint64_t interfaceHandle, const struct UsbControlRequestSetup *setup, uint32_t timeout, uint8_t *data, uint32_t *dataLen)-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t interfaceHandle | Interface operation handle, which needs to be obtained through [OH_Usb_ClaimInterface](capi-usb-ddk-api-h.md#oh_usb_claiminterface). |
| [const struct UsbControlRequestSetup](capi-usbddk-usbcontrolrequestsetup.md) *setup | Request parameters. For details, see [UsbControlRequestSetup](capi-usbddk-usbcontrolrequestsetup.md). |
| uint32_t timeout | Timeout interval, in milliseconds, which is the maximum waiting time before a response is received. The value **0** indicates that the waiting time is unlimited. |
| uint8_t *data | Data buffer to be read, which is used to store the data read from the device. |
| uint32_t *dataLen | Data length. The value must be greater than or equal to the data length specified by the **wLength**<br>field in the setup data. The return value indicates the length of the actually read data. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode): The operation is successful. <br>[USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails. Check whether the app has obtained the **ohos.permission.ACCESS_DDK_USB** permission. <br>[USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode): The USB DDK service connection fails. Call [OH_Usb_Init](capi-usb-ddk-api-h.md#oh_usb_init) to complete initialization first. <br>[USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode): The input **setup**, **data**, or **dataLen** is a null pointer, or the value of **dataLen** is less than the length of the read data. Ensure that the pointer parameters are valid and the value of **dataLen** is large enough. <br>[USB_DDK_MEMORY_ERROR](capi-usb-ddk-types-h.md#usbddkerrcode): The attempt to copy the memory that stores the read data fails. Check the memory size and validity. <br>[USB_DDK_IO_FAILED](capi-usb-ddk-types-h.md#usbddkerrcode): An I/O exception occurs. Check the parameters and device specifications. <br>[USB_DDK_TIMEOUT](capi-usb-ddk-types-h.md#usbddkerrcode): The operation times out. Check the transmission parameters and device status. |

### OH_Usb_SendControlWriteRequest()

```c
int32_t OH_Usb_SendControlWriteRequest(uint64_t interfaceHandle, const struct UsbControlRequestSetup *setup, uint32_t timeout, const uint8_t *data, uint32_t dataLen)
```

**Description**

Sends a control write transfer request. This API works in a synchronous manner.

<!--Device-int32_t OH_Usb_SendControlWriteRequest(uint64_t interfaceHandle, const struct UsbControlRequestSetup *setup, uint32_t timeout, const uint8_t *data, uint32_t dataLen)--><!--Device-int32_t OH_Usb_SendControlWriteRequest(uint64_t interfaceHandle, const struct UsbControlRequestSetup *setup, uint32_t timeout, const uint8_t *data, uint32_t dataLen)-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t interfaceHandle | Interface operation handle, which needs to be obtained through [OH_Usb_ClaimInterface](capi-usb-ddk-api-h.md#oh_usb_claiminterface). |
| [const struct UsbControlRequestSetup](capi-usbddk-usbcontrolrequestsetup.md) *setup | Request parameters. For details, see [UsbControlRequestSetup](capi-usbddk-usbcontrolrequestsetup.md). |
| uint32_t timeout | Timeout interval, in milliseconds, which is the maximum waiting time before a response is received. The value **0** indicates that the waiting time is unlimited. |
| const uint8_t *data | Data buffer to be written, which points to the data to be sent to the device. |
| uint32_t dataLen | Data length. The value must be the same as that of the **wLength** field in the setup data and cannot exceed 1024 bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode): The operation is successful. <br>[USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails. Check whether the app has obtained the **ohos.permission.ACCESS_DDK_USB** permission. <br>[USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode): The USB DDK service connection fails. Call [OH_Usb_Init](capi-usb-ddk-api-h.md#oh_usb_init) to complete initialization first. <br>[USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode): The input **setup** or **data** is a null pointer. Check the parameter validity. <br>[USB_DDK_MEMORY_ERROR](capi-usb-ddk-types-h.md#usbddkerrcode): The attempt to copy the memory that stores the read data fails. Check the memory size and validity. <br>[USB_DDK_IO_FAILED](capi-usb-ddk-types-h.md#usbddkerrcode): An I/O exception occurs. Check the parameters and device specifications. <br>[USB_DDK_TIMEOUT](capi-usb-ddk-types-h.md#usbddkerrcode): The operation times out. Check the transmission parameters and device status. |

### OH_Usb_SendPipeRequest()

```c
int32_t OH_Usb_SendPipeRequest(const struct UsbRequestPipe *pipe, UsbDeviceMemMap *devMmap)
```

**Description**

Sends a pipe request. This API works in a synchronous manner. It applies to interrupt transfer and bulk transfer.

<!--Device-int32_t OH_Usb_SendPipeRequest(const struct UsbRequestPipe *pipe, UsbDeviceMemMap *devMmap)--><!--Device-int32_t OH_Usb_SendPipeRequest(const struct UsbRequestPipe *pipe, UsbDeviceMemMap *devMmap)-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const struct UsbRequestPipe](capi-usbddk-usbrequestpipe.md) *pipe | Pipe used to transfer data. |
| [UsbDeviceMemMap](capi-usbddk-usbdevicememmap.md) *devMmap | Device memory map, which can be obtained by calling [OH_Usb_CreateDeviceMemMap](capi-usb-ddk-api-h.md#oh_usb_createdevicememmap). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode): The operation is successful. <br>[USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails. Check whether the app has obtained the **ohos.permission.ACCESS_DDK_USB** permission. <br>[USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode): The USB DDK service connection fails. Call [OH_Usb_Init](capi-usb-ddk-api-h.md#oh_usb_init) to complete initialization first. <br>[USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode): The input **pipe** or **devMmap** is a null pointer, or the **devMmap** address is null. Check the parameter validity. <br>[USB_DDK_MEMORY_ERROR](capi-usb-ddk-types-h.md#usbddkerrcode): The attempt to copy the memory that stores the read data fails. Check the memory size and validity. <br>[USB_DDK_IO_FAILED](capi-usb-ddk-types-h.md#usbddkerrcode): An I/O exception occurs. Check the parameters and device specifications. <br>[USB_DDK_TIMEOUT](capi-usb-ddk-types-h.md#usbddkerrcode): The operation times out. Check the transmission parameters and device status. |

### OH_Usb_SendPipeRequestWithAshmem()

```c
int32_t OH_Usb_SendPipeRequestWithAshmem(const struct UsbRequestPipe *pipe, DDK_Ashmem *ashmem)
```

**Description**

Sends a pipe request based on the shared memory. This API returns the result synchronously. It applies to interrupt transfer and bulk transfer.

<!--Device-int32_t OH_Usb_SendPipeRequestWithAshmem(const struct UsbRequestPipe *pipe, DDK_Ashmem *ashmem)--><!--Device-int32_t OH_Usb_SendPipeRequestWithAshmem(const struct UsbRequestPipe *pipe, DDK_Ashmem *ashmem)-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const struct UsbRequestPipe](capi-usbddk-usbrequestpipe.md) *pipe | Pipe used to transfer data. |
| [DDK_Ashmem](capi-ddk-ddk-ashmem.md) *ashmem | Shared memory, which can be obtained through [OH_DDK_CreateAshmem](capi-ddk-api-h.md#oh_ddk_createashmem). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode): The operation is successful. <br>[USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails. Check whether the app has obtained the **ohos.permission.ACCESS_DDK_USB** permission. <br>[USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode): The USB DDK service connection fails. Call [OH_Usb_Init](capi-usb-ddk-api-h.md#oh_usb_init) to complete initialization first. <br>[USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode): The input **pipe** or **ashmem** is a null pointer, or the **ashmem** address is null. Check the parameter validity. <br>[USB_DDK_MEMORY_ERROR](capi-usb-ddk-types-h.md#usbddkerrcode): The attempt to copy the memory that stores the read data fails. Check the memory size and validity. <br>[USB_DDK_IO_FAILED](capi-usb-ddk-types-h.md#usbddkerrcode): An I/O exception occurs. Check the parameters and device specifications. <br>[USB_DDK_TIMEOUT](capi-usb-ddk-types-h.md#usbddkerrcode): The operation times out. Check the transmission parameters and device status. |

### OH_Usb_CreateDeviceMemMap()

```c
int32_t OH_Usb_CreateDeviceMemMap(uint64_t deviceId, size_t size, UsbDeviceMemMap **devMmap)
```

**Description**

Creates a buffer. To prevent resource leaks, use [OH_Usb_DestroyDeviceMemMap](capi-usb-ddk-api-h.md#oh_usb_destroydevicememmap) to destroy a buffer after use.

<!--Device-int32_t OH_Usb_CreateDeviceMemMap(uint64_t deviceId, size_t size, UsbDeviceMemMap **devMmap)--><!--Device-int32_t OH_Usb_CreateDeviceMemMap(uint64_t deviceId, size_t size, UsbDeviceMemMap **devMmap)-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t deviceId | Device ID, which can be obtained by calling [OH_Usb_GetDevices](capi-usb-ddk-api-h.md#oh_usb_getdevices). It identifies the device for which a buffer is to be created. |
| size_t size | Buffer size, in bytes. |
| [UsbDeviceMemMap](capi-usbddk-usbdevicememmap.md) **devMmap | Output parameter, which is used to return the pointer to the created buffer to the caller. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode): The operation is successful. <br>[USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails. Check whether the app has obtained the **ohos.permission.ACCESS_DDK_USB** permission. <br>[USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode): The input **devMmap** is a null pointer, or ***devMmap** is a null pointer. Check the parameter validity. <br>[USB_DDK_MEMORY_ERROR](capi-usb-ddk-types-h.md#usbddkerrcode): The memory mapping fails, or the memory allocation of **devMmap** fails. Check the memory size and validity. |

### OH_Usb_DestroyDeviceMemMap()

```c
void OH_Usb_DestroyDeviceMemMap(UsbDeviceMemMap *devMmap)
```

**Description**

Destroys a buffer. To prevent resource leaks, use this API to destroy a buffer after use.

<!--Device-void OH_Usb_DestroyDeviceMemMap(UsbDeviceMemMap *devMmap)--><!--Device-void OH_Usb_DestroyDeviceMemMap(UsbDeviceMemMap *devMmap)-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [UsbDeviceMemMap](capi-usbddk-usbdevicememmap.md) *devMmap | Destroys the buffer created by [OH_Usb_CreateDeviceMemMap](capi-usb-ddk-api-h.md#oh_usb_createdevicememmap). |

### OH_Usb_GetDevices()

```c
int32_t OH_Usb_GetDevices(struct Usb_DeviceArray *devices)
```

**Description**

Obtains the USB device ID list. Ensure that the pointer parameters passed in are valid. To avoid excessive memory usage, the size of the requested device ID array is recommended not to exceed 128. After using the struct, release the memory of its members; otherwise, resource leaks may occur. Besides, make sure that the obtained USB device ID has been filtered by **vid** in the driver configuration information.

<!--Device-int32_t OH_Usb_GetDevices(struct Usb_DeviceArray *devices)--><!--Device-int32_t OH_Usb_GetDevices(struct Usb_DeviceArray *devices)-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [struct Usb_DeviceArray](capi-usbddk-usb-devicearray.md) *devices | Device memory address, which is used to store the obtained device ID list and quantity. After using it, release the memory of its members; otherwise, resource leaks may occur. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode): The operation is successful. <br>[USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails. Check whether the app has obtained the **ohos.permission.ACCESS_DDK_USB** permission. <br>[USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode): The USB DDK service connection fails. Call [OH_Usb_Init](capi-usb-ddk-api-h.md#oh_usb_init) to complete initialization first. <br>[USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode): The input **devices** is a null pointer. Check the parameter validity. |

### OH_Usb_ControlTransfer()

```c
int32_t OH_Usb_ControlTransfer(uint64_t deviceID, const struct UsbControlRequestSetup *setupPacket, uint8_t *data, uint32_t timeout)
```

**Description**

Performs USB control transfer. This API returns the result synchronously.

<!--Device-int32_t OH_Usb_ControlTransfer(uint64_t deviceID, const struct UsbControlRequestSetup *setupPacket, uint8_t *data, uint32_t timeout)--><!--Device-int32_t OH_Usb_ControlTransfer(uint64_t deviceID, const struct UsbControlRequestSetup *setupPacket, uint8_t *data, uint32_t timeout)-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t deviceID | Device ID, which can be obtained by calling [OH_Usb_GetDevices](capi-usb-ddk-api-h.md#oh_usb_getdevices). It identifies the device to be communicated with. |
| [const struct UsbControlRequestSetup](capi-usbddk-usbcontrolrequestsetup.md) *setupPacket | Setup parameter that controls the transfer request, including the transfer direction and data length. |
| uint8_t *data | Requested buffer for storing input or output data. The buffer size must be the same as the value of the **wLength** field in the setup packet and cannot exceed 1,024 bytes. Otherwise, the data will be truncated. |
| uint32_t timeout | Timeout interval, in milliseconds, which is the maximum waiting time before a response is received. The value **0** indicates that the waiting time is not limited. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Number of actually transferred bytes upon success (a non-negative number). <br>[USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails. Check whether the app has obtained the **ohos.permission.ACCESS_DDK_USB** permission. <br>[USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode): The USB DDK service connection fails. Call [OH_Usb_Init](capi-usb-ddk-api-h.md#oh_usb_init) to complete initialization first. <br>[USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode): **setupPacket** or **data** is a null pointer. Check the parameter validity. <br>[USB_DDK_TIMEOUT](capi-usb-ddk-types-h.md#usbddkerrcode): Controls transfer timeout. Check the transmission parameters and device status. <br>[USB_DDK_IO_FAILED](capi-usb-ddk-types-h.md#usbddkerrcode): Controls transfer request I/O exceptions. Check the parameters and device specifications. |

### OH_Usb_GetNonRootHubs()

```c
int32_t OH_Usb_GetNonRootHubs(struct Usb_NonRootHubArray *nonRootHub)
```

**Description**

Queries and returns the non-root hub list. Ensure that the input pointer is valid. It is recommended that the number of non-root hub IDs do not exceed 128 to prevent excessive memory usage. After using the struct, release the memory of its members; otherwise, resource leaks may occur.

<!--Device-int32_t OH_Usb_GetNonRootHubs(struct Usb_NonRootHubArray *nonRootHub)--><!--Device-int32_t OH_Usb_GetNonRootHubs(struct Usb_NonRootHubArray *nonRootHub)-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [struct Usb_NonRootHubArray](capi-usbddk-usb-nonroothubarray.md) *nonRootHub | Requested non-root hub memory address, which is used to store the queried non-root hub ID list and quantity. After using it, release the memory of its members; otherwise, resource leaks may occur. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode): The query is successful. <br>[USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails. Check whether the app has obtained the **ohos.permission.ACCESS_DDK_USB** permission. <br>[USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode): The USB DDK service connection fails. Call [OH_Usb_Init](capi-usb-ddk-api-h.md#oh_usb_init) to complete initialization first. <br>[USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode): The input **nonRootHub** is a null pointer. Check the parameter validity. |

### OH_Usb_CreateDeviceMemBuffer()

```c
UsbDdkErrCode OH_Usb_CreateDeviceMemBuffer(uint64_t deviceId, uint32_t size, uint8_t **buffer)
```

**Description**

Creates a device memory buffer. To avoid resource leakage, call [OH_Usb_DestroyDeviceMemBuffer](capi-usb-ddk-api-h.md#oh_usb_destroydevicemembuffer) to destroy the buffer after the buffer has been used.

<!--Device-UsbDdkErrCode OH_Usb_CreateDeviceMemBuffer(uint64_t deviceId, uint32_t size, uint8_t **buffer)--><!--Device-UsbDdkErrCode OH_Usb_CreateDeviceMemBuffer(uint64_t deviceId, uint32_t size, uint8_t **buffer)-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 26.1.0

**Resource release**: [OH_Usb_DestroyDeviceMemBuffer](#oh_usb_destroydevicemembuffer)

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t deviceId | [in] Device ID. |
| uint32_t size | [in] Buffer size, in bytes. |
| uint8_t **buffer | [out] Data buffer, which is used to return the created buffer to the caller. |

**Returns**:

| Type | Description |
| -- | -- |
| [UsbDdkErrCode](capi-usb-ddk-types-h.md#usbddkerrcode) | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode) The API is successfully called. <br>[USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode) Permission check failed. Check whether the app has obtained the ohos.permission.ACCESS_DDK_USB permission. <br>[USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode) Failed to connect to the USB DDK service or the device driver is invalid. Call <br>[OH_Usb_Init](capi-usb-ddk-api-h.md#oh_usb_init) to complete initialization and check the device status corresponding to **deviceId**. <br>[USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode)The input parameter **buffer** is a null pointer. Check the parameter validity. <br>[USB_DDK_MEMORY_ERROR](capi-usb-ddk-types-h.md#usbddkerrcode) Memory allocation failed. Check the memory size and validity. |

### OH_Usb_DestroyDeviceMemBuffer()

```c
UsbDdkErrCode OH_Usb_DestroyDeviceMemBuffer(uint8_t **buffer)
```

**Description**

Destroy the device memory buffer. To prevent resource leakage, destroy the buffer immediately after using the buffer.

<!--Device-UsbDdkErrCode OH_Usb_DestroyDeviceMemBuffer(uint8_t **buffer)--><!--Device-UsbDdkErrCode OH_Usb_DestroyDeviceMemBuffer(uint8_t **buffer)-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint8_t **buffer | [in,out] Destroy the buffer created by [OH_Usb_CreateDeviceMemBuffer](capi-usb-ddk-api-h.md#oh_usb_createdevicemembuffer). |

**Returns**:

| Type | Description |
| -- | -- |
| [UsbDdkErrCode](capi-usb-ddk-types-h.md#usbddkerrcode) | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode) The API is successfully called. <br>[USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode)The input parameter **buffer** or ***buffer** is null, or ***buffer** is invalid. Check the parameter validity. <br>[USB_DDK_MEMORY_ERROR](capi-usb-ddk-types-h.md#usbddkerrcode) Failed to demap the memory. Please check the buffer and device status. |

### OH_Usb_WritePipe()

```c
UsbDdkErrCode OH_Usb_WritePipe(const struct UsbRequestPipe *pipe, uint8_t *buffer, uint32_t bufferSize, uint32_t offset, uint32_t writeLength, uint32_t *transferredLength)
```

**Description**

Send a pipe write request. This interface operates in synchronous mode and is suitable for interrupt transfers and bulk transfers.

<!--Device-UsbDdkErrCode OH_Usb_WritePipe(const struct UsbRequestPipe *pipe, uint8_t *buffer, uint32_t bufferSize, uint32_t offset, uint32_t writeLength, uint32_t *transferredLength)--><!--Device-UsbDdkErrCode OH_Usb_WritePipe(const struct UsbRequestPipe *pipe, uint8_t *buffer, uint32_t bufferSize, uint32_t offset, uint32_t writeLength, uint32_t *transferredLength)-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const struct UsbRequestPipe](capi-usbddk-usbrequestpipe.md) *pipe | [in] Pipe used to transfer data. |
| uint8_t *buffer | [in] Data buffer, that is, the device memory-mapped buffer. |
| uint32_t bufferSize | [in] Buffer size, in bytes. |
| uint32_t offset | [in] Start position of the data in the buffer, in bytes. |
| uint32_t writeLength | [in] Length of the buffer to be used, indicating the length of the data written from the offset position, in bytes. |
| uint32_t *transferredLength | [out] Output parameter, indicating the length of the actually transmitted data, in bytes. This parameter is valid only when the function returns 0. |

**Returns**:

| Type | Description |
| -- | -- |
| [UsbDdkErrCode](capi-usb-ddk-types-h.md#usbddkerrcode) | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode) The API is successfully called. <br>[USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode) Permission check failed. Check whether the app has obtained the ohos.permission.ACCESS_DDK_USB permission. <br>[USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode) Failed to connect to the USB DDK service. Call [OH_Usb_Init](capi-usb-ddk-api-h.md#oh_usb_init) to complete initialization. <br>[USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode) Parameter verification failed. Check the parameter validity. Possible causes: 1. **pipe**, **buffer**, or **transferredLength** is a null pointer. <br>2. **offset** is greater than **bufferSize** or the sum of **offset** and **writeLength** is greater than **bufferSize**. 3. The direction of the endpoint in **pipe** is incorrect. <br>[USB_DDK_MEMORY_ERROR](capi-usb-ddk-types-h.md#usbddkerrcode) Failed to copy the memory for storing write data. Check the memory size and validity. <br>[USB_DDK_IO_FAILED](capi-usb-ddk-types-h.md#usbddkerrcode) Data I/O error. Check parameters and device specifications. <br>[USB_DDK_TIMEOUT](capi-usb-ddk-types-h.md#usbddkerrcode) Operation timed out. Check the transmission parameters and device status. |

### OH_Usb_ReadPipe()

```c
UsbDdkErrCode OH_Usb_ReadPipe(const struct UsbRequestPipe *pipe, uint8_t *buffer, uint32_t bufferSize, uint32_t offset, uint32_t readLength, uint32_t *transferredLength)
```

**Description**

Send a pipe read request. This interface operates in synchronous mode and is suitable for interrupt transfers and bulk transfers.

<!--Device-UsbDdkErrCode OH_Usb_ReadPipe(const struct UsbRequestPipe *pipe, uint8_t *buffer, uint32_t bufferSize, uint32_t offset, uint32_t readLength, uint32_t *transferredLength)--><!--Device-UsbDdkErrCode OH_Usb_ReadPipe(const struct UsbRequestPipe *pipe, uint8_t *buffer, uint32_t bufferSize, uint32_t offset, uint32_t readLength, uint32_t *transferredLength)-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Required permission**: ohos.permission.ACCESS_DDK_USB

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const struct UsbRequestPipe](capi-usbddk-usbrequestpipe.md) *pipe | [in] Pipe used to transfer data. |
| uint8_t *buffer | [in] Data buffer, that is, the device memory-mapped buffer. |
| uint32_t bufferSize | [in] Buffer size, in bytes. |
| uint32_t offset | [in] Start position of the data in the buffer, in bytes. |
| uint32_t readLength | [in] Length of the buffer to be used, indicating the length of the data read from the offset position, in bytes. |
| uint32_t *transferredLength | [out] Output parameter, indicating the length of the actually transmitted data, in bytes. This parameter is valid only when the function returns 0. |

**Returns**:

| Type | Description |
| -- | -- |
| [UsbDdkErrCode](capi-usb-ddk-types-h.md#usbddkerrcode) | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode) The API is successfully called. <br>[USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode) Permission check failed. Check whether the app has obtained the ohos.permission.ACCESS_DDK_USB permission. <br>[USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode) Failed to connect to the USB DDK service. Call [OH_Usb_Init](capi-usb-ddk-api-h.md#oh_usb_init) to complete initialization. <br>[USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode) Parameter verification failed. Check the parameter validity. Possible causes: 1. **pipe**, **buffer**, or **transferredLength** is a null pointer. <br>2. **offset** is greater than **bufferSize** or the sum of **offset** and **readLength** is greater than **bufferSize**. 3. The direction of the endpoint in **pipe** is incorrect. <br>[USB_DDK_MEMORY_ERROR](capi-usb-ddk-types-h.md#usbddkerrcode) Failed to copy the memory for storing read data. Check the memory size and validity. <br>[USB_DDK_IO_FAILED](capi-usb-ddk-types-h.md#usbddkerrcode) Data I/O error. Check parameters and device specifications. <br>[USB_DDK_TIMEOUT](capi-usb-ddk-types-h.md#usbddkerrcode) Operation timed out. Check the transmission parameters and device status. |


