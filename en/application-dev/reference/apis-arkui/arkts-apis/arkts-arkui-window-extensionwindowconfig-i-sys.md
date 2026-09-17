# ExtensionWindowConfig (System API)

Describes the parameters for creating a window for a UI ServiceExtensionAbility.

**Since:** 14

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## subWindowOptions

```TypeScript
subWindowOptions?: SubWindowOptions
```

Parameters used for creating a child window. There is no default value. This parameter is mandatory when **windowAttribute** is set to **SUB_WINDOW**. Otherwise, the window fails to be created.

**Type:** [SubWindowOptions](arkts-arkui-window-subwindowoptions-i.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

## systemWindowOptions

```TypeScript
systemWindowOptions?: SystemWindowOptions
```

Parameters for creating a system window. There is no default value. This parameter is mandatory when **windowAttribute** is set to **SYSTEM_WINDOW**. Otherwise, the window fails to be created.

**Type:** [SystemWindowOptions](arkts-arkui-window-systemwindowoptions-i-sys.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

## windowAttribute

```TypeScript
windowAttribute: ExtensionWindowAttribute
```

Window attribute. It specifies whether the created window is a child window or a system window. When **windowAttribute** is set to **SUB_WINDOW**, **subWindowOptions** is mandatory. When **windowAttribute** is set to **SYSTEM_WINDOW**, **systemWindowOptions** is mandatory. Otherwise, the window fails to be created.

**Type:** [ExtensionWindowAttribute](arkts-arkui-window-extensionwindowattribute-e-sys.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

## windowName

```TypeScript
windowName: string
```

Window name.

**Type:** string

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

## windowRect

```TypeScript
windowRect: Rect
```

Rectangular area of the window.

**Type:** [Rect](arkts-arkui-window-rect-i.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.
