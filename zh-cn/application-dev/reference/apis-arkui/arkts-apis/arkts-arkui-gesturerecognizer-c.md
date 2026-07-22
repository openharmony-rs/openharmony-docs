# GestureRecognizer

手势识别器对象。

**起始版本：** 12

<!--Device-unnamed-declare class GestureRecognizer--><!--Device-unnamed-declare class GestureRecognizer-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getEventTargetInfo

```TypeScript
getEventTargetInfo(): EventTargetInfo
```

返回当前手势识别器对应组件的信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GestureRecognizer-getEventTargetInfo(): EventTargetInfo--><!--Device-GestureRecognizer-getEventTargetInfo(): EventTargetInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [EventTargetInfo](arkts-arkui-eventtargetinfo-c.md) | 当前手势识别器对应组件的信息。 |

## getFingerCount

```TypeScript
getFingerCount(): number
```

返回预设手指识别数阈值。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-GestureRecognizer-getFingerCount(): number--><!--Device-GestureRecognizer-getFingerCount(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 预设手指识别数阈值。<br/>取值范围：[1, 10], 整数。 |

## getState

```TypeScript
getState(): GestureRecognizerState
```

返回当前手势识别器的状态。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GestureRecognizer-getState(): GestureRecognizerState--><!--Device-GestureRecognizer-getState(): GestureRecognizerState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [GestureRecognizerState](arkts-arkui-gesturerecognizerstate-e.md) | 当前手势识别器的状态。 |

## getTag

```TypeScript
getTag(): string
```

返回当前手势识别器的tag。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GestureRecognizer-getTag(): string--><!--Device-GestureRecognizer-getTag(): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 当前手势识别器的标志。 |

## getType

```TypeScript
getType(): GestureControl.GestureType
```

返回当前手势识别器的类型。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GestureRecognizer-getType(): GestureControl.GestureType--><!--Device-GestureRecognizer-getType(): GestureControl.GestureType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| GestureControl.GestureType | 当前手势识别器的类型。 |

## isBuiltIn

```TypeScript
isBuiltIn(): boolean
```

返回当前手势识别器是否为系统内置手势。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GestureRecognizer-isBuiltIn(): boolean--><!--Device-GestureRecognizer-isBuiltIn(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当前手势识别器是否为系统内置手势。true表示手势识别器为系统内置手势，false表示非系统内置手势。 |

## isEnabled

```TypeScript
isEnabled(): boolean
```

返回当前手势识别器的使能状态。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GestureRecognizer-isEnabled(): boolean--><!--Device-GestureRecognizer-isEnabled(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当前手势识别器的使能状态。true表示当前手势识别器能够回调应用事件，false表示当前手势识别器不回调应用事件。 |

## isFingerCountLimit

```TypeScript
isFingerCountLimit(): boolean
```

返回预设手势是否会检测触摸屏幕上手指识别数量。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-GestureRecognizer-isFingerCountLimit(): boolean--><!--Device-GestureRecognizer-isFingerCountLimit(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 预设手势是否会检测触摸屏幕上手指识别数量。当绑定手势事件且会检测触摸屏幕上手指的数量时，返回true。当绑定手势事件且不会检测触摸屏幕上手指的数量时，返回false。 |

## isHostBelongsTo

```TypeScript
isHostBelongsTo(uniqueId: number): boolean
```

返回当前手势识别器绑定节点是否为传入组件的后代节点。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-GestureRecognizer-isHostBelongsTo(uniqueId: int): boolean--><!--Device-GestureRecognizer-isHostBelongsTo(uniqueId: int): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uniqueId | number | 是 | 组件的唯一ID。可以通过[getUniqueId](arkts-arkui-eventtargetinfo-c.md#getuniqueid)接口获取该ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当前手势识别器绑定节点是否为传入组件的后代节点。true表示当前绑定节点为传入组件的后代节点，false表示当前绑定节点非传入组件的后代节点。 |

## isValid

```TypeScript
isValid(): boolean
```

返回当前手势识别器是否有效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureRecognizer-isValid(): boolean--><!--Device-GestureRecognizer-isValid(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当前手势识别器是否有效。<br/>当该识别器绑定的组件被析构或该识别器不在响应链上时返回false。<br/>当该识别器绑定的组件未被析构且该识别器在响应链上时返回true。 |

## preventBegin

```TypeScript
preventBegin(): void
```

在手指全部抬起前阻止手势识别器参与当前手势识别。如果系统已确定该手势识别器的结果（无论成功与否），调用此接口将无效。此方法与GestureRecognizer.[setEnabled](arkts-arkui-gesturerecognizer-c.md#setenabled)(isEnabled: boolean)不同，[setEnabled](arkts-arkui-gesturerecognizer-c.md#setenabled)并不会阻止手势识别器对象参与手势识别过程，而只会影响手势对应的回调函数是否执行。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-GestureRecognizer-preventBegin(): void--><!--Device-GestureRecognizer-preventBegin(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setEnabled

```TypeScript
setEnabled(isEnabled: boolean): void
```

设置当前手势识别器的使能状态。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GestureRecognizer-setEnabled(isEnabled: boolean): void--><!--Device-GestureRecognizer-setEnabled(isEnabled: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | boolean | 是 | 手势识别器的使能状态。true表示当前手势识别器能够回调应用事件，false表示当前手势识别器不回调应用事件。 |

