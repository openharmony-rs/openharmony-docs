# Button

## Button

```TypeScript
@ComponentBuilder
export declare function Button(
    label: ResourceStr, options?: ButtonOptions, 
    content_?: CustomBuilder,
): ButtonAttribute
```

使用文本内容创建相应的按钮组件，此时Button无法包含子组件。 文本内容默认单行显示。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Button(    label: ResourceStr, options?: ButtonOptions,     content_?: CustomBuilder,): ButtonAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function Button(    label: ResourceStr, options?: ButtonOptions,     content_?: CustomBuilder,): ButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| label | [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 按钮文本内容。<br/>**说明：** 当文本字符的长度超过按钮本身的宽度时，文本将会被截断。 |
| options | [ButtonOptions](arkts-na-button-buttonoptions-i.md) | 否 | 配置按钮的显示样式。<br/> 未设置时，则按照ButtonOptions中各参数的默认值配置。 |
| content_ | CustomBuilder | 否 | container |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ButtonAttribute](arkts-na-button-buttonattribute-i.md) |  |


## Button

```TypeScript
@ComponentBuilder
export declare function Button(
    options?: ButtonOptions, 
    content_?: CustomBuilder,
): ButtonAttribute
```

Defines Button Component.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Button(    options?: ButtonOptions,     content_?: CustomBuilder,): ButtonAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function Button(    options?: ButtonOptions,     content_?: CustomBuilder,): ButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ButtonOptions](arkts-na-button-buttonoptions-i.md) | 否 | the options of Button. |
| content_ | CustomBuilder | 否 | container |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ButtonAttribute](arkts-na-button-buttonattribute-i.md) |  |

