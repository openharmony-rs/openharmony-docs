# SecurityComponentMethod

```TypeScript
declare class SecurityComponentMethod<T>
```

The universal attributes module for security components enables unified configuration of universal attributes such as layout, size, text, icon, color, border, and interaction behaviors.

This module is mainly used in the following scenarios:  
- Set layout, size, text, icon, color, border, and interaction-related attributes for security components  
such as [PasteButton](../arkts-components/arkts-arkui-pastebutton-comp.md#paste_button) and [SaveButton](../arkts-components/arkts-arkui-savebutton-comp.md#save_button).  
- Adjust the display effect and interaction experience of security components while ensuring compliance with  
the security component specifications. For specific constraints, see [Constraints](../../../security/AccessToken/security-component-overview.md#constraints).  
- Reuse the universal attribute capabilities of security components through chained calls.

## Key Enums

- [SecurityComponentLayoutDirection](arkts-arkui-securitycomponentlayoutdirection-e.md): Enumeration of icon and text  
layout directions for the security component. Specifies horizontal or vertical layout.  
- ButtonType: Enumeration of button styles for the security component.  
Specifies capsule, circle, rounded rectangle, or normal button style.

## Key APIs

- [SecurityComponentMethod](arkts-arkui-securitycomponentmethod-c.md): A collection of universal attribute methods for  
security components. Configures layout, size, text, icon, color, border, and interaction attributes for specific security components.

## Child Components

- Not supported

Defines the method of a security component.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDefaultFocus

```TypeScript
accessibilityDefaultFocus(focus: boolean): T
```

Sets the initial focus for the screen reader on the page, specifying the component that the screen reader announces first after the page loads.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| focus | boolean | Yes | Sets the initial focus of the screen reader on the page. **true** means the component is the default first focus on the current page; **false** or any other value is invalid. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current object. |

## accessibilityDescription

```TypeScript
accessibilityDescription(description: string | Resource): T
```

Provides an accessibility description for the component. You can set detailed text descriptions to help users understand the component's functionality and the actions it will perform.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| description | string &#124; [Resource](arkts-arkui-resource-t.md) | Yes | Accessibility description for the component. Provides details about the component's operation, helping users understand what the current action does and its potential consequences. When the component is selected, if it has both text attributes and an accessibility description, the text content is announced first, followed by the accessibility description.<br>The default value is an empty string. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current object. |

## accessibilityNextFocusId

```TypeScript
accessibilityNextFocusId(nextId: string): T
```

Specifies the next focus component for the screen reader.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| nextId | string | Yes | The [unique ID](#id) of the next component to be focused. If the unique ID does not correspond to any component, the setting is invalid. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current object. |

## accessibilityRole

```TypeScript
accessibilityRole(role: SecurityComponentRoleType): T
```

Sets the accessibility component type. Each component type is announced in a specific way. You can modify the component type based on your app's requirements to control how the component is announced and what content is announced in accessibility mode.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| role | [SecurityComponentRoleType](arkts-arkui-securitycomponentroletype-e.md) | Yes | The component type, such as button or chart, that determines how the component is announced by the screen reader. The specific type can be customized. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current object. |

## align

```TypeScript
align(alignType: Alignment): T
```

Sets the alignment of the icon and text on the security component.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| alignType | [Alignment](arkts-arkui-alignment-e.md) | Yes | Alignment of the icon and text within the security component. The icon and text are aligned as a unit within the component's background area. The alignment is applied based on the **alignType** value after [padding](#padding) takes effect, which also affects the visual result. <br>Default value: Alignment.Center. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## alignRules

```TypeScript
alignRules(alignRule: AlignRuleOption): T
```

Sets the alignment rules for child components within a relative container. This API takes effect only when the parent container is [RelativeContainer](../arkts-components/arkts-arkui-relativecontainer-comp.md#relative_container).

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| alignRule | [AlignRuleOption](../arkts-components/arkts-arkui-common-comp-alignruleoption-i.md) | Yes | Alignment rule configuration object that defines anchor alignment options (**top**, **bottom**, **left**, **right**, and **center**). Specifies the alignment position and method of the security component in [RelativeContainer](../arkts-components/arkts-arkui-relativecontainer-comp.md#relative_container). |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

<a id="alignrules-1"></a>

## alignRules

```TypeScript
alignRules(alignRule: LocalizedAlignRuleOptions): T
```

Sets the alignment rules for child components within a relative container. This API takes effect only when the parent container is [RelativeContainer](../arkts-components/arkts-arkui-relativecontainer-comp.md#relative_container). In the horizontal direction, this method replaces **left** and **right** in the [alignRules](#alignrules) above with **start** and **end**, respectively, allowing the layout to be mirrored in RTL mode. You are advised to use this method preferentially.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| alignRule | [LocalizedAlignRuleOptions](../arkts-components/arkts-arkui-common-comp-localizedalignruleoptions-i.md) | Yes | Alignment rule configuration object that uses **start** and **end** in place of **left** and **right** to support RTL layout mirroring. Includes anchor alignment settings for **top**, **bottom**, **start**, **end**, and **center**, specifying the alignment position and method of the security component within [RelativeContainer](../arkts-components/arkts-arkui-relativecontainer-comp.md#relative_container). |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## backgroundColor

```TypeScript
backgroundColor(value: ResourceColor): T
```

Sets the background color of the security component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](arkts-arkui-resourcecolor-t.md) | Yes | Background color of the security component.<br>Default value: $r('sys.color.icon_emphasize'). <br>If the alpha value of the upper eight bits of the security component's background color is less than **0x1a** (for example, **0x1800ff00**), the system will forcibly adjust this alpha value to **0xff**. This ensures the security component remains sufficiently visible and prevents users from inadvertently triggering authorization due to an overly transparent component. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## borderColor

```TypeScript
borderColor(value: ResourceColor): T
```

Sets the border color of the security component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](arkts-arkui-resourcecolor-t.md) | Yes | Border color of the security component.<br>No border color is set by default. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## borderRadius

```TypeScript
borderRadius(value: Dimension): T
```

Sets the border radius of the security component.

The effect of **borderRadius** is influenced by **ButtonType**. When **ButtonType** is **Capsule** or **Circle**, the **borderRadius** setting does not take effect, and the corner radius is automatically determined by the button type. When the **ButtonType** is **Normal** or **ROUNDED_RECTANGLE**, the **borderRadius** setting takes effect. For details, see ButtonType.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Dimension](arkts-arkui-dimension-t.md) | Yes | Border radius of the security component.<br>Default value: **0vp**. <br>If no unit is explicitly specified, the unit is vp. <br>Percentage strings are not supported.<br>The border radius is constrained by the component size, with a minimum of **0** and a maximum of half the smaller of the width and height. If an invalid value is set, this attribute does not take effect. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

<a id="borderradius-1"></a>

## borderRadius

```TypeScript
borderRadius(radius: Dimension | BorderRadiuses): T
```

Sets the border radius of the security component, allowing individual setting of the four corner radii.

The effect of **borderRadius** is influenced by **ButtonType**. When **ButtonType** is **Capsule** or **Circle**, the **borderRadius** setting does not take effect, and the corner radius is automatically determined by the button type. When the **ButtonType** is **Normal** or **ROUNDED_RECTANGLE**, the **borderRadius** setting takes effect. For details, see ButtonType.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| radius | [Dimension](arkts-arkui-dimension-t.md) &#124; [BorderRadiuses](arkts-arkui-borderradiuses-t.md) | Yes | Border radius of the security component.<br>Default value: **0vp**. <br>When the unit is not explicitly specified, the unit is vp.<br>The Dimension type does not support setting percentage strings. The border radius is constrained by the component size, with a minimum value of **0** and a maximum value of half the smaller dimension of width and height. When an invalid value is set, this attribute does not take effect. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## borderStyle

```TypeScript
borderStyle(value: BorderStyle): T
```

Sets the border style of the security component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [BorderStyle](arkts-arkui-borderstyle-e.md) | Yes | Border style of the security component.<br>No border style is set by default. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## borderWidth

```TypeScript
borderWidth(value: Dimension): T
```

Sets the border width of the security component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Dimension](arkts-arkui-dimension-t.md) | Yes | Border width of the security component.<br>Default value: **0vp**. <br>When the unit is not explicitly specified, the unit is vp.<br>Percentage strings are not supported. This attribute does not take effect when it is set to an invalid value. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## chainMode

```TypeScript
chainMode(direction: Axis, style: ChainStyle): T
```

Sets the parameters of the chain in which the component is the head. This API takes effect only when the parent container is [RelativeContainer](../arkts-components/arkts-arkui-relativecontainer-comp.md#relative_container).

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| direction | [Axis](arkts-arkui-axis-e.md) | Yes | Direction of the chain layout. Specifies the arrangement direction of the chain headed by this component in the [RelativeContainer](../arkts-components/arkts-arkui-relativecontainer-comp.md#relative_container). |
| style | [ChainStyle](../arkts-components/arkts-arkui-common-comp-chainstyle-e.md) | Yes | Style of the chain layout. Controls how child components are distributed within the chain, such as evenly distributed, aligned at both ends, or compactly arranged. For specific values and effects, see [ChainStyle](../arkts-components/arkts-arkui-common-comp-chainstyle-e.md). |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## constraintSize

```TypeScript
constraintSize(value: ConstraintSizeOptions): T
```

Sets the constraint size, limiting the size range during component layout.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ConstraintSizeOptions](arkts-arkui-constraintsizeoptions-i.md) | Yes | Constraint size, limiting the size range during component layout. <br>When the unit is not explicitly specified, the unit is vp.<br>**constraintSize** takes precedence over **width** and **height**. When used in conjunction with adaptive font size attributes, if the text on the security component is truncated, clicking the component does not perform authorization. The **constraintSize** setting affects whether the text is fully displayed.<br>For the value results, see [impact of constraintSize values on width/height](#constraintsize). <br>Default value:<br>{<br>minWidth: 0,<br>maxWidth: Infinity,<br>minHeight: 0,<br>maxHeight: Infinity<br>}. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## enabled

```TypeScript
enabled(respond: boolean): T
```

Sets whether the security component is interactive.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| respond | boolean | Yes | Whether the security component is interactive.<br>Default value: **true** <br>**true**: The component is interactive and responds to operations such as clicks. <br>**false**: The component is non-interactive and does not respond to operations such as clicks. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## fallbackLineSpacing

```TypeScript
fallbackLineSpacing(enabled: boolean): T
```

Enables adaptive line height based on the actual text height for multi-line text.

The **fallbackLineSpacing** attribute is closely coupled with the **lineHeight** attribute of [RichEditorTextStyle](../arkts-components/arkts-arkui-richeditor-comp-richeditortextstyle-i.md). When the **lineHeight** value is less than the actual rendering height of the text at the current font size, the **fallbackLineSpacing** value determines whether the line height should adapt based on the actual text height.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether the line height adapts based on the actual text height.<br>**true**: The line height adapts based on the actual text height. **false**: The line height does not adapt based on the actual text height. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## focusBox

```TypeScript
focusBox(style: FocusBoxStyle): T
```

Sets the style of the system focus box for the security component.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [FocusBoxStyle](arkts-arkui-focusboxstyle-i.md) | Yes | Configuration object for the focus box style. Contains properties such as **margin** (the spacing between the focus box and the component) and **strokeColor** (the stroke color of the focus box) to customize the appearance of the system focus box. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## fontColor

```TypeScript
fontColor(value: ResourceColor): T
```

Sets the font color of the text on the security component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](arkts-arkui-resourcecolor-t.md) | Yes | Font color of the text on the security component.<br>Default value: $r('sys.color.font_on_primary'). |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## fontFamily

```TypeScript
fontFamily(value: string | Resource): T
```

Sets the font family of the text on the security component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string &#124; [Resource](arkts-arkui-resource-t.md) | Yes | Font family of the text on the security component.<br>Default font:**'HarmonyOS Sans'**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## fontSize

```TypeScript
fontSize(value: Dimension): T
```

Sets the font size of the text for the security component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Dimension](arkts-arkui-dimension-t.md) | Yes | Font size of the text on the security component.<br>When the unit is not explicitly specified, the unit is fp. <br>Default value: $r('sys.float.ohos_id_text_size_button1')<br>Percentage strings are not supported.<br>This attribute does not take effect when it is set to an invalid value.<br> Note: When the security component text is not fully displayed, clicking it does not perform authorization. The **fontSize** setting determines whether the text can be fully displayed and thereby affects the authorization behavior of the security component. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## fontStyle

```TypeScript
fontStyle(value: FontStyle): T
```

Sets the font style of the text on the security component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [FontStyle](arkts-arkui-fontstyle-e.md) | Yes | Font style of the text on the security component.<br>Default value: FontStyle.Normal. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## fontWeight

```TypeScript
fontWeight(value: number | FontWeight | string | Resource): T
```

Sets the font weight of the text on the security component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [FontWeight](arkts-arkui-fontweight-e.md) &#124; string &#124; [Resource](arkts-arkui-resource-t.md) | Yes | Font weight of the text on the security component.<br>For the number type, the value ranges from 100 to 900, at an interval of 100. A larger value indicates a heavier font weight. <br>For the string type, only numeric strings, for example, **'400'**, and the enumerated values of **FontWeight** are supported, including **'bold'**, **'bolder'**, **'lighter'**, **'regular'**, and **'medium'**. <br>The Resource type is supported since API version 20. The Resource type supports only **'integer'** and **'string'** formats. Values follow the number type specifications for the **'integer'** type and the string type specifications for the **'string'** type, both described earlier. <br>If **fontWeight** is not set for the component, the font weight is set to **FontWeight.Medium** by default. If **value** is **undefined** or **null**, a number outside the [100, 900] range, or a string that does not match the string format of **FontWeight** enums, the font weight is set to **FontWeight.Normal**.<br>**Since:** 20 |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## height

```TypeScript
height(value: Length): T
```

Sets the height of the security component. If not set, the height adapts to the element content. When used in conjunction with adaptive font size attributes, the height setting affects whether the text is fully displayed.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](arkts-arkui-length-t.md) | Yes | Height of the security component. If not set, the height adapts to the element content. <br>If no unit is explicitly specified, the unit is vp.<br>When used in conjunction with [minFontSize](#minfontsize), [maxFontSize](#maxfontsize), [maxLines](#maxlines), and [heightAdaptivePolicy](#heightadaptivepolicy) for adaptive font sizing, if the text on the security component is truncated, clicking the component does not perform authorization. If an invalid value is set, this attribute does not take effect. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## heightAdaptivePolicy

```TypeScript
heightAdaptivePolicy(policy: TextHeightAdaptivePolicy): T
```

Sets the method for text height adaptation. This is applicable to scenarios where the text display of a security component needs to be dynamically adjusted to ensure complete text visibility under different sizes or language environments.

The security component text is laid out at [maxFontSize](#maxfontsize). If the text can be completely displayed and no adaptive adjustment is needed, this API does not take effect. Otherwise, adaptation proceeds according to the specified policy, as follows: <br>**TextHeightAdaptivePolicy.MAX_LINES_FIRST**: prioritizes the [maxLines](#maxlines) attribute for adjusting the text height. If the layout size with **maxLines** exceeds the layout constraints, the security component attempts to reduce the font size within the range of [minFontSize](#minfontsize) and [maxFontSize](#maxfontsize) to fit more text. If the text still cannot be fully displayed, the security component adaptively adjusts its height to show all text. <br>**TextHeightAdaptivePolicy.MIN_FONT_SIZE_FIRST**: prioritizes the [minFontSize](#minfontsize) attribute for adjusting the text height. If the text can be laid out in a single line using **minFontSize**, the security component attempts to increase the font size within the range of **minFontSize** and [maxFontSize](#maxfontsize) to use the largest possible font size. If the text cannot be laid out in a single line using **minFontSize**, the security component attempts to use the [maxLines](#maxlines) attribute for layout. If the text still cannot be fully displayed, the security component adaptively adjusts its height to fully display the text. <br>**TextHeightAdaptivePolicy.LAYOUT_CONSTRAINT_FIRST**: prioritizes layout constraints for adjusting the text height. <br>If the layout size exceeds the constraints, the security component attempts to reduce the font size within the range of [minFontSize](#minfontsize) and [maxFontSize](#maxfontsize). If the layout size still exceeds the constraints after the font size is reduced to **minFontSize**, the security component truncates the excess lines. If the [maxLines](#maxlines) attribute is set, the number of lines does not exceed the **maxLines** value (horizontal truncation may occur). If **maxLines** is not set, there is no limit on the number of lines. If the security component text is not fully displayed, clicking does not trigger authorization. Whether the text is fully displayed depends on attributes such as **heightAdaptivePolicy**, **minFontSize**, **maxFontSize**, **maxLines**, **width**, and **height**.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| policy | [TextHeightAdaptivePolicy](arkts-arkui-textheightadaptivepolicy-e.md) | Yes | Policy for text height adaptation.<br>Default value: TextHeightAdaptivePolicy.MAX_LINES_FIRST. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## iconColor

```TypeScript
iconColor(value: ResourceColor): T
```

Sets the icon color of the security component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](arkts-arkui-resourcecolor-t.md) | Yes | Icon color of the security component.<br>Default value: $r('sys.color.icon_on_primary'). |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## iconSize

```TypeScript
iconSize(value: Dimension): T
```

Sets the icon size of the security component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Dimension](arkts-arkui-dimension-t.md) | Yes | Icon size of the security component, in vp by default when no unit is specified.<br>Default value: **16vp**. <br>Percentage strings are not supported.<br>If an invalid value or unit is passed, the attribute does not take effect, and the component is displayed according to the default value. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## id

```TypeScript
id(id: string): T
```

Unique ID you assigned for the component.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | Unique ID you assigned for the component.<br>Default value: ''. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## layoutDirection

```TypeScript
layoutDirection(value: SecurityComponentLayoutDirection): T
```

Sets the layout direction of the icon and text on the security component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SecurityComponentLayoutDirection](arkts-arkui-securitycomponentlayoutdirection-e.md) | Yes | Indicates the layout direction of the icon and text.<br>Default value:SecurityComponentLayoutDirection.HORIZONTAL. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## markAnchor

