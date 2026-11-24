# VkSubmitInfo2

## Overview

<!--Device-struct VkSubmitInfo2 {...}--><!--Device-struct VkSubmitInfo2 {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| VkStructureType sType | <!--Device-VkStructureType sType--><!--Device-VkStructureType sType-End--> |
| const void* pNext | <!--Device-const void* pNext--><!--Device-const void* pNext-End--> |
| VkSubmitFlags flags | <!--Device-VkSubmitFlags flags--><!--Device-VkSubmitFlags flags-End--> |
| uint32_t waitSemaphoreInfoCount | <!--Device-uint32_t waitSemaphoreInfoCount--><!--Device-uint32_t waitSemaphoreInfoCount-End--> |
| [const VkSemaphoreSubmitInfo*](capi--vksemaphoresubmitinfo.md) pWaitSemaphoreInfos | <!--Device-const VkSemaphoreSubmitInfo* pWaitSemaphoreInfos--><!--Device-const VkSemaphoreSubmitInfo* pWaitSemaphoreInfos-End--> |
| uint32_t commandBufferInfoCount | <!--Device-uint32_t commandBufferInfoCount--><!--Device-uint32_t commandBufferInfoCount-End--> |
| [const VkCommandBufferSubmitInfo*](capi--vkcommandbuffersubmitinfo.md) pCommandBufferInfos | <!--Device-const VkCommandBufferSubmitInfo* pCommandBufferInfos--><!--Device-const VkCommandBufferSubmitInfo* pCommandBufferInfos-End--> |
| uint32_t signalSemaphoreInfoCount | <!--Device-uint32_t signalSemaphoreInfoCount--><!--Device-uint32_t signalSemaphoreInfoCount-End--> |
| [const VkSemaphoreSubmitInfo*](capi--vksemaphoresubmitinfo.md) pSignalSemaphoreInfos | <!--Device-const VkSemaphoreSubmitInfo* pSignalSemaphoreInfos--><!--Device-const VkSemaphoreSubmitInfo* pSignalSemaphoreInfos-End--> |


