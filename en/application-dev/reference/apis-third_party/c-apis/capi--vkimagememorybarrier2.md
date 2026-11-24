# VkImageMemoryBarrier2

## Overview

<!--Device-struct VkImageMemoryBarrier2 {...}--><!--Device-struct VkImageMemoryBarrier2 {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| VkStructureType sType | <!--Device-VkStructureType sType--><!--Device-VkStructureType sType-End--> |
| const void* pNext | <!--Device-const void* pNext--><!--Device-const void* pNext-End--> |
| VkPipelineStageFlags2 srcStageMask | <!--Device-VkPipelineStageFlags2 srcStageMask--><!--Device-VkPipelineStageFlags2 srcStageMask-End--> |
| VkAccessFlags2 srcAccessMask | <!--Device-VkAccessFlags2 srcAccessMask--><!--Device-VkAccessFlags2 srcAccessMask-End--> |
| VkPipelineStageFlags2 dstStageMask | <!--Device-VkPipelineStageFlags2 dstStageMask--><!--Device-VkPipelineStageFlags2 dstStageMask-End--> |
| VkAccessFlags2 dstAccessMask | <!--Device-VkAccessFlags2 dstAccessMask--><!--Device-VkAccessFlags2 dstAccessMask-End--> |
| VkImageLayout oldLayout | <!--Device-VkImageLayout oldLayout--><!--Device-VkImageLayout oldLayout-End--> |
| VkImageLayout newLayout | <!--Device-VkImageLayout newLayout--><!--Device-VkImageLayout newLayout-End--> |
| uint32_t srcQueueFamilyIndex | <!--Device-uint32_t srcQueueFamilyIndex--><!--Device-uint32_t srcQueueFamilyIndex-End--> |
| uint32_t dstQueueFamilyIndex | <!--Device-uint32_t dstQueueFamilyIndex--><!--Device-uint32_t dstQueueFamilyIndex-End--> |
| VkImage image | <!--Device-VkImage image--><!--Device-VkImage image-End--> |
| [VkImageSubresourceRange](capi--vkimagesubresourcerange.md) subresourceRange | <!--Device-VkImageSubresourceRange subresourceRange--><!--Device-VkImageSubresourceRange subresourceRange-End--> |


