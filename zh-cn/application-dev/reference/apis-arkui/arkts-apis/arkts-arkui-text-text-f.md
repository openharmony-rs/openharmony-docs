# Text

## Text

```TypeScript
@Builder
export declare function Text(
    style: CustomBuilderT<TextAttribute>,
    content_?: CustomBuilder,
): TextAttribute
```

定义Text组件。

**起始版本：** 26.1.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.1.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function Text(    style: CustomBuilderT<TextAttribute>,    content_?: CustomBuilder,): TextAttribute--><!--Device-unnamed-@Builderexport declare function Text(    style: CustomBuilderT<TextAttribute>,    content_?: CustomBuilder,): TextAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;TextAttribute&gt; | 是 | Text属性实例。 |
| content_ | CustomBuilder | 否 | 容器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| TextAttribute |  |


## Text

```TypeScript
@ComponentBuilder
export declare function Text(
    content?: string | Resource, value?: TextOptions, 
    content_?: CustomBuilder,
): TextAttribute
```

定义Text组件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Text(    content?: string | Resource, value?: TextOptions,     content_?: CustomBuilder,): TextAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function Text(    content?: string | Resource, value?: TextOptions,     content_?: CustomBuilder,): TextAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | string \| [Resource](arkts-arkui-resource-t.md) | 否 |  |
| value | [TextOptions](arkts-arkui-text-textoptions-i.md) | 否 |  |
| content_ | CustomBuilder | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| TextAttribute |  |

