# BaseGestureEvent

基础手势事件类型。继承自[BaseEvent](../arkts-components/arkts-arkui-common-baseevent-i.md)。

**继承/实现关系：** BaseGestureEvent extends [BaseEvent](../arkts-components/arkts-arkui-common-baseevent-i.md)

**起始版本：** 11

<!--Device-unnamed-interface BaseGestureEvent extends BaseEvent--><!--Device-unnamed-interface BaseGestureEvent extends BaseEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fingerInfos

```TypeScript
fingerInfos?: FingerInfo[]
```

由触屏产生的手势，fingerInfos中会包含触发事件的所有触点信息；由鼠标发起的手势，fingerInfos中只会有一条记录；触摸板的事件大类与鼠标一致，所以由触摸板发起的手势，fingerInfos只会携带一条记录。

**说明：**

fingerInfos只会记录参与触摸的有效手指信息，先按下但未参与当前手势触发的手指在fingerInfos中不会显示。默认值为空数组[]，返回空数组时，表示当前无有效触点信息。

**类型：** FingerInfo[]

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-BaseGestureEvent-fingerInfos?: FingerInfo[]--><!--Device-BaseGestureEvent-fingerInfos?: FingerInfo[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fingerList

```TypeScript
fingerList: FingerInfo[]
```

触发事件的所有手指信息。

**类型：** FingerInfo[]

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BaseGestureEvent-fingerList: FingerInfo[]--><!--Device-BaseGestureEvent-fingerList: FingerInfo[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