```TypeScript
markAnchor(value: Position): T
```

Sets the anchor of the security component for moving the component with its top-left corner as the reference point.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Position | Yes | Anchor of the security component for moving the component with its top-left corner as the reference point. Generally, this attribute is used in conjunction with **position()** and **offset()** for more precise positioning.<br>No default value. <br>This attribute does not take effect when it is set to an invalid value. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## maxFontScale

```TypeScript
maxFontScale(scale: number | Resource): T
```

Sets the maximum font scale factor. When this API is invoked and the system font scaling causes the text to enlarge, the font scale factor will not exceed the set maximum scale factor.

This API can be used in conjunction with [minFontScale](#minfontscale). **maxFontScale** controls the upper limit of the scale factor, and **minFontScale** controls the lower limit. They can be set independently or together to precisely control font scaling.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scale | number &#124; [Resource](arkts-arkui-resource-t.md) | Yes | Maximum font scale factor for the text.<br>The value must be greater than or equal to 1. <br> **NOTE:** <br>If the set value is less than 1, the value **1** is used. If the value is **undefined**, **null**, or another invalid value, the attribute has no effect. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## maxFontSize

```TypeScript
maxFontSize(maxSize: number | string | Resource): T
```

Sets the maximum font size for text display.

- When used in conjunction with [minFontSize](#minfontsize) and [maxLines](#maxlines), or in combination with layout size constraints, this attribute enables font size adaptation. Using this attribute alone will not take effect.  
- **maxFontSize** must be greater than **minFontSize**. If **maxFontSize** is less than **minFontSize**,  
**minFontSize** will be treated as **maxFontSize**.  
- When adaptive font size is effective, the **fontSize** setting does not take effect.  
- If the security component text is not fully displayed, clicking does not trigger authorization. The  
**maxFontSize** setting affects text visibility, which in turn affects authorization behavior.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| maxSize | number &#124; string &#124; [Resource](arkts-arkui-resource-t.md) | Yes | Maximum display font size of the text.<br>The value must be greater than 0. <br>When the unit is not explicitly specified, the unit is fp. <br>**NOTE:** <br>When the set value is less than or equal to 0, the adaptive font size does not take effect. When an invalid value is set, this attribute does not take effect. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## maxLines

```TypeScript
maxLines(line: number | Resource): T
```

Sets the maximum number of lines for text. By default, text wraps automatically. When this attribute is specified, the text will display at most the specified number of lines. It can be used independently to limit text lines, or in conjunction with [minFontSize](#minfontsize), [maxFontSize](#maxfontsize), and [heightAdaptivePolicy](#heightadaptivepolicy). When used with adaptive font size attributes, if the security component text is not fully displayed, the click will not trigger authorization. The **maxLines** setting affects whether the text can be fully displayed, thereby affecting the authorization behavior of the security component.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| line | number &#124; [Resource](arkts-arkui-resource-t.md) | Yes | Maximum number of lines for the text.<br>The number type accepts values in [1, +∞). The Resource type is supported since API version 20. The parameter of the Resource type supports only integers in the range [1, +∞). <br>**NOTE:** <br>A value less than 1 is handled as the default value **1000000**.<br>**Since:** 20 |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## minFontScale

```TypeScript
minFontScale(scale: number | Resource): T
```

Sets the minimum font scale factor for the text. When this API is invoked and the system font scaling causes the text to shrink, the font scale factor will not fall below the set minimum scale factor.

This API can be used in conjunction with [maxFontScale](#maxfontscale). **minFontScale** controls the lower limit of the scale factor and **maxFontScale** controls the upper limit. They can be set independently or together to precisely control font scaling.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scale | number &#124; [Resource](arkts-arkui-resource-t.md) | Yes | Minimum font scale factor for the text.<br>Value range: [0,1]. <br>**NOTE:** <br>If the set value is less than 0, the value **0** is used, meaning scaling down to any factor is allowed. If the set value is greater than 1, the value **1** is used, meaning font scaling is not allowed. If the value is **undefined**, **null**, or another invalid value, the attribute has no effect. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## minFontSize

```TypeScript
minFontSize(minSize: number | string | Resource): T
```

Sets the minimum font size for text display.

- When used in conjunction with [maxFontSize](#maxfontsize) and [maxLines](#maxlines), or in combination with layout size constraints, this attribute enables font size adaptation. Using this attribute alone will not take effect.  
- **minFontSize** must be smaller than **maxFontSize**. If the set value is greater than **maxFontSize**,  
**maxFontSize** is used instead.  
- When **minFontSize** is less than or equal to 0, adaptive font size does not take effect.  
- When adaptive font size is effective, the **fontSize** setting does not take effect.  
- If the security component text is not fully displayed, clicking does not trigger authorization. The  
**minFontSize** setting affects text visibility, which in turn affects authorization behavior.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| minSize | number &#124; string &#124; [Resource](arkts-arkui-resource-t.md) | Yes | Minimum display font size of the text.<br>The value must be greater than 0. <br>When the unit is not explicitly specified, the unit is fp.<br> **minFontSize** must be less than **maxFontSize**. If the set value is greater than **maxFontSize**, **maxFontSize** is used instead. If this parameter is less than or equal to 0, the adaptive font size does not take effect. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## offset

```TypeScript
offset(value: Position | Edges | LocalizedEdges): T
```

Sets the coordinate offset of the security component relative to its own layout position.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Position &#124; [Edges](arkts-arkui-edges-i.md) &#124; [LocalizedEdges](arkts-arkui-localizededges-i.md) | Yes | Coordinate offset of the security component relative to its own layout position. This attribute does not affect the layout in the parent container. The offset is used only during drawing.<br>When the unit is not explicitly specified, the unit is vp. <br>No default value. <br>This attribute does not take effect when it is set to an invalid value.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## padding

```TypeScript
padding(value: Padding | Dimension): T
```

Sets the padding of the security component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Padding &#124; [Dimension](arkts-arkui-dimension-t.md) | Yes | Padding of the security component.<br>Default value: 8 vp for the top and bottom and 16 vp for the left and right. <br>When the unit is not explicitly specified, the unit is vp. <br>Note: Percentage strings are not supported. If a percentage string is set, the corresponding padding is **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## position

```TypeScript
position(value: Position): T
```

Sets the absolute position, which is the offset of the top-left corner of the security component relative to the top-left corner of the parent container.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Position | Yes | Offset position of the security component's top-left corner relative to the parent container's top-left corner. Applicable to scenarios where the security component is placed in a fixed area of the page through absolute positioning.<br>When the unit is not explicitly specified, the unit is vp. <br>It is recommended that you pass numeric coordinates for both **x** and **y**.<br>If the parameter is **undefined** or **null**, or **x** and **y** are non-numeric types, this attribute does not take effect, and invalid coordinates are treated as **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## size

```TypeScript
size(value: SizeOptions): T
```

Sets the width and height. If not set, the width and height adapt to the element content. The **size** method is used to set both width and height at the same time. To set the width or height individually, use the [width](#width) or [height](#height) method.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SizeOptions](arkts-arkui-sizeoptions-i.md) | Yes | Width and height of the security component. When this parameter is not specified, the security component automatically adapts its size to the element content. <br>If no unit is explicitly specified, the unit is vp. <br>When used in conjunction with [minFontSize](#minfontsize), [maxFontSize](#maxfontsize), [maxLines](#maxlines), and [heightAdaptivePolicy](#heightadaptivepolicy) for adaptive font sizing, if the text on the security component is truncated, clicking the component does not perform authorization. If an invalid value is set, this attribute does not take effect. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## textIconSpace

```TypeScript
textIconSpace(value: Dimension): T
```

Sets the spacing between the icon and text in the security component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Dimension](arkts-arkui-dimension-t.md) | Yes | Spacing between the icon and text in the security component.<br>Default value: **4vp**. <br>When the unit is not explicitly specified, the unit is vp. <br>Note: Percentage strings are not supported. If a percentage string is set, the corresponding spacing between the icon and text is **0**. Since API version 14, negative values are treated as the default value. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |

## width

```TypeScript
width(value: Length): T
```

Sets the width of the security component. If not set, the width adapts to the element content. When used in conjunction with adaptive font size attributes, the width setting affects whether the text is fully displayed.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](arkts-arkui-length-t.md) | Yes | Width of the security component itself. If not set, the width adapts to the element content. <br>When the unit is not explicitly specified, the unit is vp.<br>When used in conjunction with [minFontSize](#minfontsize), [maxFontSize](#maxfontsize), [maxLines](#maxlines), and [heightAdaptivePolicy](#heightadaptivepolicy) for adaptive font sizing, if the text on the security component is truncated, clicking the component does not perform authorization. If an invalid value is set, this attribute does not take effect. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attribute of the security component. |
