# Repeat properties/events

```TypeScript
declare class RepeatAttribute<T> extends DynamicNode<RepeatAttribute<T>>
```

In addition to the drag-and-drop sorting attribute, the following attributes are supported.

**Inheritance/Implementation:** RepeatAttribute extends DynamicNode<RepeatAttribute<T>>

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## each

```TypeScript
each(itemGenerator: (repeatItem: RepeatItem<T>) => void)
```

Component generator. When the return value of [.templateId()](#templateid) does not match any [.template()](#template) type (that is, the current item does not match any defined template style), the data item is processed using **.each()**.

> **NOTE:** 
> 
> - The **each** property is mandatory. If it is omitted, runtime errors will occur.
> 
> - The **itemGenerator** parameter is of the **RepeatItem** type, which combines **item** and **index**. Do not destructure **RepeatItem**.
> 
> - This API cannot be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| itemGenerator | (repeatItem: RepeatItem&lt;T&gt;) =&gt; void | Yes | Component generator. |

## key

```TypeScript
key(keyGenerator: (item: T, index: number) => string)
```

Key generator.

> **NOTE:** 
> 
> This API cannot be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyGenerator | (item: T, index: number) =&gt; string | Yes | Key generator.<br>**item**: data item in the **arr** array. It is optional.<br> **index**: index of a data item in the **arr** array. It is optional. |

## template

```TypeScript
template(type: string, itemBuilder: RepeatItemBuilder<T>, templateOptions?: TemplateOptions)
```

Renders the corresponding template child component based on the template type.

> **NOTE:** 
> 
> This API cannot be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Current template type. |
| itemBuilder | [RepeatItemBuilder](arkts-arkui-repeat-comp-repeatitembuilder-t.md)&lt;T&gt; | Yes | Component generator. |
| templateOptions | [TemplateOptions](arkts-arkui-repeat-comp-templateoptions-i.md) | No | Current template configuration. |

## templateId

```TypeScript
templateId(typedFunc: TemplateTypedFunc<T>)
```

Assigns a template type for this data item.

> **NOTE:** 
> 
> This API cannot be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typedFunc | [TemplateTypedFunc](arkts-arkui-repeat-comp-templatetypedfunc-t.md)&lt;T&gt; | Yes | Function that generates a template type for each data item. |

## virtualScroll

```TypeScript
virtualScroll(virtualScrollOptions?: VirtualScrollOptions)
```

Enables virtual scrolling for **Repeat**.

> **NOTE:** 
> 
> This API cannot be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| virtualScrollOptions | [VirtualScrollOptions](arkts-arkui-repeat-comp-virtualscrolloptions-i.md) | No | Virtual scrolling configuration. |
