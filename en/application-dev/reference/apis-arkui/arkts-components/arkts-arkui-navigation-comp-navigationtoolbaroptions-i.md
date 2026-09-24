# NavigationToolbarOptions

```TypeScript
declare interface NavigationToolbarOptions
```

Defines the toolbar options.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

Background blur style of the title bar. If this parameter is not set, the background blur effect is disabled.

**Type:** [BlurStyle](arkts-arkui-common-comp-blurstyle-e.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyleOptions

```TypeScript
backgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

Options for the title bar background blur style.

**NOTE:** 

This parameter is only effective when **backgroundBlurStyle** is set.

Avoid using this API in conjunction with **backgroundEffect**.

**Type:** [BackgroundBlurStyleOptions](arkts-arkui-common-comp-backgroundblurstyleoptions-i.md)

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

Background color of the title bar. If this parameter is not set, the default color is used.

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundEffect

```TypeScript
backgroundEffect?: BackgroundEffectOptions
```

Title bar background properties, including blur radius, brightness, saturation, and color.

**NOTE:** 

Avoid using this API in conjunction with **backgroundBlurStyleOptions**.

**Type:** [BackgroundEffectOptions](arkts-arkui-common-comp-backgroundeffectoptions-i.md)

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full
