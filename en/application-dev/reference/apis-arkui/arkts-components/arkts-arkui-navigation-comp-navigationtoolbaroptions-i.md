# NavigationToolbarOptions

```TypeScript
declare interface NavigationToolbarOptions
```

Defines the toolbar options.

**Since:** 11

<!--Device-unnamed-declare interface NavigationToolbarOptions--><!--Device-unnamed-declare interface NavigationToolbarOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

Background blur style of the toolbar. After this parameter is set, the toolbar will apply the specified blur style. If this parameter is not set, the background blur effect is disabled.

**Type:** [BlurStyle](arkts-arkui-common-comp-blurstyle-e.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-NavigationToolbarOptions-backgroundBlurStyle?: BlurStyle--><!--Device-NavigationToolbarOptions-backgroundBlurStyle?: BlurStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyleOptions

```TypeScript
backgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

Options for the toolbar background blur style.

**NOTE:** 

This parameter is only effective when **backgroundBlurStyle** is set.

Avoid using this API in conjunction with **backgroundEffect**.

**Type:** [BackgroundBlurStyleOptions](arkts-arkui-common-comp-backgroundblurstyleoptions-i.md)

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-NavigationToolbarOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions--><!--Device-NavigationToolbarOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

Background color of the toolbar. After this parameter is set, the toolbar background is displayed in the specified color. If this parameter is not set, the default color is used.

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-NavigationToolbarOptions-backgroundColor?: ResourceColor--><!--Device-NavigationToolbarOptions-backgroundColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundEffect

```TypeScript
backgroundEffect?: BackgroundEffectOptions
```

Toolbar background properties, including blur radius, brightness, saturation, and color.

**NOTE:** 

Avoid using this API in conjunction with **backgroundBlurStyleOptions**.

**Type:** [BackgroundEffectOptions](arkts-arkui-common-comp-backgroundeffectoptions-i.md)

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-NavigationToolbarOptions-backgroundEffect?: BackgroundEffectOptions--><!--Device-NavigationToolbarOptions-backgroundEffect?: BackgroundEffectOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## barStyle

```TypeScript
barStyle?: BarStyle
```

Layout style of the toolbar.

Default value: **BarStyle.STANDARD**

**Type:** [BarStyle](arkts-arkui-navigation-comp-barstyle-e.md)

**Default:** BarStyle.STANDARD

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-NavigationToolbarOptions-barStyle?: BarStyle--><!--Device-NavigationToolbarOptions-barStyle?: BarStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## hideItemValue

```TypeScript
hideItemValue?: boolean
```

Whether to hide the toolbar text.

Default value: **false**

**true**: yes; **false**: no

Default value: **false**

**Type:** boolean

**Default:** false

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-NavigationToolbarOptions-hideItemValue?: boolean--><!--Device-NavigationToolbarOptions-hideItemValue?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## moreButtonOptions

```TypeScript
moreButtonOptions?: MoreButtonOptions
```

Options for the toolbar's more button menu.

**Type:** [MoreButtonOptions](arkts-arkui-navigation-comp-morebuttonoptions-i.md)

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-NavigationToolbarOptions-moreButtonOptions?: MoreButtonOptions--><!--Device-NavigationToolbarOptions-moreButtonOptions?: MoreButtonOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
