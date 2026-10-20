# SubTabBarStyle

```TypeScript
declare class SubTabBarStyle
```

Implements the subtab style. A transition animation is played when the user switches between tabs.

**Since:** 9

<!--Device-unnamed-declare class SubTabBarStyle--><!--Device-unnamed-declare class SubTabBarStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## board

```TypeScript
board(value: BoardStyle): SubTabBarStyle
```

Sets the background style (board style) of the selected subtab. It takes effect only in the horizontal layout.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SubTabBarStyle-board(value: BoardStyle): SubTabBarStyle--><!--Device-SubTabBarStyle-board(value: BoardStyle): SubTabBarStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [BoardStyle](arkts-arkui-tabcontent-comp-boardstyle-i.md) | Yes | Backing board style object of the selected subtab, which is used to set the corner radius and other styles of the backing board. |

**Return value:**

| Type | Description |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-tabcontent-comp-subtabbarstyle-c.md) | The **SubTabBarStyle** object itself, which is used for chain calling. |

## constructor

```TypeScript
constructor(content: ResourceStr)
```

Constructor used to create a **SubTabBarStyle** instance.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SubTabBarStyle-constructor(content: ResourceStr)--><!--Device-SubTabBarStyle-constructor(content: ResourceStr)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Text for the tab. |

## constructor

```TypeScript
constructor(content: ResourceStr | ComponentContent)
```

Constructor used to create a **SubTabBarStyle** instance. You can set custom content with **ComponentContent**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SubTabBarStyle-constructor(content: ResourceStr | ComponentContent)--><!--Device-SubTabBarStyle-constructor(content: ResourceStr | ComponentContent)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; ComponentContent | Yes | Content on the tab. <br>**NOTE:** <br>1. Custom content does not support the **labelStyle** attribute. <br>2. If the custom content exceeds the content box of the tab page, the excess part is not displayed. <br>3. If the custom content is within the content box of the tab page, it is aligned in the center. <br>4. If the custom content is abnormal or no display component is available, a blank area is displayed. |

## id

```TypeScript
id(value: string): SubTabBarStyle
```

Sets the subtab ID. It can be used to find or control a specified tab through **TabsController**, and identify different tabs in status management and event processing.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SubTabBarStyle-id(value: string): SubTabBarStyle--><!--Device-SubTabBarStyle-id(value: string): SubTabBarStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | ID of a subtab, which is used to identify and distinguish different tabs. This parameter can be set when you need to display, hide, or perform other operations on a specified tab using code. The ID must be unique in the same **Tabs** component. |

**Return value:**

| Type | Description |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-tabcontent-comp-subtabbarstyle-c.md) | The **SubTabBarStyle** object itself, which is used for chain calling. |

## indicator

```TypeScript
indicator(value: IndicatorStyle): SubTabBarStyle
```

Sets the indicator style of the selected subtab. It takes effect only in the horizontal layout.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SubTabBarStyle-indicator(value: IndicatorStyle): SubTabBarStyle--><!--Device-SubTabBarStyle-indicator(value: IndicatorStyle): SubTabBarStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [IndicatorStyle](arkts-arkui-tabcontent-comp-indicatorstyle-i.md) | Yes | Underline style object of the selected subtab, which is used to set the color, height, width, and corner radius of the underline. |

**Return value:**

| Type | Description |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-tabcontent-comp-subtabbarstyle-c.md) | Returns the **SubTabBarStyle** object itself for chain calls. |

## indicator

```TypeScript
indicator(value: IndicatorStyle | DrawableTabBarIndicator): SubTabBarStyle
```

Sets the indicator style of the selected subtab. Compared with [indicator](#indicator), the image format is added. For details about the display effect of the image, see [ImageFit.Cover](../arkts-apis/arkts-arkui-imagefit-e.md). It takes effect only in the horizontal layout.

> **NOTE:** 
> 
> - **IndicatorStyle**: a solid line. By default, the animation transition effect is displayed when a tab is switched.
> 
> - **DrawableTabBarIndicator**: an image. By default, the animation transition effect is not displayed when a tab is switched.If an invalid image source is passed, the common indicator style is displayed.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-SubTabBarStyle-indicator(value: IndicatorStyle | DrawableTabBarIndicator): SubTabBarStyle--><!--Device-SubTabBarStyle-indicator(value: IndicatorStyle | DrawableTabBarIndicator): SubTabBarStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [IndicatorStyle](arkts-arkui-tabcontent-comp-indicatorstyle-i.md) &#124; [DrawableTabBarIndicator](arkts-arkui-tabcontent-comp-drawabletabbarindicator-i.md) | Yes | Indicator style object for the selected subtab. **IndicatorStyle**: common indicator style.<br>**DrawableTabBarIndicator**: image indicator style. |

**Return value:**

| Type | Description |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-tabcontent-comp-subtabbarstyle-c.md) | The **SubTabBarStyle** object itself, which is used for chain calling. |

## labelStyle

```TypeScript
labelStyle(value: LabelStyle): SubTabBarStyle
```

