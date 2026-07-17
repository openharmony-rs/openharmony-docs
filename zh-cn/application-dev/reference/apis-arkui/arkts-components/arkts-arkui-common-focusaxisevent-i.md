# FocusAxisEvent

焦点轴事件的对象说明，继承于[BaseEvent](arkts-arkui-common-baseevent-i.md)。

**继承/实现关系：** FocusAxisEvent extends [BaseEvent](arkts-arkui-common-baseevent-i.md)

**起始版本：** 15

<!--Device-unnamed-declare interface FocusAxisEvent extends BaseEvent--><!--Device-unnamed-declare interface FocusAxisEvent extends BaseEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## axisMap

```TypeScript
axisMap: Map<AxisModel, number>
```

焦点轴事件的轴值表。

**类型：** Map<AxisModel, number>

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-FocusAxisEvent-axisMap: Map<AxisModel, number>--><!--Device-FocusAxisEvent-axisMap: Map<AxisModel, number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## stopPropagation

```TypeScript
stopPropagation: Callback<void>
```

阻塞[事件冒泡](../../../../ui/arkts-interaction-basic-principles.md#事件冒泡)传递。

**类型：** Callback<void>

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-FocusAxisEvent-stopPropagation: Callback<void>--><!--Device-FocusAxisEvent-stopPropagation: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

