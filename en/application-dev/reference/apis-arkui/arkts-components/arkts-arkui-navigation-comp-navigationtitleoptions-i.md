# NavigationTitleOptions

```TypeScript
declare interface NavigationTitleOptions
```

Defines the title bar options.

> **systemMaterial attribute description**
> 
> The title bar material takes effect on the background of the back button, the background of the menu button, and
> the background of the **More** dialog box of the menu. When the application-level system material switch is set to
> **disable**, the title bar material effect does not take effect regardless of the value of **systemMaterial**. For
> details about the application-level system material switch, see
> [MaterialState](../arkts-apis/arkts-arkui-uimaterial-materialstate-e.md). The effects of different values for the
> system material of the title bar are as follows:
> 
> - **undefined** (default value): When the application-level system material switch is set to **default**, the title bar has no material effect. When the application-level system material switch is set to **enable**, the default immersive material effect takes effect on the title bar.
> 
> - [Material.empty](../arkts-apis/arkts-arkui-uimaterial-material-c.md#empty): The title bar has no material effect.
> 
> - [Material](../arkts-apis/arkts-arkui-uimaterial-material-c.md): When the application-level system material switch is set to **default** or **enable**, the specified material effect takes effect.

**Since:** 11

<!--Device-unnamed-declare interface NavigationTitleOptions--><!--Device-unnamed-declare interface NavigationTitleOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

Background blur style of the title bar. After this parameter is set, the title bar will apply the specified blur style. If this parameter is not set, the background blur effect is disabled.

**Type:** [BlurStyle](arkts-arkui-common-comp-blurstyle-e.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-NavigationTitleOptions-backgroundBlurStyle?: BlurStyle--><!--Device-NavigationTitleOptions-backgroundBlurStyle?: BlurStyle-End-->

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

<!--Device-NavigationTitleOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions--><!--Device-NavigationTitleOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

Background color of the title bar. After this parameter is set, the background color of the title bar is displayed in the specified color. If this parameter is not set, the default color is used.

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-NavigationTitleOptions-backgroundColor?: ResourceColor--><!--Device-NavigationTitleOptions-backgroundColor?: ResourceColor-End-->

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

<!--Device-NavigationTitleOptions-backgroundEffect?: BackgroundEffectOptions--><!--Device-NavigationTitleOptions-backgroundEffect?: BackgroundEffectOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## barStyle

```TypeScript
barStyle?: BarStyle
```

Layout style of the title bar.

Default value: **BarStyle.STANDARD**

**Type:** [BarStyle](arkts-arkui-navigation-comp-barstyle-e.md)

**Default:** BarStyle.STANDARD

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-NavigationTitleOptions-barStyle?: BarStyle--><!--Device-NavigationTitleOptions-barStyle?: BarStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

Whether to respond when the device is in semi-folded mode.

Observe the following when using this API:

1. Make sure the **Navigation** component is in full screen.
2. When the title bar is in [Free](arkts-arkui-navigation-comp-navigationtitlemode-e.md) display mode or in [STANDARD](arkts-arkui-navigation-comp-barstyle-e.md) layout style, this API has no effect.

**true**: yes; **false**: no

Default value: **false**

**Type:** boolean

**Default:** false

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-NavigationTitleOptions-enableHoverMode?: boolean--><!--Device-NavigationTitleOptions-enableHoverMode?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## mainTitleModifier

```TypeScript
mainTitleModifier?: TextModifier
```

Main title attribute modifier.

1. Attribute settings configured by this modifier will override the system's default attribute settings.
For example, if the modifier is used to set font size attributes, such as **fontSize**, **maxFontSize**, and **minFontSize**, the settings will take precedence over the system's default settings for size-related attributes.
2. If no modifier is used or an invalid value is set, the system reverts to its default settings.
3. In [Free](arkts-arkui-navigation-comp-navigationtitlemode-e.md) mode, setting the font size will disable the effect where the main title's
size changes in response to content scrolling.

**Type:** TextModifier

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-NavigationTitleOptions-mainTitleModifier?: TextModifier--><!--Device-NavigationTitleOptions-mainTitleModifier?: TextModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## paddingEnd

```TypeScript
paddingEnd?: LengthMetrics
```

Padding at the end of the title bar.

Only supported in one of the following scenarios:

1. Using non-custom menus, that is, the [menus](arkts-arkui-navigation-comp-attribute.md#menus-1) attribute adopts the Array<NavigationMenuItem> type.
2. Using no top-right menu with a non-custom title, that is, the [title](arkts-arkui-navigation-comp-attribute.md#title) type is **ResourceStr** or **NavigationCommonTitle**.

Default value:

LengthMetrics.resource(`$r('sys.float.margin_right')`)

**Type:** LengthMetrics

**Default:** LengthMetrics.resource($r('sys.float.margin_right'))

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-NavigationTitleOptions-paddingEnd?: LengthMetrics--><!--Device-NavigationTitleOptions-paddingEnd?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## paddingStart

```TypeScript
paddingStart?: LengthMetrics
```

Padding at the start of the title bar.

Only supported in one of the following scenarios:

1. Displaying the back icon, that is, [hideBackButton](arkts-arkui-navigation-comp-attribute.md#hidebackbutton) is **false**
2. Using a non-custom title, that is, the [title](arkts-arkui-navigation-comp-attribute.md#title) type is **ResourceStr** or **NavigationCommonTitle**.

Default value:

LengthMetrics.resource(**$r('sys.float.margin_left')**)

**Type:** LengthMetrics

**Default:** LengthMetrics.resource($r('sys.float.margin_left'))

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-NavigationTitleOptions-paddingStart?: LengthMetrics--><!--Device-NavigationTitleOptions-paddingStart?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scrollEffectOptions

```TypeScript
scrollEffectOptions?: ScrollEffectOptions
```

Scroll blur effect options of the title bar. The default value is **undefined**, indicating that the scroll blur effect is disabled for the title bar.

**Type:** [ScrollEffectOptions](arkts-arkui-navigation-comp-scrolleffectoptions-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-NavigationTitleOptions-scrollEffectOptions?: ScrollEffectOptions--><!--Device-NavigationTitleOptions-scrollEffectOptions?: ScrollEffectOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## subTitleModifier

```TypeScript
subTitleModifier?: TextModifier
```

Subtitle attribute modifier.

1. Attribute settings configured by this modifier will override the system's default attribute settings.
For example, if the modifier is used to set font size attributes, such as **fontSize**, **maxFontSize**, and **minFontSize**, the settings will take precedence over the system's default settings for size-related attributes.
2. If no modifier is used or an invalid value is set, the system reverts to its default settings.

**Type:** TextModifier

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-NavigationTitleOptions-subTitleModifier?: TextModifier--><!--Device-NavigationTitleOptions-subTitleModifier?: TextModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: Material
```

System material of the title bar. The default value is **undefined**. The system material effect depends on the device computing power. For details, see [@ohos.arkui.uiMaterial (System Material)](../arkts-apis/arkts-arkui-arkui-uimaterial.md).

**Type:** [Material](arkts-arkui-navigation-comp-material-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-NavigationTitleOptions-systemMaterial?: Material--><!--Device-NavigationTitleOptions-systemMaterial?: Material-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
