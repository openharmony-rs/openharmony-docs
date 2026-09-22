# SubTabBarStyle

```TypeScript
declare class SubTabBarStyle
```

Implements the subtab style. A transition animation is played when the user switches between tabs.

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## board

```TypeScript
board(value: BoardStyle): SubTabBarStyle
```

Sets the background style (board style) of the selected subtab. It takes effect only in the horizontal layout.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [BoardStyle](arkts-arkui-tabcontent-comp-boardstyle-i.md) | Yes | Background style object for the selected subtab. |

**Return value:**

| Type | Description |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-tabcontent-comp-subtabbarstyle-c.md) | **SubTabBarStyle** object. |

## constructor

```TypeScript
constructor(content: ResourceStr)
```

Constructor used to create a **SubTabBarStyle** instance.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Text for the tab. |

<a id="constructor-1"></a>

## constructor

```TypeScript
constructor(content: ResourceStr | ComponentContent)
```

Constructor used to create a **SubTabBarStyle** instance. You can set custom content with **ComponentContent**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; ComponentContent | Yes | Content on the tab.<br>**NOTE:** <br>1. Custom content does not support the **labelStyle** attribute.<br>2. If the custom content exceeds the content box of the tab page, the excess part is not displayed.<br>3. If the custom content is within the content box of the tab page, it is aligned in the center.<br>4. If the custom content is abnormal or no display component is available, a blank area is displayed. |

## id

```TypeScript
id(value: string): SubTabBarStyle
```

Sets the [ID](arkts-arkui-common-comp-commonmethod-c.md#id) of the subtab.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | [ID](arkts-arkui-common-comp-commonmethod-c.md#id) of the subtab. |

**Return value:**

| Type | Description |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-tabcontent-comp-subtabbarstyle-c.md) | **SubTabBarStyle** object. |

## indicator

```TypeScript
indicator(value: IndicatorStyle): SubTabBarStyle
```

Sets the indicator style of the selected subtab. It takes effect only in the horizontal layout.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [IndicatorStyle](arkts-arkui-tabcontent-comp-indicatorstyle-i.md) | Yes | Indicator style object for the selected subtab. |

**Return value:**

| Type | Description |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-tabcontent-comp-subtabbarstyle-c.md) | **SubTabBarStyle** object. |

<a id="indicator-1"></a>

## indicator

```TypeScript
indicator(value: IndicatorStyle | DrawableTabBarIndicator): SubTabBarStyle
```

Sets the indicator style of the selected subtab. Compared with [indicator](#indicator), the image format is added. For details about the display effect of the image, see [ImageFit.Cover](../arkts-apis/arkts-arkui-imagefit-e.md). It takes effect only in the horizontal layout.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [IndicatorStyle](arkts-arkui-tabcontent-comp-indicatorstyle-i.md) &#124; [DrawableTabBarIndicator](arkts-arkui-tabcontent-comp-drawabletabbarindicator-i.md) | Yes | Yes |

**Return value:**

| Type | Description |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-tabcontent-comp-subtabbarstyle-c.md) | **SubTabBarStyle** object. |

## labelStyle

```TypeScript
labelStyle(value: LabelStyle): SubTabBarStyle
```

Sets the style of the label text and font for the subtab.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [LabelStyle](arkts-arkui-tabcontent-comp-labelstyle-i.md) | Yes | Style object for the label text and font of the subtab. |

**Return value:**

| Type | Description |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-tabcontent-comp-subtabbarstyle-c.md) | **SubTabBarStyle** object. |

## of

```TypeScript
static of(content: ResourceStr): SubTabBarStyle
```

Static constructor used to create a **SubTabBarStyle** instance.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Text for the tab. |

**Return value:**

| Type | Description |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-tabcontent-comp-subtabbarstyle-c.md) | **SubTabBarStyle** object created. |

<a id="of-1"></a>

## of

```TypeScript
static of(content: ResourceStr | ComponentContent): SubTabBarStyle
```

Static constructor used to create a **SubTabBarStyle** instance. You can set custom content with **ComponentContent**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; ComponentContent | Yes | Content on the tab. You can set custom content with **ComponentContent**.<br>**NOTE:** <br>1. Custom content does not support the **labelStyle** attribute.<br>2. If the custom content exceeds the content box of the tab page, the excess part is not displayed.<br>3. If the custom content is within the content box of the tab page, it is aligned in the center.<br>4. If the custom content is abnormal or no display component is available, a blank area is displayed. |

**Return value:**

| Type | Description |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-tabcontent-comp-subtabbarstyle-c.md) | **SubTabBarStyle** object created. |

## padding

```TypeScript
padding(value: Padding | Dimension): SubTabBarStyle
```

Sets the padding of the subtab. It cannot be set in percentage. When the parameter is of the Dimension type, the value applies to all sides.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Padding &#124; [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | Yes | Padding of the subtab.<br>Value range: [0, +∞]<br>Default value: **{left:8.0vp,right:8.0vp,top:17.0vp,bottom:18.0vp}** |

**Return value:**

| Type | Description |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-tabcontent-comp-subtabbarstyle-c.md) | **SubTabBarStyle** object. |

<a id="padding-1"></a>

## padding

```TypeScript
padding(padding: LocalizedPadding): SubTabBarStyle
```

Sets the padding of the subtab. This API supports mirroring but does not support percentage-based settings.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| padding | [LocalizedPadding](../arkts-apis/arkts-arkui-localizedpadding-i.md) | Yes | Padding of the subtab.<br>Value range: [0, +∞]<br>Default value: **{start:LengthMetrics.vp(8),end:LengthMetrics.vp(8)**<br> **top:LengthMetrics.vp(17),bottom:LengthMetrics.vp(18)}** |

**Return value:**

| Type | Description |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-tabcontent-comp-subtabbarstyle-c.md) | **SubTabBarStyle** object. |

## selectedMode

```TypeScript
selectedMode(value: SelectedMode): SubTabBarStyle
```

Sets the display mode of the selected subtab. It takes effect only in the horizontal layout.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SelectedMode](arkts-arkui-tabcontent-comp-selectedmode-e.md) | Yes | Display mode of the selected subtab.<br>Default value: **SelectedMode.INDICATOR** |

**Return value:**

| Type | Description |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-tabcontent-comp-subtabbarstyle-c.md) | **SubTabBarStyle** object. |
