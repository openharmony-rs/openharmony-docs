# usb_ddk_api.h
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->

## Overview

Claims the USB DDK APIs used by the USB host to access USB devices.

**File to include**: <usb/usb_ddk_api.h>

**Library**: libusb_ndk.z.so

**System capability**: SystemCapability.Driver.USB.Extension

**Since**: 10

**Related module**: [UsbDdk](capi-usbddk.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [int32_t OH_Usb_Init(void)](#oh_usb_init) | Initializes the USB DDK.|
| [void OH_Usb_Release(void)](#oh_usb_release) | Releases the USB DDK.|
| [int32_t OH_Usb_ReleaseResource(void)](#oh_usb_releaseresource) | Releases the DDK.|
| [int32_t OH_Usb_GetDeviceDescriptor(uint64_t deviceId, struct UsbDeviceDescriptor *desc)](#oh_usb_getdevicedescriptor) | Obtains the device descriptor.|
| [int32_t OH_Usb_GetConfigDescriptor(uint64_t deviceId, uint8_t configIndex, struct UsbDdkConfigDescriptor ** const config)](#oh_usb_getconfigdescriptor) | Obtains the configuration descriptor. To avoid memory leakage, use [OH_Usb_FreeConfigDescriptor](capi-usb-ddk-api-h.md#oh_usb_freeconfigdescriptor) to release a descriptor after use.|
| [void OH_Usb_FreeConfigDescriptor(struct UsbDdkConfigDescriptor * const config)](#oh_usb_freeconfigdescriptor) | Releases a configuration descriptor after use to prevent memory leakage.|
| [int32_t OH_Usb_ClaimInterface(uint64_t deviceId, uint8_t interfaceIndex, uint64_t *interfaceHandle)](#oh_usb_claiminterface) | Claims a USB interface.|
| [int32_t OH_Usb_ReleaseInterface(uint64_t interfaceHandle)](#oh_usb_releaseinterface) | Releases a USB interface.|
| [int32_t OH_Usb_SelectInterfaceSetting(uint64_t interfaceHandle, uint8_t settingIndex)](#oh_usb_selectinterfacesetting) | Activates the alternate setting of a USB interface.|
| [int32_t OH_Usb_GetCurrentInterfaceSetting(uint64_t interfaceHandle, uint8_t *settingIndex)](#oh_usb_getcurrentinterfacesetting) | Obtains the activated alternate setting of a USB interface.|
| [int32_t OH_Usb_SendControlReadRequest(uint64_t interfaceHandle, const struct UsbControlRequestSetup *setup,uint32_t timeout, uint8_t *data, uint32_t *dataLen)](#oh_usb_sendcontrolreadrequest) | Sends a control read transfer request. This API works in a synchronous manner.|
| [int32_t OH_Usb_SendControlWriteRequest(uint64_t interfaceHandle, const struct UsbControlRequestSetup *setup,uint32_t timeout, const uint8_t *data, uint32_t dataLen)](#oh_usb_sendcontrolwriterequest) | Sends a control write transfer request. This API works in a synchronous manner.|
| [int32_t OH_Usb_SendPipeRequest(const struct UsbRequestPipe *pipe, UsbDeviceMemMap *devMmap)](#oh_usb_sendpiperequest) | Sends a pipe request. This API works in a synchronous manner. It applies to interrupt transfer and bulk transfer.|
| [int32_t OH_Usb_SendPipeRequestWithAshmem(const struct UsbRequestPipe *pipe, DDK_Ashmem *ashmem)](#oh_usb_sendpiperequestwithashmem) | Sends a pipe request based on the shared memory. This API returns the result synchronously. It applies to interrupt transfer and bulk transfer.|
| [int32_t OH_Usb_CreateDeviceMemMap(uint64_t deviceId, size_t size, UsbDeviceMemMap **devMmap)](#oh_usb_createdevicememmap) | Creates a buffer. To avoid resource leakage, use [OH_Usb_DestroyDeviceMemMap](capi-usb-ddk-api-h.md#oh_usb_destroydevicememmap) to destroy a buffer after use.|
| [void OH_Usb_DestroyDeviceMemMap(UsbDeviceMemMap *devMmap)](#oh_usb_destroydevicememmap) | Destroys a buffer. To prevent resource leakage, destroy a buffer in time after use.|
| [int32_t OH_Usb_GetDevices(struct Usb_DeviceArray *devices)](#oh_usb_getdevices) | Obtains the USB device ID list. Ensure that the pointer parameters passed in are valid. To avoid excessive memory usage, the size of the requested device ID array is recommended not to exceed 128. After using the struct, release the memory of its members; otherwise, resource leaks may occur. Besides, make sure that the obtained USB device ID has been filtered by **vid** in the driver configuration information.|
| [int32_t OH_Usb_ControlTransfer(uint64_t deviceID, const struct UsbControlRequestSetup *setupPacket, uint8_t *data, uint32_t timeout)](#oh_usb_controltransfer) | Performs USB control transfer. This API returns the result synchronously.|
| [int32_t OH_Usb_GetNonRootHubs(struct Usb_NonRootHubArray *nonRootHub)](#oh_usb_getnonroothubs) | Queries and returns the non-root hub list. Ensure that the input pointer is valid. It is recommended that the number of non-root hub IDs do not exceed 128 to prevent excessive memory usage. After using the struct, release the memory of its members; otherwise, resource leaks may occur.|

## Function Description

### OH_Usb_Init()

```c
int32_t OH_Usb_Init(void)
```

**Description**

Initializes the USB DDK.

**Required permissions**: ohos.permission.ACCESS_DDK_USB

**Since**: 10

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode): The operation is successful.<br>         [USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode): The USB DDK service connection fails, or an internal error occurs.<br>         [USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails.<br>         [USB_DDK_MEMORY_ERROR](capi-usb-ddk-types-h.md#usbddkerrcode): The memory allocation fails.|

### OH_Usb_Release()

```c
void OH_Usb_Release(void)
```

**Description**

Releases the USB DDK.

**Required permissions**: ohos.permission.ACCESS_DDK_USB

**Since**: 10

### OH_Usb_ReleaseResource()

```c
int32_t OH_Usb_ReleaseResource(void)
```

**Description**

Releases the USB DDK.

**Required permissions**: ohos.permission.ACCESS_DDK_USB

**Since**: 18

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode): The operation is successful.<br>         [USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails.<br>         [USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode): The USB DDK service connection fails.|

### OH_Usb_GetDeviceDescriptor()

```c
int32_t OH_Usb_GetDeviceDescriptor(uint64_t deviceId, struct UsbDeviceDescriptor *desc)
```

**Description**

Obtains the device descriptor.

**Required permissions**: ohos.permission.ACCESS_DDK_USB

**Since**: 10


**Parameters**

| Name| Description|
| -- | -- |
| uint64_t deviceId | Device ID.|
| [struct UsbDeviceDescriptor](capi-usbddk-usbdevicedescriptor.md) *desc | Device descriptor. For details, see [UsbDeviceDescriptor](capi-usbddk-usbdevicedescriptor.md).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode): The operation is successful.<br>         [USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails.<br>         [USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode): The USB DDK service connection fails.<br>         [USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode): The input **desc** is a null pointer.|

### OH_Usb_GetConfigDescriptor()

```c
int32_t OH_Usb_GetConfigDescriptor(uint64_t deviceId, uint8_t configIndex, struct UsbDdkConfigDescriptor ** const config)
```

**Description**

Obtains the configuration descriptor. To avoid memory leakage, use [OH_Usb_FreeConfigDescriptor](capi-usb-ddk-api-h.md#oh_usb_freeconfigdescriptor) to release a descriptor after use.

**Required permissions**: ohos.permission.ACCESS_DDK_USB

**Since**: 10


**Parameters**

| Name                                              | Description|
|---------------------------------------------------| -- |
| uint64_t deviceId                                 | Device ID.|
| uint8_t configIndex                               | Configuration index, which corresponds to the **bConfigurationValue** field in the USB configuration descriptor.|
| struct [UsbDdkConfigDescriptor](capi-usbddk-usbddkconfigdescriptor.md) ** const config | Configuration descriptor, which includes the standard configuration descriptor defined in the USB protocol and the associated interface descriptor and endpoint descriptor.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode): The operation is successful.<br>         [USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails.<br>         [USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode): The USB DDK service connection fails.<br>         [USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode): The input **config** is a null pointer.<br>         [USB_DDK_IO_FAILED](capi-usb-ddk-types-h.md#usbddkerrcode): An I/O exception occurs.<br>         [USB_DDK_MEMORY_ERROR](capi-usb-ddk-types-h.md#usbddkerrcode): The memory allocation fails.|

### OH_Usb_FreeConfigDescriptor()

```c
void OH_Usb_FreeConfigDescriptor(struct UsbDdkConfigDescriptor * const config)
```

**Description**

Releases a configuration descriptor after use to prevent memory leakage.

**Required permissions**: ohos.permission.ACCESS_DDK_USB

**Since**: 10


**Parameters**

| Name| Description|
| -- | -- |
| const struct [UsbDdkConfigDescriptor](capi-usbddk-usbddkconfigdescriptor.md) * const config | Configuration descriptor, which is obtained by calling [OH_Usb_GetConfigDescriptor](capi-usb-ddk-api-h.md#oh_usb_getconfigdescriptor).|

### OH_Usb_ClaimInterface()

```c
int32_t OH_Usb_ClaimInterface(uint64_t deviceId, uint8_t interfaceIndex, uint64_t *interfaceHandle)
```

**Description**

Claims a USB interface.

**Required permissions**: ohos.permission.ACCESS_DDK_USB

**Since**: 10


**Parameters**

| Name| Description|
| -- | -- |
| uint64_t deviceId | Device ID.|
| uint8_t interfaceIndex | Interface index, which corresponds to [bInterfaceNumber](capi-usbddk-usbinterfacedescriptor.md) in the USB protocol.|
| uint64_t *interfaceHandle | Interface operation handle. After the interface is claimed successfully, a value will be assigned to this parameter.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode): The operation is successful.<br>         [USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails.<br>         [USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode): The USB DDK service connection fails.<br>         [USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode): The input **interfaceHandle** is a null pointer.<br>         [USB_DDK_MEMORY_ERROR](capi-usb-ddk-types-h.md#usbddkerrcode): The memory to be allocated exceeds the limit.|

### OH_Usb_ReleaseInterface()

```c
int32_t OH_Usb_ReleaseInterface(uint64_t interfaceHandle)
```

**Description**

Releases a USB interface.

**Required permissions**: ohos.permission.ACCESS_DDK_USB

**Since**: 10


**Parameters**

| Name| Description|
| -- | -- |
| uint64_t interfaceHandle | Interface operation handle.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode): The operation is successful.<br>         [USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails.<br>         [USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode): The USB DDK service connection fails.<br>         [USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode): One or more parameters are invalid.|

### OH_Usb_SelectInterfaceSetting()

```c
int32_t OH_Usb_SelectInterfaceSetting(uint64_t interfaceHandle, uint8_t settingIndex)
```

**Description**

Activates the alternate setting of a USB interface.

**Required permissions**: ohos.permission.ACCESS_DDK_USB

**Since**: 10


**Parameters**

| Name| Description|
| -- | -- |
| uint64_t interfaceHandle | Interface operation handle.|
| uint8_t settingIndex | Alternate setting index, which corresponds to the **bAlternateSetting** field of the interface descriptor in the USB protocol.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode): The operation is successful.<br>         [USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails.<br>         [USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode): The USB DDK service connection fails.<br>         [USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode): One or more parameters are invalid.|

### OH_Usb_GetCurrentInterfaceSetting()

```c
int32_t OH_Usb_GetCurrentInterfaceSetting(uint64_t interfaceHandle, uint8_t *settingIndex)
```

**Description**

Obtains the activated alternate setting of a USB interface.

**Required permissions**: ohos.permission.ACCESS_DDK_USB

**Since**: 10


**Parameters**

| Name| Description|
| -- | -- |
| uint64_t interfaceHandle | Interface operation handle.|
| uint8_t *settingIndex | Alternate setting index, which corresponds to the **bAlternateSetting** field of the interface descriptor in the USB protocol.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode): The operation is successful.<br>         [USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails.<br>         [USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode): The USB DDK service connection fails.<br>         [USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode): The input **settingIndex** is a null pointer.|

### OH_Usb_SendControlReadRequest()

```c
int32_t OH_Usb_SendControlReadRequest(uint64_t interfaceHandle, const struct UsbControlRequestSetup *setup,uint32_t timeout, uint8_t *data, uint32_t *dataLen)
```

**Description**

Sends a control read transfer request. This API works in a synchronous manner.

**Required permissions**: ohos.permission.ACCESS_DDK_USB

**Since**: 10


**Parameters**

| Name| Description|
| -- | -- |
| uint64_t interfaceHandle | Interface operation handle.|
| [const struct UsbControlRequestSetup](capi-usbddk-usbcontrolrequestsetup.md) *setup | Request parameters. For details, see [UsbControlRequestSetup](capi-usbddk-usbcontrolrequestsetup.md).|
| uint32_t timeout | Timeout duration, in ms.|
| uint8_t *data | Data to transfer.|
| uint32_t *dataLen | Data length. The return value indicates the length of the actually read data.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode): The operation is successful.<br>         [USB_DDK_FAILED](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails.<br>         [USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode): The USB DDK service connection fails.<br>         [USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode): The input **setup**, **data**, or **dataLen** is a null pointer, or the value of **datalen** is less than the length of the read data.<br>         [USB_DDK_MEMORY_ERROR](capi-usb-ddk-types-h.md#usbddkerrcode): The attempt to copy the memory that stores the read data fails.<br>         [USB_DDK_IO_FAILED](capi-usb-ddk-types-h.md#usbddkerrcode): An I/O exception occurs.<br>         [USB_DDK_TIMEOUT](capi-usb-ddk-types-h.md#usbddkerrcode): The operation times out.|

### OH_Usb_SendControlWriteRequest()

```c
int32_t OH_Usb_SendControlWriteRequest(uint64_t interfaceHandle, const struct UsbControlRequestSetup *setup,uint32_t timeout, const uint8_t *data, uint32_t dataLen)
```

**Description**

Sends a control write transfer request. This API works in a synchronous manner.

**Required permissions**: ohos.permission.ACCESS_DDK_USB

**Since**: 10


**Parameters**

| Name| Description|
| -- | -- |
| uint64_t interfaceHandle | Interface operation handle.|
| [const struct UsbControlRequestSetup](capi-usbddk-usbcontrolrequestsetup.md) *setup | Request parameters. For details, see [UsbControlRequestSetup](capi-usbddk-usbcontrolrequestsetup.md).|
| uint32_t timeout | Timeout duration, in ms.|
| const uint8_t *data | Data to transfer.|
| uint32_t dataLen | Data length.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode): The operation is successful.<br>         [USB_DDK_FAILED](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails.<br>         [USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode): The USB DDK service connection fails.<br>         [USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode): The input **setup** or **data** is a null pointer.<br>         [USB_DDK_MEMORY_ERROR](capi-usb-ddk-types-h.md#usbddkerrcode): The attempt to copy the memory that stores the read data fails.<br>         [USB_DDK_IO_FAILED](capi-usb-ddk-types-h.md#usbddkerrcode): An I/O exception occurs.<br>         [USB_DDK_TIMEOUT](capi-usb-ddk-types-h.md#usbddkerrcode): The operation times out.|

### OH_Usb_SendPipeRequest()

```c
int32_t OH_Usb_SendPipeRequest(const struct UsbRequestPipe *pipe, UsbDeviceMemMap *devMmap)
```

**Description**

Sends a pipe request. This API works in a synchronous manner. It applies to interrupt transfer and bulk transfer.

**Required permissions**: ohos.permission.ACCESS_DDK_USB

**Since**: 10


**Parameters**

| Name| Description|
| -- | -- |
| [const struct UsbRequestPipe](capi-usbddk-usbrequestpipe.md) *pipe | Pipe used to transfer data.|
| [UsbDeviceMemMap](capi-usbddk-usbdevicememmap.md) *devMmap | Data buffer, which can be obtained by calling [OH_Usb_CreateDeviceMemMap](capi-usb-ddk-api-h.md#oh_usb_createdevicememmap).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode): The operation is successful.<br>         [USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails.<br>         [USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode): The USB DDK service connection fails.<br>         [USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode): The input **pipe** or **devMmap** is a null pointer, or the **devMmap** address is null.<br>         [USB_DDK_MEMORY_ERROR](capi-usb-ddk-types-h.md#usbddkerrcode): The attempt to copy the memory that stores the read data fails.<br>         [USB_DDK_IO_FAILED](capi-usb-ddk-types-h.md#usbddkerrcode): An I/O exception occurs.<br>         [USB_DDK_TIMEOUT](capi-usb-ddk-types-h.md#usbddkerrcode): The operation times out.|

### OH_Usb_SendPipeRequestWithAshmem()

```c
int32_t OH_Usb_SendPipeRequestWithAshmem(const struct UsbRequestPipe *pipe, DDK_Ashmem *ashmem)
```

**Description**

Sends a pipe request based on the shared memory. This API returns the result synchronously. It applies to interrupt transfer and bulk transfer.

**Required permissions**: ohos.permission.ACCESS_DDK_USB

**Since**: 12


**Parameters**

| Name                                                        | Description|
|-------------------------------------------------------------| -- |
| [const struct UsbRequestPipe](capi-usbddk-usbrequestpipe.md) *pipe | Pipe used to transfer data.|
| [DDK_Ashmem](capi-baseddk-ddk-ashmem.md) *ashmem            | Shared memory, which can be obtained through [OH_DDK_CreateAshmem](capi-ddk-api-h.md#oh_ddk_createashmem).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode): The operation is successful.<br>         [USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails.<br>         [USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode): The USB DDK service connection fails.<br>         [USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode): The input **pipe** or **ashmem** is a null pointer, or the **ashmem** address is null.<br>         [USB_DDK_MEMORY_ERROR](capi-usb-ddk-types-h.md#usbddkerrcode): The attempt to copy the memory that stores the read data fails.<br>         [USB_DDK_IO_FAILED](capi-usb-ddk-types-h.md#usbddkerrcode): An I/O exception occurs.<br>         [USB_DDK_TIMEOUT](capi-usb-ddk-types-h.md#usbddkerrcode): The operation times out.|

### OH_Usb_CreateDeviceMemMap()

```c
int32_t OH_Usb_CreateDeviceMemMap(uint64_t deviceId, size_t size, UsbDeviceMemMap **devMmap)
```

**Description**

Creates a buffer. To avoid resource leakage, use [OH_Usb_DestroyDeviceMemMap](capi-usb-ddk-api-h.md#oh_usb_destroydevicememmap) to destroy a buffer after use.

**Required permissions**: ohos.permission.ACCESS_DDK_USB

**Since**: 10


**Parameters**

| Name| Description|
| -- | -- |
| uint64_t deviceId | Device ID.|
| size_t size | Buffer size.|
| [UsbDeviceMemMap](capi-usbddk-usbdevicememmap.md) **devMmap | Data memory map, through which the created buffer is returned to the caller.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode): The operation is successful.<br>         [USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails.<br>         [USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode): The input parameter **devMmap** or ***devMmap** is a null pointer.<br>         [USB_DDK_MEMORY_ERROR](capi-usb-ddk-types-h.md#usbddkerrcode): The memory mapping fails, or the memory allocation of **devMmap** fails.|

### OH_Usb_DestroyDeviceMemMap()

```c
void OH_Usb_DestroyDeviceMemMap(UsbDeviceMemMap *devMmap)
```

**Description**

Destroys a buffer. To prevent resource leakage, destroy a buffer in time after use.

**Required permissions**: ohos.permission.ACCESS_DDK_USB

**Since**: 10


**Parameters**

| Name| Description|
| -- | -- |
| [UsbDeviceMemMap](capi-usbddk-usbdevicememmap.md) *devMmap | Destroys the buffer created by calling [OH_Usb_CreateDeviceMemMap](capi-usb-ddk-api-h.md#oh_usb_createdevicememmap).|

### OH_Usb_GetDevices()

```c
int32_t OH_Usb_GetDevices(struct Usb_DeviceArray *devices)
```

**Description**

Obtains the USB device ID list. Ensure that the pointer parameters passed in are valid. To avoid excessive memory usage, the size of the requested device ID array is recommended not to exceed 128. After using the struct, release the memory of its members; otherwise, resource leaks may occur. Besides, make sure that the obtained USB device ID has been filtered by **vid** in the driver configuration information.

**Required permissions**: ohos.permission.ACCESS_DDK_USB

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [struct Usb_DeviceArray](capi-usbddk-usb-devicearray.md) *devices | Device memory address, which is used to store the obtained device ID list and quantity.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode): The operation is successful.<br>         [USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails.<br>         [USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode): The USB DDK service connection fails.<br>         [USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode): The input **devices** is a null pointer.|

### OH_Usb_ControlTransfer()

```c
int32_t OH_Usb_ControlTransfer(uint64_t deviceID, const struct UsbControlRequestSetup *setupPacket, uint8_t *data, uint32_t timeout)
```

**Description**

Performs USB control transfer. This API returns the result synchronously.

**Required permissions**: ohos.permission.ACCESS_DDK_USB

**Since**: 26.0.0


**Parameters**

| Name| Description|
| -- | -- |
| uint64_t deviceID | Device ID.|
| [const struct UsbControlRequestSetup](capi-usbddk-usbcontrolrequestsetup.md) *setupPacket | Setup packet parameter that controls the transfer request, including the transfer direction and data length.|
| uint8_t *data | Requested buffer for storing input or output data. The buffer size must be the same as the value of the **wLength** field in the setup packet and cannot exceed 1,024 bytes. Otherwise, the data will be truncated.|
| uint32_t timeout | Timeout interval, in milliseconds, which is the maximum waiting time before a response is received. The value **0** means to wait infinitely.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Number of actually transferred bytes upon success (a non-negative number).<br>         [USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails.<br>         [USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode): DDK initialization fails. Call **OH_Usb_Init** to initialize the DDK.<br>         [USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode): The **setupPacket** or **data** parameter is invalid.<br>         [USB_DDK_TIMEOUT](capi-usb-ddk-types-h.md#usbddkerrcode): Controls transfer timeout.<br>         [USB_DDK_IO_FAILED](capi-usb-ddk-types-h.md#usbddkerrcode): Controls transfer request I/O exceptions.|

### OH_Usb_GetNonRootHubs()

```c
int32_t OH_Usb_GetNonRootHubs(struct Usb_NonRootHubArray *nonRootHub)
```

**Description**

Queries and returns the non-root hub list. Ensure that the input pointer is valid. It is recommended that the number of non-root hub IDs do not exceed 128 to prevent excessive memory usage. After using the struct, release the memory of its members; otherwise, resource leaks may occur.

**Required permissions**: ohos.permission.ACCESS_DDK_USB

**Since**: 26.0.0


**Parameters**

| Name| Description|
| -- | -- |
| [struct Usb_NonRootHubArray](capi-usbddk-usb-nonroothubarray.md) *nonRootHub | Requested non-root hub memory address, which is used to store the queried non-root hub ID list and quantity.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | [USB_DDK_SUCCESS](capi-usb-ddk-types-h.md#usbddkerrcode): The query is successful.<br>         [USB_DDK_NO_PERM](capi-usb-ddk-types-h.md#usbddkerrcode): The permission check fails.<br>         [USB_DDK_INVALID_OPERATION](capi-usb-ddk-types-h.md#usbddkerrcode): DDK initialization fails. Call **OH_Usb_Init** to initialize the DDK.<br>         [USB_DDK_INVALID_PARAMETER](capi-usb-ddk-types-h.md#usbddkerrcode): The input **nonRootHub** is a null pointer.|
