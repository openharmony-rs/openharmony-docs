# TreeListenerV2

Declare class TreeListenerV2

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { CallbackParamV2, NodeParamV2, TreeControllerV2, TreeListenerV2, TreeListenerManagerV2, TreeViewV2 } from '@kit.ArkUI';
```

## offNodeAdd

```TypeScript
offNodeAdd(callback?: OnChangedCallback): void
```

Destroy node add callback event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | No |  |

## offNodeClick

```TypeScript
offNodeClick(callback?: OnChangedCallback): void
```

Destroy node click callback event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | No |  |

## offNodeDelete

```TypeScript
offNodeDelete(callback?: OnChangedCallback): void
```

Destroy node delete callback event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | No |  |

## offNodeModify

```TypeScript
offNodeModify(callback?: OnChangedCallback): void
```

Destroy node modify callback event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | No |  |

## offNodeMove

```TypeScript
offNodeMove(callback?: OnChangedCallback): void
```

Destroy node move callback event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | No |  |

## onceNodeAdd

```TypeScript
onceNodeAdd(callback: OnChangedCallback): void
```

Node add event registration and processing. After the event is processed once, it will be destroyed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | Yes |  |

## onceNodeClick

```TypeScript
onceNodeClick(callback: OnChangedCallback): void
```

Node click event registration and processing. After the event is processed once, it will be destroyed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | Yes |  |

## onceNodeDelete

```TypeScript
onceNodeDelete(callback: OnChangedCallback): void
```

Node delete event registration and processing. After the event is processed once, it will be destroyed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | Yes |  |

## onceNodeModify

```TypeScript
onceNodeModify(callback: OnChangedCallback): void
```

Node modify event registration and processing. After the event is processed once, it will be destroyed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | Yes |  |

## onceNodeMove

```TypeScript
onceNodeMove(callback: OnChangedCallback): void
```

Node move event registration and processing. After the event is processed once, it will be destroyed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | Yes |  |

## onNodeAdd

```TypeScript
onNodeAdd(callback: OnChangedCallback): void
```

Node add event registration and processing. The event will not be destroyed after being processed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | Yes |  |

## onNodeClick

```TypeScript
onNodeClick(callback: OnChangedCallback): void
```

Node click event registration and processing. The event will not be destroyed after being processed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | Yes |  |

## onNodeDelete

```TypeScript
onNodeDelete(callback: OnChangedCallback): void
```

Node delete event registration and processing. The event will not be destroyed after being processed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | Yes |  |

## onNodeModify

```TypeScript
onNodeModify(callback: OnChangedCallback): void
```

Node modify event registration and processing. The event will not be destroyed after being processed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | Yes |  |

## onNodeMove

```TypeScript
onNodeMove(callback: OnChangedCallback): void
```

Node move event registration and processing. The event will not be destroyed after being processed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | Yes |  |
