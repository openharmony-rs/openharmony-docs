# PageContent (System API)

```TypeScript
export interface PageContent
```

Defines the onscreen content.

**Since:** 20

<!--Device-onScreen-export interface PageContent--><!--Device-onScreen-export interface PageContent-End-->

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

<!--Device-PageContent-bundleName: string--><!--Device-PageContent-bundleName: string-End-->

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## content

```TypeScript
content?: string
```

Body of the onscreen content. This parameter is available only when **options.contentUnderstand** is set to **True**.

**Type:** string

**Since:** 20

<!--Device-PageContent-content?: string--><!--Device-PageContent-content?: string-End-->

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## pageLink

```TypeScript
pageLink?: string
```

Page link of the onscreen content. This parameter is available only when **options.pageLink** is set to **True**.

**Type:** string

**Since:** 20

<!--Device-PageContent-pageLink?: string--><!--Device-PageContent-pageLink?: string-End-->

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## paragraphs

```TypeScript
paragraphs?: Paragraph[]
```

Paragraph information of the onscreen content. This parameter is available only when **options.textOnly** is set to **True**.

**Type:** [Paragraph](arkts-multimodalawareness-onscreen-paragraph-i-sys.md)[]

**Since:** 20

<!--Device-PageContent-paragraphs?: Paragraph[]--><!--Device-PageContent-paragraphs?: Paragraph[]-End-->

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## scenario

```TypeScript
scenario?: Scenario
```

Scenario of the onscreen content. This parameter is available only when **options.contentUnderstand** is set to **True**.

**Type:** [Scenario](arkts-multimodalawareness-onscreen-scenario-e-sys.md)

**Since:** 20

<!--Device-PageContent-scenario?: Scenario--><!--Device-PageContent-scenario?: Scenario-End-->

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## sessionId

```TypeScript
sessionId: number
```

Session ID, which identifies the call action.

**Type:** number

**Since:** 20

<!--Device-PageContent-sessionId: long--><!--Device-PageContent-sessionId: long-End-->

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## title

```TypeScript
title?: string
```

Title of the onscreen content. This parameter is available only when **options.contentUnderstand** is set to **True**.

**Type:** string

**Since:** 20

<!--Device-PageContent-title?: string--><!--Device-PageContent-title?: string-End-->

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## windowId

```TypeScript
windowId: number
```

Window ID of the onscreen content.

**Type:** number

**Since:** 20

<!--Device-PageContent-windowId: int--><!--Device-PageContent-windowId: int-End-->

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.
