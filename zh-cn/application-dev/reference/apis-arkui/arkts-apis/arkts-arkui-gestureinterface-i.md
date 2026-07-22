# GestureInterface

定义Gesture接口。

**起始版本：** 11

<!--Device-unnamed-interface GestureInterface<T>--><!--Device-unnamed-interface GestureInterface<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## allowedTypes

```TypeScript
allowedTypes(types: Array<SourceTool>): T
```

设置手势响应的输入类型。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-GestureInterface-allowedTypes(types: Array<SourceTool>): T--><!--Device-GestureInterface-allowedTypes(types: Array<SourceTool>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| types | Array&lt;SourceTool&gt; | 是 | 手势响应的输入类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

## tag

```TypeScript
tag(tag: string): T
```

设置手势的标志。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GestureInterface-tag(tag: string): T--><!--Device-GestureInterface-tag(tag: string): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tag | string | 是 | 手势的标志。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

