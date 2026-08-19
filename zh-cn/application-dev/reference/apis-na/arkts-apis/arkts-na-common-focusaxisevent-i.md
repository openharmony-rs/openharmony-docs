# FocusAxisEvent

Focus axis event object description.

**继承/实现关系：** FocusAxisEvent extends [BaseEvent](arkts-na-common-baseevent-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface FocusAxisEvent--><!--Device-unnamed-export declare interface FocusAxisEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## stopPropagation

```TypeScript
stopPropagation(): void
```

The blocking event pops up.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FocusAxisEvent-stopPropagation(): void--><!--Device-FocusAxisEvent-stopPropagation(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## axisMap

```TypeScript
axisMap: Map<AxisModel, double>
```

The axis values of axis event.

**类型：** Map&lt;[AxisModel](../../apis-arkui/arkts-apis/arkts-arkui-axismodel-e.md), double&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FocusAxisEvent-axisMap: Map<AxisModel, double>--><!--Device-FocusAxisEvent-axisMap: Map<AxisModel, double>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

