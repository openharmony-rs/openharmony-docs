# @ohos.userIAM.userAuthIcon(Embedded User Authentication Icons)

## Modules to Import

```TypeScript
import { UserAuthIcon } from '@kit.UserAuthenticationKit';
```

## Summary

### Structs

| Name | Description |
| --- | --- |
| [UserAuthIcon](arkts-userauthentication-useriam-userauthicon-userauthicon-s.md) | The **userAuthIcon** module is a UI component module of the OpenHarmony user identity and access management (UserIAM) system. It provides an out-of-the-box authentication icon component (**UserAuthIcon**). This component is used to display the face or fingerprint authentication icon in the application UI. It supports custom icon colors and sizes, and tapping the icon launches the system authentication dialog box component. |

## Examples

```TypeScript
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
