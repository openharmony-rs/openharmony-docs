# Progress properties/events

```TypeScript
declare class ProgressAttribute<Type extends keyof ProgressStyleMap = keyof ProgressStyleMap,
  Style extends ProgressStyleMap[Type] = ProgressStyleMap[Type]> extends CommonMethod<ProgressAttribute<Type>>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md), the following attributes are supported.

> **NOTE:** 
> 
> This component overrides the universal attribute
> [backgroundColor](arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor1). When applied directly to the
> **Progress** component, it sets the background color of the progress indicator itself. To set the background color
> for the entire **Progress** component area, apply **backgroundColor** to the outer container that wraps the
> **Progress** component.

**Inheritance/Implementation:** ProgressAttribute extends CommonMethod&lt;ProgressAttribute&lt;Type&gt;&gt;

**Since:** 7

<!--Device-unnamed-declare class ProgressAttribute<Type extends keyof ProgressStyleMap = keyof ProgressStyleMap,  Style extends ProgressStyleMap[Type] = ProgressStyleMap[Type]> extends CommonMethod<ProgressAttribute<Type>>--><!--Device-unnamed-declare class ProgressAttribute<Type extends keyof ProgressStyleMap = keyof ProgressStyleMap,  Style extends ProgressStyleMap[Type] = ProgressStyleMap[Type]> extends CommonMethod<ProgressAttribute<Type>>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color(value: ResourceColor | LinearGradient)
```

Sets the foreground color of the progress indicator.

Since API version 10, LinearGradient can be used to set a gradient color for the ring style. Setting opacity is not recommended for the ring type. If opacity is required, use [DataPanel](arkts-arkui-datapanel-comp.md).

Since API version 23, LinearGradient can be used to set the gradient color of the Linear style and Capsule style. In API version 22 and earlier, when this method is used, the default theme color is displayed.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ProgressAttribute-color(value: ResourceColor | LinearGradient): ProgressAttribute<Type>--><!--Device-ProgressAttribute-color(value: ResourceColor | LinearGradient): ProgressAttribute<Type>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) &#124; LinearGradient | Yes | Foreground color of the progress bar.<br>Since API version 10, LinearGradient is supported for setting the gradient color of the Ring style. Since API version 23, LinearGradient is supported for setting the gradient color of the Linear style and Capsule style. <br>Default value: <br>- Capsule: <br>   API version 9 and earlier: '#ff007dff'<br>   API version 10: '#33006cde'<br>   API version 11 and later: '#33007dff'<br>- Ring: <br>   API version 9 and earlier: '#ff007dff'<br>   API version 10 and later: start: '#ff86c1ff', end: '#ff254ff7'<br>- Other styles: '#ff007dff' |

## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<ProgressConfiguration>)
```

Creates a content modifier.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ProgressAttribute-contentModifier(modifier: ContentModifier<ProgressConfiguration>): ProgressAttribute<Type>--><!--Device-ProgressAttribute-contentModifier(modifier: ContentModifier<ProgressConfiguration>): ProgressAttribute<Type>-End-->

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

<!--Device-ProgressAttribute-privacySensitive(isPrivacySensitiveMode: Optional<boolean>): ProgressAttribute<Type>--><!--Device-ProgressAttribute-privacySensitive(isPrivacySensitiveMode: Optional<boolean>): ProgressAttribute<Type>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isPrivacySensitiveMode | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Sets privacy sensitivity. In privacy mode, the progress is cleared and the text is masked. true: enables privacy sensitivity; false: disables privacy sensitivity. <br> Default value: false <br>**Note:** <br>Setting null indicates that the component is not sensitive. <!--Del--> <br>To use Progress in a card and set the [privacy mask](arkts-arkui-common-comp.md) attribute with the [FormComponent](arkts-arkui-formcomponent-comp-sys.md) component, the privacy mask effect is available only when the card is displayed.<!--DelEnd--> |

## style

```TypeScript
style(value: Style)
```

Sets the component style.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ProgressAttribute-style(value: Style): ProgressAttribute<Type>--><!--Device-ProgressAttribute-style(value: Style): ProgressAttribute<Type>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Style | Yes | Style of the component. Style inherits from [ProgressStyleMap](arkts-arkui-progress-comp-progressstylemap-i.md). <br>**Note:** Different [ProgressType](arkts-arkui-progress-comp-progresstype-e.md) values must correspond to the respective [style](#style) attribute settings. For the detailed mapping, see [ProgressStyleMap](arkts-arkui-progress-comp-progressstylemap-i.md). <br>- [CapsuleStyleOptions](arkts-arkui-progress-comp-capsulestyleoptions-i.md): Sets the style of Capsule. <br>- [RingStyleOptions](arkts-arkui-progress-comp-ringstyleoptions-i.md): Sets the style of Ring. <br>- [LinearStyleOptions](arkts-arkui-progress-comp-linearstyleoptions-i.md): Sets the style of Linear. <br>- [ScaleRingStyleOptions](arkts-arkui-progress-comp-scaleringstyleoptions-i.md): Sets the style of ScaleRing. <br>- [EclipseStyleOptions](arkts-arkui-progress-comp-eclipsestyleoptions-i.md): Sets the style of Eclipse. <br>- [ProgressStyleOptions](arkts-arkui-progress-comp-progressstyleoptions-i.md): Can only set strokeWidth, scaleCount, and scaleWidth of each type of progress bar, and takes effect only for progress bars that support these style settings. |

## value

```TypeScript
value(value: number)
```

Sets the current progress value. When a value less than 0 is set, it is set to 0; when a value greater than total is set, it is set to total. When an invalid value is set, it is handled as the default value. When the status attribute of the Ring style is set to ProgressStatus.LOADING, setting the progress value does not take effect.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ProgressAttribute-value(value: number): ProgressAttribute<Type>--><!--Device-ProgressAttribute-value(value: number): ProgressAttribute<Type>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Current progress value.<br>Default value: 0 <br>Value range: [0, total]. When the value is set to less than 0, it is set to 0. When the value is set to greater than total, it is set to total. When an invalid value is set, it is handled as the default value. <br>**Note:** When the status of a Ring type progress bar is set to ProgressStatus.LOADING, the set progress value does not take effect. |
