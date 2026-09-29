# SearchOptions

```TypeScript
declare interface SearchOptions
```

Initialization parameters of Search.

> **NOTE:** 
> 
> To standardize the definition of anonymous objects, the element definitions here were modified in API version 18.
> The since version information of the historical anonymous objects is retained, which may result in the

**Since:** 18

<!--Device-unnamed-declare interface SearchOptions--><!--Device-unnamed-declare interface SearchOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: SearchController
```

Sets the controller of the Search component. Pass this parameter when you need to operate the search box through the controller (for example, setting the cursor position or stopping editing). If it is not passed, the controller- related methods cannot be used.

**Type:** [SearchController](arkts-arkui-search-comp-searchcontroller-c.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SearchOptions-controller?: SearchController--><!--Device-SearchOptions-controller?: SearchController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: string
```

Sets the path of the search icon. The system search icon is used by default.

**NOTE:** 

The data source of icon supports [displaying an image using a relative path](../../../reference/apis-arkui/arkui-ts/ts-basic-components-image.md#example-25-displaying-an-image-using-a-relative-path) and network images.

- The supported image formats include png, jpg, bmp, svg, gif, pixelmap, and heif.

- Base64 strings are supported. Format data:image/[png|jpeg|bmp|webp|heif];base64,[base64 data], where [base64 data] is the Base64 string data.

If this parameter is set together with the searchIcon attribute, searchIcon takes precedence.

On wearable devices, the default icon size is 16 vp.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SearchOptions-icon?: string--><!--Device-SearchOptions-icon?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## placeholder

```TypeScript
placeholder?: ResourceStr
```

Sets the placeholder text displayed when there is no input. Pass this parameter when you need to customize the placeholder text. If it is not passed, no placeholder text is displayed.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SearchOptions-placeholder?: ResourceStr--><!--Device-SearchOptions-placeholder?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value?: ResourceStr
```

Sets the search text currently displayed. Pass this parameter when you need to set the initial text content of the search box. If it is not passed, the search box is empty.

Since API version 10, this parameter supports [$$](../../../ui/state-management/arkts-two-way-sync.md) two-way binding variables.

Since API version 18, this parameter supports [!!](../../../ui/state-management/arkts-new-binding.md#two-way-binding-between-built-in-component-parameters) two- way binding variables.

Since API version 20, the Resource type is supported.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SearchOptions-value?: ResourceStr--><!--Device-SearchOptions-value?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
