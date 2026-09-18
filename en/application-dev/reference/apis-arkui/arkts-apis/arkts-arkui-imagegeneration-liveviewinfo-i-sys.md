# LiveViewInfo (System API)

Information for LiveView in AI image generation.

@interface LiveViewInfo

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## getLongTermTaskId

```TypeScript
getLongTermTaskId(): number
```

Get the long-term task ID for LiveView.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the long-term task ID. |

## getWant

```TypeScript
getWant(): Want
```

Get the Want object for LiveView.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Returns the Want object. |

## isLiveViewNeeded

```TypeScript
isLiveViewNeeded(): boolean
```

Check whether LiveView is needed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns true if LiveView is needed, false otherwise. |