Sets the style of the label text and font for the subtab. The label text and font style of the subtab are valid only in horizontal mode.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SubTabBarStyle-labelStyle(value: LabelStyle): SubTabBarStyle--><!--Device-SubTabBarStyle-labelStyle(value: LabelStyle): SubTabBarStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [LabelStyle](arkts-arkui-tabcontent-comp-labelstyle-i.md) | Yes | Label text and font style object of a subtab, which is used to set the text color, size, font, and number of lines. |

**Return value:**

| Type | Description |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-tabcontent-comp-subtabbarstyle-c.md) | The **SubTabBarStyle** object itself, which is used for chain call. |

## of

```TypeScript
static of(content: ResourceStr): SubTabBarStyle
```

Static constructor used to create a **SubTabBarStyle** instance.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SubTabBarStyle-static of(content: ResourceStr): SubTabBarStyle--><!--Device-SubTabBarStyle-static of(content: ResourceStr): SubTabBarStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Text for the tab. |

**Return value:**

| Type | Description |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-tabcontent-comp-subtabbarstyle-c.md) | Returns the created **SubTabBarStyle** object, which is used to set the child tab style. |

## of

```TypeScript
static of(content: ResourceStr | ComponentContent): SubTabBarStyle
```

Static constructor used to create a **SubTabBarStyle** instance. You can set custom content with **ComponentContent**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SubTabBarStyle-static of(content: ResourceStr | ComponentContent): SubTabBarStyle--><!--Device-SubTabBarStyle-static of(content: ResourceStr | ComponentContent): SubTabBarStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; ComponentContent | Yes | Content on the tab. You can set custom content with **ComponentContent**. <br>**NOTE:** <br>1. Custom content does not support the **labelStyle** attribute. <br>2. If the custom content exceeds the content box of the tab page, the excess part is not displayed. <br>3. If the custom content is within the content box of the tab page, it is aligned in the center. <br>4. If the custom content is abnormal or no display component is available, a blank area is displayed. |

**Return value:**

| Type | Description |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-tabcontent-comp-subtabbarstyle-c.md) | Returns the created **SubTabBarStyle** object, which is used to set the style of the selected subtab. |

## padding

```TypeScript
padding(value: Padding | Dimension): SubTabBarStyle
```

Sets the padding of the subtab. It cannot be set in percentage. When the parameter is of the Dimension type, the value applies to all sides.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SubTabBarStyle-padding(value: Padding | Dimension): SubTabBarStyle--><!--Device-SubTabBarStyle-padding(value: Padding | Dimension): SubTabBarStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Padding &#124; [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | Yes | Padding attributes of a subtab (percentage setting is not supported), which are used to adjust the distance between the tab content and the boundary. <br>Value range: [0, +∞] <br>If the value is abnormal, the default value is used. <br>Default value: **{left:8.0vp,right:8.0vp,top:17.0vp,bottom:18.0vp}** <br>**NOTE:** <br>Since API version 12, the [padding<sup>12+</sup>](#padding) method is added to support the [LocalizedPadding](../arkts-apis/arkts-arkui-localizedpadding-i.md) type and the mirroring capability. |

**Return value:**

| Type | Description |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-tabcontent-comp-subtabbarstyle-c.md) | The **SubTabBarStyle** object itself, which is used for chain call. |

## padding

```TypeScript
padding(padding: LocalizedPadding): SubTabBarStyle
```

Sets the padding of the subtab. This API supports mirroring but does not support percentage-based settings.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SubTabBarStyle-padding(padding: LocalizedPadding): SubTabBarStyle--><!--Device-SubTabBarStyle-padding(padding: LocalizedPadding): SubTabBarStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| padding | [LocalizedPadding](../arkts-apis/arkts-arkui-localizedpadding-i.md) | Yes | Inner margin of the subtab, which is used to adjust the distance between the tab content and the boundary. The value cannot be set to a percentage. This property supports the mirroring capability. <br>Value range: [0, +∞] <br>If the value is abnormal, the default value is used. <br>Default value: **{start:LengthMetrics.vp(8),end:LengthMetrics.vp(8)** <br>**top:LengthMetrics.vp(17),bottom:LengthMetrics.vp(18)}** |

**Return value:**

| Type | Description |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-tabcontent-comp-subtabbarstyle-c.md) | The **SubTabBarStyle** object itself, which is used for chain calling. |

## selectedMode

```TypeScript
selectedMode(value: SelectedMode): SubTabBarStyle
```

Sets the display mode of the selected subtab. It takes effect only in the horizontal layout.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SubTabBarStyle-selectedMode(value: SelectedMode): SubTabBarStyle--><!--Device-SubTabBarStyle-selectedMode(value: SelectedMode): SubTabBarStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SelectedMode](arkts-arkui-tabcontent-comp-selectedmode-e.md) | Yes | Display mode of the selected subtab, which is used to control the style of the selected subtab. The value can be **SelectedMode.INDICATOR** (underline mode, which is applicable to scenarios where the selected state needs to be clearly indicated) or **SelectedMode.BOARD** (backing board mode, which is applicable to scenarios where the selected tab needs to be highlighted). <br>Default value: **SelectedMode.INDICATOR** |

**Return value:**

| Type | Description |
| --- | --- |
| [SubTabBarStyle](arkts-arkui-tabcontent-comp-subtabbarstyle-c.md) | The **SubTabBarStyle** object itself, which is used for chain calling. |
