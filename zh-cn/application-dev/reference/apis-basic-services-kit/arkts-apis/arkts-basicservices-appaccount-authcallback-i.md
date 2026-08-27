# AuthCallback

认证器回调类。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

## 导入模块

```TypeScript
import { appAccount } from '@kit.BasicServicesKit';
```

## onRequestContinued

```TypeScript
onRequestContinued?: () => void
```

通知请求被继续处理。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let appAccountManager: appAccount.AppAccountManager = appAccount.createAppAccountManager();
let sessionId = '1234';
appAccountManager.getAuthCallback(sessionId).then((callback: appAccount.AuthCallback) => {
  if (callback.onRequestContinued != undefined) {
    callback.onRequestContinued();
  }
}).catch((err: BusinessError) => {
  console.error(`getAuthCallback err: code is ${err.code}, message is ${err.message}`);
});
```

## onRequestRedirected

```TypeScript
onRequestRedirected: (request: Want) => void
```

通知请求被跳转。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 |  |

**示例**

```TypeScript
import { Want } from '@kit.AbilityKit';

class MyAuthenticator extends appAccount.Authenticator {
  createAccountImplicitly(
    options: appAccount.CreateAccountImplicitlyOptions, callback: appAccount.AuthCallback) {
    let want: Want = {
      bundleName: 'com.example.accountjsdemo',
      abilityName: 'com.example.accountjsdemo.LoginAbility',
    };
    callback.onRequestRedirected(want);
  }

  auth(name: string, authType: string,
    options: Record<string, Object>, callback: appAccount.AuthCallback) {
    let result: appAccount.AuthResult = {
      account: {
        name: 'Lisi',
        owner: 'com.example.accountjsdemo',
      },
      tokenInfo: {
        token: 'xxxxxx',
        authType: 'getSocialData'
      }
    };
    callback.onResult(0, result);
  }
}
```

```TypeScript
import { Want } from '@kit.AbilityKit';

class MyAuthenticator extends appAccount.Authenticator {
  addAccountImplicitly(authType: string, callerBundleName: string,
    options: Record<string, Object>, callback: appAccount.AuthenticatorCallback) {
    let want: Want = {
      bundleName: 'com.example.accountjsdemo',
      abilityName: 'com.example.accountjsdemo.LoginAbility',
    };
    callback.onRequestRedirected(want);
  }

  authenticate(name: string, authType: string, callerBundleName: string,
    options: Record<string, Object>, callback: appAccount.AuthenticatorCallback) {
    callback.onResult(appAccount.ResultCode.SUCCESS, {
      name: name,
      authType: authType,
      token: 'xxxxxx'
    });
  }
}
```

## onResult

```TypeScript
onResult: (code: number, result?: AuthResult) => void
```

通知请求结果。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 |  |
| result | AuthResult | 否 |  |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let appAccountManager: appAccount.AppAccountManager = appAccount.createAppAccountManager();
let sessionId = '1234';
appAccountManager.getAuthCallback(sessionId).then((callback: appAccount.AuthCallback) => {
  let result: appAccount.AuthResult = {
    account: {
      name: 'Lisi',
      owner: 'com.example.accountjsdemo',
    },
    tokenInfo: {
      token: 'xxxxxx',
      authType: 'getSocialData'
    }
  };
  callback.onResult(0, result);
}).catch((err: BusinessError) => {
  console.error(`getAuthCallback err: code is ${err.code}, message is ${err.message}`);
});
```
