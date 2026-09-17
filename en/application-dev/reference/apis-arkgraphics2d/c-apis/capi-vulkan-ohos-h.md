# vulkan_ohos.h

## Overview

Declares the Vulkan APIs extended by OpenHarmony. File to include: <vulkan/vulkan.h>

**Library**: libvulkan.so

**System capability**: SystemCapability.Graphic.Vulkan

**Since**: 10

**Related module**: [Vulkan](capi-vulkan.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [VkSurfaceCreateInfoOHOS](capi-vulkan-vksurfacecreateinfoohos.md) | VkSurfaceCreateInfoOHOS | Defines the parameters required for creating a Vulkan surface. |
| [VkNativeBufferOHOS](capi-vulkan-vknativebufferohos.md) | VkNativeBufferOHOS | move to vk_ohos_native_buffer.h |
| [VkSwapchainImageCreateInfoOHOS](capi-vulkan-vkswapchainimagecreateinfoohos.md) | VkSwapchainImageCreateInfoOHOS | move to vk_ohos_native_buffer.h |
| [VkPhysicalDevicePresentationPropertiesOHOS](capi-vulkan-vkphysicaldevicepresentationpropertiesohos.md) | VkPhysicalDevicePresentationPropertiesOHOS | move to vk_ohos_native_buffer.h |
| [VkNativeBufferUsageOHOS](capi-vulkan-vknativebufferusageohos.md) | VkNativeBufferUsageOHOS | Defines the usage of a <b>OH_NativeBuffer</b>. |
| [VkNativeBufferPropertiesOHOS](capi-vulkan-vknativebufferpropertiesohos.md) | VkNativeBufferPropertiesOHOS | Defines the properties of a <b>OH_NativeBuffer</b>. |
| [VkNativeBufferFormatPropertiesOHOS](capi-vulkan-vknativebufferformatpropertiesohos.md) | VkNativeBufferFormatPropertiesOHOS | Defines the format properties of a <b>OH_NativeBuffer</b>. |
| [VkImportNativeBufferInfoOHOS](capi-vulkan-vkimportnativebufferinfoohos.md) | VkImportNativeBufferInfoOHOS | Defines the pointer to an <b>OH_NativeBuffer</b> struct. |
| [VkMemoryGetNativeBufferInfoOHOS](capi-vulkan-vkmemorygetnativebufferinfoohos.md) | VkMemoryGetNativeBufferInfoOHOS | Defines a struct used to obtain an <b>OH_NativeBuffer</b> from the Vulkan memory. |
| [VkExternalFormatOHOS](capi-vulkan-vkexternalformatohos.md) | VkExternalFormatOHOS | Defines an externally defined format. |
| [NativeWindow](capi-vulkan-nativewindow.md) | OHNativeWindow | Defines the <b>OHNativeWindow</b> struct. |
| [OH_NativeBuffer](capi-vulkan-oh-nativebuffer.md) | - | Defines the <b>OH_NativeBuffer</b> struct. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [VkSwapchainImageUsageFlagBitsOHOS](#vkswapchainimageusageflagbitsohos) | VkSwapchainImageUsageFlagBitsOHOS | move to vk_ohos_native_buffer.h(Deprecated in API23) |

### Macro

| Name | Description |
| -- | -- |
| VK_OHOS_surface 1 | Defines the surface extension of OpenHarmony.<br>**Since**: 10 |
| VK_OHOS_SURFACE_SPEC_VERSION      1 | Defines the surface extension version of OpenHarmony.<br>**Since**: 10 |
| VK_OHOS_SURFACE_EXTENSION_NAME    "VK_OHOS_surface" | Defines the surface extension name of OpenHarmony.<br>**Since**: 10 |
| VK_OHOS_external_memory 1 | Defines the external memory extension of OpenHarmony.<br>**Since**: 10 |
| VK_OHOS_EXTERNAL_MEMORY_SPEC_VERSION 1 | Defines the external memory extension version of OpenHarmony.<br>**Since**: 10 |
| VK_OHOS_EXTERNAL_MEMORY_EXTENSION_NAME "VK_OHOS_external_memory" | Defines the external memory extension name of OpenHarmony.<br>**Since**: 10 |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef VkResult (VKAPI_PTR *PFN_vkCreateSurfaceOHOS)(VkInstance instance, const VkSurfaceCreateInfoOHOS* pCreateInfo, const VkAllocationCallbacks* pAllocator, VkSurfaceKHR* pSurface)](#pfn_vkcreatesurfaceohos) | PFN_vkCreateSurfaceOHOS | Defines the function pointer for creating a Vulkan surface. |
| [VKAPI_ATTR VkResult VKAPI_CALL vkCreateSurfaceOHOS(VkInstance instance, const VkSurfaceCreateInfoOHOS* pCreateInfo, const VkAllocationCallbacks* pAllocator, VkSurfaceKHR* pSurface)](#vkcreatesurfaceohos) | - | Creates a Vulkan surface. |
| [typedef VkResult (VKAPI_PTR *PFN_vkSetNativeFenceFdOpenHarmony)(VkDevice device, int32_t nativeFenceFd, VkSemaphore semaphore, VkFence fence)](#pfn_vksetnativefencefdopenharmony) | PFN_vkSetNativeFenceFdOpenHarmony | this type is deprecated, please use PFN_vkAcquireImageOHOS instead(Deprecated in API10) |
| [typedef VkResult (VKAPI_PTR *PFN_vkGetNativeFenceFdOpenHarmony)(VkQueue queue, uint32_t waitSemaphoreCount, const VkSemaphore* pWaitSemaphores, VkImage image, int32_t* pNativeFenceFd)](#pfn_vkgetnativefencefdopenharmony) | PFN_vkGetNativeFenceFdOpenHarmony | this type is deprecated, please use PFN_vkQueueSignalReleaseImageOHOS instead(Deprecated in API10) |
| [typedef VkResult (VKAPI_PTR *PFN_vkGetSwapchainGrallocUsageOHOS)(VkDevice device, VkFormat format, VkImageUsageFlags imageUsage, uint64_t* grallocUsage)](#pfn_vkgetswapchaingrallocusageohos) | PFN_vkGetSwapchainGrallocUsageOHOS | move to vk_ohos_native_buffer.h(Deprecated in API23) |
| [typedef VkResult (VKAPI_PTR *PFN_vkAcquireImageOHOS)(VkDevice device, VkImage image, int32_t nativeFenceFd, VkSemaphore semaphore, VkFence fence)](#pfn_vkacquireimageohos) | PFN_vkAcquireImageOHOS | move to vk_ohos_native_buffer.h(Deprecated in API23) |
| [typedef VkResult (VKAPI_PTR *PFN_vkQueueSignalReleaseImageOHOS)(VkQueue queue, uint32_t waitSemaphoreCount, const VkSemaphore* pWaitSemaphores, VkImage image, int32_t* pNativeFenceFd)](#pfn_vkqueuesignalreleaseimageohos) | PFN_vkQueueSignalReleaseImageOHOS | move to vk_ohos_native_buffer.h(Deprecated in API23) |
| [VKAPI_ATTR VkResult VKAPI_CALL vkSetNativeFenceFdOpenHarmony(VkDevice device, int32_t nativeFenceFd, VkSemaphore semaphore, VkFence fence)](#vksetnativefencefdopenharmony) | - | this interface is deprecated, please use vkAcquireImageOHOS instead(Deprecated in API10) |
| [VKAPI_ATTR VkResult VKAPI_CALL vkGetNativeFenceFdOpenHarmony(VkQueue queue, uint32_t waitSemaphoreCount, const VkSemaphore* pWaitSemaphores, VkImage image, int32_t* pNativeFenceFd)](#vkgetnativefencefdopenharmony) | - | this interface is deprecated, please use vkQueueSignalReleaseImageOHOS instead(Deprecated in API10) |
| [VKAPI_ATTR VkResult VKAPI_CALL vkGetSwapchainGrallocUsageOHOS(VkDevice device, VkFormat format, VkImageUsageFlags imageUsage, uint64_t* grallocUsage)](#vkgetswapchaingrallocusageohos) | - | Returns the appropriate gralloc usage flag based on the given Vulkan device, image format, and image usage flag. move to vk_ohos_native_buffer.h(Deprecated in API23) |
| [VKAPI_ATTR VkResult VKAPI_CALL vkAcquireImageOHOS(VkDevice device, VkImage image, int32_t nativeFenceFd, VkSemaphore semaphore, VkFence fence)](#vkacquireimageohos) | - | Obtains the ownership of the swap chain image and imports the fence of the external signal to the VkSemaphore and VkFence objects. move to vk_ohos_native_buffer.h(Deprecated in API23) |
| [VKAPI_ATTR VkResult VKAPI_CALL vkQueueSignalReleaseImageOHOS(VkQueue queue, uint32_t waitSemaphoreCount, const VkSemaphore* pWaitSemaphores, VkImage image, int32_t* pNativeFenceFd)](#vkqueuesignalreleaseimageohos) | - | Sends a signal to the system hardware buffer to release an image once it is no longer needed so that other components can access it. move to vk_ohos_native_buffer.h(Deprecated in API23) |
| [typedef VkResult (VKAPI_PTR *PFN_vkGetNativeBufferPropertiesOHOS)(VkDevice device, const struct OH_NativeBuffer* buffer, VkNativeBufferPropertiesOHOS* pProperties)](#pfn_vkgetnativebufferpropertiesohos) | PFN_vkGetNativeBufferPropertiesOHOS | Defines a function pointer used to obtain <b>OH_NativeBuffer</b> properties. |
| [typedef VkResult (VKAPI_PTR *PFN_vkGetMemoryNativeBufferOHOS)(VkDevice device, const VkMemoryGetNativeBufferInfoOHOS* pInfo, struct OH_NativeBuffer** pBuffer)](#pfn_vkgetmemorynativebufferohos) | PFN_vkGetMemoryNativeBufferOHOS | Defines a function pointer used to obtain an <b>OH_NativeBuffer</b> instance. |
| [VKAPI_ATTR VkResult VKAPI_CALL vkGetNativeBufferPropertiesOHOS(VkDevice device, const struct OH_NativeBuffer* buffer, VkNativeBufferPropertiesOHOS* pProperties)](#vkgetnativebufferpropertiesohos) | - | Obtains the properties of an <b>OH_NativeBuffer</b> instance. |
| [VKAPI_ATTR VkResult VKAPI_CALL vkGetMemoryNativeBufferOHOS(VkDevice device, const VkMemoryGetNativeBufferInfoOHOS* pInfo, struct OH_NativeBuffer** pBuffer)](#vkgetmemorynativebufferohos) | - | Obtains an <b>OH_NativeBuffer</b> instance. |

### Variable

| Name | Description |
| -- | -- |
| VkFlags VkSurfaceCreateFlagsOHOS | Defines the bit mask of the VkFlags type used for the creation of a Vulkan surface. It is a reserved flag type.<br>**Since**: 10 |
| VkResult (VKAPI_PTR *PFN_vkCreateSurfaceOHOS)( VkInstance instance, const VkSurfaceCreateInfoOHOS* pCreateInfo, const VkAllocationCallbacks* pAllocator, VkSurfaceKHR* pSurface ) | Defines the function pointer for creating a Vulkan surface.<br>**Since**: 10 |
| VkResult (VKAPI_PTR *PFN_vkSetNativeFenceFdOpenHarmony)(VkDevice device, int32_t nativeFenceFd, VkSemaphore semaphore, VkFence fence) | this type is deprecated, please use PFN_vkAcquireImageOHOS instead<br>**Since**: 10<br>**Deprecated**: 10 |
| VkResult (VKAPI_PTR *PFN_vkGetNativeFenceFdOpenHarmony)(VkQueue queue, uint32_t waitSemaphoreCount, const VkSemaphore* pWaitSemaphores, VkImage image, int32_t* pNativeFenceFd) | this type is deprecated, please use PFN_vkQueueSignalReleaseImageOHOS instead<br>**Since**: 10<br>**Deprecated**: 10 |
| VkResult (VKAPI_PTR *PFN_vkGetSwapchainGrallocUsageOHOS)(VkDevice device, VkFormat format, VkImageUsageFlags imageUsage, uint64_t* grallocUsage) | move to vk_ohos_native_buffer.h<br>**Since**: 10<br>**Deprecated**: 23 |
| VkResult (VKAPI_PTR *PFN_vkAcquireImageOHOS)(VkDevice device, VkImage image, int32_t nativeFenceFd, VkSemaphore semaphore, VkFence fence) | move to vk_ohos_native_buffer.h<br>**Since**: 10<br>**Deprecated**: 23 |
| VkResult (VKAPI_PTR *PFN_vkQueueSignalReleaseImageOHOS)(VkQueue queue, uint32_t waitSemaphoreCount, const VkSemaphore* pWaitSemaphores, VkImage image, int32_t* pNativeFenceFd) | move to vk_ohos_native_buffer.h<br>**Since**: 10<br>**Deprecated**: 23 |
| VkResult (VKAPI_PTR *PFN_vkGetNativeBufferPropertiesOHOS)( VkDevice device, const struct OH_NativeBuffer* buffer, VkNativeBufferPropertiesOHOS* pProperties ) | Defines a function pointer used to obtain <b>OH_NativeBuffer</b> properties.<br>**Since**: 10 |
| VkResult (VKAPI_PTR *PFN_vkGetMemoryNativeBufferOHOS)( VkDevice device, const VkMemoryGetNativeBufferInfoOHOS* pInfo, struct OH_NativeBuffer** pBuffer ) | Defines a function pointer used to obtain an <b>OH_NativeBuffer</b> instance.<br>**Since**: 10 |

## Enum type description

### VkSwapchainImageUsageFlagBitsOHOS

```c
enum VkSwapchainImageUsageFlagBitsOHOS
```

**Description**

move to vk_ohos_native_buffer.h

**Since**: 10

**Deprecated**: 23

| Enum item | Description |
| -- | -- |


## Function description

### PFN_vkCreateSurfaceOHOS()

```c
typedef VkResult (VKAPI_PTR *PFN_vkCreateSurfaceOHOS)(VkInstance instance, const VkSurfaceCreateInfoOHOS* pCreateInfo, const VkAllocationCallbacks* pAllocator, VkSurfaceKHR* pSurface)
```

**Description**

Defines the function pointer for creating a Vulkan surface.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| VkInstance instance | <b>Vulkan</b> instance. |
| [const VkSurfaceCreateInfoOHOS](capi-vulkan-vksurfacecreateinfoohos.md)\* pCreateInfo | Pointer to the <b>VkSurfaceCreateInfoOHOS</b> struct, including the parameters required for creating a Vulkan surface. |
| const VkAllocationCallbacks\* pAllocator | Pointer to a callback function for custom memory allocation. If custom memory allocation is not required, pass in <b>NULL</b>, and the default memory allocation function is used. |
| VkSurfaceKHR\* pSurface | Pointer to the Vulkan surface created. The type is <b>VkSurfaceKHR</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| VkResult | Returns <b>VK_SUCCESS</b> if the execution is successful;  returns an error code of the VkResult type otherwise. |

### vkCreateSurfaceOHOS()

```c
VKAPI_ATTR VkResult VKAPI_CALL vkCreateSurfaceOHOS(VkInstance instance, const VkSurfaceCreateInfoOHOS* pCreateInfo, const VkAllocationCallbacks* pAllocator, VkSurfaceKHR* pSurface)
```

**Description**

Creates a Vulkan surface.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| VkInstance instance | <b>Vulkan</b> instance. |
| [const VkSurfaceCreateInfoOHOS](capi-vulkan-vksurfacecreateinfoohos.md)* pCreateInfo | Pointer to the <b>VkSurfaceCreateInfoOHOS</b> struct, including the parameters required for creating a Vulkan surface. |
| const VkAllocationCallbacks* pAllocator | Pointer to a callback function for custom memory allocation. If custom memory allocation is not required, pass in <b>NULL</b>, and the default memory allocation function is used. |
| VkSurfaceKHR* pSurface | Pointer to the Vulkan surface created. The type is <b>VkSurfaceKHR</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| VKAPI_ATTR VkResult VKAPI_CALL | Returns <b>VK_SUCCESS</b> if the execution is successful;  returns an error code of the VkResult type otherwise. |

### PFN_vkSetNativeFenceFdOpenHarmony()

```c
typedef VkResult (VKAPI_PTR *PFN_vkSetNativeFenceFdOpenHarmony)(VkDevice device, int32_t nativeFenceFd, VkSemaphore semaphore, VkFence fence)
```

**Description**

this type is deprecated, please use PFN_vkAcquireImageOHOS instead

**Since**: 10

**Deprecated**: 10

### PFN_vkGetNativeFenceFdOpenHarmony()

```c
typedef VkResult (VKAPI_PTR *PFN_vkGetNativeFenceFdOpenHarmony)(VkQueue queue, uint32_t waitSemaphoreCount, const VkSemaphore* pWaitSemaphores, VkImage image, int32_t* pNativeFenceFd)
```

**Description**

this type is deprecated, please use PFN_vkQueueSignalReleaseImageOHOS instead

**Since**: 10

**Deprecated**: 10

### PFN_vkGetSwapchainGrallocUsageOHOS()

```c
typedef VkResult (VKAPI_PTR *PFN_vkGetSwapchainGrallocUsageOHOS)(VkDevice device, VkFormat format, VkImageUsageFlags imageUsage, uint64_t* grallocUsage)
```

**Description**

move to vk_ohos_native_buffer.h

**Since**: 10

**Deprecated**: 23

### PFN_vkAcquireImageOHOS()

```c
typedef VkResult (VKAPI_PTR *PFN_vkAcquireImageOHOS)(VkDevice device, VkImage image, int32_t nativeFenceFd, VkSemaphore semaphore, VkFence fence)
```

**Description**

move to vk_ohos_native_buffer.h

**Since**: 10

**Deprecated**: 23

### PFN_vkQueueSignalReleaseImageOHOS()

```c
typedef VkResult (VKAPI_PTR *PFN_vkQueueSignalReleaseImageOHOS)(VkQueue queue, uint32_t waitSemaphoreCount, const VkSemaphore* pWaitSemaphores, VkImage image, int32_t* pNativeFenceFd)
```

**Description**

move to vk_ohos_native_buffer.h

**Since**: 10

**Deprecated**: 23

### vkSetNativeFenceFdOpenHarmony()

```c
VKAPI_ATTR VkResult VKAPI_CALL vkSetNativeFenceFdOpenHarmony(VkDevice device, int32_t nativeFenceFd, VkSemaphore semaphore, VkFence fence)
```

**Description**

this interface is deprecated, please use vkAcquireImageOHOS instead

**Since**: 10

**Deprecated**: 10

### vkGetNativeFenceFdOpenHarmony()

```c
VKAPI_ATTR VkResult VKAPI_CALL vkGetNativeFenceFdOpenHarmony(VkQueue queue, uint32_t waitSemaphoreCount, const VkSemaphore* pWaitSemaphores, VkImage image, int32_t* pNativeFenceFd)
```

**Description**

this interface is deprecated, please use vkQueueSignalReleaseImageOHOS instead

**Since**: 10

**Deprecated**: 10

### vkGetSwapchainGrallocUsageOHOS()

```c
VKAPI_ATTR VkResult VKAPI_CALL vkGetSwapchainGrallocUsageOHOS(VkDevice device, VkFormat format, VkImageUsageFlags imageUsage, uint64_t* grallocUsage)
```

**Description**

Returns the appropriate gralloc usage flag based on the given Vulkan device, image format, and image usage flag. move to vk_ohos_native_buffer.h

**Since**: 10

**Deprecated**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| VkDevice device | <b>VkDevice</b> instance. |
| VkFormat format | Image format. |
| VkImageUsageFlags imageUsage | Image usage flag. |
| uint64_t* grallocUsage | Pointer to the gralloc usage flag. |

**Returns**:

| Type | Description |
| -- | -- |
| VKAPI_ATTR VkResult VKAPI_CALL | Returns <b>VK_SUCCESS</b> if the execution is successful;  returns an error code of the VkResult type otherwise. |

### vkAcquireImageOHOS()

```c
VKAPI_ATTR VkResult VKAPI_CALL vkAcquireImageOHOS(VkDevice device, VkImage image, int32_t nativeFenceFd, VkSemaphore semaphore, VkFence fence)
```

**Description**

Obtains the ownership of the swap chain image and imports the fence of the external signal to the VkSemaphore and VkFence objects. move to vk_ohos_native_buffer.h

**Since**: 10

**Deprecated**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| VkDevice device | <b>VkDevice</b> instance. |
| VkImage image | Vulkan image to obtain. |
| int32_t nativeFenceFd | File descriptor of the native fence. |
| VkSemaphore semaphore | Vulkan semaphore indicating that the image is available. |
| VkFence fence | Vulkan fence used for synchronization when the image acquisition is complete. |

**Returns**:

| Type | Description |
| -- | -- |
| VKAPI_ATTR VkResult VKAPI_CALL | Returns <b>VK_SUCCESS</b> if the execution is successful;  returns an error code of the VkResult type otherwise. |

### vkQueueSignalReleaseImageOHOS()

```c
VKAPI_ATTR VkResult VKAPI_CALL vkQueueSignalReleaseImageOHOS(VkQueue queue, uint32_t waitSemaphoreCount, const VkSemaphore* pWaitSemaphores, VkImage image, int32_t* pNativeFenceFd)
```

**Description**

Sends a signal to the system hardware buffer to release an image once it is no longer needed so that other components can access it. move to vk_ohos_native_buffer.h

**Since**: 10

**Deprecated**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| VkQueue queue | Handle to the Vulkan queue. |
| uint32_t waitSemaphoreCount | Number of semaphores to wait on. |
| const VkSemaphore* pWaitSemaphores | Pointer to the array of semaphores to wait on. |
| images | Handle to the Vulkan image to be released. |
| int32_t* pNativeFenceFd | Pointer to the file descriptor of the fence. |

**Returns**:

| Type | Description |
| -- | -- |
| VKAPI_ATTR VkResult VKAPI_CALL | Returns <b>VK_SUCCESS</b> if the execution is successful;  returns an error code of the VkResult type otherwise. |

### PFN_vkGetNativeBufferPropertiesOHOS()

```c
typedef VkResult (VKAPI_PTR *PFN_vkGetNativeBufferPropertiesOHOS)(VkDevice device, const struct OH_NativeBuffer* buffer, VkNativeBufferPropertiesOHOS* pProperties)
```

**Description**

Defines a function pointer used to obtain <b>OH_NativeBuffer</b> properties.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| VkDevice device | <b>VkDevice</b> instance. |
| [const struct OH_NativeBuffer](capi-vulkan-oh-nativebuffer.md)\* buffer | Pointer to the <b>OH_NativeBuffer</b> struct. |
| [VkNativeBufferPropertiesOHOS](capi-vulkan-vknativebufferpropertiesohos.md)\* pProperties | Pointer to the struct holding the properties of <b>OH_NativeBuffer</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| VkResult | Returns <b>VK_SUCCESS</b> if the execution is successful;  returns an error code of the VkResult type otherwise. |

### PFN_vkGetMemoryNativeBufferOHOS()

```c
typedef VkResult (VKAPI_PTR *PFN_vkGetMemoryNativeBufferOHOS)(VkDevice device, const VkMemoryGetNativeBufferInfoOHOS* pInfo, struct OH_NativeBuffer** pBuffer)
```

**Description**

Defines a function pointer used to obtain an <b>OH_NativeBuffer</b> instance.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| VkDevice device | <b>VkDevice</b> instance. |
| [const VkMemoryGetNativeBufferInfoOHOS](capi-vulkan-vkmemorygetnativebufferinfoohos.md)\* pInfo | Pointer to the <b>VkMemoryGetNativeBufferInfoOHOS</b> struct. |
| [struct OH_NativeBuffer](capi-vulkan-oh-nativebuffer.md)\*\* pBuffer | Double pointer to the <b>OH_NativeBuffer</b> obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| VkResult | Returns <b>VK_SUCCESS</b> if the execution is successful;  returns an error code of the VkResult type otherwise. |

### vkGetNativeBufferPropertiesOHOS()

```c
VKAPI_ATTR VkResult VKAPI_CALL vkGetNativeBufferPropertiesOHOS(VkDevice device, const struct OH_NativeBuffer* buffer, VkNativeBufferPropertiesOHOS* pProperties)
```

**Description**

Obtains the properties of an <b>OH_NativeBuffer</b> instance.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| VkDevice device | <b>VkDevice</b> instance. |
| [const struct OH_NativeBuffer](capi-vulkan-oh-nativebuffer.md)* buffer | Pointer to the <b>OH_NativeBuffer</b> struct. |
| [VkNativeBufferPropertiesOHOS](capi-vulkan-vknativebufferpropertiesohos.md)* pProperties | Pointer to the struct holding the properties of <b>OH_NativeBuffer</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| VKAPI_ATTR VkResult VKAPI_CALL | Returns <b>VK_SUCCESS</b> if the execution is successful;  returns an error code of the VkResult type otherwise. |

### vkGetMemoryNativeBufferOHOS()

```c
VKAPI_ATTR VkResult VKAPI_CALL vkGetMemoryNativeBufferOHOS(VkDevice device, const VkMemoryGetNativeBufferInfoOHOS* pInfo, struct OH_NativeBuffer** pBuffer)
```

**Description**

Obtains an <b>OH_NativeBuffer</b> instance.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| VkDevice device | <b>VkDevice</b> instance. |
| [const VkMemoryGetNativeBufferInfoOHOS](capi-vulkan-vkmemorygetnativebufferinfoohos.md)* pInfo | Pointer to the <b>VkMemoryGetNativeBufferInfoOHOS</b> struct. |
| [struct OH_NativeBuffer](capi-vulkan-oh-nativebuffer.md)** pBuffer | Double pointer to the <b>OH_NativeBuffer</b> obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| VKAPI_ATTR VkResult VKAPI_CALL | Returns <b>VK_SUCCESS</b> if the execution is successful;  returns an error code of the VkResult type otherwise. |


