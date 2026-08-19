# Gesture

定义Gesture接口。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class Gesture--><!--Device-unnamed-export declare class Gesture-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## allowedTypes

```TypeScript
allowedTypes(types: Array<SourceTool>): this
```

设置手势响应的输入类型。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Gesture-allowedTypes(types: Array<SourceTool>): this--><!--Device-Gesture-allowedTypes(types: Array<SourceTool>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| types | Array&lt;[SourceTool](../arkts-components/arkts-arkui-sourcetool-e.md)&gt; | 是 | 手势响应的输入类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前组件。 |

## tag

```TypeScript
tag(tag: string): this
```

设置手势的标志。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Gesture-tag(tag: string): this--><!--Device-Gesture-tag(tag: string): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tag | string | 是 | 手势的标志。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前组件。 |

