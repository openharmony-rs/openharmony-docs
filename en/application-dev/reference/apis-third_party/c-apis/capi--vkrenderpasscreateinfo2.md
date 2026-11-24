# VkRenderPassCreateInfo2

## Overview

<!--Device-struct VkRenderPassCreateInfo2 {...}--><!--Device-struct VkRenderPassCreateInfo2 {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| VkStructureType sType | <!--Device-VkStructureType sType--><!--Device-VkStructureType sType-End--> |
| const void* pNext | <!--Device-const void* pNext--><!--Device-const void* pNext-End--> |
| VkRenderPassCreateFlags flags | <!--Device-VkRenderPassCreateFlags flags--><!--Device-VkRenderPassCreateFlags flags-End--> |
| uint32_t attachmentCount | <!--Device-uint32_t attachmentCount--><!--Device-uint32_t attachmentCount-End--> |
| [const VkAttachmentDescription2*](capi--vkattachmentdescription2.md) pAttachments | <!--Device-const VkAttachmentDescription2* pAttachments--><!--Device-const VkAttachmentDescription2* pAttachments-End--> |
| uint32_t subpassCount | <!--Device-uint32_t subpassCount--><!--Device-uint32_t subpassCount-End--> |
| [const VkSubpassDescription2*](capi--vksubpassdescription2.md) pSubpasses | <!--Device-const VkSubpassDescription2* pSubpasses--><!--Device-const VkSubpassDescription2* pSubpasses-End--> |
| uint32_t dependencyCount | <!--Device-uint32_t dependencyCount--><!--Device-uint32_t dependencyCount-End--> |
| [const VkSubpassDependency2*](capi--vksubpassdependency2.md) pDependencies | <!--Device-const VkSubpassDependency2* pDependencies--><!--Device-const VkSubpassDependency2* pDependencies-End--> |
| uint32_t correlatedViewMaskCount | <!--Device-uint32_t correlatedViewMaskCount--><!--Device-uint32_t correlatedViewMaskCount-End--> |
| const uint32_t* pCorrelatedViewMasks | <!--Device-const uint32_t* pCorrelatedViewMasks--><!--Device-const uint32_t* pCorrelatedViewMasks-End--> |


