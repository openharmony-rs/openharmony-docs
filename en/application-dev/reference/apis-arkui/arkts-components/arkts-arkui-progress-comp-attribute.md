# Progress properties/events

```TypeScript
declare class ProgressAttribute<Type extends keyof ProgressStyleMap = keyof ProgressStyleMap,
  Style extends ProgressStyleMap[Type] = ProgressStyleMap[Type]> extends CommonMethod<ProgressAttribute<Type>>
```

In addition to the [universal attributes](../../../reference/apis-arkui/arkui-ts/ts-component-general-attributes.md), the following attributes are supported.

The [universal events][universal events](../../../reference/apis-arkui/arkui-ts/ts-component-general-events.md) are supported.

**Inheritance/Implementation:** ProgressAttribute extends CommonMethod<ProgressAttribute<Type>>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color(value: ResourceColor | LinearGradient)
```

Sets the foreground color of the progress indicator.

Since API version 10, LinearGradient can be used to set a gradient color for the ring style. Setting opacity is not recommended for the ring type. If opacity is required, use [DataPanel](arkts-arkui-datapanel-comp.md#data_panel).

Since API version 23, LinearGradient can be used to set gradient colors for the linear and capsule styles. In API version 22 and earlier versions, setting gradient colors via **LinearGradient** for the **Linear** and **Capsule** styles will not render the custom colors; the system's default theme colors will be used instead.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) &#124; LinearGradient | Yes | Foreground color of the progress indicator.<br>Default value:<br>   - Capsule:<br>   API version 9 or earlier: **'#ff007dff'**<br>   API version 10: **'#33006cde'**<br>   API   version 11 or later: **'#33007dff'**<br>- Ring:<br>   API version 9 or earlier: **'#ff007dff'**<br>   API version 10 or later: start: **'#ff86c1ff'**, end: **'#ff254ff7'**<br>- Other styles: **'#ff007dff'** |

## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<ProgressConfiguration>)
```

Creates a content modifier.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| modifier | [ContentModifier](arkts-arkui-common-comp-contentmodifier-i.md)&lt;[ProgressConfiguration](arkts-arkui-progress-comp-progressconfiguration-i.md)&gt; | Yes | The contentModifier of progress. |

## privacySensitive

```TypeScript
privacySensitive(isPrivacySensitiveMode: Optional<boolean>)
```

Sets whether to enable privacy-sensitive mode.

> **NOTE:** 
> 
> This API can be called in [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 20.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isPrivacySensitiveMode | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable privacy-sensitive mode, in which the progress indicator is cleared and text content is masked. **true**: The privacy-sensitive mode is enabled. **false**: The privacy-sensitive mode is disabled.<br> Default value: **false**<br>**NOTE:** <br>Setting this parameter to **null** indicates that no specific privacy sensitivity is applied.<!--Del--><br>For widgets, this property must be used with [FormComponent](arkts-arkui-formcomponent-comp-sys.md#form_component) and the [obscured](arkts-arkui-common-comp-commonmethod-c.md#obscured) attribute to display privacy masking effects.<!--DelEnd--> |

## style

```TypeScript
style(value: Style)
```

Sets the component style.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Style | Yes | Component style.<br>- **CapsuleStyleOptions**: capsule style.<br>- **RingStyleOptions**: ring style.<br>- **LinearStyleOptions**: linear style.<br>- **ScaleRingStyleOptions**: determinate ring style.<br>- **EclipseStyleOptions**: eclipse style.<br>- **ProgressStyleOptions**: **strokeWidth**, **scaleCount**, and **scaleWidth** of a progress indicator. This parameter is valid only for the progress indicator that supports these style settings. |

## value

```TypeScript
value(value: number)
```

Current progress. Values less than 0 are adjusted to **0**, and values greater than the **total** value are capped at the **total** value. Invalid values do not take effect.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Current progress.<br> Default value: **0** |
