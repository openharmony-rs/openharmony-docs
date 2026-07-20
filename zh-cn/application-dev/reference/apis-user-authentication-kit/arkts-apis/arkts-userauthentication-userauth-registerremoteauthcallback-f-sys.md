# registerRemoteAuthCallback（系统接口）

## 导入模块

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

<a id="registerremoteauthcallback"></a>
## registerRemoteAuthCallback

```TypeScript
function registerRemoteAuthCallback(callback: IRemoteAuthCallback): void
```

注册远程认证回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_USER_AUTH_INTERNAL

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-userAuth-function registerRemoteAuthCallback(callback: IRemoteAuthCallback): void--><!--Device-userAuth-function registerRemoteAuthCallback(callback: IRemoteAuthCallback): void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [IRemoteAuthCallback](arkts-userauthentication-userauth-iremoteauthcallback-i-sys.md) | 是 | 用于获取远程身份验证WidgetParam并返回结果的回调 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied. Called by non-system application. |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |

**示例：**

```TypeScript
import userAuth from '@ohos.userIAM.userAuth';

let remoteAuthCallback: userAuth.IRemoteAuthCallback = {
  onGetRemoteAuthWidgetParam(challenge: Uint8Array): userAuth.WidgetParam {
    console.info('Received challenge for remote auth, length: ' + challenge.length);
    return {
      title: 'Remote Authentication',
      navigationButtonText: 'Cancel'
    } as userAuth.WidgetParam;
  },
  onRemoteAuthResult(challenge: Uint8Array, result: userAuth.UserAuthResult): void {
    console.info('Remote auth result, result: ' + result.result + ', authType: ' + result.authType);
  }
};

try {
  userAuth.registerRemoteAuthCallback(remoteAuthCallback);
  console.info('Remote auth callback registered successfully');
} catch (error) {
  console.error('Failed to register remote auth callback: ' + error.code + ', ' + error.message);
}

```

