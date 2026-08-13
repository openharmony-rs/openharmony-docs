# TouchRecognizer

触摸识别器对象。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare class TouchRecognizer--><!--Device-unnamed-export declare class TouchRecognizer-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## cancelTouch

```TypeScript
cancelTouch(): void
```

向当前触摸识别器发送触摸取消事件的信息。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TouchRecognizer-cancelTouch(): void--><!--Device-TouchRecognizer-cancelTouch(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getEventTargetInfo

```TypeScript
getEventTargetInfo(): EventTargetInfo
```

返回当前触摸识别器对应组件的信息。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TouchRecognizer-getEventTargetInfo(): EventTargetInfo--><!--Device-TouchRecognizer-getEventTargetInfo(): EventTargetInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [EventTargetInfo](arkts-arkui-gesture-eventtargetinfo-c.md) | 当前触摸识别器对应组件的信息。 |

## isHostBelongsTo

```TypeScript
isHostBelongsTo(uniqueId: int): boolean
```

返回当前触摸识别器绑定节点是否为传入组件的后代节点。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TouchRecognizer-isHostBelongsTo(uniqueId: int): boolean--><!--Device-TouchRecognizer-isHostBelongsTo(uniqueId: int): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uniqueId | int | 是 | 组件的唯一ID。可以通过[getUniqueId](arkts-arkui-gesture-eventtargetinfo-c.md#getUniqueId)接口获取该ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当前触摸识别器绑定节点是否为传入组件的后代节点。true表示当前绑定节点为传入组件的后代节点，false表示当前绑定节点非传入组件的后代节点。 |

