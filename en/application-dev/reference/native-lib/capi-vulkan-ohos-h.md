# vulkan_ohos.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @GaoPan_t-->
<!--Designer: @vvan9cha0-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=740dcdea7b2e0f63c4b99baa0eb4f2e92e763430 translatedAt=2026-11-04T02:54:04.520Z pushedAt=2026-11-04T03:24:28.630Z nl=1 -->

## Overview

The file declares the Vulkan interfaces extended by OpenHarmony.

**File to include**: <vulkan/vulkan_ohos.h>

**Library**: libvulkan.so

**System Capability**: SystemCapability.Graphic.Vulkan 

**Since**: 10

**Related module**: [Vulkan](capi-vulkan.md)

## Summary

### Structs

| Name                                                                                     | typedef Keyword                        | Description                              |
|-----------------------------------------------------------------------------------------|------------------------------------|----------------------------------|
| [VkSurfaceCreateInfoOHOS](capi-vulkan-vksurfacecreateinfoohos.md)                       | VkSurfaceCreateInfoOHOS            | Describes the parameters required for creating a Vulkan surface.       |
| [VkNativeBufferOHOS](capi-vulkan-vknativebufferohos.md) | VkNativeBufferOHOS | Describes the parameters of the device memory.|
| [VkSwapchainImageCreateInfoOHOS](capi-vulkan-vkswapchainimagecreateinfoohos.md) | VkSwapchainImageCreateInfoOHOS | Describes the parameters required for creating an image.|
| [VkPhysicalDevicePresentationPropertiesOHOS](capi-vulkan-vkphysicaldevicepresentationpropertiesohos.md) | VkPhysicalDevicePresentationPropertiesOHOS | Describes the parameters of the device display properties.|
| [VkNativeBufferUsageOHOS](capi-vulkan-vknativebufferusageohos.md)                       | VkNativeBufferUsageOHOS            | Describes the usage of the NativeBuffer.|
| [VkNativeBufferPropertiesOHOS](capi-vulkan-vknativebufferpropertiesohos.md)             | VkNativeBufferPropertiesOHOS       | Describes the properties of the NativeBuffer.             |
| [VkNativeBufferFormatPropertiesOHOS](capi-vulkan-vknativebufferformatpropertiesohos.md) | VkNativeBufferFormatPropertiesOHOS | Describes the format properties of the NativeBuffer.         |
| [VkImportNativeBufferInfoOHOS](capi-vulkan-vkimportnativebufferinfoohos.md)             | VkImportNativeBufferInfoOHOS       | Describes the pointer to an OH_NativeBuffer struct.       |
| [VkMemoryGetNativeBufferInfoOHOS](capi-vulkan-vkmemorygetnativebufferinfoohos.md)       | VkMemoryGetNativeBufferInfoOHOS    | Used to obtain an OH_NativeBuffer from the Vulkan memory.  |
| [VkExternalFormatOHOS](capi-vulkan-vkexternalformatohos.md)                             | VkExternalFormatOHOS               | Describes an externally defined format.                   |
| [NativeWindow](capi-vulkan-nativewindow.md)                                             | OHNativeWindow                     | Describes a native window.                           |
| [OHBufferHandle](capi-vulkan-ohbufferhandle.md) | - | Describes the buffer handle, which is used to transfer and obtain buffer information.|
| [OH_NativeBuffer](capi-vulkan-oh-nativebuffer.md)                                   | -                                  | Describes the OH_NativeBuffer struct.                                |

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [VkSwapchainImageUsageFlagBitsOHOS](#vkswapchainimageusageflagbitsohos) | VkSwapchainImageUsageFlagBitsOHOS | Enumerates the image usage flags.|

### Variables

| Name | typedef Keyword | Description |
| -- | -- | -- |
| VkFlags | VkSwapchainImageUsageFlagsOHOS | Bitmask type for setting masks.<br>**Since:** 10 |
| VkFlags | VkSurfaceCreateFlagsOHOS | VkFlags bitmask reserved for use during Vulkan Surface creation.<br>**Since:** 10 |

### Macros

| Name| Description|
| -- | -- |
| VK_OHOS_surface 1 | Surface extension macro definition of OpenHarmony.<br>**Since**: 10|
| VK_OHOS_SURFACE_SPEC_VERSION      1 | Surface extension version of OpenHarmony.<br>**Since**: 10|
| VK_OHOS_SURFACE_EXTENSION_NAME    "VK_OHOS_surface" | Surface extension name of OpenHarmony.<br>**Since**: 10|
| VK_OHOS_native_buffer 1 | **native_buffer** extension macro definition.<br>**Since**: 10|
| VK_OHOS_NATIVE_BUFFER_SPEC_VERSION 1 | **native_buffer** extension version.<br>**Since**: 10|
| VK_OHOS_NATIVE_BUFFER_EXTENSION_NAME "VK_OHOS_native_buffer" | **native_buffer** extension name.<br>**Since**: 10|
| VK_OHOS_external_memory 1 | External memory extension macro definition of OpenHarmony.<br>**Since**: 10|
| VK_OHOS_EXTERNAL_MEMORY_SPEC_VERSION 1 | External memory extension version of OpenHarmony.<br>**Since**: 10|
| VK_OHOS_EXTERNAL_MEMORY_EXTENSION_NAME "VK_OHOS_external_memory" | External memory extension name of OpenHarmony.<br>**Since**: 10|

### Functions

| Name                                                                                                                                                                                                                    | typedef Keyword             | Description                         |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------|-----------------------------|
| [VkResult (VKAPI_PTR *PFN_vkCreateSurfaceOHOS)(VkInstance instance, const VkSurfaceCreateInfoOHOS* pCreateInfo, const VkAllocationCallbacks* pAllocator, VkSurfaceKHR* pSurface)](#pfn_vkcreatesurfaceohos)            | PFN_vkCreateSurfaceOHOS | Defines the function pointer for creating a Vulkan surface.   |
| [VKAPI_ATTR VkResult VKAPI_CALL vkCreateSurfaceOHOS(VkInstance instance, const VkSurfaceCreateInfoOHOS* pCreateInfo, const VkAllocationCallbacks* pAllocator, VkSurfaceKHR* pSurface)](#vkcreatesurfaceohos)           | -                       | Creates a Vulkan surface.          |
| [VkResult (VKAPI_PTR *PFN_vkGetNativeBufferPropertiesOHOS)(VkDevice device, const struct OH_NativeBuffer* buffer, VkNativeBufferPropertiesOHOS* pProperties)](#pfn_vkgetnativebufferpropertiesohos)                    | PFN_vkGetNativeBufferPropertiesOHOS    |  Defines a function pointer used to obtain OH_NativeBuffer properties.|
| [VkResult (VKAPI_PTR *PFN_vkGetMemoryNativeBufferOHOS)(VkDevice device, const VkMemoryGetNativeBufferInfoOHOS* pInfo, struct OH_NativeBuffer** pBuffer)](#pfn_vkgetmemorynativebufferohos)                             | PFN_vkGetMemoryNativeBufferOHOS             |  Defines a function pointer used to obtain an OH_NativeBuffer instance.|
| [VKAPI_ATTR VkResult VKAPI_CALL vkGetNativeBufferPropertiesOHOS(VkDevice device, const struct OH_NativeBuffer* buffer, VkNativeBufferPropertiesOHOS* pProperties)](#vkgetnativebufferpropertiesohos)                   | -                       | Obtains the properties of an OH_NativeBuffer instance.|
| [VKAPI_ATTR VkResult VKAPI_CALL vkGetMemoryNativeBufferOHOS(VkDevice device, const VkMemoryGetNativeBufferInfoOHOS* pInfo, struct OH_NativeBuffer** pBuffer)](#vkgetmemorynativebufferohos)                            | -                       | Obtains an OH_NativeBuffer instance.|
| [VKAPI_ATTR VkResult VKAPI_CALL vkGetSwapchainGrallocUsageOHOS(VkDevice device, VkFormat format, VkImageUsageFlags imageUsage, uint64_t* grallocUsage)](#vkgetswapchaingrallocusageohos)                               | -                       | Returns appropriate Gralloc (memory allocator) usage flags according to the given Vulkan device, image format, and image usage flags. |
| [VKAPI_ATTR VkResult VKAPI_CALL vkAcquireImageOHOS(VkDevice device, VkImage image, int32_t nativeFenceFd, VkSemaphore semaphore, VkFence fence)](#vkacquireimageohos)                                                  | -                       | Used to obtain ownership of all of the swapchain image and import the external signal Fence into the VkSemaphore object and VkFence object. |
| [VKAPI_ATTR VkResult VKAPI_CALL vkQueueSignalReleaseImageOHOS(VkQueue queue, uint32_t waitSemaphoreCount, const VkSemaphore* pWaitSemaphores, VkImage image, int32_t* pNativeFenceFd)](#vkqueuesignalreleaseimageohos) | -                       | After the current image is used, releases a signal to the system hardware buffer through this function so that other components can access the image. |
| [VkResult (VKAPI_PTR *PFN_vkSetNativeFenceFdOpenHarmony)(VkDevice device, int32_t nativeFenceFd, VkSemaphore semaphore, VkFence fence)](#vkapi_ptr-pfn_vksetnativefencefdopenharmony) | VKAPI_PTR \*PFN_vkSetNativeFenceFdOpenHarmony | This API has been deprecated.|
| [typedef VkResult (VKAPI_PTR *PFN_vkGetNativeFenceFdOpenHarmony)(VkQueue queue, uint32_t waitSemaphoreCount, const VkSemaphore* pWaitSemaphores, VkImage image, int32_t* pNativeFenceFd)](#vkapi_ptr-pfn_vkgetnativefencefdopenharmony) | VKAPI_PTR \*PFN_vkGetNativeFenceFdOpenHarmony | This API has been deprecated.|
| [VkResult (VKAPI_PTR *PFN_vkGetSwapchainGrallocUsageOHOS)(VkDevice device, VkFormat format, VkImageUsageFlags imageUsage, uint64_t* grallocUsage)](#vkapi_ptr-pfn_vkgetswapchaingrallocusageohos) | VKAPI_PTR \*PFN_vkGetSwapchainGrallocUsageOHOS | Returns appropriate Gralloc (memory allocator) usage flags according to the given Vulkan device, image format, and image usage flags. Application developers do not need to use this interface. |
| [VkResult (VKAPI_PTR *PFN_vkAcquireImageOHOS)(VkDevice device, VkImage image, int32_t nativeFenceFd, VkSemaphore semaphore, VkFence fence)](#vkapi_ptr-pfn_vkacquireimageohos) | VKAPI_PTR \*PFN_vkAcquireImageOHOS | Used to obtain ownership of all of the swapchain image and import the external signal Fence into the VkSemaphore object and VkFence object. Application developers do not need to use this interface.|
| [typedef VkResult (VKAPI_PTR *PFN_vkQueueSignalReleaseImageOHOS)(VkQueue queue, uint32_t waitSemaphoreCount, const VkSemaphore* pWaitSemaphores, VkImage image, int32_t* pNativeFenceFd)](#vkapi_ptr-pfn_vkqueuesignalreleaseimageohos) | VKAPI_PTR \*PFN_vkQueueSignalReleaseImageOHOS | After the current image is used, releases a signal to the system hardware buffer through this function so that other components can access the image. Application developers do not need to use this interface. |
| [VKAPI_ATTR VkResult VKAPI_CALL vkSetNativeFenceFdOpenHarmony(VkDevice device, int32_t nativeFenceFd, VkSemaphore semaphore, VkFence fence)](#vksetnativefencefdopenharmony) | - | This API has been deprecated.|
| [VKAPI_ATTR VkResult VKAPI_CALL vkGetNativeFenceFdOpenHarmony(VkQueue queue, uint32_t waitSemaphoreCount, const VkSemaphore* pWaitSemaphores, VkImage image, int32_t* pNativeFenceFd)](#vkgetnativefencefdopenharmony) | - | This API has been deprecated.|


## Enum Description

### VkSwapchainImageUsageFlagBitsOHOS

```c
enum VkSwapchainImageUsageFlagBitsOHOS
```

**Description**

Enumerates the image usage flags.

**Since**: 10

| Value| Description|
| -- | -- |
| VK_SWAPCHAIN_IMAGE_USAGE_SHARED_BIT_OHOS = 0x00000001 | Shared image flag.|
| VK_SWAPCHAIN_IMAGE_USAGE_FLAG_BITS_MAX_ENUM_OHOS = 0x7FFFFFFF | Maximum value.|

## Function Description

###  PFN_vkCreateSurfaceOHOS()

```c
typedef VkResult (VKAPI_PTR *PFN_vkCreateSurfaceOHOS)(VkInstance instance, const VkSurfaceCreateInfoOHOS* pCreateInfo, const VkAllocationCallbacks* pAllocator, VkSurfaceKHR* pSurface)
```

**Description**

Defines the function pointer for creating a Vulkan surface.

**System capability**: SystemCapability.Graphic.Vulkan

**Since**: 10


**Parameters**

| Name| Description|
| -- | -- |
| VkInstance instance | Vulkan instance.|
| [const VkSurfaceCreateInfoOHOS](capi-vulkan-vksurfacecreateinfoohos.md)* pCreateInfo | Pointer to the VkSurfaceCreateInfoOHOS struct, including the parameters required for creating a Vulkan surface.|
| const VkAllocationCallbacks*   pAllocator | Pointer to a callback function for custom memory allocation. If custom memory allocation is not required, pass in NULL, and the default memory allocation function is used.|
| VkSurfaceKHR* pSurface | Pointer to the Vulkan surface created. The type is **VkSurfaceKHR**.|

**Returns**

| Type| Description|
| -- | -- |
| VkResult  | **VK_SUCCESS**. If the operation fails, an error code of the VkResult type is returned.|

### vkCreateSurfaceOHOS()

```c
VKAPI_ATTR VkResult VKAPI_CALL vkCreateSurfaceOHOS(VkInstance instance, const VkSurfaceCreateInfoOHOS* pCreateInfo, const VkAllocationCallbacks* pAllocator, VkSurfaceKHR* pSurface)
```

**Description**

Creates a Vulkan surface.

**System capability**: SystemCapability.Graphic.Vulkan

**Since**: 10


**Parameters**

| Name| Description|
| -- | -- |
| VkInstance instance | Vulkan instance.|
| [const VkSurfaceCreateInfoOHOS](capi-vulkan-vksurfacecreateinfoohos.md)* pCreateInfo | Pointer to the VkSurfaceCreateInfoOHOS struct, including the parameters required for creating a Vulkan surface.|
| const VkAllocationCallbacks* pAllocator | Pointer to a callback function for custom memory allocation. If custom memory allocation is not required, pass in NULL, and the default memory allocation function is used.|
| VkSurfaceKHR* pSurface | Pointer to the Vulkan surface created. The type is **VkSurfaceKHR**.|

**Returns**

| Type| Description|
| -- | -- |
| VkResult  | One of the following error codes of the VkResult type:<br> **VK_SUCCESS**: The operation is successful.<br> **VK_ERROR_OUT_OF_HOST_MEMORY**: The VkSurfaceKHR memory fails to be allocated.<br> **VK_ERROR_SURFACE_LOST_KHR**: The NativeWindow operation fails.|

### PFN_vkGetNativeBufferPropertiesOHOS()

```c
typedef VkResult (VKAPI_PTR *PFN_vkGetNativeBufferPropertiesOHOS)(VkDevice device, const struct OH_NativeBuffer* buffer, VkNativeBufferPropertiesOHOS* pProperties)
```

**Description**

Defines a function pointer used to obtain OH_NativeBuffer properties.

**System capability**: SystemCapability.Graphic.Vulkan

**Since**: 10


**Parameters**

| Name                                                                   | Description|
|------------------------------------------------------------------------| -- |
| VkDevice device                                                        | VkDevice object.|
| const [struct OH_NativeBuffer](capi-vulkan-oh-nativebuffer.md)* buffer | Pointer to an OH_NativeBuffer struct.|
| [VkNativeBufferPropertiesOHOS](capi-vulkan-vknativebufferpropertiesohos.md)* pProperties                          | Pointer to the struct holding the properties of OH_NativeBuffer.|

**Returns**

| Type| Description|
| -- | -- |
| VkResult | **VK_SUCCESS**. If the operation fails, an error code of the VkResult type is returned.|

### PFN_vkGetMemoryNativeBufferOHOS()

```c
typedef VkResult (VKAPI_PTR *PFN_vkGetMemoryNativeBufferOHOS)(VkDevice device, const VkMemoryGetNativeBufferInfoOHOS* pInfo, struct OH_NativeBuffer** pBuffer)
```

**Description**

Defines a function pointer used to obtain an OH_NativeBuffer instance.

**System capability**: SystemCapability.Graphic.Vulkan

**Since**: 10


**Parameters**

| Name| Description|
| -- | -- |
| VkDevice device | VkDevice object.|
| [const VkMemoryGetNativeBufferInfoOHOS](capi-vulkan-vkmemorygetnativebufferinfoohos.md)* pInfo | Pointer to a VkMemoryGetNativeBufferInfoOHOS struct.|
| [struct OH_NativeBuffer](capi-vulkan-oh-nativebuffer.md)** pBuffer | Pointer to the OH_NativeBuffer obtained.|

**Returns**

| Type| Description|
| -- | -- |
| VkResult | **VK_SUCCESS**. If the operation fails, an error code of the VkResult type is returned.|

### vkGetNativeBufferPropertiesOHOS()

```c
VKAPI_ATTR VkResult VKAPI_CALL vkGetNativeBufferPropertiesOHOS(VkDevice device, const struct OH_NativeBuffer* buffer, VkNativeBufferPropertiesOHOS* pProperties)
```

**Description**

Obtains the properties of an OH_NativeBuffer instance.

**System capability**: SystemCapability.Graphic.Vulkan

**Since**: 10


**Parameters**

| Name| Description|
| -- | -- |
| VkDevice device | VkDevice object.|
| const [struct OH_NativeBuffer](capi-vulkan-oh-nativebuffer.md)* buffer | Pointer to an OH_NativeBuffer struct.|
| [VkNativeBufferPropertiesOHOS](capi-vulkan-vknativebufferpropertiesohos.md)* pProperties | Pointer to the struct holding the properties of OH_NativeBuffer.|

**Returns**

| Type| Description|
| -- | -- |
| VkResult | One of the following error codes of the VkResult type:<br> **VK_SUCCESS**: The operation is successful.<br> **VK_ERROR_INVALID_EXTERNAL_HANDLE_KHR**: An input parameter is abnormal.<br> **VK_ERROR_OUT_OF_DEVICE_MEMORY**: The device memory is insufficient.|

### vkGetMemoryNativeBufferOHOS()

```c
VKAPI_ATTR VkResult VKAPI_CALL vkGetMemoryNativeBufferOHOS(VkDevice device, const VkMemoryGetNativeBufferInfoOHOS* pInfo, struct OH_NativeBuffer** pBuffer)
```

**Description**

Obtains an OH_NativeBuffer instance.

**System capability**: SystemCapability.Graphic.Vulkan

**Since**: 10


**Parameters**

| Name| Description|
| -- | -- |
| VkDevice device | VkDevice object.|
| [const VkMemoryGetNativeBufferInfoOHOS](capi-vulkan-vkmemorygetnativebufferinfoohos.md)* pInfo | Pointer to a VkMemoryGetNativeBufferInfoOHOS struct.|
| [struct OH_NativeBuffer](capi-vulkan-oh-nativebuffer.md)** pBuffer | Pointer to the OH_NativeBuffer obtained.|

**Returns**

| Type| Description|
| -- | -- |
| VkResult | One of the following error codes of the VkResult type:<br> **VK_SUCCESS**: The operation is successful.<br> **VK_ERROR_OUT_OF_HOST_MEMORY**: The input parameter **pInfo** is abnormal or the obtained **pBuffer** is abnormal.|

### vkGetSwapchainGrallocUsageOHOS()

```c
VKAPI_ATTR VkResult VKAPI_CALL vkGetSwapchainGrallocUsageOHOS(VkDevice device, VkFormat format, VkImageUsageFlags imageUsage, uint64_t* grallocUsage)
```

**Description**

Returns appropriate Gralloc (memory allocator) usage flags according to the given Vulkan device, image format, and image usage. Application developers do not need to use this interface.

**System capability**: SystemCapability.Graphic.Vulkan

**Since**: 10

**Deprecated from**: 23


**Parameters**

| Name| Description|
| -- | -- |
| VkDevice device | VkDevice object.|
| VkFormat format | Image format.|
| VkImageUsageFlags imageUsage | Image use flag.|
| uint64_t* grallocUsage | Output parameter, returns the Gralloc (memory allocator) usage flags. |

**Returns**

| Type| Description|
| -- | -- |
| VkResult | One of the following error codes of the VkResult type:<br> **VK_SUCCESS**: The operation is successful.<br> **VK_ERROR_INITIALIZATION_FAILED**: An input parameter is abnormal.|

### VKAPI_PTR *PFN_vkGetSwapchainGrallocUsageOHOS()

```c
typedef VkResult (VKAPI_PTR *PFN_vkGetSwapchainGrallocUsageOHOS)(VkDevice device, VkFormat format, VkImageUsageFlags imageUsage, uint64_t* grallocUsage)
```

**Description**

Returns appropriate Gralloc (memory allocator) usage flags according to the given Vulkan device, image format, and image usage. Application developers do not need to use this interface.

**System capability**: SystemCapability.Graphic.Vulkan

**Since**: 10

**Deprecated from**: 23

**Parameters**

| Name| Description|
| -- | -- |
| VkDevice device | VkDevice object.|
| VkFormat format | Image format.|
| VkImageUsageFlags imageUsage | Image use flag.|
| uint64_t\* grallocUsage | Output parameter, which returns the Gralloc (memory allocator) usage flags. |

**Returns**

| Type| Description|
| -- | -- |
| VkResult | One of the following error codes of the VkResult type:<br>**VK_SUCCESS**: The operation is successful.<br>**VK_ERROR_INITIALIZATION_FAILED**: An input parameter is abnormal.|

### vkAcquireImageOHOS()

```c
VKAPI_ATTR VkResult VKAPI_CALL vkAcquireImageOHOS(VkDevice device, VkImage image, int32_t nativeFenceFd, VkSemaphore semaphore, VkFence fence)
```

**Description**

Used to obtain ownership of all of the swapchain image and import the external signal Fence into the VkSemaphore object and VkFence object. Application developers do not need to use this interface.

**System capability**: SystemCapability.Graphic.Vulkan

**Since**: 10

**Deprecated from**: 23


**Parameters**

| Name| Description|
| -- | -- |
| VkDevice device | VkDevice object.|
| VkImage image | Vulkan image to obtain.|
| int32_t nativeFenceFd | File descriptor of the native fence.|
| VkSemaphore semaphore | Vulkan semaphore indicating that the image is available.|
| VkFence fence | Vulkan fence used for synchronization when the image acquisition is complete.|

**Returns**

| Type| Description|
| -- | -- |
| VkResult | One of the following error codes of the VkResult type:<br> **VK_SUCCESS**: The operation is successful.<br> **VK_ERROR_OUT_OF_HOST_MEMORY**: The host memory is insufficient.|

### VKAPI_PTR *PFN_vkAcquireImageOHOS()

```c
typedef VkResult (VKAPI_PTR *PFN_vkAcquireImageOHOS)(VkDevice device, VkImage image, int32_t nativeFenceFd, VkSemaphore semaphore, VkFence fence)
```

**Description**

Used to obtain ownership of all of the swapchain image and import the external signal Fence into the VkSemaphore object and VkFence object. Application developers do not need to use this interface.

**System capability**: SystemCapability.Graphic.Vulkan

**Since**: 10

**Deprecated from**: 23

**Parameters**

| Name| Description|
| -- | -- |
| VkDevice device | VkDevice object.|
| VkImage image | Vulkan image to obtain.|
| int32_t nativeFenceFd | File descriptor of the native fence.|
| VkSemaphore semaphore | Vulkan semaphore indicating that the image is available.|
| VkFence fence | Vulkan fence used for synchronization when the image acquisition is complete.|

**Returns**

| Type| Description|
| -- | -- |
| VkResult | One of the following error codes of the VkResult type:<br>**VK_SUCCESS**: The operation is successful.<br>**VK_ERROR_OUT_OF_HOST_MEMORY**: The host memory is insufficient.|

### vkQueueSignalReleaseImageOHOS()

```c
VKAPI_ATTR VkResult VKAPI_CALL vkQueueSignalReleaseImageOHOS(VkQueue queue, uint32_t waitSemaphoreCount, const VkSemaphore* pWaitSemaphores, VkImage image, int32_t* pNativeFenceFd)
```

**Description**

After the current image is used, this function sends a release signal to the system hardware buffer so that other components can access the image. Application developers do not need to use this interface.

**System capability**: SystemCapability.Graphic.Vulkan

**Since**: 10

**Deprecated from**: 23


**Parameters**

| Name| Description|
| -- | -- |
| VkQueue queue | Handle to the Vulkan queue.|
| uint32_t waitSemaphoreCount | Number of semaphores to wait on.|
| const VkSemaphore* pWaitSemaphores | Pointer to the array of semaphores to wait on.|
| VkImage image | Handle to the Vulkan image to be released.|
| int32_t* pNativeFenceFd | Pointer to the file descriptor of the fence.|

**Returns**

| Type| Description|
| -- | -- |
| VkResult | One of the following error codes of the VkResult type:<br> **VK_SUCCESS**: The operation is successful.<br> **VK_ERROR_DEVICE_LOST**: The Vulkan device link is lost.<br> **VK_ERROR_OUT_OF_HOST_MEMORY**: The host memory is insufficient.|

### VKAPI_PTR *PFN_vkQueueSignalReleaseImageOHOS()

```c
typedef VkResult (VKAPI_PTR *PFN_vkQueueSignalReleaseImageOHOS)(VkQueue queue, uint32_t waitSemaphoreCount, const VkSemaphore* pWaitSemaphores, VkImage image, int32_t* pNativeFenceFd)
```

**Description**

After the current image is used, this function sends a release signal to the system hardware buffer so that other components can access the image. Application developers do not need to use this interface.

**System capability**: SystemCapability.Graphic.Vulkan

**Since**: 10

**Deprecated from**: 23

**Parameters**

| Name| Description|
| -- | -- |
| VkQueue queue | Handle to the Vulkan queue.|
| uint32_t waitSemaphoreCount | Number of semaphores to wait on.|
| const VkSemaphore\* pWaitSemaphores | Pointer to the array of semaphores to wait on.|
| images | Handle to the Vulkan image to be released.|
| int32_t\* pNativeFenceFd | Pointer to the file descriptor of the fence.|

**Returns**

| Type| Description|
| -- | -- |
| VkResult | One of the following error codes of the VkResult type:<br>**VK_SUCCESS**: The operation is successful.<br>**VK_ERROR_DEVICE_LOST**: The Vulkan device link is lost.<br>**VK_ERROR_OUT_OF_HOST_MEMORY**: The host memory is insufficient.|


### VKAPI_PTR *PFN_vkSetNativeFenceFdOpenHarmony()

```c
typedef VkResult (VKAPI_PTR *PFN_vkSetNativeFenceFdOpenHarmony)(VkDevice device, int32_t nativeFenceFd, VkSemaphore semaphore, VkFence fence)
```

**Description**

This API has been deprecated.

**Since**: 10

**Deprecated from**: 10

**Substitute**: [PFN_vkAcquireImageOHOS](#vkapi_ptr-pfn_vkacquireimageohos)

### VKAPI_PTR *PFN_vkGetNativeFenceFdOpenHarmony()

```c
typedef VkResult (VKAPI_PTR *PFN_vkGetNativeFenceFdOpenHarmony)(VkQueue queue, uint32_t waitSemaphoreCount, const VkSemaphore* pWaitSemaphores, VkImage image, int32_t* pNativeFenceFd)
```

**Description**

This API has been deprecated.

**Since**: 10

**Deprecated from**: 10

**Substitute**: [PFN_vkQueueSignalReleaseImageOHOS](#vkapi_ptr-pfn_vkqueuesignalreleaseimageohos)

### vkSetNativeFenceFdOpenHarmony()

```c
VKAPI_ATTR VkResult VKAPI_CALL vkSetNativeFenceFdOpenHarmony(VkDevice device, int32_t nativeFenceFd, VkSemaphore semaphore, VkFence fence)
```

**Description**

This API has been deprecated.

**Since**: 10

**Deprecated from**: 10

**Substitute**: [vkAcquireImageOHOS](capi-vulkan-ohos-h.md#vkacquireimageohos)

### vkGetNativeFenceFdOpenHarmony()

```c
VKAPI_ATTR VkResult VKAPI_CALL vkGetNativeFenceFdOpenHarmony(VkQueue queue, uint32_t waitSemaphoreCount, const VkSemaphore* pWaitSemaphores, VkImage image, int32_t* pNativeFenceFd)
```

**Description**

This API has been deprecated.

**Since**: 10

**Deprecated from**: 10

**Substitute**: [vkQueueSignalReleaseImageOHOS](capi-vulkan-ohos-h.md#vkqueuesignalreleaseimageohos)