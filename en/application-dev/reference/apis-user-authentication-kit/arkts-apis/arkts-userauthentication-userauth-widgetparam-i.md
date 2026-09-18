# WidgetParam

Represents the information presented on the user authentication page. This API is used to configure the display style and interaction mode of the authentication screen, including the title, navigation button text, and window mode. By properly setting these parameters, you can provide clear authentication guidance and good interaction experience for users.

**Since:** 10

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## Modules to Import

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## navigationButtonText

```TypeScript
navigationButtonText?: string
```

Description text of the navigation button, with a maximum length of 60 characters. Tapping this button triggers custom application operations, such as navigating to a custom authentication page or canceling authentication. This parameter is supported in single-fingerprint and single-face authentication scenarios. Since API version 18, it is also supported in combined face-and-fingerprint authentication. By default, the custom navigation button is not displayed.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## title

```TypeScript
title: string
```

Title of the user authentication page, which cannot be empty or exceed 500 characters in length. You are advised to set it to the authentication purpose, such as payment or application login. The title is displayed on the authentication screen to help users understand the purpose of the current authentication, improving user trust and cooperation.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## uiContext

```TypeScript
uiContext?: Context
```

Used to display an application modal dialog for authentication. Since API version 18, this parameter is supported on 2-in-1 devices. When a valid **uiContext** is passed, the authentication dialog box is displayed as an application modal dialog. After the authentication result is returned, the application must first obtain the widget release message (subscribe to [on('authTip')](arkts-userauthentication-userauth-userauthinstance-i.md#onauthtip) and wait for the callback where **authTipInfo.tipCode** is **WIDGET_RELEASED**) before displaying other windows. If this parameter is not provided or if the device is of another type, the authentication dialog box is displayed as a system modal dialog. In this case, the application can directly perform follow-up procedures after the widget is released.

**Default value:** The authentication dialog box is displayed as a system modal dialog.

**Type:** [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.UserIAM.UserAuth.Core
