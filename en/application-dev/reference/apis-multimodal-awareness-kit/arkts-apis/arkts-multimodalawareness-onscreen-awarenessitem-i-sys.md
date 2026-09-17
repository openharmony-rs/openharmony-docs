# AwarenessItem (System API)

Provides page information, which includes:

* Basic page information, such as page content, links, and screenshots.  
* Page entity information, such as the title and body of a page article.  
* Page interaction information, such as clicks and scrolling.

**Since:** 23

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { onScreen } from '@kit.MultimodalAwarenessKit';
```

## itemInfo

```TypeScript
itemInfo: Record<string, Object>
```

Entity information of the awareness result, including the content, links, screenshots, and other entity information.

**Type:** Record&lt;string, Object&gt;

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.
