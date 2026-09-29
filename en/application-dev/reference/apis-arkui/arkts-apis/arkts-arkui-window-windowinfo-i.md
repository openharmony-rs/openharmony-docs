# WindowInfo

```TypeScript
interface WindowInfo
```

Describes the window information.

**Since:** 18

<!--Device-window-interface WindowInfo--><!--Device-window-interface WindowInfo-End-->

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## abilityName

```TypeScript
abilityName: string
```

abilityName of window

**Type:** string

**Since:** 18

<!--Device-WindowInfo-abilityName: string--><!--Device-WindowInfo-abilityName: string-End-->

**System capability:** SystemCapability.Window.SessionManager

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the application.

**Type:** string

**Since:** 18

<!--Device-WindowInfo-bundleName: string--><!--Device-WindowInfo-bundleName: string-End-->

**System capability:** SystemCapability.Window.SessionManager

## displayId

```TypeScript
displayId?: number
```

Indicates the ID of the display where the window is located.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-WindowInfo-displayId?: int--><!--Device-WindowInfo-displayId?: int-End-->

**System capability:** SystemCapability.Window.SessionManager

## globalDisplayRect

```TypeScript
globalDisplayRect?: Rect
```

Window size in the global coordinate system. In extended screen scenarios, the top-left corner of the primary screen is used as the coordinate origin. In virtual screen scenarios, the top-left corner of the virtual screen is used as the coordinate origin. The default value is [0, 0, 0, 0].

**Type:** [Rect](arkts-arkui-window-rect-i.md)

**Since:** 20

<!--Device-WindowInfo-globalDisplayRect?: Rect--><!--Device-WindowInfo-globalDisplayRect?: Rect-End-->

**System capability:** SystemCapability.Window.SessionManager

## globalRect

```TypeScript
globalRect?: Rect
```

Indicates the actual display size and position of the window.

**Type:** [Rect](arkts-arkui-window-rect-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-WindowInfo-globalRect?: Rect--><!--Device-WindowInfo-globalRect?: Rect-End-->

**System capability:** SystemCapability.Window.SessionManager

## isFocused

```TypeScript
isFocused?: boolean
```

Whether the window gains focus. **true** if the window gains focus, **false** otherwise. The return value is the same as that of the [isFocused()](arkts-arkui-window-window-i.md#isfocused) API.

**Type:** boolean

**Since:** 18

<!--Device-WindowInfo-isFocused?: boolean--><!--Device-WindowInfo-isFocused?: boolean-End-->

**System capability:** SystemCapability.Window.SessionManager

## rect

```TypeScript
rect: Rect
```

Window size.

**Type:** [Rect](arkts-arkui-window-rect-i.md)

**Since:** 18

<!--Device-WindowInfo-rect: Rect--><!--Device-WindowInfo-rect: Rect-End-->

**System capability:** SystemCapability.Window.SessionManager

## windowId

```TypeScript
windowId: number
```

Window ID.

**Type:** number

**Since:** 18

<!--Device-WindowInfo-windowId: int--><!--Device-WindowInfo-windowId: int-End-->

**System capability:** SystemCapability.Window.SessionManager

## windowStatusType

```TypeScript
windowStatusType: WindowStatusType
```

Window mode.

**Type:** [WindowStatusType](arkts-arkui-window-windowstatustype-e.md)

**Since:** 18

<!--Device-WindowInfo-windowStatusType: WindowStatusType--><!--Device-WindowInfo-windowStatusType: WindowStatusType-End-->

**System capability:** SystemCapability.Window.SessionManager
