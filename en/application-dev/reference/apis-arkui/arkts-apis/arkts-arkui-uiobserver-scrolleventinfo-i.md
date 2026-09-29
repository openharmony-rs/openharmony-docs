# ScrollEventInfo

```TypeScript
export interface ScrollEventInfo
```

Provides the scroll event information.

**Since:** 12

<!--Device-uiObserver-export interface ScrollEventInfo--><!--Device-uiObserver-export interface ScrollEventInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { uiObserver } from '@kit.ArkUI';
```

## axis

```TypeScript
axis?: Axis
```

Scroll direction of the scrollable component.

**Type:** [Axis](arkts-arkui-axis-e.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-ScrollEventInfo-axis?: Axis--><!--Device-ScrollEventInfo-axis?: Axis-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id: string
```

ID of the scrollable component.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ScrollEventInfo-id: string--><!--Device-ScrollEventInfo-id: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset: number
```

Current offset of the scrollable component.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ScrollEventInfo-offset: number--><!--Device-ScrollEventInfo-offset: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scrollEvent

```TypeScript
scrollEvent: ScrollEventType
```

Enumerates the scroll event types.

**Type:** [ScrollEventType](arkts-arkui-uiobserver-scrolleventtype-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ScrollEventInfo-scrollEvent: ScrollEventType--><!--Device-ScrollEventInfo-scrollEvent: ScrollEventType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## uniqueId

```TypeScript
uniqueId: number
```

Unique ID of the scrollable component.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ScrollEventInfo-uniqueId: number--><!--Device-ScrollEventInfo-uniqueId: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
