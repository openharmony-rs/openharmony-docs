# Hyperlink

## Hyperlink

```TypeScript
@ComponentBuilder
export declare function Hyperlink(
    address: string | Resource | undefined, content?: string | Resource, 
    content_?: CustomBuilder,
): HyperlinkAttribute
```

定义Hyperlink组件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Hyperlink(    address: string | Resource | undefined, content?: string | Resource,     content_?: CustomBuilder,): HyperlinkAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function Hyperlink(    address: string | Resource | undefined, content?: string | Resource,     content_?: CustomBuilder,): HyperlinkAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| address | string \| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) \| undefined | 是 | Hyperlink组件跳转的网页地址。<br/>取值为undefined时，按无跳转链接地址处理。 |
| content | string \| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) | 否 | Hyperlink组件中超链接显示文本。<br/>若不传该参数且组件内无子组件时，默认显示address参数值链接地址。<br/> **说明：** <br/>组件内有子组件时，不显示超链接文本。 <br>默认值：''。 |
| content_ | CustomBuilder | 否 | The node of component. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| HyperlinkAttribute |  |


## Hyperlink

```TypeScript
@Builder
export declare function Hyperlink(
    style: CustomBuilderT<HyperlinkAttribute>,
    content_?: CustomBuilder,
): HyperlinkAttribute
```

定义Hyperlink组件。

**起始版本：** 26.1.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.1.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function Hyperlink(    style: CustomBuilderT<HyperlinkAttribute>,    content_?: CustomBuilder,): HyperlinkAttribute--><!--Device-unnamed-@Builderexport declare function Hyperlink(    style: CustomBuilderT<HyperlinkAttribute>,    content_?: CustomBuilder,): HyperlinkAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;HyperlinkAttribute&gt; | 是 | Hyperlink属性实例。 |
| content_ | CustomBuilder | 否 | 容器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| HyperlinkAttribute |  |

