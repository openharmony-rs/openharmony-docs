# BottomTabBarStyle

```TypeScript
declare class BottomTabBarStyle
```

Implements the bottom and side tab style.

**Since:** 9

<!--Device-unnamed-declare class BottomTabBarStyle--><!--Device-unnamed-declare class BottomTabBarStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## badge

```TypeScript
badge(badgeStyle:TabBarBadgeStyle): BottomTabBarStyle
```

Sets the badge style of the bottom tab. If this parameter is not set, no badge is displayed.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-BottomTabBarStyle-badge(badgeStyle:TabBarBadgeStyle): BottomTabBarStyle--><!--Device-BottomTabBarStyle-badge(badgeStyle:TabBarBadgeStyle): BottomTabBarStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| badgeStyle | [TabBarBadgeStyle](arkts-arkui-tabcontent-comp-tabbarbadgestyle-i.md) | Yes | Badge style of the bottom tab. |

**Return value:**

| Type | Description |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-tabcontent-comp-bottomtabbarstyle-c.md) | **BottomTabBarStyle** object. |

## constructor

```TypeScript
constructor(icon: ResourceStr | TabBarSymbol, text: ResourceStr)
```

A constructor used to create a **BottomTabBarStyle** instance.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-BottomTabBarStyle-constructor(icon: ResourceStr | TabBarSymbol, text: ResourceStr)--><!--Device-BottomTabBarStyle-constructor(icon: ResourceStr | TabBarSymbol, text: ResourceStr)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| icon | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [TabBarSymbol](arkts-arkui-tabcontent-comp-tabbarsymbol-c.md) | Yes | Image for the tab. If the icon resource fails to be loaded or does not exist, a gray block is displayed. If the icon uses an SVG image source, the built-in width and height attributes of the image source must be deleted. Otherwise, the width and height attribute values built in the SVG image source are used.<br>**Since:** 12 |
| text | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Text for the tab. |

## iconStyle

```TypeScript
iconStyle(style: TabBarIconStyle): BottomTabBarStyle
```

Sets the style of the bottom tab icon.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-BottomTabBarStyle-iconStyle(style: TabBarIconStyle): BottomTabBarStyle--><!--Device-BottomTabBarStyle-iconStyle(style: TabBarIconStyle): BottomTabBarStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [TabBarIconStyle](arkts-arkui-tabcontent-comp-tabbariconstyle-i.md) | Yes | Style of the bottom tab icon, which is used to set the colors of the selected and unselected states of the settings icon. |

**Return value:**

| Type | Description |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-tabcontent-comp-bottomtabbarstyle-c.md) | The **BottomTabBarStyle** object itself, which is used for chain call. |

## id

```TypeScript
id(value: string): BottomTabBarStyle
```

Sets the ID of the bottom tab.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-BottomTabBarStyle-id(value: string): BottomTabBarStyle--><!--Device-BottomTabBarStyle-id(value: string): BottomTabBarStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | ID of the bottom tab. |

**Return value:**

| Type | Description |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-tabcontent-comp-bottomtabbarstyle-c.md) | Returns the **BottomTabBarStyle** object itself for chaining calls. |

## labelStyle

```TypeScript
labelStyle(value: LabelStyle): BottomTabBarStyle
```

Sets the style of the label text and font for the bottom tab.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-BottomTabBarStyle-labelStyle(value: LabelStyle): BottomTabBarStyle--><!--Device-BottomTabBarStyle-labelStyle(value: LabelStyle): BottomTabBarStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [LabelStyle](arkts-arkui-tabcontent-comp-labelstyle-i.md) | Yes | Label text and font style of the bottom tab, which is used to set the text color, size, font, and number of lines. |

**Return value:**

| Type | Description |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-tabcontent-comp-bottomtabbarstyle-c.md) | Returns the **BottomTabBarStyle** object itself for chaining calls. |

## layoutMode

```TypeScript
layoutMode(value: LayoutMode): BottomTabBarStyle
```

Sets the layout mode of the images and texts on the bottom tab.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-BottomTabBarStyle-layoutMode(value: LayoutMode): BottomTabBarStyle--><!--Device-BottomTabBarStyle-layoutMode(value: LayoutMode): BottomTabBarStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [LayoutMode](arkts-arkui-tabcontent-comp-layoutmode-e.md) | Yes | Layout mode of the images and text on the bottom tab.<br>Default value: **LayoutMode.VERTICAL** |

**Return value:**

