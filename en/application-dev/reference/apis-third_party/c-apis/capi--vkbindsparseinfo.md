# VkBindSparseInfo

## Overview

<!--Device-struct VkBindSparseInfo {...}--><!--Device-struct VkBindSparseInfo {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| VkStructureType sType | <!--Device-VkStructureType sType--><!--Device-VkStructureType sType-End--> |
| const void* pNext | <!--Device-const void* pNext--><!--Device-const void* pNext-End--> |
| uint32_t waitSemaphoreCount | <!--Device-uint32_t waitSemaphoreCount--><!--Device-uint32_t waitSemaphoreCount-End--> |
| const VkSemaphore* pWaitSemaphores | <!--Device-const VkSemaphore* pWaitSemaphores--><!--Device-const VkSemaphore* pWaitSemaphores-End--> |
| uint32_t bufferBindCount | <!--Device-uint32_t bufferBindCount--><!--Device-uint32_t bufferBindCount-End--> |
| [const VkSparseBufferMemoryBindInfo*](capi--vksparsebuffermemorybindinfo.md) pBufferBinds | <!--Device-const VkSparseBufferMemoryBindInfo* pBufferBinds--><!--Device-const VkSparseBufferMemoryBindInfo* pBufferBinds-End--> |
| uint32_t imageOpaqueBindCount | <!--Device-uint32_t imageOpaqueBindCount--><!--Device-uint32_t imageOpaqueBindCount-End--> |
| [const VkSparseImageOpaqueMemoryBindInfo*](capi--vksparseimageopaquememorybindinfo.md) pImageOpaqueBinds | <!--Device-const VkSparseImageOpaqueMemoryBindInfo* pImageOpaqueBinds--><!--Device-const VkSparseImageOpaqueMemoryBindInfo* pImageOpaqueBinds-End--> |
| uint32_t imageBindCount | <!--Device-uint32_t imageBindCount--><!--Device-uint32_t imageBindCount-End--> |
| [const VkSparseImageMemoryBindInfo*](capi--vksparseimagememorybindinfo.md) pImageBinds | <!--Device-const VkSparseImageMemoryBindInfo* pImageBinds--><!--Device-const VkSparseImageMemoryBindInfo* pImageBinds-End--> |
| uint32_t signalSemaphoreCount | <!--Device-uint32_t signalSemaphoreCount--><!--Device-uint32_t signalSemaphoreCount-End--> |
| const VkSemaphore* pSignalSemaphores | <!--Device-const VkSemaphore* pSignalSemaphores--><!--Device-const VkSemaphore* pSignalSemaphores-End--> |


