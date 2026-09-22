# SearchOptions

```TypeScript
declare interface SearchOptions
```

Describes the initialization options of the **Search** component.

> **NOTE:** 
> 
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18.
> While historical version information is preserved for anonymous objects, there may be cases where the outer element
> 's

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: SearchController
```

Controller of the **Search** component.

**Type:** [SearchController](arkts-arkui-search-comp-searchcontroller-c.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: string
```

Path to the search icon. By default, the system search icon is used.

**NOTE:** 

The icon data source supports both [relative paths](../../../reference/apis-arkui/arkui-ts/ts-basic-components-image.md#example-25-displaying-an-image-using-a-relative-path) and network images.

- The supported formats include PNG, JPG, BMP, SVG, GIF, pixelmap, and HEIF.  
- The Base64 string is supported in the following format: data:image/[png|jpeg|bmp|webp|heif];base64,[base64 data],  
where *[base64 data]* is a Base64 string.

If this attribute and the **searchIcon** attribute are both set, the **searchIcon** attribute takes precedence.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## placeholder

```TypeScript
placeholder?: ResourceStr
```

Text displayed when there is no input.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value?: ResourceStr
```

Sets the text input in the search text box.

Since API version 10, this parameter supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md).

Since API version 18, this parameter supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md#two-way-binding-between-built-in-component-parameters).

The Resource type is supported since API version 20.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
