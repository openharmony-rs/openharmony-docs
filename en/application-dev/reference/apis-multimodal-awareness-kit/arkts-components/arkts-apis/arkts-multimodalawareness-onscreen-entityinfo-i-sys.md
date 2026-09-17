# EntityInfo (System API)

Provides entity information perceived, including content, links, images, and other types of entities.

**Since:** 23

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { onScreen } from '@kit.MultimodalAwarenessKit';
```

## entityInfo

```TypeScript
entityInfo: Record<string, Object>
```

Entity information of the awareness result, including the content, links, images, and other entity information.

**Type:** Record&lt;string, Object&gt;

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## entityName

```TypeScript
entityName: string
```

Name of the perceived entity, which is fixed.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.
