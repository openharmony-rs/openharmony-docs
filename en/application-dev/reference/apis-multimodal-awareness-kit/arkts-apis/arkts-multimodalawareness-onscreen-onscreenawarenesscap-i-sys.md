# OnscreenAwarenessCap (System API)

```TypeScript
export interface OnscreenAwarenessCap
```

On-screen awareness capabilities (including but not limited to reading scenario awareness, OCR recognition, and other functions).

Parameter constraint description:<br> Users can use the on-screen awareness feature through capability items (**capList**) or group IDs (**groupId**).  
* Logical relationship: **capList** and **groupId** are complementary required items. At least one of them must be provided and must not be empty.<br>  
* Validation rule: When the API is called, the system checks capList and groupId separately.<br>  
* Capability list: Use the on-screen awareness feature by capability item or group ID. The specific definitions are as follows.

    * capList Supported Capability List<br>Capabilities preset for specific business scenarios, which can be subscribed to or triggered individually, as follows:

|capList Capability List|Description|  
| ---- | ------ |  
|Article|Obtains the awareness information of the reading scenario.|  
|ShortVideo|Obtains the awareness information of the short video scenario.|  
|Todo|Obtains the awareness information of the to-do scenario.|  
|Activity|Obtains the awareness information of basic services.|  
|UiImage|Obtains the sub-image information within the page.|  
|JumpContext|Highlights and jumps to the specified context.|  
|QuickSnap|Obtains single screenshot information.<br> **Usage Specification**: Takes effect only when used with the **capture** API and when **capList** passes only "QuickSnap". Other APIs return error code 401.|  
|UiTree|Obtains the JSON tree information within the page.<br> **Since:** 26.0.0|  
|InjectEvent|Injects events.<br> **Since:** 26.0.0|  
|CollectStrategy|Obtains the screen collection strategy.<br> **Since:** 26.0.0|  
|SmartAutoFill|Intelligently fills the content of the page input box.<br> **Since:** 26.0.0|  
|SmartAutoFillSwitch|Subscribes to or unsubscribes from the smart fill switch status of page content.<br> **Usage Specification**: Only the smart fill application (com.huawei.hms.textautofill) is allowed to call this API. Calling by non-trustlisted applications returns error code 34000002.<br> **Since:** 26.0.0|

    * groupId Capability List<br>A set of capabilities preset for business scenarios. Business scenarios can be subscribed to in a unified manner, as follows:

|groupId Capability List|Corresponding Sub-Item Capability|Description|  
| ---- | ------ | ------|  
|SmartEdge|Article|Obtains the awareness information of the reading scenario.|  
|SmartEdge|ShortVideo|Obtains the awareness information of the short video scenario.|  
|SmartEdge|Todo|Obtains the awareness information of the to-do scenario.|  
|SmartEdge|Activity|Obtains the awareness information of basic services.|  
|CeliaMemory|Article|Obtains the awareness information of the reading scenario.|  
|SmartBar|SmartAutoFill|Intelligently fills the content of the page input box.|

**Since:** 23

<!--Device-onScreen-export interface OnscreenAwarenessCap--><!--Device-onScreen-export interface OnscreenAwarenessCap-End-->

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { onScreen } from '@kit.MultimodalAwarenessKit';
```

## capList

```TypeScript
capList?: string[]
```

Capability list, including the capabilities for obtaining page content, page link, and text selection.

**Type:** string[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-OnscreenAwarenessCap-capList?: string[]--><!--Device-OnscreenAwarenessCap-capList?: string[]-End-->

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## groupId

```TypeScript
groupId?: string
```

Service group ID.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-OnscreenAwarenessCap-groupId?: string--><!--Device-OnscreenAwarenessCap-groupId?: string-End-->

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.
