# TouchRecognizer

触摸识别器对象。

**起始版本：** 20

<!--Device-unnamed-declare class TouchRecognizer--><!--Device-unnamed-declare class TouchRecognizer-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## cancelTouch

```TypeScript
cancelTouch(): void
```

向当前触摸识别器发送触摸取消事件的信息。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TouchRecognizer-cancelTouch(): void--><!--Device-TouchRecognizer-cancelTouch(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getEventTargetInfo

```TypeScript
getEventTargetInfo(): EventTargetInfo
```

返回当前触摸识别器对应组件的信息。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TouchRecognizer-getEventTargetInfo(): EventTargetInfo--><!--Device-TouchRecognizer-getEventTargetInfo(): EventTargetInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [EventTargetInfo](arkts-arkui-gesture-eventtargetinfo-c.md) | 当前触摸识别器对应组件的信息。 |

## isHostBelongsTo

```TypeScript
isHostBelongsTo(uniqueId: number): boolean
```

Check whether the current gesture binding node is a descendant of the passed-in component.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TouchRecognizer-isHostBelongsTo(uniqueId: number): boolean--><!--Device-TouchRecognizer-isHostBelongsTo(uniqueId: number): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uniqueId | number | 是 | the unique id of the component. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | - the query result. |

## isHostBelongsTo

```TypeScript
isHostBelongsTo(uniqueId: number): boolean
```

返回当前触摸识别器绑定节点是否为传入组件的后代节点。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TouchRecognizer-isHostBelongsTo(uniqueId: int): boolean--><!--Device-TouchRecognizer-isHostBelongsTo(uniqueId: int): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uniqueId | number | 是 | 组件的唯一ID。可以通过[getUniqueId](arkts-arkui-gesture-eventtargetinfo-c.md#getuniqueid-1)接口获取该ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当前触摸识别器绑定节点是否为传入组件的后代节点。true表示当前绑定节点为传入组件的后代节点，false表示当前绑定节点非传入组件的后代节点。 |

