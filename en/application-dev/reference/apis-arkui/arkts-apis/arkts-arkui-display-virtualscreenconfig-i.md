# VirtualScreenConfig

```TypeScript
interface VirtualScreenConfig
```

Describes the virtual screen parameters.

**Since:** 16

<!--Device-display-interface VirtualScreenConfig--><!--Device-display-interface VirtualScreenConfig-End-->

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { display } from '@kit.ArkUI';
```

## density

```TypeScript
density: number
```

Density of the virtual screen, in px. The value is a floating-point number.

**Type:** number

**Since:** 16

<!--Device-VirtualScreenConfig-density: double--><!--Device-VirtualScreenConfig-density: double-End-->

**System capability:** SystemCapability.Window.SessionManager

## height

```TypeScript
height: number
```

Height of the virtual screen, in px. The value must be a positive integer.

**Type:** number

**Since:** 16

<!--Device-VirtualScreenConfig-height: long--><!--Device-VirtualScreenConfig-height: long-End-->

**System capability:** SystemCapability.Window.SessionManager

## name

```TypeScript
name: string
```

Name of the virtual screen, which can be customized.

**Type:** string

**Since:** 16

<!--Device-VirtualScreenConfig-name: string--><!--Device-VirtualScreenConfig-name: string-End-->

**System capability:** SystemCapability.Window.SessionManager

## supportsFocus

```TypeScript
supportsFocus?: boolean
```

Whether the virtual screen is focusable. **true** if focusable, **false** otherwise. The default value is **true**.

**Type:** boolean

**Since:** 22

<!--Device-VirtualScreenConfig-supportsFocus?: boolean--><!--Device-VirtualScreenConfig-supportsFocus?: boolean-End-->

**System capability:** SystemCapability.Window.SessionManager

## surfaceId

```TypeScript
surfaceId: string
```

Surface ID of the virtual screen, which can be customized. The maximum length for this parameter is 4096 bytes. If it goes beyond that, only the first 4096 bytes are used.

**Type:** string

**Since:** 16

<!--Device-VirtualScreenConfig-surfaceId: string--><!--Device-VirtualScreenConfig-surfaceId: string-End-->

**System capability:** SystemCapability.Window.SessionManager

## width

```TypeScript
width: number
```

Width of the virtual screen, in px. The value must be a positive integer.

**Type:** number

**Since:** 16

<!--Device-VirtualScreenConfig-width: long--><!--Device-VirtualScreenConfig-width: long-End-->

**System capability:** SystemCapability.Window.SessionManager
