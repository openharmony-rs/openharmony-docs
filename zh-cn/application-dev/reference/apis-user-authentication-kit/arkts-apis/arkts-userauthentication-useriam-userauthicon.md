# @ohos.userIAM.userAuthIcon(嵌入式用户身份认证控件)

## 导入模块

```TypeScript
import { UserAuthIcon } from '@kit.UserAuthenticationKit';
```

## 汇总

### 结构体

| 名称 | 说明 |
| --- | --- |
| [UserAuthIcon](arkts-userauthentication-useriam-userauthicon-userauthicon-s.md) | **userAuthIcon**模块是OpenHarmony用户身份认证体系（UserIAM）的UI组件模块，提供了一个开箱即用的身份认证图标组件（UserAuthIcon）。该组件用于在应用UI中展示人脸认证或指纹认证的图标，支持自定义图标颜色和尺寸，点击图标可启动系统身份认证弹窗组件。 |

## 示例

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
    title: '请进行身份认证'
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
