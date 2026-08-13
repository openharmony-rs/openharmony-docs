# GestureHandler

手势处理器的基础类型。

**继承/实现关系：** GestureHandler implements GestureInterface<T>

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-unnamed-declare class GestureHandler--><!--Device-unnamed-declare class GestureHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## allowedTypes

```TypeScript
allowedTypes(types: Array<SourceTool>): T
```

设置手势处理器所支持的事件输入源。

**起始版本：** 14

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为14。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-GestureHandler-allowedTypes(types: Array<SourceTool>): T--><!--Device-GestureHandler-allowedTypes(types: Array<SourceTool>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| types | Array&lt;SourceTool&gt; | 是 | 手势处理器所支持的事件输入源。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

## tag

```TypeScript
tag(tag: string): T
```

设置手势处理器的标志。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GestureHandler-tag(tag: string): T--><!--Device-GestureHandler-tag(tag: string): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tag | string | 是 | 手势处理器的标志。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

