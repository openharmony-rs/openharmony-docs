# GestureHandler

手势处理器的基础类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class GestureHandler--><!--Device-unnamed-export declare class GestureHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## allowedTypes

```TypeScript
allowedTypes(types: Array<SourceTool>): this
```

设置手势处理器所支持的事件输入源。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureHandler-allowedTypes(types: Array<SourceTool>): this--><!--Device-GestureHandler-allowedTypes(types: Array<SourceTool>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| types | Array&lt;[SourceTool](../arkts-components/arkts-arkui-sourcetool-e.md)&gt; | 是 | 手势处理器所支持的事件输入源。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前组件。 |

## tag

```TypeScript
tag(tag: string): this
```

设置手势处理器的标志。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureHandler-tag(tag: string): this--><!--Device-GestureHandler-tag(tag: string): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tag | string | 是 | 手势处理器的标志。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前组件。 |

