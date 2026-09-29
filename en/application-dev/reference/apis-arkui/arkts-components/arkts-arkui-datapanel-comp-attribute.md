# DataPanel properties/events

```TypeScript
declare class DataPanelAttribute extends CommonMethod<DataPanelAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md), the following attributes are supported.

@extends CommonMethod [since 7 - 10] @extends CommonMethod&lt;DataPanelAttribute&gt; [since 11]

**Inheritance/Implementation:** DataPanelAttribute extends CommonMethod<DataPanelAttribute>

**Since:** 7

<!--Device-unnamed-declare class DataPanelAttribute extends CommonMethod<DataPanelAttribute>--><!--Device-unnamed-declare class DataPanelAttribute extends CommonMethod<DataPanelAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## closeEffect

```TypeScript
closeEffect(value: boolean)
```

Sets whether to disable the rotation and shadow effects for the data proportion chart. When the [trackShadow](#trackshadow) attribute is not set, this attribute controls the shadow effect. When **closeEffect** is set to **false** (shadow enabled), the default shadow effect is used. When the **trackShadow** attribute is set, the shadow effect is controlled by the value of the **trackShadow** attribute.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-DataPanelAttribute-closeEffect(value: boolean): DataPanelAttribute--><!--Device-DataPanelAttribute-closeEffect(value: boolean): DataPanelAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to disable the rotation and shadow effects for the data proportion chart.<br>Default value: **false**, which means the rotation and shadow effects are enabled. The value **true** means the rotation and shadow effects are disabled. |

## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<DataPanelConfiguration>)
```

Creates a content modifier.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DataPanelAttribute-contentModifier(modifier: ContentModifier<DataPanelConfiguration>): DataPanelAttribute--><!--Device-DataPanelAttribute-contentModifier(modifier: ContentModifier<DataPanelConfiguration>): DataPanelAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| modifier | [ContentModifier](arkts-arkui-common-comp-contentmodifier-i.md)&lt;[DataPanelConfiguration](arkts-arkui-datapanel-comp-datapanelconfiguration-i.md)&gt; | Yes | Content modifier to apply to the **DataPanel** component. After this parameter, the content you define replaces the original content displayed by **DataPanel**.<br>**modifier**: content modifier. You need to define a custom class to implement the **ContentModifier** API. |

## strokeWidth

```TypeScript
strokeWidth(value: Length)
```

Sets the stroke width of the border. This attribute does not take effect when the data panel type is **DataPanelType.Line**.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DataPanelAttribute-strokeWidth(value: Length): DataPanelAttribute--><!--Device-DataPanelAttribute-strokeWidth(value: Length): DataPanelAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Stroke width of the border.<br>Default value: **24** <br>Unit: vp <br>When string values are provided without explicit units, the default unit px will be applied. For example, '10' is equivalent to '10px'.<br>**Note:** <br>This parameter does not take effect when the data panel type is **DataPanelType.Line**. <br>If a value less than 0 is set, the default value is used. <br>If the value is greater than the ring radius, the ring thickness is automatically set to 12% of the ring radius. If the value is too large, the ring may disappear. |

## trackBackgroundColor

```TypeScript
trackBackgroundColor(value: ResourceColor)
```

Sets the background color.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DataPanelAttribute-trackBackgroundColor(value: ResourceColor): DataPanelAttribute--><!--Device-DataPanelAttribute-trackBackgroundColor(value: ResourceColor): DataPanelAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Background color.<br>Default value: **'#08182431'**, in hexadecimal ARGB format, where the first two digits indicate the transparency. |

## trackShadow

```TypeScript
trackShadow(value: DataPanelShadowOptions)
```

Sets the shadow style. If this attribute is set, the shadow effect is controlled by this attribute, and the control of **closeEffect** over the shadow effect no longer takes effect (the control of **closeEffect** over the rotation effect is not affected).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DataPanelAttribute-trackShadow(value: DataPanelShadowOptions): DataPanelAttribute--><!--Device-DataPanelAttribute-trackShadow(value: DataPanelShadowOptions): DataPanelAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [DataPanelShadowOptions](arkts-arkui-datapanel-comp-datapanelshadowoptions-i.md) | Yes | Shadow style.<br>**Note:** <br>When set to null, the shadow effect is not enabled. |

## valueColors

```TypeScript
valueColors(value: Array<ResourceColor | LinearGradient>)
```

Sets an array of data segment colors.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DataPanelAttribute-valueColors(value: Array<ResourceColor | LinearGradient>): DataPanelAttribute--><!--Device-DataPanelAttribute-valueColors(value: Array<ResourceColor | LinearGradient>): DataPanelAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Array&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) &#124; [LinearGradient](arkts-arkui-datapanel-comp-lineargradient-c.md)&gt; | Yes | Array of data segment colors. A value of the **ResourceColor** type indicates a solid color, and a value of the **LinearGradient** type indicates a color gradient. The array defaults to gradient colors. The default colors for the nine data segments are: [{ color: '#F7CE00', offset: 0 }, { color: '#F99B11', offset: 1 }], [{ color: '#F76223', offset: 0 }, { color: '#F2400A', offset: 1 }], [{ color: '#F772AC', offset: 0 }, { color: '#E65392', offset: 1 }], [{ color: '#A575EB', offset: 0 }, { color: '#A12DF7', offset: 1 }], [{ color: '#7B79F7', offset: 0 }, { color: '#4B48F7', offset: 1 }], [{ color: '#4B8AF3', offset: 0 }, { color: '#007DFF', offset: 1 }], [{ color: '#73C1E6', offset: 0 }, { color: '#4FB4E3', offset: 1 }], [{ color: '#A5D61D', offset: 0 }, { color: '#69D14F', offset: 1 }], [{ color: '#A2A2B0', offset: 0 }, { color: '#8E8E93', offset: 1 }].<br>**Note:** <br>If the number of colors set is less than the number of data segments, the remaining data segments automatically match the colors in the corresponding order in the default color list. If the number of colors set is greater than the number of data segments, the number of colors displayed is the same as the number of data segments, and the extra colors are ignored. |
