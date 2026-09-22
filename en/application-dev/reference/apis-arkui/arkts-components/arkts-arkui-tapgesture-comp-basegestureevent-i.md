# BaseGestureEvent

```TypeScript
interface BaseGestureEvent extends BaseEvent
```

Defines the basic gesture event type. Inherits from [BaseEvent](arkts-arkui-common-comp-baseevent-i.md).

**Inheritance/Implementation:** BaseGestureEvent extends [BaseEvent](arkts-arkui-common-comp-baseevent-i.md)

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fingerInfos

```TypeScript
fingerInfos?: FingerInfo[]
```

Information about touch points of the gesture event. For gesture events initiated by a touchscreen, **fingerInfos** includes information about all touch points. For gesture events initiated by a mouse or touchpad, **fingerInfos** contains only one touch point.

**NOTE:** 

**fingerInfos** only records information about effective fingers that participate in the touch. Fingers that are pressed first but do not participate in triggering of the current gesture will not be shown in **fingerInfos**. The default value is an empty array **[]**, and an empty array indicates no effective touch point information.

**Type:** [FingerInfo](arkts-arkui-tapgesture-comp-fingerinfo-i.md)[]

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fingerList

```TypeScript
fingerList: FingerInfo[]
```

Information about all fingers triggering the event.

**Type:** [FingerInfo](arkts-arkui-tapgesture-comp-fingerinfo-i.md)[]

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
