# VkSubmitInfo

## Overview

<!--Device-struct VkSubmitInfo {...}--><!--Device-struct VkSubmitInfo {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| VkStructureType sType | <!--Device-VkStructureType sType--><!--Device-VkStructureType sType-End--> |
| const void* pNext | <!--Device-const void* pNext--><!--Device-const void* pNext-End--> |
| uint32_t waitSemaphoreCount | <!--Device-uint32_t waitSemaphoreCount--><!--Device-uint32_t waitSemaphoreCount-End--> |
| const VkSemaphore* pWaitSemaphores | <!--Device-const VkSemaphore* pWaitSemaphores--><!--Device-const VkSemaphore* pWaitSemaphores-End--> |
| const VkPipelineStageFlags* pWaitDstStageMask | <!--Device-const VkPipelineStageFlags* pWaitDstStageMask--><!--Device-const VkPipelineStageFlags* pWaitDstStageMask-End--> |
| uint32_t commandBufferCount | <!--Device-uint32_t commandBufferCount--><!--Device-uint32_t commandBufferCount-End--> |
| const VkCommandBuffer* pCommandBuffers | <!--Device-const VkCommandBuffer* pCommandBuffers--><!--Device-const VkCommandBuffer* pCommandBuffers-End--> |
| uint32_t signalSemaphoreCount | <!--Device-uint32_t signalSemaphoreCount--><!--Device-uint32_t signalSemaphoreCount-End--> |
| const VkSemaphore* pSignalSemaphores | <!--Device-const VkSemaphore* pSignalSemaphores--><!--Device-const VkSemaphore* pSignalSemaphores-End--> |


