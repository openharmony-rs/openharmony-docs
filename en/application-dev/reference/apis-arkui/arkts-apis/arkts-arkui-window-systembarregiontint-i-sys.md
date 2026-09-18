# SystemBarRegionTint (System API)

Describes the callback for a single system bar.

**Since:** 8

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## backgroundColor

```TypeScript
backgroundColor?: string
```

Background color of the system bar. The value is a hexadecimal RGB or ARGB color code and is case insensitive, for example, **'#00FF00'** or **'#FF00FF00'**. The default value is **'0x66000000'**.

**Type:** string

**Since:** 8

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

## contentColor

```TypeScript
contentColor?: string
```

Color of the text on the system bar. The default value is **'0xE5FFFFFF'**.

**Type:** string

**Since:** 8

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

## isEnable

```TypeScript
isEnable?: boolean
```

Whether the system bar is displayed. **true** if displayed, **false** otherwise. The default value is **true**.

**Type:** boolean

**Since:** 8

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

## region

```TypeScript
region?: Rect
```

Current position and size of the system bar. The default value is {0,0,0,0}.

**Type:** [Rect](arkts-arkui-window-rect-i.md)

**Since:** 8

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

## type

```TypeScript
type: WindowType
```

Type of the system bar whose properties are changed. Only the status bar and navigation bar are supported.

**Type:** [WindowType](arkts-arkui-window-windowtype-e.md)

**Since:** 8

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.
