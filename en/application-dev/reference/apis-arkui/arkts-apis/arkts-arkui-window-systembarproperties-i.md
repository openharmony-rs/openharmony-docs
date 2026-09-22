# SystemBarProperties

```TypeScript
interface SystemBarProperties
```

Describes the properties of the status bar<!--Del--> and three-button navigation bar<!--DelEnd-->.

**Since:** 6

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

&lt;!--RP13--&gt;&lt;!--RP13End--&gt;

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

## enableStatusBarAnimation

```TypeScript
enableStatusBarAnimation?: boolean
```

Whether to enable animation for a status bar property change. **true** to enable, **false** otherwise. The default value is **false**.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

## isNavigationBarLightIcon

```TypeScript
isNavigationBarLightIcon?: boolean
```

Whether any icon on the three-button navigation bar is highlighted. **true** if highlighted, **false** otherwise. The default value is **false**.

&lt;!--RP13--&gt;&lt;!--RP13End--&gt;

**Type:** boolean

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## isStatusBarLightIcon

```TypeScript
isStatusBarLightIcon?: boolean
```

Whether any icon on the status bar is highlighted. **true** if highlighted, **false** otherwise. The default value is **false**.

**Type:** boolean

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## navigationBarColor

```TypeScript
navigationBarColor?: string
```

Background color of the three-button navigation bar. The value is a hexadecimal RGB or ARGB color code and is case insensitive, for example, **'#00FF00'** or **'#FF00FF00'**. The default value is **'#66000000'**.

&lt;!--RP13--&gt;&lt;!--RP13End--&gt;

**Type:** string

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## navigationBarContentColor

```TypeScript
navigationBarContentColor?: string
```

Color of the text on the three-button navigation bar. After this property is set, the setting of **isNavigationBarLightIcon** is invalid. The default value is **'#E5FFFFFF'**.

&lt;!--RP13--&gt;&lt;!--RP13End--&gt;

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## statusBarColor

```TypeScript
statusBarColor?: string
```

Background color of the status bar. The value is a hexadecimal RGB or ARGB color code and is case insensitive, for example, **'#00FF00'** or **'#FF00FF00'**. The default value is **'#66000000'**.

**Type:** string

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## statusBarContentColor

```TypeScript
statusBarContentColor?: string
```

Color of the text on the status bar. After this property is set, the setting of **isStatusBarLightIcon** is invalid. The default value is **'#E5FFFFFF'**.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core
