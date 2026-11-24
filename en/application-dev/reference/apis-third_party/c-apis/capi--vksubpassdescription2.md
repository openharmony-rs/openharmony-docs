# VkSubpassDescription2

## Overview

<!--Device-struct VkSubpassDescription2 {...}--><!--Device-struct VkSubpassDescription2 {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| VkStructureType sType | <!--Device-VkStructureType sType--><!--Device-VkStructureType sType-End--> |
| const void* pNext | <!--Device-const void* pNext--><!--Device-const void* pNext-End--> |
| VkSubpassDescriptionFlags flags | <!--Device-VkSubpassDescriptionFlags flags--><!--Device-VkSubpassDescriptionFlags flags-End--> |
| VkPipelineBindPoint pipelineBindPoint | <!--Device-VkPipelineBindPoint pipelineBindPoint--><!--Device-VkPipelineBindPoint pipelineBindPoint-End--> |
| uint32_t viewMask | <!--Device-uint32_t viewMask--><!--Device-uint32_t viewMask-End--> |
| uint32_t inputAttachmentCount | <!--Device-uint32_t inputAttachmentCount--><!--Device-uint32_t inputAttachmentCount-End--> |
| [const VkAttachmentReference2*](capi--vkattachmentreference2.md) pInputAttachments | <!--Device-const VkAttachmentReference2* pInputAttachments--><!--Device-const VkAttachmentReference2* pInputAttachments-End--> |
| uint32_t colorAttachmentCount | <!--Device-uint32_t colorAttachmentCount--><!--Device-uint32_t colorAttachmentCount-End--> |
| [const VkAttachmentReference2*](capi--vkattachmentreference2.md) pColorAttachments | <!--Device-const VkAttachmentReference2* pColorAttachments--><!--Device-const VkAttachmentReference2* pColorAttachments-End--> |
| [const VkAttachmentReference2*](capi--vkattachmentreference2.md) pResolveAttachments | <!--Device-const VkAttachmentReference2* pResolveAttachments--><!--Device-const VkAttachmentReference2* pResolveAttachments-End--> |
| [const VkAttachmentReference2*](capi--vkattachmentreference2.md) pDepthStencilAttachment | <!--Device-const VkAttachmentReference2* pDepthStencilAttachment--><!--Device-const VkAttachmentReference2* pDepthStencilAttachment-End--> |
| uint32_t preserveAttachmentCount | <!--Device-uint32_t preserveAttachmentCount--><!--Device-uint32_t preserveAttachmentCount-End--> |
| const uint32_t* pPreserveAttachments | <!--Device-const uint32_t* pPreserveAttachments--><!--Device-const uint32_t* pPreserveAttachments-End--> |


