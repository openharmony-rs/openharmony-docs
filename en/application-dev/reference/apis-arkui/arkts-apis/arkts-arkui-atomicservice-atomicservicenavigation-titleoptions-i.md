# TitleOptions

Title bar options.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceNavigation, NavDestinationBuilder, MixMode, GradientAlpha, BackgroundTheme, TitleBarType, SideBarOptions, TitleOptions, GradientBackground } from '@kit.ArkUI';
```

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

Background color.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## barStyle

```TypeScript
barStyle?: BarStyle
```

Set title bar style.

**Type:** [BarStyle](../arkts-components/arkts-arkui-barstyle-e.md)

**Default:** BarStyle.STANDARD

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isBlurEnabled

```TypeScript
isBlurEnabled?: boolean
```

Whether to enable the blur effect.

**Type:** boolean

**Default:** true

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## titleBarType

```TypeScript
titleBarType?: TitleBarType
```

Set title bar type.

**Type:** [TitleBarType](arkts-arkui-atomicservice-atomicservicenavigation-titlebartype-e.md)

**Default:** TitleBarType.ROUND_ICON

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## titleIcon

```TypeScript
titleIcon?: Resource | SymbolGlyphModifier
```

Set title bar icon.

**Type:** [Resource](arkts-arkui-resource-t.md) &#124; [SymbolGlyphModifier](../arkts-components/arkts-arkui-symbolglyphmodifier-t.md)

**Default:** atomicservice icon

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
