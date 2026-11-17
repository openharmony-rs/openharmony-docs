# ContentOptions (System API)

```TypeScript
export interface ContentOptions
```

Defines the options for obtaining the onscreen content.

**Since:** 20

<!--Device-onScreen-export interface ContentOptions--><!--Device-onScreen-export interface ContentOptions-End-->

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { onScreen } from '@kit.MultimodalAwarenessKit';
```

## contentUnderstand

```TypeScript
contentUnderstand?: boolean
```

Whether to perform content understanding. The value **true** means yes, and **false** means no. The default value is **false**.

**Type:** boolean

**Since:** 20

<!--Device-ContentOptions-contentUnderstand?: boolean--><!--Device-ContentOptions-contentUnderstand?: boolean-End-->

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## pageLink

```TypeScript
pageLink?: boolean
```

Whether to obtain the revisit link. The value **true** means to obtain it, and **false** means not to obtain it. The default value is **false**.

**Type:** boolean

**Since:** 20

<!--Device-ContentOptions-pageLink?: boolean--><!--Device-ContentOptions-pageLink?: boolean-End-->

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## textOnly

```TypeScript
textOnly?: boolean
```

Whether to obtain only text and divide it into paragraphs. The value **true** means yes, and **false** means no. The default value is **false**.

**Type:** boolean

**Since:** 20

<!--Device-ContentOptions-textOnly?: boolean--><!--Device-ContentOptions-textOnly?: boolean-End-->

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## windowId

```TypeScript
windowId?: number
```

Window ID of the content to be obtained. If not assigned or assigned **undefined**, the full-screen window is obtained by default.

**Type:** number

**Since:** 20

<!--Device-ContentOptions-windowId?: int--><!--Device-ContentOptions-windowId?: int-End-->

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.
