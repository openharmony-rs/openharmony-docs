# SideBarOptions

```TypeScript
export interface SideBarOptions
```

Defines sidebar options.

**Since:** 18

<!--Device-unnamed-export interface SideBarOptions--><!--Device-unnamed-export interface SideBarOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceNavigation, NavDestinationBuilder, MixMode, GradientAlpha, BackgroundTheme, TitleBarType, SideBarOptions, TitleOptions, GradientBackground } from '@kit.ArkUI';
```

## onChange

```TypeScript
onChange?: Callback<boolean>
```

Side bar status change callback.

**Type:** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt;

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SideBarOptions-onChange?: Callback<boolean>--><!--Device-SideBarOptions-onChange?: Callback<boolean>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## sideBarBackground

```TypeScript
sideBarBackground?: ResourceColor
```

Side bar Background.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SideBarOptions-sideBarBackground?: ResourceColor--><!--Device-SideBarOptions-sideBarBackground?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## sideBarIcon

```TypeScript
sideBarIcon?: Resource | SymbolGlyphModifier
```

Side bar icon.

**Type:** [Resource](arkts-arkui-resource-t.md) &#124; [SymbolGlyphModifier](../arkts-components/arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Default:** $r('sys.symbol.open_sidebar')

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SideBarOptions-sideBarIcon?: Resource | SymbolGlyphModifier--><!--Device-SideBarOptions-sideBarIcon?: Resource | SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
