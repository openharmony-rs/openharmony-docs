# NodeSensitiveInputEventType

```TypeScript
export const enum NodeSensitiveInputEventType
```

Defines the types of input events that can be reported through the node sensitive input listener. The event object is carried by the member field of [NodeSensitiveInputInfo](arkts-arkui-arkui-uicontext-nodesensitiveinputinfo-i.md) that matches this type; for example, when the value is **TOUCH**, the event object is carried by **touchEvent**.

**Since:** 26.1.0

<!--Device-unnamed-export const enum NodeSensitiveInputEventType--><!--Device-unnamed-export const enum NodeSensitiveInputEventType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## KEY

```TypeScript
KEY = 2
```

The reported event is a key event.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-NodeSensitiveInputEventType-KEY = 2--><!--Device-NodeSensitiveInputEventType-KEY = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## MOUSE

```TypeScript
MOUSE = 1
```

The reported event is a mouse event.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-NodeSensitiveInputEventType-MOUSE = 1--><!--Device-NodeSensitiveInputEventType-MOUSE = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## TOUCH

```TypeScript
TOUCH = 0
```

The reported event is a touch event.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-NodeSensitiveInputEventType-TOUCH = 0--><!--Device-NodeSensitiveInputEventType-TOUCH = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
