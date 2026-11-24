# VkImageMemoryBarrier

## Overview

<!--Device-struct VkImageMemoryBarrier {...}--><!--Device-struct VkImageMemoryBarrier {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| VkStructureType sType | <!--Device-VkStructureType sType--><!--Device-VkStructureType sType-End--> |
| const void* pNext | <!--Device-const void* pNext--><!--Device-const void* pNext-End--> |
| VkAccessFlags srcAccessMask | <!--Device-VkAccessFlags srcAccessMask--><!--Device-VkAccessFlags srcAccessMask-End--> |
| VkAccessFlags dstAccessMask | <!--Device-VkAccessFlags dstAccessMask--><!--Device-VkAccessFlags dstAccessMask-End--> |
| VkImageLayout oldLayout | <!--Device-VkImageLayout oldLayout--><!--Device-VkImageLayout oldLayout-End--> |
| VkImageLayout newLayout | <!--Device-VkImageLayout newLayout--><!--Device-VkImageLayout newLayout-End--> |
| uint32_t srcQueueFamilyIndex | <!--Device-uint32_t srcQueueFamilyIndex--><!--Device-uint32_t srcQueueFamilyIndex-End--> |
| uint32_t dstQueueFamilyIndex | <!--Device-uint32_t dstQueueFamilyIndex--><!--Device-uint32_t dstQueueFamilyIndex-End--> |
| VkImage image | <!--Device-VkImage image--><!--Device-VkImage image-End--> |
| [VkImageSubresourceRange](capi--vkimagesubresourcerange.md) subresourceRange | <!--Device-VkImageSubresourceRange subresourceRange--><!--Device-VkImageSubresourceRange subresourceRange-End--> |


