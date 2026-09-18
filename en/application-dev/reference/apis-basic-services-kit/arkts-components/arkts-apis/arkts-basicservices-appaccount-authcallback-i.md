# AuthCallback

Defines authenticator callbacks.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

## Modules to Import

```TypeScript
import { appAccount } from '@kit.BasicServicesKit';
```

## onRequestContinued

```TypeScript
onRequestContinued?: () => void
```

Called to continue to process the request.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Examples**

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

Called to redirect a request.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| request | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes |  |

**Examples**

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

## onResult

```TypeScript
onResult: (code: number, result?: AuthResult) => void
```

Called to return the result of an authentication request.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| code | number | Yes |  |
| result | [AuthResult](arkts-basicservices-appaccount-authresult-i.md) | No |  |

**Examples**

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
