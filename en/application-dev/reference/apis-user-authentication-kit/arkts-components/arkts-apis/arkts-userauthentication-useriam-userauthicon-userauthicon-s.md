# UserAuthIcon

The **userAuthIcon** module is a UI component module of the OpenHarmony user identity and access management (UserIAM) system. It provides an out-of-the-box authentication icon component (**UserAuthIcon**). This component is used to display the face or fingerprint authentication icon in the application UI. It supports custom icon colors and sizes, and tapping the icon launches the system authentication dialog box component.

This module applies to the following scenarios:

- Quickly integrating the face or fingerprint authentication entry into the application UI.  
- Displaying biometric authentication icons in a unified style.  
- Tapping the icon to trigger the system-level authentication process.

**Since:** 12

**Decorator:** @Component

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## Modules to Import

```TypeScript
import { UserAuthIcon } from '@kit.UserAuthenticationKit';
```

## onAuthResult

```TypeScript
onAuthResult: (result: userAuth.UserAuthResult) => void
```

Result callback. This callback is triggered after a user completes authentication. The callback parameters include the authentication result code (**result**), authentication token (**token**), and authentication type (**authType**). Your application needs to process the authentication result in this callback. For example, if the authentication is successful, your application can obtain the token for subsequent security operations. If the authentication fails, your application can prompt the user to try again.

Note:The application must request the **ohos.permission.ACCESS_BIOMETRIC** permission. Otherwise, it will only display the icon and cannot start the authentication component.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| result | [userAuth.UserAuthResult](arkts-userauthentication-userauth-userauthresult-i.md) | Yes | Authentication result information. |

## onIconClick

```TypeScript
onIconClick?: () => void
```

Icon click callback. This callback is triggered when a user taps the authentication icon. You can use this callback to prepare for the tap or record user behavior logs. If this callback is not set, the authentication process is directly triggered after the icon is tapped.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## authParam

```TypeScript
authParam: userAuth.AuthParam
```

User authentication parameters. The parameters include the **challenge** value, authentication type (**authType**), and authentication trust level (**authTrustLevel**). The challenge value is used to prevent replay attacks. The authentication type specifies the available authentication methods (such as face, fingerprint, and PIN). The authentication trust level determines the security strength of the authentication.

**Type:** [userAuth.AuthParam](arkts-userauthentication-userauth-authparam-i.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## iconColor

```TypeScript
iconColor?: ResourceColor
```

Icon color. Multiple formats are supported, such as color values and resource references. By default, the system accent color is used. You can customize the color based on the application theme, for example, using **Color.Blue** or **&#36;r('app.color.primary')**.

**Type:** [ResourceColor](../../apis-arkui/arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** $r('sys.color.ohos_id_color_activated')

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## iconHeight

```TypeScript
iconHeight?: Dimension
```

Icon height, with an aspect ratio of 1:1. Percentage strings are not supported. You are advised to select an appropriate size based on the UI layout.

**Type:** [Dimension](../../apis-arkui/arkts-apis/arkts-arkui-dimension-t.md)

**Default:** 64fp

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## widgetParam

```TypeScript
widgetParam: userAuth.WidgetParam
```

Parameters on the user authentication page. The parameters include the authentication screen title (**title**) and navigation button text (**navigationButtonText**), which are used to customize the content displayed in the authentication dialog box.

**Type:** [userAuth.WidgetParam](arkts-userauthentication-userauth-widgetparam-i.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core
