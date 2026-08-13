# GestureListenerCallback

```TypeScript
export declare type GestureListenerCallback = (info: GestureTriggerInfo) => void
```

定义UIObserver监听指定手势触发信息时使用的回调类型。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare type GestureListenerCallback = (info: GestureTriggerInfo) => void--><!--Device-unnamed-export declare type GestureListenerCallback = (info: GestureTriggerInfo) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [GestureTriggerInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-gesturetriggerinfo-i.md) | 是 | the gesture details triggered with user interaction |