| Type | Description |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-tabcontent-comp-bottomtabbarstyle-c.md) | Returns the **BottomTabBarStyle** object itself for chained calls. |

## of

```TypeScript
static of(icon: ResourceStr | TabBarSymbol, text: ResourceStr): BottomTabBarStyle
```

Static constructor used to create a **BottomTabBarStyle** instance.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-BottomTabBarStyle-static of(icon: ResourceStr | TabBarSymbol, text: ResourceStr): BottomTabBarStyle--><!--Device-BottomTabBarStyle-static of(icon: ResourceStr | TabBarSymbol, text: ResourceStr): BottomTabBarStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| icon | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [TabBarSymbol](arkts-arkui-tabcontent-comp-tabbarsymbol-c.md) | Yes | Image for the tab. When the icon resource fails to be loaded or does not exist, a gray block is displayed. If the icon uses an SVG image source, the built-in width and height attributes of the image source must be deleted. Otherwise, the width and height attribute values built in the SVG image source are used.<br>**Since:** 12 |
| text | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Text for the tab. |

**Return value:**

| Type | Description |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-tabcontent-comp-bottomtabbarstyle-c.md) | Returns the created **BottomTabBarStyle** object, which is used to set the bottom tab and side tab in approved sample mode. |

## padding

```TypeScript
padding(value: Padding | Dimension | LocalizedPadding): BottomTabBarStyle
```

Sets the padding of the bottom tab. It cannot be set in percentage. When the parameter is of the Dimension type, the value applies to all sides.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-BottomTabBarStyle-padding(value: Padding | Dimension | LocalizedPadding): BottomTabBarStyle--><!--Device-BottomTabBarStyle-padding(value: Padding | Dimension | LocalizedPadding): BottomTabBarStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Padding &#124; [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) &#124; [LocalizedPadding](../arkts-apis/arkts-arkui-localizedpadding-i.md) | Yes | Padding of the bottom tab, which is used to set the distance between the tab content and the boundary. (The percentage setting is not supported.) When you need to adjust the interior space distribution of the tab and optimize the visual effect, pass a custom value.<br>Value range: [0, +∞] <br>Default value: **{left:4.0vp,right:4.0vp,top:0.0vp,bottom:0.0vp}** <br>If of the LocalizedPadding type, this attribute supports the mirroring capability. <br>Default value: **{start:LengthMetrics.vp(4),end:LengthMetrics.vp(4),** <br>**top:LengthMetrics.vp(0),bottom:LengthMetrics.vp(0)}**<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-tabcontent-comp-bottomtabbarstyle-c.md) | The **BottomTabBarStyle** object itself is returned for chain call. |

## symmetricExtensible

```TypeScript
symmetricExtensible(value: boolean): BottomTabBarStyle
```

Sets whether the images and text on the bottom tab can be symmetrically extended by the minimum value of the available space on the left and right bottom tabs. This parameter is valid only between bottom tabs in fixed horizontal mode.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-BottomTabBarStyle-symmetricExtensible(value: boolean): BottomTabBarStyle--><!--Device-BottomTabBarStyle-symmetricExtensible(value: boolean): BottomTabBarStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the images and text on the bottom tab can be symmetrically extended by the minimum value of the available space on the left and right bottom tabs. If **true** is passed, the symmetric borrowing function is enabled (when you need to optimize the tab layout and fully utilize the space). If **false** is passed, the symmetric borrowing function is disabled (when you need to keep the fixed tab layout and avoid positional changes of tab content).<br>The default value is **false**. |

**Return value:**

| Type | Description |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-tabcontent-comp-bottomtabbarstyle-c.md) | Returns the **BottomTabBarStyle** object itself for chaining calls. |

## verticalAlign

```TypeScript
verticalAlign(value: VerticalAlign): BottomTabBarStyle
```

Sets the vertical alignment mode of the images and text on the bottom tab.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-BottomTabBarStyle-verticalAlign(value: VerticalAlign): BottomTabBarStyle--><!--Device-BottomTabBarStyle-verticalAlign(value: VerticalAlign): BottomTabBarStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [VerticalAlign](../arkts-apis/arkts-arkui-verticalalign-e.md) | Yes | Vertical alignment mode of the images and text on the bottom tab.<br>Default value: **VerticalAlign.Center** |

**Return value:**

| Type | Description |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-tabcontent-comp-bottomtabbarstyle-c.md) | Returns the **BottomTabBarStyle** object itself for chained calls. |
