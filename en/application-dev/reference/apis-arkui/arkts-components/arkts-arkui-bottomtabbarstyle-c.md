# BottomTabBarStyle

Implements the bottom and side tab style.

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(icon: ResourceStr | TabBarSymbol, text: ResourceStr)
```

A constructor used to create a **BottomTabBarStyle** instance.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| icon | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [TabBarSymbol](arkts-arkui-tabbarsymbol-c.md) | Yes | Image for the tab.<br>**Since:** 12 |
| text | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Text for the tab. |

## iconStyle

```TypeScript
iconStyle(style: TabBarIconStyle): BottomTabBarStyle
```

Sets the style of the label icon on the bottom tab.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [TabBarIconStyle](arkts-arkui-tabbariconstyle-i.md) | Yes | Style of the label icon on the bottom tab. |

**Return value:**

| Type | Description |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-bottomtabbarstyle-c.md) | **BottomTabBarStyle** object. |

## id

```TypeScript
id(value: string): BottomTabBarStyle
```

Sets the ID of the bottom tab.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | ID of the bottom tab. |

**Return value:**

| Type | Description |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-bottomtabbarstyle-c.md) | **BottomTabBarStyle** object. |

## labelStyle

```TypeScript
labelStyle(value: LabelStyle): BottomTabBarStyle
```

Sets the style of the label text and font for the bottom tab.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [LabelStyle](arkts-arkui-labelstyle-i.md) | Yes | Style of the label text and font for the bottom tab. |

**Return value:**

| Type | Description |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-bottomtabbarstyle-c.md) | **BottomTabBarStyle** object. |

## layoutMode

```TypeScript
layoutMode(value: LayoutMode): BottomTabBarStyle
```

Sets the layout mode of the images and texts on the bottom tab.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [LayoutMode](arkts-arkui-layoutmode-e.md) | Yes | Layout mode of the images and text on the bottom tab.<br>Default value: **LayoutMode.VERTICAL** |

**Return value:**

| Type | Description |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-bottomtabbarstyle-c.md) | **BottomTabBarStyle** object. |

## of

```TypeScript
static of(icon: ResourceStr | TabBarSymbol, text: ResourceStr): BottomTabBarStyle
```

Static constructor used to create a **BottomTabBarStyle** instance.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| icon | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [TabBarSymbol](arkts-arkui-tabbarsymbol-c.md) | Yes | Image for the tab.<br>**Since:** 12 |
| text | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Text for the tab. |

**Return value:**

| Type | Description |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-bottomtabbarstyle-c.md) | **BottomTabBarStyle** object created. |

## padding

```TypeScript
padding(value: Padding | Dimension | LocalizedPadding): BottomTabBarStyle
```

Sets the padding of the bottom tab. It cannot be set in percentage. When the parameter is of the Dimension type, the value applies to all sides.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Padding &#124; [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) &#124; [LocalizedPadding](../arkts-apis/arkts-arkui-localizedpadding-i.md) | Yes | Padding of the bottom tab.<br>Value range: [0, +∞]<br> Default value: **{left:4.0vp,right:4.0vp,top:0.0vp,bottom:0.0vp}**<br>If of the LocalizedPadding type, this attribute supports the mirroring capability.<br>Default value: **{start:LengthMetrics.vp(4),end:LengthMetrics.vp(4),**<br> **top:LengthMetrics.vp(0),bottom:LengthMetrics.vp(0)}**<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-bottomtabbarstyle-c.md) | **BottomTabBarStyle** object. |

## symmetricExtensible

```TypeScript
symmetricExtensible(value: boolean): BottomTabBarStyle
```

Sets whether the images and text on the bottom tab can be symmetrically extended by the minimum value of the available space on the left and right bottom tabs. This parameter is valid only between bottom tabs in fixed horizontal mode.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the images and text on the bottom tab can be symmetrically extended by the minimum value of the available space on the left and right bottom tabs.<br>Default value: **false**, indicating that the images and text on the bottom tab cannot be symmetrically extended by the minimum value of the available space on the left and right bottom tabs. |

**Return value:**

| Type | Description |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-bottomtabbarstyle-c.md) | **BottomTabBarStyle** object. |

## verticalAlign

```TypeScript
verticalAlign(value: VerticalAlign): BottomTabBarStyle
```

Sets the vertical alignment mode of the images and text on the bottom tab.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [VerticalAlign](../arkts-apis/arkts-arkui-verticalalign-e.md) | Yes | Vertical alignment mode of the images and text on the bottom tab.<br>Default value: **VerticalAlign.Center** |

**Return value:**

| Type | Description |
| --- | --- |
| [BottomTabBarStyle](arkts-arkui-bottomtabbarstyle-c.md) | **BottomTabBarStyle** object. |
