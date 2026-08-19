# TextInput

## TextInput

```TypeScript
@ComponentBuilder
export declare function TextInput(
    value?: TextInputOptions
): TextInputAttribute
```

定义TextInput组件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function TextInput(    value?: TextInputOptions): TextInputAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function TextInput(    value?: TextInputOptions): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [TextInputOptions](arkts-arkui-textinput-textinputoptions-i.md) | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| TextInputAttribute |  |


## TextInput

```TypeScript
@Builder
export declare function TextInput(
    style: CustomBuilderT<TextInputAttribute>,
): TextInputAttribute
```

定义TextInput组件。

**起始版本：** 26.1.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.1.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function TextInput(    style: CustomBuilderT<TextInputAttribute>,): TextInputAttribute--><!--Device-unnamed-@Builderexport declare function TextInput(    style: CustomBuilderT<TextInputAttribute>,): TextInputAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;TextInputAttribute&gt; | 是 | TextInput属性的实例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| TextInputAttribute |  |

