# SaveButton properties/events

```TypeScript
declare class SaveButtonAttribute extends SecurityComponentMethod<SaveButtonAttribute>
```

Universal attributes are not supported. This component supports the attributes listed below, as well as [universal attributes of security components](../arkts-apis/arkts-arkui-security_component.md). Only the following events are supported.

**Inheritance/Implementation:** SaveButtonAttribute extends SecurityComponentMethod<SaveButtonAttribute>

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## iconBorderRadius

```TypeScript
iconBorderRadius(radius: Dimension | BorderRadiuses)
```

Sets the corner radius of the **SaveButton** component.

**Since:** 20

**Required permissions:** ohos.permission.CUSTOMIZE_SAVE_BUTTON

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| radius | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) &#124; [BorderRadiuses](../arkts-apis/arkts-arkui-borderradiuses-t.md) | Yes | Corner radius of the **SaveButton** component. You can set the radius for each of the four corners individually.<br>The default value is 0 vp for all four corners. Units such as vp and px are supported, and valid values are greater than or equal to 0. Negative values are automatically clamped to **0**. <br>If the app does not have the **ohos.permission.CUSTOMIZE_SAVE_BUTTON** permission, the corner radius setting of the icon does not take effect. |

## iconSize

```TypeScript
iconSize(size: Dimension | SizeOptions)
```

Sets the icon size of the **SaveButton** component.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) &#124; [SizeOptions](../arkts-apis/arkts-arkui-sizeoptions-i.md) | Yes | Icon size. Pixel units such as vp and px are supported. <br>The default width and height are 16 vp.<br>Percentage strings are not supported. If a percentage string is passed as a Dimension parameter, the icon will be displayed with the default size. If either the **width** or **height** property of a SizeOptions type parameter is set to a percentage string, the icon will be displayed with a size of 0 vp. <br>For the system icons provided by the **SaveButton** component: <br>- Dimension type: Width and height are both set to the specified value. <br>- SizeOptions type: If width and height are different, the smaller value is used for both. If only one value is specified, it applies to both dimensions. This rule ensures square display and consistent visual appearance of system icons. <br>For custom icons: <br>- Dimension type: Width and height are both set to the specified value. <br>- SizeOptions type: It is recommended that you set both width and height explicitly; if only one value is set, it applies to both dimensions. Custom icons support flexible sizing to adapt to different image aspect ratios. <br>- If the specified size's aspect ratio does not match the custom icon's original ratio, the icon displays in [ImageFit.Cover](../arkts-apis/arkts-arkui-imagefit-e.md) mode. |

## onClick

```TypeScript
onClick(event: SaveButtonCallback)
```

