# ContainerSpan properties/events

```TypeScript
declare class ContainerSpanAttribute
```

Only the following attributes are supported.

The [universal events](../../../reference/apis-arkui/arkui-ts/ts-component-general-events.md) are not supported.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## attributeModifier

```TypeScript
attributeModifier(modifier: AttributeModifier<ContainerSpanAttribute>)
```

Creates an attribute modifier.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| modifier | [AttributeModifier](arkts-arkui-common-comp-attributemodifier-i.md)&lt;[ContainerSpanAttribute](arkts-arkui-containerspan-comp-attribute.md)&gt; | Yes | Modifier for dynamically setting attributes on the current component. |

## textBackgroundStyle

```TypeScript
textBackgroundStyle(style: TextBackgroundStyle)
```

Span background style.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [TextBackgroundStyle](arkts-arkui-span-comp-textbackgroundstyle-i.md) | Yes | The background style of span. |
