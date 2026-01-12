# Security Component Universal Attributes

<!--Kit: ArkUI-->
<!--Subsystem: Security-->
<!--Owner: @harylee-->
<!--Designer: @linshuqing; @hehehe-li-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->

Universal attributes of security components are basic attributes applicable to all security components.

> **NOTE**
>
> This component is supported since API version 10. Updates will be marked with a superscript to indicate their earliest API version.

## iconSize

iconSize(value: Dimension): T

Sets the icon size of the security component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description                  |
|------------|------|-------|---------|
| value | [Dimension](ts-types.md#dimension10) | Yes|Icon size of the security component.<br>Default value: **16vp**.<br>Percentage strings are not supported.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## layoutDirection

layoutDirection(value: SecurityComponentLayoutDirection): T

Sets the layout direction of icons and text in the security component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description                  |
|------------|------|-------|---------|
| value | [SecurityComponentLayoutDirection](#securitycomponentlayoutdirection) |Yes| Layout direction of icons and text in the security component.<br>Default value: **SecurityComponentLayoutDirection.HORIZONTAL**.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## position

position(value: Position): T

Sets the absolute position of the security component, that is, the offset of the component's upper left corner relative to its parent container's.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description                  |
|------------|------|-------|---------|
| value | [Position](ts-types.md#position) |Yes|Offset of the security component's upper left corner relative to its parent container's.<br>Default value:<br>{<br>x: 0,<br>y: 0<br>}.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## markAnchor

markAnchor(value: Position): T

Sets the anchor of the security component for moving the component with its upper left corner as the reference point.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| value | [Position](ts-types.md#position) |Yes|Anchor of the security component for moving the component with its upper left corner as the reference point. Generally, this attribute is used together with the **position** and **offset** attributes. When used alone, it produces an effect similar to that produced by **offset**.<br>Default value:<br>{<br>x: 0,<br>y: 0<br>}.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## offset

offset(value: Position | Edges | LocalizedEdges): T

Sets the coordinate offset of the security component relative to its own layout position.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| value | [Position](ts-types.md#position) \| [Edges<sup>12+</sup>](ts-types.md#edges12) \| [LocalizedEdges<sup>12+</sup>](ts-types.md#localizededges12) |Yes|Coordinate offset of the security component relative to its own layout position. This attribute does not affect the layout in the parent container. The offset is used only during drawing.<br>Default value:<br>{<br>x: 0,<br>y: 0<br>}.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## fontSize

fontSize(value: Dimension): T

Sets the font size of the text in the security component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| value | [Dimension](ts-types.md#dimension10) |Yes|Font size of the text in the security component.<br>Default value: **16fp**.<br>Percentage strings are not supported.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## fontStyle

fontStyle(value: FontStyle): T

Sets the font style of the text in the security component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| value | [FontStyle](ts-appendix-enums.md#fontstyle) |Yes|Font style of the text in the security component.<br>Default value: **FontStyle.Normal**.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## fontWeight

fontWeight(value: number | FontWeight | string | Resource): T

Sets the font weight of the text in the security component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| value | number \| [FontWeight](ts-appendix-enums.md#fontweight) \| string \| [Resource](ts-types.md#resource)<sup>20+</sup> |Yes|Font weight of the text in the security component.<br>For the number type, the value ranges from 100 to 900, at an interval of 100. A larger value indicates a heavier font weight.<br>For the string type, only numeric strings, for example, **'400'**, and the enumerated values of **FontWeight** are supported, including **'bold'**, **'bolder'**, **'lighter'**, **'regular'**, and **'medium'**.<br>The Resource type is supported since API version 20. The Resource type supports only 'integer' and 'string' formats. For the 'integer' type, values follow the number type specifications described earlier; for the 'string' type, values follow the string type specifications mentioned previously.<br>If fontWeight is not set for a control, the font weight is set to FontWeight.Medium by default. If the value of value is invalid, the font weight is set to FontWeight.Normal.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## fontFamily

fontFamily(value: string | Resource): T

Sets the font family of the text in the security component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| value | string \| [Resource](ts-types.md#resource) |Yes|Font family of the text in the security component.<br>Default font: **'HarmonyOS Sans'**.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## fontColor

fontColor(value: ResourceColor): T

Sets the font color of the text in the security component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| value | [ResourceColor](ts-types.md#resourcecolor) |Yes|Font color of the text in the security component.<br>Default value: **$r('sys.color.font_on_primary')**.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## iconColor

iconColor(value: ResourceColor): T

Sets the icon color of the security component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| value | [ResourceColor](ts-types.md#resourcecolor) |Yes|Icon color of the security component.<br>Default value: **$r('sys.color.icon_on_primary')**.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## backgroundColor

backgroundColor(value: ResourceColor): T

Sets the background color of the security component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| value | [ResourceColor](ts-types.md#resourcecolor) |Yes|Background color of the security component. If the alpha value of the upper 8 bits of the background color of the security component is less than 0x1a (for example, 0x1800ff00), the system will forcibly adjust this alpha value to 0xff.<br>Default value: **$r('sys.color.icon_emphasize')**.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## borderStyle

borderStyle(value: BorderStyle): T

Sets the border style of the security component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| value | [BorderStyle](ts-appendix-enums.md#borderstyle) |Yes|Border style of the security component.<br>By default, the border style is not set.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## borderWidth

borderWidth(value: Dimension): T

Sets the border width of the security component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| value | [Dimension](ts-types.md#dimension10) |Yes|Border width of the security component.<br>By default, the border width is not set.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## borderColor

borderColor(value: ResourceColor): T

Sets the border color of the security component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| value | [ResourceColor](ts-types.md#resourcecolor) |Yes|Border color of the security component.<br>By default, the border color is not set.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## borderRadius

borderRadius(value: Dimension): T

Sets the radius of the rounded border corners of the security component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| value |  [Dimension](ts-types.md#dimension10) |Yes|Radius of the rounded border corners of the security component.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## borderRadius<sup>15+</sup>

borderRadius(radius: Dimension | BorderRadiuses): T

Sets the radius of the border corners for the security component. You can set the radius for each of the four corners individually.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| radius |  [Dimension](ts-types.md#dimension10) \| [BorderRadiuses](ts-types.md#borderradiuses9) |Yes|Radius of the rounded border corners of the security component.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## padding

padding(value: Padding | Dimension): T

Sets the padding of the security component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| value | [Padding](ts-types.md#padding) \| [Dimension](ts-types.md#dimension10) |Yes|Padding of the security component.<br>Default value: 8 vp for the top and bottom paddings and 16 vp for the left and right paddings.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## align<sup>15+</sup>

align(alignType: Alignment): T

Sets the alignment of the icon and text in the security component.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| alignType | [Alignment](ts-appendix-enums.md#alignment) |Yes|Alignment mode of the icon text in the security component. The icon text is aligned as a whole within the background of the control. The UX display is affected by [padding](ts-securitycomponent-attributes.md#padding). The alignment mode is specified based on the effective padding.<br>Default value: **Alignment.Center**.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## textIconSpace

textIconSpace(value: Dimension): T

Sets the space between the icon and text in the security component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| value | [Dimension](ts-types.md#dimension10) |Yes|Space between the icon and text in the security component. Percentage strings are not supported. Since API version 14, if a negative value is assigned, the default value is used instead.<br>Default value: **4vp**.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## width<sup>11+</sup>

width(value: Length): T

Sets the width of the security component. By default, the security component automatically adapts its width to the content.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
|value | [Length](ts-types.md#length) |Yes|Width of the security component. By default, the security component automatically adapts its width to the content.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## height<sup>11+</sup>

height(value: Length): T

Sets the height of the security component. By default, the security component automatically adapts its height to the content.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| value | [Length](ts-types.md#length) |Yes|Height of the security component. By default, the security component automatically adapts its height to the content.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## size<sup>11+</sup>

size(value: SizeOptions): T

Sets the size of the security component. By default, the security component automatically adapts its size to the content.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| value | [SizeOptions](ts-types.md#sizeoptions) |Yes|Width and height of the element. By default, the width and height are automatically adapted based on the element content.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## constraintSize<sup>11+</sup>

constraintSize(value: ConstraintSizeOptions): T

Sets the size constraints of the component during component layout.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| value | [ConstraintSizeOptions](ts-types.md#constraintsizeoptions) |Yes|Size constraints of the component during component layout. **constraintSize** takes precedence over **width** and **height**. For details about the value, see [Impact of constraintSize on width/height](ts-universal-attributes-size.md#constraintsize).<br>Default value:<br>{<br>minWidth: 0,<br>maxWidth: Infinity,<br>minHeight: 0,<br>maxHeight: Infinity<br>}.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## alignRules<sup>15+</sup>

alignRules(alignRule: AlignRuleOption): T

Sets the alignment rules in the relative container. This API is valid only when the container is [RelativeContainer](ts-container-relativecontainer.md).

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                       | Mandatory| Description                    |
| ------ | ------------------------------------------- | ---- | ------------------------ |
| alignRule | [AlignRuleOption](ts-universal-attributes-location.md#alignruleoption9) | Yes  | Alignment rule in the relative container.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## alignRules<sup>15+</sup>

alignRules(alignRule: LocalizedAlignRuleOptions): T

Sets the alignment rules in the relative container. This API is valid only when the container is [RelativeContainer](ts-container-relativecontainer.md). This API takes the right-to-left scripts into account, using **start** and **end** instead of **left** and **right** in [alignRules](#alignrules15) for alignment in the horizontal direction. Prioritize this API in aligning child components in the relative container.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                       | Mandatory| Description                    |
| ------ | ------------------------------------------- | ---- | ------------------------ |
| alignRule | [LocalizedAlignRuleOptions](ts-universal-attributes-location.md#localizedalignruleoptions12) | Yes  | Alignment rule in the relative container.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## id<sup>15+</sup>

id(description: string): T

Unique ID you assigned for the component.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type     | Mandatory| Description                      |
| ------ | -------- | -----|---------------------- |
| description | string   |  Yes | Unique ID you assigned for the component.<br>Default value: **''**.<br>|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## chainMode<sup>15+</sup>

chainMode(direction: Axis, style: ChainStyle): T

Sets the parameters of the chain in which the component is the head. This parameter has effect only when the parent container is [RelativeContainer](ts-container-relativecontainer.md).

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                       | Mandatory| Description                    |
| ------ | ------------------------------------------- | ---- | ------------------------ |
| direction | [Axis](ts-appendix-enums.md#axis) | Yes  | Direction of the chain.|
| style | [ChainStyle](ts-universal-attributes-location.md#chainstyle12) | Yes  | Style of the chain.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## minFontScale<sup>18+</sup>

minFontScale(scale: number | Resource): T

Sets the minimum font scale factor for text.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                         | Mandatory| Description                                         |
| ------ | --------------------------------------------- | ---- | --------------------------------------------- |
| scale  | number \| [Resource](ts-types.md#resource) | Yes  | Minimum font scale factor for text.<br>Value range: [0, 1].<br>**NOTE**<br>If the value is less than 0, it will be handled as 0, meaning no limit on scaling down. If the value is greater than 1, it will be handled as 1, meaning the scaling down will not take effect. Values outside the range are considered invalid and will not take effect by default.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## maxFontScale<sup>18+</sup>

maxFontScale(scale: number | Resource): T

Sets the maximum font scale factor for text.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                         | Mandatory| Description                                         |
| ------ | --------------------------------------------- | ---- | --------------------------------------------- |
| scale  | number \| [Resource](ts-types.md#resource) | Yes  | Maximum font scale factor for text.<br>Value range: [1, +∞).<br>**NOTE**<br>A value less than 1 is handled as **1**. Abnormal values are ineffective by default.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## minFontSize<sup>18+</sup>

minFontSize(minSize: number | string | Resource): T

Sets the minimum font size.
- When used in conjunction with [maxFontSize](#maxfontsize18) and [maxLines](#maxlines18), or in combination with layout size constraints, this attribute enables font size adaptation. Using this attribute alone will not take effect.
- If the value of **minFontSize** is less than or equal to 0, font size adaptation does not take effect.
- When font size adaptation is enabled, the **fontSize** settings do not take effect.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description              |
| ------ | ------------------------------------------------------------ | ---- | ------------------ |
| minSize  | number \| string \| [Resource](ts-types.md#resource) | Yes  | Minimum font size.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## maxFontSize<sup>18+</sup>

maxFontSize(maxSize: number | string | Resource): T

Sets the maximum font size.
- When used in conjunction with [minFontSize](#minfontsize18) and [maxLines](#maxlines18), or in combination with layout size constraints, this attribute enables font size adaptation. Using this attribute alone will not take effect.
- When font size adaptation is enabled, the **fontSize** settings do not take effect.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description              |
| ------ | ------------------------------------------------------------ | ---- | ------------------ |
| maxSize  | number \| string \| [Resource](ts-types.md#resource) | Yes  | Maximum font size.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## maxLines<sup>18+</sup>

maxLines(line: number | Resource): T

Maximum number of lines in the text. By default, the text is automatically wrapped. After this attribute is specified, the maximum number of lines of the text does not exceed the specified value.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description            |
| ------ | ------ | ---- | ---------------- |
| line  | number \| [Resource](ts-types.md#resource)<sup>20+</sup> | Yes  | Maximum number of lines in the text.<br>The value range of the input parameter of the number type is [1, +∞). The Resource type is supported since API version 20. The Resource type supports only integer. The value range is [1, +∞).<br>**NOTE**<br>If the value is less than 1, it is handled as the default value 100000.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## heightAdaptivePolicy<sup>18+</sup>

heightAdaptivePolicy(policy: TextHeightAdaptivePolicy): T

Sets the policy for text height adaptation.

The text size is automatically adjusted based on the text height adaptation policy.

The secure text control text is laid out based on the value of [maxFontSize](#maxfontsize18). If the text can be completely displayed, adaptation adjustment is not required and this API does not take effect. Otherwise, the text height is adjusted based on the specified text height adaptation policy. The specific adaptation adjustment specifications are as follows:

**TextHeightAdaptivePolicy.MAX_LINES_FIRST**: prioritizes the [maxLines](#maxlines18) attribute for adjusting the text height. If the layout size using the **maxLines** attribute exceeds the layout constraints, the security component attempts to reduce the font size within the range of [minFontSize](#minfontsize18) and [maxFontSize](#maxfontsize18) to display more text. If the text still cannot be fully displayed, the security component adaptively adjusts its height to fully display the text.

**TextHeightAdaptivePolicy.MIN_FONT_SIZE_FIRST**: prioritizes the [minFontSize](#minfontsize18) attribute for adjusting the text height. If the text can be laid out in a single line using **minFontSize**, the security component attempts to increase the font size within the range of **minFontSize** and [maxFontSize](#maxfontsize18) to use the largest possible font size. If the text cannot be laid out in a single line using **minFontSize**, the security component attempts to use the [maxLines](#maxlines18) attribute for layout. If the text still cannot be fully displayed, the security component adaptively adjusts its height to fully display the text.

**TextHeightAdaptivePolicy.LAYOUT_CONSTRAINT_FIRST**: prioritizes layout constraints for adjusting the text height. If the layout size exceeds the constraints, the security component attempts to reduce the font size within the range of [minFontSize](#minfontsize18) and [maxFontSize](#maxfontsize18). If the layout size still exceeds the constraints after the font size is reduced to **minFontSize**, the security component truncates the excess lines. If the [maxLines](#maxlines18) attribute is set, the number of lines does not exceed the **maxLines** value (horizontal truncation may occur). If **maxLines** is not set, there is no limit on the number of lines.

If the security component text is not completely displayed, the click is not authorized.

For details, see [Example](#example-3).

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| policy  | [TextHeightAdaptivePolicy](ts-appendix-enums.md#textheightadaptivepolicy10) | Yes  | Policy for text height adaptation.<br>Default value: **TextHeightAdaptivePolicy.MAX_LINES_FIRST**.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|

## enabled<sup>18+</sup>

enabled(respond: boolean): T

Sets whether the security component is interactive.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                                        |
| ------ | ------- | ---- | ------------------------------------------------------------ |
| respond  | boolean | Yes  | Whether the security component is interactive.<br>**true**: The component is interactive and responds to operations such as clicks.<br>**false**: The component is non-interactive and does not respond to operations such as clicks.<br>Default value: **true**.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Attributes of the security component.|



## SecurityComponentLayoutDirection

Enumerates the layout directions of icons and texts in a security component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value| Description|
| -------- | -------- | -------- |
| HORIZONTAL | 0 | The icons and text in the security component are horizontally arranged.|
| VERTICAL | 1 | The icons and text on the security component are vertically arranged.|

## ButtonType

Enumerates the button types.

The button type affects how the settings for the [borderRadius](ts-securitycomponent-attributes.md#borderradius) attribute are applied. The specific impact is as follows:

- For a button of the **Capsule** type, the **borderRadius** settings do not take effect, and the button's corner radius is always half of the button's height or width, whichever is smaller.
- When the button type is Circle, the setting of borderRadius does not take effect.
  - If both the width and height are set, the rounded corner radius of the button is half of the smaller value between the width and height.
  - If only one of the width and height is set, the rounded corner radius of the button is half of the set width or height.
  - If the width and height are not set or the value of borderRadius is a negative number, the rounded corner radius of the button is determined based on the specific layout.
- When the button type is Normal, the rounded corner radius of the button can be set by borderRadius. The rounded corner size is limited by the component size. The minimum value is 0, and the maximum value is half of the smaller value between the width and height.
- If the button type is ROUNDED_RECTANGLE and **borderRadius** is not specified, the corner radius of a rounded rectangle button remains at the default value, 20 vp, regardless of the button's height.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Value| Description              |
| ------- | -------- | ------------------ |
| Normal  | 0 | Normal button, with no rounded corners by default.     |
| Capsule | 1 | Capsule button (the default radius is half of the height).|
| Circle  | 2 | Circular button.             |
| ROUNDED_RECTANGLE<sup>16+</sup> | 8 | Rounded rectangle button, with a default corner radius of 20 vp.|

## Example

> **NOTE**
> You may want to learn the [restrictions on security component styles](../../../security/AccessToken/security-component-overview.md#constraints) to avoid authorization failures caused by incompliant styles.

### Example 1

This example shows how to create a **SaveButton** component and set its security component attributes.

```ts
@Entry
@Component
struct Index {
  build() {
    Row() {
      Column({ space: 5 }) {
        // Create a SaveButton component and set its security component attributes.
        SaveButton()
          .fontSize(35)
          .fontColor(Color.White)
          .iconSize(30)
          .layoutDirection(SecurityComponentLayoutDirection.HORIZONTAL)
          .borderWidth(1)
          .borderStyle(BorderStyle.Dashed)
          .borderColor(Color.Blue)
          .borderRadius(20)
          .fontWeight(100)
          .iconColor(Color.White)
          .padding({
            left: 50,
            top: 50,
            bottom: 50,
            right: 50
          })
          .textIconSpace(20)
          .backgroundColor(0x3282f6)
        SaveButton().size({ width: 200, height: 100 })
        SaveButton()
          .size({ width: 200, height: 100 })
          .align(Alignment.Start)
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD, buttonType: ButtonType.Normal })
          .size({ width: 150, height: 80 })
          .borderRadius({
            topLeft: 20,
            topRight: 25,
            bottomRight: 30,
            bottomLeft: 35
          })
        SaveButton().constraintSize({ maxWidth: 60 })
      }.width('100%')
    }.height('100%')
  }
}
```

![en-us_image_0000001643038221](figures/en-us_image_0000001643038221.png)

### Example 2

This example demonstrates how to implement a layout using containers and components as anchors.

```ts
@Entry
@Component
struct Index {
  build() {
    Row() {
      RelativeContainer() {
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD, buttonType: ButtonType.Normal })
          .width(100)
          .height(100)
          .backgroundColor('#A3CF62')
          .alignRules({
            top: { anchor: '__container__', align: VerticalAlign.Top },
            left: { anchor: '__container__', align: HorizontalAlign.Start }
          })
          .id('row1')

        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD, buttonType: ButtonType.Normal })
          .width(100)
          .height(100)
          .backgroundColor('#00AE9D')
          .alignRules({
            top: { anchor: '__container__', align: VerticalAlign.Top },
            right: { anchor: '__container__', align: HorizontalAlign.End }
          })
          .id('row2')

        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD, buttonType: ButtonType.Normal })
          .height(100)
          .backgroundColor('#0A59F7')
          .alignRules({
            top: { anchor: 'row1', align: VerticalAlign.Bottom },
            left: { anchor: 'row1', align: HorizontalAlign.End },
            right: { anchor: 'row2', align: HorizontalAlign.Start }
          })
          .id('row3')

        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD, buttonType: ButtonType.Normal })
          .backgroundColor('#2CA9E0')
          .alignRules({
            top: { anchor: 'row3', align: VerticalAlign.Bottom },
            bottom: { anchor: '__container__', align: VerticalAlign.Bottom },
            left: { anchor: '__container__', align: HorizontalAlign.Start },
            right: { anchor: 'row1', align: HorizontalAlign.End }
          })
          .id('row4')

        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD, buttonType: ButtonType.Normal })
          .backgroundColor('#30C9F7')
          .alignRules({
            top: { anchor: 'row3', align: VerticalAlign.Bottom },
            bottom: { anchor: '__container__', align: VerticalAlign.Bottom },
            left: { anchor: 'row2', align: HorizontalAlign.Start },
            right: { anchor: '__container__', align: HorizontalAlign.End }
          })
          .id('row5')
      }
      .width(300).height(300)
      .margin({ left: 50 })
      .border({ width: 2, color: '#6699FF' })
    }
    .height('100%')
  }
}
```

![SaveBotton_alignRules_1.png](figures/SaveBotton_alignRules_1.png)

### Example 3

```ts
@Entry
@Component
struct Index {
  build() {
    Column() {
      Scroll() {
        Column({ space: 10 }) {
          Column({ space: 10 }) {
            Row() {
              Text('FontSize = 20, Legend: ').fontSize(20)
              Text('Quickly save images').fontSize(20).fontColor(Color.Blue)
            }.width('100%')

            Row() {
              Text('FontSize = 10, Legend: ').fontSize(20)
              Text('Quickly save images').fontSize(10).fontColor(Color.Blue)
            }.width('100%')
          }.width('100%')

          Flex({ wrap: FlexWrap.Wrap }) {
            Column() {
              Row() {
                Text('heightAdaptivePolicy = MIN_FONT_SIZE_FIRST').fontSize(16).fontWeight(FontWeight.Bold)
              }
            }.height(40)

            Column() {
              Column({ space: 10 }) {
                Row() {
                  Text('No need to adjust the text size.')
                }.width('90%')

                // The text can be completely displayed in the current layout without adjustment.
                SaveButton({
                  text: SaveDescription.QUICK_SAVE_TO_GALLERY, buttonType: ButtonType.Normal
                })
                  .maxFontSize(20)
                  .minFontSize(10)
                  .maxLines(6)
                  .heightAdaptivePolicy(TextHeightAdaptivePolicy.MIN_FONT_SIZE_FIRST)
                  .width(120)
                  .height(20)
                  .padding(0)
                  .borderRadius(10)
              }
            }.width('50%').height(90).backgroundColor(0x10000000)

            Column() {
              Column({ space: 10 }) {
                Row() {
                  Text('Decrease the font size first.')
                }.width('90%')

                //The text cannot be completely displayed in the current layout. Decrease the font size first. If the text can be displayed in one line after the font size is decreased, the font size is decreased.
                SaveButton({
                  text: SaveDescription.QUICK_SAVE_TO_GALLERY, buttonType: ButtonType.Normal
                })
                  .maxFontSize(20)
                  .minFontSize(10)
                  .maxLines(6)
                  .heightAdaptivePolicy(TextHeightAdaptivePolicy.MIN_FONT_SIZE_FIRST)
                  .width(60)
                  .height(20)
                  .padding(0)
                  .borderRadius(10)
              }
            }.width('50%').height(90).backgroundColor(0x30000000)

            Column() {
              Column({ space: 10 }) {
                Row() {
                  Text('Decrease the font size first, and then wrap the text.')
                }.width('90%')

                //The text cannot be completely displayed in the current layout. Decrease the font size first. If the text still cannot be completely displayed after the font size is decreased, use the maxLines attribute to wrap the text.
                //If the height is insufficient for the text to be completely displayed, the height is automatically adjusted to ensure that the text can be completely displayed.
                SaveButton({
                  text: SaveDescription.QUICK_SAVE_TO_GALLERY, buttonType: ButtonType.Normal
                })
                  .maxFontSize(20)
                  .minFontSize(10)
                  .maxLines(6)
                  .heightAdaptivePolicy(TextHeightAdaptivePolicy.MIN_FONT_SIZE_FIRST)
                  .width(20)
                  .height(20)
                  .padding(0)
                  .borderRadius(10)
              }
            }.width('50%').height(90).backgroundColor(0x30000000)

            Column() {
              Column({ space: 10 }) {
                Row() {
                  Text('Decrease the font size and wrap lines. The text is truncated.')
                }.width('90%')

                //If the current layout cannot display the text completely, the fontSize is decreased first. If the text still cannot be displayed completely after the fontSize is decreased, the maxLines attribute is used to wrap lines.
                //The maxLines attribute is set to 3, and only three lines can be displayed. Therefore, the text is truncated.
                //If the height is insufficient to display the text completely, the height is automatically adjusted to display the text completely.
                SaveButton({
                  text: SaveDescription.QUICK_SAVE_TO_GALLERY, buttonType: ButtonType.Normal
                })
                  .maxFontSize(20)
                  .minFontSize(10)
                  .maxLines(3)
                  .heightAdaptivePolicy(TextHeightAdaptivePolicy.MIN_FONT_SIZE_FIRST)
                  .width(10)
                  .height(20)
                  .padding(0)
                  .borderRadius(10)
              }
            }.width('50%').height(90).backgroundColor(0x10000000)
          }.width('100%')

          Flex({ wrap: FlexWrap.Wrap }) {
            Column() {
              Row() {
                Text('heightAdaptivePolicy = MAX_LINES_FIRST').fontSize(16).fontWeight(FontWeight.Bold)
              }
            }.height(40)

            Column() {
              Column({ space: 10 }) {
                Row() {
                  Text('No need to adjust the text automatically')
                }.width('90%')

                // The text can be completely displayed in the current layout without adjustment.
                SaveButton({
                  text: SaveDescription.QUICK_SAVE_TO_GALLERY, buttonType: ButtonType.Normal
                })
                  .maxFontSize(20)
                  .minFontSize(10)
                  .maxLines(6)
                  .heightAdaptivePolicy(TextHeightAdaptivePolicy.MAX_LINES_FIRST)
                  .width(120)
                  .height(20)
                  .padding(0)
                  .borderRadius(10)
              }
            }.width('50%').height(90).backgroundColor(0x10000000)

            Column() {
              Column({ space: 10 }) {
                Row() {
                  Text('Wrap first')
                }.width('90%')

                //The text cannot be completely displayed in the current layout. The maxlines attribute is used to wrap the text. After the text is wrapped, it can be completely displayed.
                //The height is automatically adjusted to ensure that the text can be completely displayed.
                SaveButton({
                  text: SaveDescription.QUICK_SAVE_TO_GALLERY, buttonType: ButtonType.Normal
                })
                  .maxFontSize(20)
                  .minFontSize(10)
                  .maxLines(6)
                  .heightAdaptivePolicy(TextHeightAdaptivePolicy.MAX_LINES_FIRST)
                  .width(60)
                  .height(20)
                  .padding(0)
                  .borderRadius(10)
              }
            }.width('50%').height(90).backgroundColor(0x30000000)

            Column() {
              Column({ space: 10 }) {
                Row() {
                  Text('Wrap first, then reduce the font size')
                }.width('90%')

                //The text cannot be completely displayed in the current layout. The maxlines attribute is used to wrap the text. After the text is wrapped, it still cannot be completely displayed. The fontSize is reduced to try to display the text. After the font size is reduced, the text can be completely displayed.
                //The height is automatically adjusted to ensure that the text can be completely displayed.
                SaveButton({
                  text: SaveDescription.QUICK_SAVE_TO_GALLERY, buttonType: ButtonType.Normal
                })
                  .maxFontSize(20)
                  .minFontSize(10)
                  .maxLines(3)
                  .heightAdaptivePolicy(TextHeightAdaptivePolicy.MAX_LINES_FIRST)
                  .width(20)
                  .height(20)
                  .padding(0)
                  .borderRadius(10)
              }
            }.width('50%').height(90).backgroundColor(0x30000000)

            Column() {
              Column({ space: 10 }) {
                Row() {
                  Text('Line break + font size reduction, text truncation')
                }.width('90%')

                //The current layout cannot completely display the text. The maxlines attribute is used to break lines. If the text still cannot be completely displayed after line break, the fontSize attribute is used to reduce the font size.
                //The minFontSize attribute is set to 10. Only one word can be displayed in each line. As a result, the text is truncated.
                //If the height is insufficient to display the text completely, the height is automatically adjusted to display the text completely.
                SaveButton({
                  text: SaveDescription.QUICK_SAVE_TO_GALLERY, buttonType: ButtonType.Normal
                })
                  .maxFontSize(20)
                  .minFontSize(10)
                  .maxLines(3)
                  .heightAdaptivePolicy(TextHeightAdaptivePolicy.MAX_LINES_FIRST)
                  .width(10)
                  .height(20)
                  .padding(0)
                  .borderRadius(10)
              }
            }.width('50%').height(90).backgroundColor(0x10000000)
          }.width('100%')

          Flex({ wrap: FlexWrap.Wrap }) {

            Column() {
              Row() {
                Text('heightAdaptivePolicy = LAYOUT_CONSTRAINT_FIRST').fontSize(16).fontWeight(FontWeight.Bold)
              }
            }.height(40)

            Column() {
              Column({ space: 10 }) {
                Row() {
                  Text('No need to adjust the layout')
                }.width('90%')

                //The text can be completely displayed without adjusting the layout. The text does not need to be adjusted adaptively.
                SaveButton({
                  text: SaveDescription.QUICK_SAVE_TO_GALLERY, buttonType: ButtonType.Normal
                })
                  .maxFontSize(20)
                  .minFontSize(10)
                  .maxLines(6)
                  .heightAdaptivePolicy(TextHeightAdaptivePolicy.LAYOUT_CONSTRAINT_FIRST)
                  .width(120)
                  .height(20)
                  .padding(0)
                  .borderRadius(10)
              }
            }.width('50%').height(90).backgroundColor(0x10000000)

            Column() {
              Column({ space: 10 }) {
                Row() {
                  Text('Do not change the layout constraint. Reduce the font size first.')
                }.width('90%')

                //The text cannot be completely displayed in the current layout. The fontSize is reduced first. After the fontSize is reduced, the text can be displayed in one line.
                SaveButton({
                  text: SaveDescription.QUICK_SAVE_TO_GALLERY, buttonType: ButtonType.Normal
                })
                  .maxFontSize(20)
                  .minFontSize(10)
                  .maxLines(6)
                  .heightAdaptivePolicy(TextHeightAdaptivePolicy.LAYOUT_CONSTRAINT_FIRST)
                  .width(60)
                  .height(20)
                  .padding(0)
                  .borderRadius(10)
              }
            }.width('50%').height(90).backgroundColor(0x30000000)

            Column() {
              Column({ space: 10 }) {
                Row() {
                  Text('Do not change the layout constraint. Reduce the font size and then wrap the text.')
                }.width('90%')

                //The text cannot be completely displayed in the current layout. The fontSize is reduced first. After the fontSize is reduced, the text cannot be completely displayed. Use the maxlines attribute to wrap the text. After the layout, the text can be completely displayed.
                //In LAYOUT_CONSTRAINT_FIRST mode, the height of the secure control cannot be adjusted adaptively.
                SaveButton({
                  text: SaveDescription.QUICK_SAVE_TO_GALLERY, buttonType: ButtonType.Normal
                })
                  .maxFontSize(20)
                  .minFontSize(10)
                  .maxLines(6)
                  .heightAdaptivePolicy(TextHeightAdaptivePolicy.LAYOUT_CONSTRAINT_FIRST)
                  .width(20)
                  .height(40)
                  .padding(0)
                  .borderRadius(10)
              }
            }.width('50%').height(90).backgroundColor(0x30000000)

            Column() {
              Column({ space: 10 }) {
                Row() {
                  Text(`Maxlines is insufficient.\nThe text is truncated.`)
                }.width('90%')

                //The current layout cannot display the text completely. The fontSize is reduced first. After the reduction, the text cannot be displayed completely. However, the height can display only one line. Therefore, the text is truncated.
                //In LAYOUT_CONSTRAINT_FIRST mode, the height of the secure control cannot be automatically adjusted.
                SaveButton({
                  text: SaveDescription.QUICK_SAVE_TO_GALLERY, buttonType: ButtonType.Normal
                })
                  .maxFontSize(20)
                  .minFontSize(10)
                  .maxLines(2)
                  .heightAdaptivePolicy(TextHeightAdaptivePolicy.LAYOUT_CONSTRAINT_FIRST)
                  .width(20)
                  .height(40)
                  .padding(0)
                  .borderRadius(10)
              }
            }.width('25%').height(90).backgroundColor(0x10000000)

            Column() {
              Column({ space: 10 }) {
                Row() {
                  Text(`The height is insufficient.\nThe text is truncated.`)
                }.width('90%')

                //The current layout cannot display the text completely. The fontSize is reduced first. After the reduction, the text cannot be displayed completely. However, the height can display only one line. Therefore, the text is truncated.
                //In LAYOUT_CONSTRAINT_FIRST mode, the height of the secure control cannot be automatically adjusted.
                SaveButton({
                  text: SaveDescription.QUICK_SAVE_TO_GALLERY, buttonType: ButtonType.Normal
                })
                  .maxFontSize(20)
                  .minFontSize(10)
                  .maxLines(6)
                  .heightAdaptivePolicy(TextHeightAdaptivePolicy.LAYOUT_CONSTRAINT_FIRST)
                  .width(20)
                  .height(20)
                  .padding(0)
                  .borderRadius(10)
              }
            }.width('25%').height(90).backgroundColor(0x20000000)
          }.width('100%')

        }.width('100%')
      }.width('100%').margin({ top: 10, left: 10, right: 10 })
    }
  }
}
```


