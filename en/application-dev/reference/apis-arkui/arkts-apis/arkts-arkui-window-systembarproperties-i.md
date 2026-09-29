# SystemBarProperties

```TypeScript
interface SystemBarProperties
```

Describes the properties of the status bar<!--Del--> and three-button navigation bar<!--DelEnd-->.

**Since:** 6

<!--Device-window-interface SystemBarProperties--><!--Device-window-interface SystemBarProperties-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## enableNavigationBarAnimation

```TypeScript
enableNavigationBarAnimation?: boolean
```

Whether to enable animation for a three-button navigation bar property change. **true** to enable, **false** otherwise. The default value is **false**.

<!--RP13--><!--RP13End-->

**Type:** boolean

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-SystemBarProperties-enableNavigationBarAnimation?: boolean--><!--Device-SystemBarProperties-enableNavigationBarAnimation?: boolean-End-->

**System capability:** SystemCapability.Window.SessionManager

## enableStatusBarAnimation

```TypeScript
enableStatusBarAnimation?: boolean
```

Whether to enable animation for a status bar property change. **true** to enable, **false** otherwise. The default value is **false**.

**Type:** boolean

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-SystemBarProperties-enableStatusBarAnimation?: boolean--><!--Device-SystemBarProperties-enableStatusBarAnimation?: boolean-End-->

**System capability:** SystemCapability.Window.SessionManager

## isNavigationBarLightIcon

```TypeScript
isNavigationBarLightIcon?: boolean
```

Whether any icon on the three-button navigation bar is highlighted. **true** if highlighted, **false** otherwise. The default value is **false**.

<!--RP13--><!--RP13End-->

**Type:** boolean

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-SystemBarProperties-isNavigationBarLightIcon?: boolean--><!--Device-SystemBarProperties-isNavigationBarLightIcon?: boolean-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## isStatusBarLightIcon

```TypeScript
isStatusBarLightIcon?: boolean
```

Whether any icon on the status bar is highlighted. **true** if highlighted, **false** otherwise. The default value is **false**.

**Type:** boolean

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-SystemBarProperties-isStatusBarLightIcon?: boolean--><!--Device-SystemBarProperties-isStatusBarLightIcon?: boolean-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## navigationBarColor

```TypeScript
navigationBarColor?: string
```

Background color of the three-button navigation bar. The value is a hexadecimal RGB or ARGB color code and is case insensitive, for example, **'#00FF00'** or **'#FF00FF00'**. The default value is **'#66000000'**.

<!--RP13--><!--RP13End-->

**Type:** string

**Since:** 6

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-SystemBarProperties-navigationBarColor?: string--><!--Device-SystemBarProperties-navigationBarColor?: string-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## navigationBarContentColor

```TypeScript
navigationBarContentColor?: string
```

Color of the text on the three-button navigation bar. After this property is set, the setting of **isNavigationBarLightIcon** is invalid. The default value is **'#E5FFFFFF'**.

<!--RP13--><!--RP13End-->

**Type:** string

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-SystemBarProperties-navigationBarContentColor?: string--><!--Device-SystemBarProperties-navigationBarContentColor?: string-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## statusBarColor

```TypeScript
statusBarColor?: string
```

Background color of the status bar. The value is a hexadecimal RGB or ARGB color code and is case insensitive, for example, **'#00FF00'** or **'#FF00FF00'**. The default value is **'#66000000'**.

**Type:** string

**Since:** 6

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-SystemBarProperties-statusBarColor?: string--><!--Device-SystemBarProperties-statusBarColor?: string-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## statusBarContentColor

```TypeScript
statusBarContentColor?: string
```

Color of the text on the status bar. After this property is set, the setting of **isStatusBarLightIcon** is invalid. The default value is **'#E5FFFFFF'**.

**Type:** string

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-SystemBarProperties-statusBarContentColor?: string--><!--Device-SystemBarProperties-statusBarContentColor?: string-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core
