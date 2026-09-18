# SubWindowAttachOptions (System API)

Describes the parameters used to maintain the relative position between the child window and the main window.

**Since:** 24

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## currentLayoutMode

```TypeScript
currentLayoutMode?: string
```

Current layout mode of the child window, which is used to control the UI effect customized by the application. If this parameter is not passed, the default value is an empty string.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

## isIntersectedHeightLimit

```TypeScript
isIntersectedHeightLimit?: boolean
```

Whether to use the intersection of the height limits of both windows in the attachment.

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

## isIntersectedWidthLimit

```TypeScript
isIntersectedWidthLimit?: boolean
```

Whether to use the intersection of the width limits of both windows in the attachment.

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

## parentWindowSizeChangeCallback

```TypeScript
parentWindowSizeChangeCallback?: Callback<Size>
```

Callback triggered when the parent window size changes. The callback is triggered immediately after the binding, and notifications are sent when the parent window size changes. By default, this parameter is not passed, and notifications about the parent window size changes cannot be received.

**Type:** [Callback](arkts-arkui-window-callback-i.md)&lt;Size&gt;

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

## parentWindowStatusChangeCallback

```TypeScript
parentWindowStatusChangeCallback?: Callback<WindowStatusType>
```

Callback triggered when the parent window mode changes. The callback is triggered immediately after the binding, and notifications are sent when the parent window mode changes. By default, this parameter is not passed, and notifications about the parent window mode changes cannot be received.

**Type:** [Callback](arkts-arkui-window-callback-i.md)&lt;[WindowStatusType](arkts-arkui-window-windowstatustype-e.md)&gt;

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.
