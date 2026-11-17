# WindowShowParams

```TypeScript
interface WindowShowParams
```

Describes the window parameters during application show.

**Since:** 26.1.0

<!--Device-window-interface WindowShowParams--><!--Device-window-interface WindowShowParams-End-->

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## raiseTop

```TypeScript
raiseTop?: boolean
```

Whether the window automatically raise to top. If true, the window will be raised to top. If false, the window will not raise to top.

**Type:** boolean

**Default:** true

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-WindowShowParams-raiseTop?: boolean--><!--Device-WindowShowParams-raiseTop?: boolean-End-->

**System capability:** SystemCapability.Window.SessionManager

## windowFocused

```TypeScript
windowFocused?: boolean
```

Whether the window automatically gains focus. If true, the window gains focus. If false, the window will not automatically gain focus.

**Type:** boolean

**Default:** true

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-WindowShowParams-windowFocused?: boolean--><!--Device-WindowShowParams-windowFocused?: boolean-End-->

**System capability:** SystemCapability.Window.SessionManager
