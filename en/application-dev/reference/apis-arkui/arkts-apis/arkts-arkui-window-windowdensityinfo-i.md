# WindowDensityInfo

```TypeScript
interface WindowDensityInfo
```

Describes the information about the display density of the screen where the window is located and the window's custom display density. It is a scale factor independent of pixel units, that is, a factor for scaling display size.

**Since:** 15

<!--Device-window-interface WindowDensityInfo--><!--Device-window-interface WindowDensityInfo-End-->

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## customDensity

```TypeScript
customDensity: number
```

Custom display size scale factor of the window. The value ranges from 0.5 to 4.0. If this parameter is left unspecified, the system's display size scale factor is used. This parameter takes effect only for the main window. For the child window or system window, it is equivalent to the system's display size scale factor (**systemDensity**).

**Type:** number

**Since:** 15

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 15.

<!--Device-WindowDensityInfo-customDensity: double--><!--Device-WindowDensityInfo-customDensity: double-End-->

**System capability:** SystemCapability.Window.SessionManager

## defaultDensity

```TypeScript
defaultDensity: number
```

Default display size scale factor for the screen where the window is located. The value ranges from 0.5 to 4.0 and varies with the screen.

**Type:** number

**Since:** 15

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 15.

<!--Device-WindowDensityInfo-defaultDensity: double--><!--Device-WindowDensityInfo-defaultDensity: double-End-->

**System capability:** SystemCapability.Window.SessionManager

## systemDensity

```TypeScript
systemDensity: number
```

System's display size scale factor for the screen where the window is located. The value ranges from 0.5 to 4.0 and varies according to user settings.

**Type:** number

**Since:** 15

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 15.

<!--Device-WindowDensityInfo-systemDensity: double--><!--Device-WindowDensityInfo-systemDensity: double-End-->

**System capability:** SystemCapability.Window.SessionManager
