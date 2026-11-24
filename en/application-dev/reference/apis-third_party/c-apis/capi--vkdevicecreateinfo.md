# VkDeviceCreateInfo

## Overview

<!--Device-struct VkDeviceCreateInfo {...}--><!--Device-struct VkDeviceCreateInfo {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| VkStructureType sType | <!--Device-VkStructureType sType--><!--Device-VkStructureType sType-End--> |
| const void* pNext | <!--Device-const void* pNext--><!--Device-const void* pNext-End--> |
| VkDeviceCreateFlags flags | <!--Device-VkDeviceCreateFlags flags--><!--Device-VkDeviceCreateFlags flags-End--> |
| uint32_t queueCreateInfoCount | <!--Device-uint32_t queueCreateInfoCount--><!--Device-uint32_t queueCreateInfoCount-End--> |
| [const VkDeviceQueueCreateInfo*](capi--vkdevicequeuecreateinfo.md) pQueueCreateInfos | <!--Device-const VkDeviceQueueCreateInfo* pQueueCreateInfos--><!--Device-const VkDeviceQueueCreateInfo* pQueueCreateInfos-End--> |
| // enabledLayerCount is deprecated and should not be used
 uint32_t enabledLayerCount | <!--Device-// enabledLayerCount is deprecated and should not be used uint32_t enabledLayerCount--><!--Device-// enabledLayerCount is deprecated and should not be used uint32_t enabledLayerCount-End--> |
| // ppEnabledLayerNames is deprecated and should not be used
 const char* const* ppEnabledLayerNames | <!--Device-// ppEnabledLayerNames is deprecated and should not be used const char* const* ppEnabledLayerNames--><!--Device-// ppEnabledLayerNames is deprecated and should not be used const char* const* ppEnabledLayerNames-End--> |
| uint32_t enabledExtensionCount | <!--Device-uint32_t enabledExtensionCount--><!--Device-uint32_t enabledExtensionCount-End--> |
| const char* const* ppEnabledExtensionNames | <!--Device-const char* const* ppEnabledExtensionNames--><!--Device-const char* const* ppEnabledExtensionNames-End--> |
| [const VkPhysicalDeviceFeatures*](capi--vkphysicaldevicefeatures.md) pEnabledFeatures | <!--Device-const VkPhysicalDeviceFeatures* pEnabledFeatures--><!--Device-const VkPhysicalDeviceFeatures* pEnabledFeatures-End--> |


