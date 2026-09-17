# PageContent (System API)

Defines the onscreen content.

**Since:** 20

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { onScreen } from '@kit.MultimodalAwarenessKit';
```

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the onscreen content.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## content

```TypeScript
content?: string
```

Body of the onscreen content. This parameter is available only when **options.contentUnderstand** is set to **True**.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## pageLink

```TypeScript
pageLink?: string
```

Page link of the onscreen content. This parameter is available only when **options.pageLink** is set to **True**.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## paragraphs

```TypeScript
paragraphs?: Paragraph[]
```

Paragraph information of the onscreen content. This parameter is available only when **options.textOnly** is set to **True**.

**Type:** [Paragraph](arkts-multimodalawareness-onscreen-paragraph-i-sys.md)[]

**Since:** 20

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## scenario

```TypeScript
scenario?: Scenario
```

Scenario of the onscreen content. This parameter is available only when **options.contentUnderstand** is set to **True**.

**Type:** [Scenario](arkts-multimodalawareness-onscreen-scenario-e-sys.md)

**Since:** 20

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## sessionId

```TypeScript
sessionId: number
```

Session ID, which identifies the call action.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## title

```TypeScript
title?: string
```

Title of the onscreen content. This parameter is available only when **options.contentUnderstand** is set to **True**.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## windowId

```TypeScript
windowId: number
```

Window ID of the onscreen content.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.
