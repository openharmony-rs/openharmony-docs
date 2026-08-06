# ShouldBuiltInRecognizerParallelWithCallback

```TypeScript
declare type ShouldBuiltInRecognizerParallelWithCallback = (current: GestureRecognizer, others: Array<GestureRecognizer>) => GestureRecognizer
```

系统内置手势与响应链上其他组件的手势设置并行关系的回调事件类型。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type ShouldBuiltInRecognizerParallelWithCallback = (current: GestureRecognizer, others: Array<GestureRecognizer>) => GestureRecognizer--><!--Device-unnamed-declare type ShouldBuiltInRecognizerParallelWithCallback = (current: GestureRecognizer, others: Array<GestureRecognizer>) => GestureRecognizer-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| current | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 当前组件的系统内置手势识别器，当前版本只提供内置的[GestureType]\_\_\_JSDOC\_LINK\_USD\_0\_\_\_.PAN\_GESTURE类型的手势识别器。  |
| others | Array&lt;GestureRecognizer&gt; | 是 | 响应链上更高优先级的其他组件相同类别的手势识别器。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 与current识别器绑定并行关系的某个手势识别器。 |

