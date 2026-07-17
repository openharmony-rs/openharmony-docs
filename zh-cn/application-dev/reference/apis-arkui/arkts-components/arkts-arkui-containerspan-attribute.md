# ContainerSpan属性/事件

仅支持以下属性：

不支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)。

**起始版本：** 11

<!--Device-unnamed-declare class ContainerSpanAttribute--><!--Device-unnamed-declare class ContainerSpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## attributeModifier

```TypeScript
attributeModifier(modifier: AttributeModifier<ContainerSpanAttribute>)
```

设置组件的动态属性。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ContainerSpanAttribute-attributeModifier(modifier: AttributeModifier<ContainerSpanAttribute>): ContainerSpanAttribute--><!--Device-ContainerSpanAttribute-attributeModifier(modifier: AttributeModifier<ContainerSpanAttribute>): ContainerSpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [AttributeModifier](arkts-arkui-common-attributemodifier-i.md)<ContainerSpanAttribute> | 是 | 动态设置组件的属性。 |

## textBackgroundStyle

```TypeScript
textBackgroundStyle(style: TextBackgroundStyle)
```

Span的背景样式

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ContainerSpanAttribute-textBackgroundStyle(style: TextBackgroundStyle): ContainerSpanAttribute--><!--Device-ContainerSpanAttribute-textBackgroundStyle(style: TextBackgroundStyle): ContainerSpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [TextBackgroundStyle](arkts-arkui-span-textbackgroundstyle-i.md) | 是 | The background style of span. |

