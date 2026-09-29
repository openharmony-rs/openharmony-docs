# GestureListenerCallback

```TypeScript
export declare type GestureListenerCallback = (info: GestureTriggerInfo) => void
```

Defines the callback type for listening for specific gesture trigger information in **UIObserver**.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-unnamed-export declare type GestureListenerCallback = (info: GestureTriggerInfo) => void--><!--Device-unnamed-export declare type GestureListenerCallback = (info: GestureTriggerInfo) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [GestureTriggerInfo](arkts-arkui-arkui-uicontext-gesturetriggerinfo-i.md) | Yes | Details of the gesture triggered by the interaction. |
