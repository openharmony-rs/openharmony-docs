# WidgetParam

Represents the information presented on the user authentication page. This API is used to configure the display style and interaction mode of the authentication screen, including the title, navigation button text, and window mode. By properly setting these parameters, you can provide clear authentication guidance and good interaction experience for users.

**Since:** 10

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## Modules to Import

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## appWindow

```TypeScript
appWindow?: window.Window
```

Application window object. This API is used to display the authentication dialog box as an application modal dialog. It is applicable to scenarios where the dialog box needs to be displayed by using the window object. If this parameter is provided, **uiContext** will be ignored. If this parameter is not passed, the display of the authentication dialog box is controlled by **uiContext**.

**Type:** [window.Window](../../apis-arkui/arkts-apis/arkts-arkui-window-window-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

## windowMode

```TypeScript
windowMode?: WindowModeType
```

Window type of the authentication widget. **DIALOG_BOX** is applicable to most authentication scenarios (with good user experience), and **FULLSCREEN** is applicable to scenarios that require immersive authentication experience or scenarios where a large amount of authentication information needs to be displayed. If no value is passed, **WindowModeType.DIALOG_BOX** is used by default.

**Type:** [WindowModeType](arkts-userauthentication-userauth-windowmodetype-e-sys.md)

**Default:** WindowModeType.DIALOG_BOX

**Since:** 10

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.
