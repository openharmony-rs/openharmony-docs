# BaseGestureEvent

基础手势事件类型。继承自BaseEvent。

**继承/实现关系：** BaseGestureEvent extends BaseEvent

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface BaseGestureEvent--><!--Device-unnamed-export interface BaseGestureEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fingerInfos

```TypeScript
fingerInfos?: FingerInfo[]
```

参与触发事件的所有有效触点信息。默认值为空数组[]，返回空数组时，表示当前无有效触点信息。

**类型：** [FingerInfo](arkts-arkui-gesture-fingerinfo-i.md)[]

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseGestureEvent-fingerInfos?: FingerInfo[]--><!--Device-BaseGestureEvent-fingerInfos?: FingerInfo[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fingerList

```TypeScript
fingerList: FingerInfo[]
```

触发事件的所有手指信息。

**类型：** [FingerInfo](arkts-arkui-gesture-fingerinfo-i.md)[]

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseGestureEvent-fingerList: FingerInfo[]--><!--Device-BaseGestureEvent-fingerList: FingerInfo[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

