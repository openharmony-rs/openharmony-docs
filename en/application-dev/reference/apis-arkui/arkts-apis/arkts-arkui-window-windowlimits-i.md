# WindowLimits

```TypeScript
interface WindowLimits
```

Describes the parameters for window size limits. Applications can obtain the current window size limits (in px) via [getWindowLimits](arkts-arkui-window-window-i.md#getwindowlimits). Starting from API version 22, they can also be obtained via [getWindowLimitsVP](arkts-arkui-window-window-i.md#getwindowlimitsvp) (in vp).

The actual window size limits applied are determined by the intersection of the default system limits, application configurations, and runtime settings, with the priority (from highest to lowest) as follows:

1. Window size limits configured by the application via [setWindowLimits](arkts-arkui-window-window-i.md#setwindowlimits).
2. Window size limits specified by the application via [StartOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-startoptions-startoptions-c.md) when the application starts the window through [startAbility](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md#startability-2). (This approach is supported since API version 17.)
3. Window size limits configured by the application in [abilities in the module.json5 file](../../../quick-start/module-configuration-file.md#abilities).
4. Default system limits (which vary depending on the product and window type).

> **NOTE:** 
> 
> For the **maxWidth**, **maxHeight**, **minWidth**, and **minHeight** properties:
> 
> - The default unit is px. Starting from API version 22, the unit can be px or vp, depending on the setting of
> **pixelUnit**.
> 
> - The value is an integer. Floating-point values will be rounded down.
> 
> - The default value is **0**, indicating that the property does not change.
> 
> - The lower bound of the effective range is the minimum height/width limited by the system.
> 
> - The upper bound of the effective range is the maximum height/width limited by the system.

**Since:** 11

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## maxHeight

```TypeScript
maxHeight?: number
```

Maximum window height.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

## maxWidth

```TypeScript
maxWidth?: number
```

Maximum window width.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

## minHeight

```TypeScript
minHeight?: number
```

Minimum window height.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

## minWidth

```TypeScript
minWidth?: number
```

Minimum window width.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

## pixelUnit

```TypeScript
pixelUnit?: PixelUnit
```

Unit of the window size limits. The default value is **px**. The value can be **px** or **vp**.

**Type:** [PixelUnit](arkts-arkui-window-pixelunit-e.md)

**Since:** 22

**System capability:** SystemCapability.Window.SessionManager
