# ContentOptions (System API)

Defines the options for obtaining the onscreen content.

**Since:** 20

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

Whether content understanding is required. The default value is **False**.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## pageLink

```TypeScript
pageLink?: boolean
```

Whether to obtain the page link. The default value is **False**.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## textOnly

```TypeScript
textOnly?: boolean
```

Whether to obtain only the text and divide the text into paragraphs. The default value is **False**.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## windowId

```TypeScript
windowId?: number
```

ID of the window whose content needs to be obtained. If this parameter is not set or is set to **undefined**, the content of the full-screen window is obtained by default.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.
