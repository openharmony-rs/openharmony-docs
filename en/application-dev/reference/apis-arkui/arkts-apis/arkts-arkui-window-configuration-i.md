# Configuration

```TypeScript
interface Configuration
```

Defines the parameters for creating a child window or system window.

**Since:** 9

<!--Device-window-interface Configuration--><!--Device-window-interface Configuration-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## ctx

```TypeScript
ctx?: BaseContext
```

Indicates window context.

**Type:** [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-basecontext-c.md)

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Configuration-ctx?: BaseContext--><!--Device-Configuration-ctx?: BaseContext-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## decorEnabled

```TypeScript
decorEnabled?: boolean
```

Indicates whether enable window decor, only support dialog, The default value is false.

**Type:** boolean

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Configuration-decorEnabled?: boolean--><!--Device-Configuration-decorEnabled?: boolean-End-->

**System capability:** SystemCapability.Window.SessionManager

## displayId

```TypeScript
displayId?: number
```

Screen ID of the current window. If it is not set, the screen ID of the parent window is used by default. The value is a non-negative integer and must correspond to an existing screen. In scenarios involving extended screens or heterogeneous virtual screens, a global floating window can be displayed on a specified screen by setting the screen ID. For modal windows and system windows, this parameter takes no effect, and the parent window's screen ID is used by default.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Configuration-displayId?: long--><!--Device-Configuration-displayId?: long-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## name

```TypeScript
name: string
```

Indicates window id.

**Type:** string

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Configuration-name: string--><!--Device-Configuration-name: string-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## parentId

```TypeScript
parentId?: number
```

Indicates Parent window id

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Configuration-parentId?: int--><!--Device-Configuration-parentId?: int-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## title

```TypeScript
title?: string
```

Indicates dialog window title when decor enabled.

**Type:** string

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Configuration-title?: string--><!--Device-Configuration-title?: string-End-->

**System capability:** SystemCapability.Window.SessionManager

## windowType

```TypeScript
windowType: WindowType
```

Indicates window type

**Type:** [WindowType](arkts-arkui-window-windowtype-e.md)

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Configuration-windowType: WindowType--><!--Device-Configuration-windowType: WindowType-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core
