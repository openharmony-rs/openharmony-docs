# @ohos.userIAM.userAuthIcon (Embedded User Authentication Icons)

<!--Kit: User Authentication Kit-->
<!--Subsystem: UserIAM-->
<!--Owner: @WALL_EYE-->
<!--Designer: @lichangting518-->
<!--Tester: @jane_lz-->
<!--Adviser: @zengyawen-->

## Overview

The **userAuthIcon** module is a UI component module of the OpenHarmony user identity and access management (UserIAM) system. It provides an out-of-the-box authentication icon component (**UserAuthIcon**). This component is used to display the face authentication or fingerprint authentication icon on the application UI. It supports custom icon colors and dimensions, and can directly launch the system authentication dialog box component when the icon is tapped.

This module applies to the following scenarios:
- Quickly integrating the face or fingerprint authentication entry into the application UI.
- Displaying biometric authentication icons in a unified style.
- Tapping the icon to trigger the system-level authentication process.


> **NOTE**
>
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Key Classes and APIs

### UserAuthIcon Component

**UserAuthIcon** is an ArkTS custom component (@Component struct) that encapsulates the logic for displaying the authentication icon and triggering authentication. You only need to pass the authentication parameters and result callback to quickly implement the authentication function.

The main attributes are as follows:
- **authParam**: authentication parameters, including the authentication mode and trust level.
- **widgetParam**: parameters of the authentication dialog box, including the title and window mode.
- **iconHeight**: icon height (aspect ratio 1:1).
- **iconColor**: icon color.
- **onAuthResult**: authentication result callback.
- **onIconClick**: icon click callback.

![Class relationship diagram](figures/uml_userauthicon.png)

## APIs Called in Pairs

The typical process of using the **userAuthIcon** module is as follows:

```ts
// The following is the pseudocode for describing the calling logic. It provides only the step description and does not provide detailed executable code.
// 1. Use the UserAuthIcon component directly on the ArkTS page.
// Configure authentication parameters.
let authParam = {
  challenge: new Uint8Array([]), // challenge is used to prevent replay attacks and must be obtained using the secure random number generator.
  authType: [userAuth.UserAuthType.FACE, userAuth.UserAuthType.FINGERPRINT],
  authTrustLevel: userAuth.AuthTrustLevel.ATL3
};

// Configure the parameters of the dialog box page.
let widgetParam = {
  title: 'Verify identity'
};

// 2. Use the component in the page layout.
UserAuthIcon({
  authParam: authParam,
  widgetParam: widgetParam,
  iconHeight: '80fp',
  iconColor: Color.Blue,
  onAuthResult: (result) => {
    // Process the authentication result.
  },
  onIconClick: () => {
    // (Optional) Process the icon tap event.
  }
})
```

## Modules to Import

```ts
import { userAuth, UserAuthIcon } from '@kit.UserAuthenticationKit';
```

## Child Components

None.

## Attributes

The universal attributes are not supported.

## UserAuthIcon

Defines the embedded user authentication icon component. It provides the face and fingerprint authentication icons of the system criterion. You can tap the icons to automatically trigger the authentication process. You only need to configure the authentication parameters and callback function to integrate the authentication entry into the application UI.

```ts
UserAuthIcon({
  authParam: userAuth.AuthParam,
  widgetParam: userAuth.WidgetParam,
  iconHeight?: Dimension,
  iconColor?: ResourceColor,
  onIconClick?: ()=>void,
  onAuthResult: (result: userAuth.UserAuthResult)=>void
})
```

**Decorator**: @Component

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**Parameters**

| Name          | Type                                                        | Mandatory| Description                                                        |
| -------------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| authParam      | [userAuth.AuthParam](js-apis-useriam-userauth.md#authparam10)        | Yes  | User authentication parameters. The parameters include the **challenge** value, authentication type (**authType**), and authentication trust level (**authTrustLevel**). The challenge value is used to prevent replay attacks. The authentication type specifies the available authentication methods (such as face, fingerprint, and PIN). The authentication trust level determines the security strength of the authentication.|
| widgetParam    | [userAuth.WidgetParam](js-apis-useriam-userauth.md#widgetparam10)    | Yes  | Parameters on the user authentication page. The parameters include the authentication screen title (**title**) and navigation button text (**navigationButtonText**), which are used to customize the content displayed in the authentication dialog box.|
| iconHeight     | [Dimension](../apis-arkui/arkui-ts/ts-types.md#dimension10) | No  | Icon height. It is used to set the height of the authentication icon. The aspect ratio is 1:1 (that is, the height is the same as the width). The default value is **64fp**, and percentage strings are not supported. You are advised to select a proper size based on the UI layout.<br>Default value: **64fp**|
| iconColor      | [ResourceColor](../apis-arkui/arkui-ts/ts-types.md#resourcecolor) | No  | Icon color. It is used to set the color of the authentication icon. Multiple formats are supported, such as color values and resource references. By default, the system accent color is used. You can customize the color based on the application theme, for example, using **Color.Blue** or **$r('app.color.primary')**.<br>Default value: **$r('sys.color.ohos_id_color_activated')**|
| onIconClick    | ()=>void                                                      | No  | Icon click callback. This callback is triggered when a user taps the authentication icon. You can use this callback to prepare for the tap or record user behavior logs. If this callback is not set, the authentication process is directly triggered after the icon is tapped.|
| onAuthResult   | (result: [userAuth.UserAuthResult](js-apis-useriam-userauth.md#userauthresult10))=>void| Yes  | Result callback. This callback is triggered after a user completes authentication. The callback parameters include the authentication result code (**result**), authentication token (**token**), and authentication type (**authType**). Your application needs to process the authentication result in this callback. For example, if the authentication is successful, your application can obtain the token for subsequent security operations. If the authentication fails, your application can prompt the user to try again.<br>Note:The application must request the **ohos.permission.ACCESS_BIOMETRIC** permission. Otherwise, it will only display the icon and cannot start the authentication component.|

## Events

Universal events are not supported.

## Example

```ts
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { userAuth, UserAuthIcon } from '@kit.UserAuthenticationKit';

@Entry
@Component
struct Index {
  rand = cryptoFramework.createRandom();
  len: number = 16;
  randData: Uint8Array = this.rand?.generateRandomSync(this.len)?.data;
  authParam: userAuth.AuthParam = {
    challenge: this.randData,
    authType: [userAuth.UserAuthType.FACE, userAuth.UserAuthType.PIN],
    authTrustLevel: userAuth.AuthTrustLevel.ATL3
  };
  widgetParam: userAuth.WidgetParam = {
    title: 'Verify identity'
  };

  build() {
    Row() {
      Column() {
        UserAuthIcon({
          authParam: this.authParam,
          widgetParam: this.widgetParam,
          iconHeight: 200,
          iconColor: Color.Blue,
          onIconClick: () => {
            console.info('The user clicked the icon.');
          },
          onAuthResult: (result: userAuth.UserAuthResult) => {
            console.info(`Get user auth result, result = ${result.result}`);
          }
        })
      }
    }
  }
}
```

Calling **onAuthResult** may throw an error code. For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

**Facial authentication icon**

![Face Icon](figures/user_auth_icon_face.png)

**Fingerprint authentication icon**

![Fingerprint icon](figures/user_auth_icon_fingerprint.png)