Triggered when the **SaveButton** component is clicked. When a user clicks the save button for the first time, an authorization dialog box is displayed. If the user allows authorization, the app obtains temporary access to media library APIs. For details about the authorization duration, see the description of the [SaveButton](arkts-arkui-savebutton-comp.md#savebutton) constructor. Authorization fails if the user declines authorization or closes the dialog box.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [SaveButtonCallback](arkts-arkui-savebutton-comp-savebuttoncallback-t.md) | Yes | Callback object for the click event, which carries click details, authorization result and error information.<br>Starting from API version 18, **SaveButtonCallback** is adopted uniformly, which additionally provides error information.<br>**Since:** 18 |

## setIcon

```TypeScript
setIcon(icon: Resource)
```

Sets the icon of the **SaveButton** component.

**Since:** 20

**Required permissions:** ohos.permission.CUSTOMIZE_SAVE_BUTTON

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| icon | [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Custom icon resource information. Only data sources of the Resource type are supported. <br>Images in the following formats are supported: PNG, JPG, JPEG, BMP, SVG, WebP, GIF, and HEIF. For details about the supported image formats, see [Image](arkts-arkui-image-comp.md#image). If the resource is not an image resource or the format is not supported, the icon is displayed as blank. <br>Since API version 26.0.0, data sources of the Resource type in Symbol format are supported. <br>If the app does not have the **ohos.permission.CUSTOMIZE_SAVE_BUTTON** permission, the custom icon does not take effect and the save button uses the default style. |

## setText

```TypeScript
setText(text: string | Resource)
```

Sets the text of the **SaveButton** component.

**Since:** 20

**Required permissions:** ohos.permission.CUSTOMIZE_SAVE_BUTTON

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Custom text, used to replace the default system text for business-specific scenarios. When a string is passed, the text content is directly used. When a Resource is passed, multi- language adaptation is implemented via resource management.<br>If the app does not have the **ohos.permission.CUSTOMIZE_SAVE_BUTTON** permission, this setting does not take effect and the save button uses the default style. |

## stateEffect

```TypeScript
stateEffect(enabled: boolean)
```

Sets the press effect of the **SaveButton** component.

**Since:** 20

**Required permissions:** ohos.permission.CUSTOMIZE_SAVE_BUTTON

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to enable the press effect. **true** to enable, **false** otherwise.<br>Default value: **false**.<br>If the app does not have the **ohos.permission.CUSTOMIZE_SAVE_BUTTON** permission, the press effect setting does not take effect. |

## symbolFontWeight

```TypeScript
symbolFontWeight(fontWeight: number | FontWeight | string | Resource)
```

Sets the font weight of the symbol icon for the save button.

- Before calling this method, you need to call [setIcon](#seticon) to configure a symbol-  
style icon resource (i.e., **$r('sys.symbol.*xxx*')**).  
- If no symbol icon is configured, the font weight setting will not apply.

**Since:** 26.0.0

**Required permissions:** ohos.permission.CUSTOMIZE_SAVE_BUTTON

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fontWeight | number &#124; [FontWeight](../arkts-apis/arkts-arkui-fontweight-e.md) &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Symbol icon font weight of the save button.<br>For the number type: The value range is [100, 900] with an increment of 100. Larger values result in bolder font weight. <br>For the string type: The value can be a numeric string of the number type (for example, **"400"**) or a lowercase string of the enumerated value of FontWeight (for example, **"normal"**). <br>Default value: **FontWeight.Normal** (the corresponding value is **400**) <br>If the app does not have the **ohos.permission.CUSTOMIZE_SAVE_BUTTON** permission, the setting does not take effect. |

## symbolIconColor

```TypeScript
symbolIconColor(color: Array<ResourceColor>)
```

Sets the color of the symbol icon for the save button.

- Before calling this method, you need to call [setIcon](#seticon) to configure a symbol-  
style icon resource (i.e., **$r('sys.symbol.xxx')**).  
- If no symbol icon is set, the color set via this method does not take effect.  
- It is recommended that you use this API together with [symbolRenderingStrategy](#symbolrenderingstrategy) to achieve different rendering effects.

**Since:** 26.0.0

**Required permissions:** ohos.permission.CUSTOMIZE_SAVE_BUTTON

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | Array&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | Yes | Symbol icon color of the save button. This parameter applies to scenarios where the symbol icon needs to be consistent with the service visual style. <br>Default value: varies depending on [symbolRenderingStrategy](#symbolrenderingstrategy). <br>If the app does not have the **ohos.permission.CUSTOMIZE_SAVE_BUTTON** permission, the setting does not take effect. |

## symbolRenderingStrategy

```TypeScript
symbolRenderingStrategy(strategy: SymbolRenderingStrategy)
```

Sets the rendering strategy for the symbol icon of the save button.

- Before calling this method, you need to call [setIcon](#seticon) to configure a symbol-  
style icon resource (i.e., **$r('sys.symbol.*xxx*')**).  
- The configured rendering strategy will not apply if no symbol icon is set.  
- When this parameter is used together with [symbolIconColor](#symboliconcolor), the  
rendering strategy determines how the color array is applied.

**Since:** 26.0.0

**Required permissions:** ohos.permission.CUSTOMIZE_SAVE_BUTTON

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strategy | [SymbolRenderingStrategy](arkts-arkui-symbolglyph-comp-symbolrenderingstrategy-e.md) | Yes | Rendering strategy for the symbol icon of the save button, which defines how the symbol icon is rendered.<br>Default value: SymbolRenderingStrategy.SINGLE. <br>If the app does not have the **ohos.permission.CUSTOMIZE_SAVE_BUTTON** permission, the setting does not take effect. |

## userCancelEvent

```TypeScript
userCancelEvent(enabled: boolean)
```

Sets the user authorization cancellation event for the **SaveButton** component. This API can be used to distinguish between user cancellation and authorization failures for differentiated service logic, such as logging user behaviors or prompting users to retry.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to receive the user authorization cancellation event of the save button.<br>Default value: **false**.<br>The value **true** indicates that when a user manually cancels authorization in the authorization dialog box, the callback returns the result **CANCELED_BY_USER**. The value **false** indicates that user cancellation is not distinguished from other scenarios. <br>You are advised to enable this parameter if your service needs to distinguish between user cancellation and system errors/authorization failures. |
