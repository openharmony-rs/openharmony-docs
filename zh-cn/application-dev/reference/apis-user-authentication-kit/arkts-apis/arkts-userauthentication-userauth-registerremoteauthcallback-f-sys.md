# registerRemoteAuthCallback（系统接口）

## 导入模块

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
import { UserAuthIcon } from '@kit.UserAuthenticationKit';
```

## registerRemoteAuthCallback

```TypeScript
function registerRemoteAuthCallback(callback: IRemoteAuthCallback): void
```

注册远程认证回调。该接口用于在远程认证场景下注册回调接口，注册后系统可通过回调获取远程认证所需的页面参数，并在认证完成后接收认证结果。不允许重复注册，在不使用时应调用 [unregisterRemoteAuthCallback](#registerremoteauthcallback系统接口)取消注册，避免回调无法释放。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_USER_AUTH_INTERNAL

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-userAuth-function registerRemoteAuthCallback(callback: IRemoteAuthCallback): void--><!--Device-userAuth-function registerRemoteAuthCallback(callback: IRemoteAuthCallback): void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [IRemoteAuthCallback](arkts-userauthentication-userauth-iremoteauthcallback-i-sys.md) | 是 | 远程认证回调接口。包含获取认证页面参数和返回认证结果的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied. Called by non-system application. |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { userAuth } from '@kit.UserAuthenticationKit';

let remoteAuthCallback: userAuth.IRemoteAuthCallback = {
  onGetRemoteAuthWidgetParam(challenge: Uint8Array): userAuth.WidgetParam {
    console.info('Received challenge for remote auth, length: ' + challenge.length);
    return {
      title: 'Remote Authentication',
      navigationButtonText: 'Cancel'
    } as userAuth.WidgetParam;
  },
  onRemoteAuthResult(challenge: Uint8Array, result: userAuth.UserAuthResult): void {
    console.info('remote auth result, result: ' + result.result + ', authType: ' + result.authType);
  }
};

try {
  userAuth.unregisterRemoteAuthCallback();
  userAuth.registerRemoteAuthCallback(remoteAuthCallback);
  console.info('Remote auth callback registered successfully');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`failed to register remote auth callback. Code is ${err?.code}, message is ${err?.message}`);
}
```

