# getUserAuthInstance

## Modules to Import

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## getUserAuthInstance

```TypeScript
function getUserAuthInstance(authParam: AuthParam, widgetParam: WidgetParam): UserAuthInstance
```

Obtains a [UserAuthInstance](arkts-userauthentication-userauth-userauthinstance-i.md) instance for user authentication. The user authentication widget is also supported. This API is used to create a user authentication instance. After authentication parameters and UI parameters are configured, you can use the returned instance object to start authentication and subscribe to the authentication result.

> **NOTE:** 

> Each **UserAuthInstance** can be used for authentication only once. To perform authentication again, you must
> obtain a new **UserAuthInstance**. After the authentication is complete (regardless of whether it is successful
> or fails), the instance cannot be used again.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| authParam | [AuthParam](arkts-userauthentication-userauth-authparam-i.md) | Yes | User authentication parameters, including the challenge value, authentication type list, authentication trust level, and authentication result reuse configuration. It is recommended that the challenge value be a random number generated using the crypto framework. Multiple authentication types can be specified for the user to choose from, and the authentication trust level should be selected based on the security requirements of the service scenario. |
| widgetParam | [WidgetParam](arkts-userauthentication-userauth-widgetparam-i.md) | Yes | User authentication widget configuration parameters, including the widget title, navigation button text, window mode, and application modal dialog context. It is recommended that the title be set to the authentication purpose, and the navigation button text can be used to customize the authentication navigation. |

**Return value:**

| Type | Description |
| --- | --- |
| [UserAuthInstance](arkts-userauthentication-userauth-userauthinstance-i.md) | **UserAuthInstance** instance that supports UI. After obtaining the instance, call [on('result')](arkts-userauthentication-userauth-userauthinstance-i.md#onresult) to subscribe to the authentication result, and then call [start](arkts-userauthentication-userauth-userauthinstance-i.md#start) to start authentication. After the authentication is complete, you can obtain the authentication result through a callback. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. <br>3. Parameter verification failed. |
| [12500002](../errorcode-useriam.md#12500002-common-error-code-of-the-identity-authentication-system) | General operation error. |
| [12500005](../errorcode-useriam.md#12500005-unsupported-authentication-type) | The authentication type is not supported. |
| [12500006](../errorcode-useriam.md#12500006-unsupported-authentication-trust-level) | The authentication trust level is not supported. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { userAuth } from '@kit.UserAuthenticationKit';

try {
  const rand = cryptoFramework.createRandom();
  const len: number = 16;
  let randData: Uint8Array | null = null;
  let retryCount = 0;
  while (retryCount < 3) {
    randData = rand?.generateRandomSync(len)?.data;
    if (randData) {
      break;
    }
    retryCount++;
  }
  if (!randData) {
    return;
  }
  const authParam: userAuth.AuthParam = {
    challenge: randData,
    authType: [userAuth.UserAuthType.PIN],
    authTrustLevel: userAuth.AuthTrustLevel.ATL3,
  };
  const widgetParam: userAuth.WidgetParam = {
    title: 'Enter password',
  };
  let userAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
  console.info('get userAuth instance successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`auth failed. Code is ${err?.code}, message is ${err?.message}`);
}
```
