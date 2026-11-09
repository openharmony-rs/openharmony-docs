# VkImageMemoryBarrier2

## Overview

<!--Device-struct VkImageMemoryBarrier2 {...}--><!--Device-struct VkImageMemoryBarrier2 {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| VkStructureType sType |  |
| const void* pNext |  |
| VkPipelineStageFlags2 srcStageMask |  |
| VkAccessFlags2 srcAccessMask |  |
| VkPipelineStageFlags2 dstStageMask |  |
| VkAccessFlags2 dstAccessMask |  |
| VkImageLayout oldLayout |  |
| VkImageLayout newLayout |  |
| uint32_t srcQueueFamilyIndex |  |
| uint32_t dstQueueFamilyIndex |  |
| VkImage image |  |
| [VkImageSubresourceRange](capi--vkimagesubresourcerange.md) subresourceRange |  |


