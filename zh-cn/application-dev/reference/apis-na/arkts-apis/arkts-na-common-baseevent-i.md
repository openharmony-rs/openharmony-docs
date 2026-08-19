# BaseEvent

Defines the base event.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface BaseEvent--><!--Device-unnamed-export declare interface BaseEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## axisHorizontal

```TypeScript
axisHorizontal?: double
```

the Horizontal axis coordinate.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseEvent-axisHorizontal?: double--><!--Device-BaseEvent-axisHorizontal?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## axisPinch

```TypeScript
axisPinch?: double
```

Indicates the Pinch axis coordinate.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseEvent-axisPinch?: double--><!--Device-BaseEvent-axisPinch?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## axisVertical

```TypeScript
axisVertical?: double
```

the Vertical axis coordinate.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseEvent-axisVertical?: double--><!--Device-BaseEvent-axisVertical?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## deviceId

```TypeScript
deviceId?: int
```

Indicates the ID of the input device that triggers the current event.

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseEvent-deviceId?: int--><!--Device-BaseEvent-deviceId?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getModifierKeyState

```TypeScript
getModifierKeyState?: ModifierKeyStateGetter
```

Query the modifier key press state, support 'ctrl'|'alt'|'shift'

**类型：** [ModifierKeyStateGetter](arkts-na-modifierkeystategetter-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseEvent-getModifierKeyState?: ModifierKeyStateGetter--><!--Device-BaseEvent-getModifierKeyState?: ModifierKeyStateGetter-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pressure

```TypeScript
pressure: double
```

Press pressure.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseEvent-pressure: double--><!--Device-BaseEvent-pressure: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## rollAngle

```TypeScript
rollAngle?: double
```

Indicates the angle at which the stylus rotates around the Z-axis.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseEvent-rollAngle?: double--><!--Device-BaseEvent-rollAngle?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## source

```TypeScript
source: SourceType
```

Event input device.

**类型：** [SourceType](arkts-na-common-sourcetype-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseEvent-source: SourceType--><!--Device-BaseEvent-source: SourceType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## sourceTool

```TypeScript
sourceTool: SourceTool
```

Event input source.

**类型：** [SourceTool](arkts-na-common-sourcetool-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseEvent-sourceTool: SourceTool--><!--Device-BaseEvent-sourceTool: SourceTool-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## target

```TypeScript
target: EventTarget
```

Display area of the element that triggers the gesture event.

**类型：** [EventTarget](arkts-na-common-eventtarget-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseEvent-target: EventTarget--><!--Device-BaseEvent-target: EventTarget-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## targetDisplayId

```TypeScript
targetDisplayId?: int
```

Indicates the screen ID on which the event occurred.

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseEvent-targetDisplayId?: int--><!--Device-BaseEvent-targetDisplayId?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## tiltX

```TypeScript
tiltX: double
```

Angle between the projection of the stylus on the device plane and the x-axis.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseEvent-tiltX: double--><!--Device-BaseEvent-tiltX: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## tiltY

```TypeScript
tiltY: double
```

Angle between the projection of the stylus on the device plane and the y-axis.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseEvent-tiltY: double--><!--Device-BaseEvent-tiltY: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## timestamp

```TypeScript
timestamp: long
```

Timestamp of the event.

**类型：** long

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseEvent-timestamp: long--><!--Device-BaseEvent-timestamp: long-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

