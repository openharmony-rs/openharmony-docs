# PiPConfiguration

Defines the parameters for creating a PiP controller.

**Since:** 11

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { PiPWindow } from '@kit.ArkUI';
```

## componentController

```TypeScript
componentController: XComponentController
```

Original XComponent controller.

**Type:** XComponentController

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

## contentHeight

```TypeScript
contentHeight?: number
```

Height of the original content, in px. It is used to determine the aspect ratio of the PiP window. When the PiP controller is created in [typeNode mode](arkts-arkui-pipwindow-create-f.md), the default value is 1080. When the PiP controller is created [not in typeNode mode](arkts-arkui-pipwindow-create-f.md), the default value is the height of the XComponent.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

## contentWidth

```TypeScript
contentWidth?: number
```

Width of the original content, in px. It is used to determine the aspect ratio of the PiP window. When the PiP controller is created in [typeNode mode](arkts-arkui-pipwindow-create-f.md), the default value is 1920. When the PiP controller is created [not in typeNode mode](arkts-arkui-pipwindow-create-f.md), the default value is the width of the XComponent.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

## context

```TypeScript
context: BaseContext
```

Context environment.

**Type:** [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-basecontext-c.md)

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

## controlGroups

```TypeScript
controlGroups?: Array<PiPControlGroup>
```

A list of optional component groups of the PiP controller. An application can configure whether to display these optional components. If this parameter is not set for the application, the panel displays basic components (such as the play/pause component of the video playback component group). If this parameter is set for the application, a maximum of three components can be selected. If more than three controls are selected, error code 401 is reported by the API.

**Type:** Array&lt;[PiPControlGroup](arkts-arkui-pipwindow-pipcontrolgroup-t.md)&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

## cornerAdsorptionEnabled

```TypeScript
cornerAdsorptionEnabled?: boolean
```

Whether the PiP window automatically snaps to screen corners. When this feature is enabled, the screen is divided into four hot zones (top-left, top-right, bottom-left, and bottom-right). When users lift their finger while dragging the PiP window within a hot zone, the PiP window is automatically snapped to the nearest corner.

**true**: enables corner snapping.

**false**: disables corner snapping.

The default value is **true**.

This API can be properly called on phones and tablets. If it is called on other device types, it has no effect.

**Type:** boolean

**Default:** true

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Window.SessionManager

## customUIController

```TypeScript
customUIController?: NodeController
```

Custom UI controller, which is used to implement the custom UI features on the PiP page. If this parameter is left empty, the custom UI features are not used by default.

**Type:** [NodeController](arkts-arkui-nodecontroller-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

## defaultWindowSizeType

```TypeScript
defaultWindowSizeType?: number
```

Size of the PiP window that the current app starts for the first time.

**0**: no size is set. The PiP window is started based on the size before the PiP window of the previous application is closed.

**1**: small window.

**2**: large window.

If no value is passed, **0** is used.

**Type:** number

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Window.SessionManager

## handleId

```TypeScript
handleId?: number
```

ID of the subpage under the **Navigation** component. After the Full-screen Window button is touched, the specified page is restored. This parameter applies only in scenarios where the UIAbility uses Navigation to manage pages. It can be set to any subpage ID within the Navigation hierarchy. The default value is **-1**, indicating that the topmost page in the Navigation stack is restored. You are advised to use getUniqueId() to obtain the page ID. When you use page routing provided by Navigation, you are advised to use the [system routing table](../../../ui/arkts-navigation-cross-package.md#system-routing-table). Otherwise, the page ID obtained by calling getUniqueId() may be incorrect.

**Type:** number

**Default:** -1

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Window.SessionManager

## localStorage

```TypeScript
localStorage?: LocalStorage
```

A page-level UI state storage unit. In multi-instance scenarios, it can be used to track the UI state storage object of the main window instance. If no value is passed, you cannot retrieve the main window's UI storage object through the PiP window.

**Type:** LocalStorage

**Since:** 17

**Atomic service API:** This API can be used in atomic services since API version 17.

**System capability:** SystemCapability.Window.SessionManager

## navigationId

```TypeScript
navigationId?: string
```

ID of the **Navigation** component. If no value is passed, the page does not need to be cached.

1. When the UIAbility uses Navigation to manage pages,
set the ID of the **Navigation** component for the PiP controller. This ensures that the original page can be restored from the PiP window.
2. When the UIAbility uses [Router](arkts-arkui-router.md) to manage pages,
you do not need to set the ID of the **Navigation** component for the PiP controller.
3. If the UIAbility has only one page, you do not need to set the navigation ID.
The original page can be restored from the PiP window.

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

## templateType

```TypeScript
templateType?: PiPTemplateType
```

Template type, which is used to distinguish video playback, video call, video meeting, and live broadcast scenarios. If no value is passed, the video playback template is used by default.

**Type:** [PiPTemplateType](arkts-arkui-pipwindow-piptemplatetype-e.md)

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager
