# VirtualScreenOption (System API)

Defines virtual screen parameters.

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { screen } from '@kit.ArkUI';
```

## density

```TypeScript
density: number
```

Density of the virtual screen, in px. The value must be a floating-point number.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

## height

```TypeScript
height: number
```

Height of the virtual screen, in px. The value must be an integer.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

## name

```TypeScript
name: string
```

Name of a virtual screen.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

## supportsFocus

```TypeScript
supportsFocus?: boolean
```

Whether the virtual screen is focusable. **true** if focusable; **false** otherwise. The default value is **true**.

**Type:** boolean

**Since:** 22

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

## surfaceId

```TypeScript
surfaceId: string
```

Surface ID of the virtual screen.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

## userId

```TypeScript
userId?: number
```

User ID of the virtual screen, which is an integer. The default value is **-1**.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

## width

```TypeScript
width: number
```

Width of the virtual screen, in px. The value must be an integer.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.
