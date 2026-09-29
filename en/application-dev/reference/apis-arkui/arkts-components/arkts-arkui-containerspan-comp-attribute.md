# ContainerSpan properties/events

```TypeScript
declare class ContainerSpanAttribute
```

Only the following attributes are supported.

**Since:** 11

<!--Device-unnamed-declare class ContainerSpanAttribute--><!--Device-unnamed-declare class ContainerSpanAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## attributeModifier

```TypeScript
attributeModifier(modifier: AttributeModifier<ContainerSpanAttribute>)
```

Creates an attribute modifier.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ContainerSpanAttribute-attributeModifier(modifier: AttributeModifier<ContainerSpanAttribute>): ContainerSpanAttribute--><!--Device-ContainerSpanAttribute-attributeModifier(modifier: AttributeModifier<ContainerSpanAttribute>): ContainerSpanAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| modifier | [AttributeModifier](arkts-arkui-common-comp-attributemodifier-i.md)&lt;[ContainerSpanAttribute](arkts-arkui-containerspan-comp-attribute.md)&gt; | Yes | Modifier for dynamically setting attributes on the current component. You need to customize a class that inherits from the **AttributeModifier** API to receive a **ContainerSpanAttribute** instance in the **applyNormalAttribute** API and dynamically modify the value of the **ContainerSpan** attribute. |

## textBackgroundStyle

```TypeScript
textBackgroundStyle(style: TextBackgroundStyle)
```

Sets the text background style. Child components inherit this attribute value when they do not set it. When this API is not used, the default background color is **Color.Transparent** and the default corner radius is 0.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 12.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ContainerSpanAttribute-textBackgroundStyle(style: TextBackgroundStyle): ContainerSpanAttribute--><!--Device-ContainerSpanAttribute-textBackgroundStyle(style: TextBackgroundStyle): ContainerSpanAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [TextBackgroundStyle](arkts-arkui-span-comp-textbackgroundstyle-i.md) | Yes | Text background style, used to set the text background color and corner radius of **Span** and **ImageSpan** in the **ContainerSpan** component. Child components inherit this parameter value when they do not set it. |
