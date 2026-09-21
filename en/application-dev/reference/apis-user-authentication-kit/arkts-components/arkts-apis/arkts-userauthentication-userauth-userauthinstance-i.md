# UserAuthInstance

```TypeScript
interface UserAuthInstance
```

Provides APIs for user authentication. The user authentication widget is supported. This API provides complete user authentication capabilities, including subscribing to authentication results and intermediate states, and starting and canceling authentication. The unified authentication widget provides users with a standardized authentication UI and consistent authentication experience.

Before using the APIs of **UserAuthInstance**, you must obtain a **UserAuthInstance** instance by using [getUserAuthInstance](arkts-userauthentication-userauth-getuserauthinstance-f.md).

> **NOTE:** 

> Each **UserAuthInstance** can be used for only one authentication process. To perform authentication again, you
> must obtain a new **UserAuthInstance** instance.

**Since:** 10

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## Modules to Import

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## cancel

```TypeScript
cancel(): void
```

Cancels this authentication. This API is commonly used in the following scenarios: the application needs to abort authentication due to service logic changes; the authentication operation is aborted due to timeout or exceptions.

> **NOTE:** 

> **UserAuthInstance** must be the instance being authenticated.

**Since:** 10

**Required permissions:** ohos.permission.ACCESS_BIOMETRIC

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Incorrect parameter types. |
| [12500002](../errorcode-useriam.md#12500002-common-error-code-of-the-identity-authentication-system) | General operation error. |

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
  const authParam : userAuth.AuthParam = {
    challenge: randData,
    authType: [userAuth.UserAuthType.PIN],
    authTrustLevel: userAuth.AuthTrustLevel.ATL3,
  };
  const widgetParam: userAuth.WidgetParam = {
    title: 'Enter password',
  };
  const userAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
  console.info('get userAuth instance successfully.');
  // The cancel() API can be called only after the authentication is started by start() of UserAuthInstance.
  userAuthInstance.start();
  console.info('auth start successfully.');
  userAuthInstance.cancel();
  console.info('auth cancel successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`auth failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

## off('result')

```TypeScript
off(type: 'result', callback?: IAuthCallback): void
```

Unsubscribes from the user authentication result. This API is commonly used in the following scenarios: unsubscribing when a page is destroyed or a component is unmounted; releasing resources when it is no longer necessary to listen for authentication results.

> **NOTE:** 

> The [UserAuthInstance](arkts-userauthentication-userauth-userauthinstance-i.md) instance used to invoke this API must be the one used
> to subscribe to the event.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'result' | Yes | Event type. The value is **result**, which indicates the authentication result. |
| callback | [IAuthCallback](arkts-userauthentication-userauth-iauthcallback-i.md) | No | Callback used to return the user authentication result. If this parameter is not passed, the value passed when the [on('result')](#onresult) API is called is used by default. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. <br>3. Parameter verification failed. |
| [12500002](../errorcode-useriam.md#12500002-common-error-code-of-the-identity-authentication-system) | General operation error. |

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
  const userAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
  console.info('get userAuth instance successfully.');
  userAuthInstance.off('result', {
    onResult: (result) => {
      console.info(`auth off result = ${result.result}`);
    }
  });
  console.info('auth off successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`auth failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

## off('authTip')

```TypeScript
off(type: 'authTip', callback?: AuthTipCallback): void
```

Unsubscribes from the authentication tip information. This API is commonly used in the following scenarios: cleaning up subscription listeners and releasing resources after authentication is complete; unsubscribing when it is no longer necessary to listen for tip information during the authentication process; unsubscribing when a page is destroyed or a component is unmounted.

> **NOTE:** 

> The [UserAuthInstance](arkts-userauthentication-userauth-userauthinstance-i.md) instance used to invoke this API must be the one used
> to subscribe to the event.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'authTip' | Yes | Event type. The supported event is **'authTip'**. This API unsubscribes from the event triggered by [on('authTip')](#onauthtip) after the [start()](#start) call and the initiation of authentication. |
| callback | [AuthTipCallback](arkts-userauthentication-userauth-authtipcallback-t.md) | No | Callback used to return the intermediate authentication status. If this parameter is not passed, the value passed when the [on('authTip')](#onauthtip) API is called is used by default. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12500002](../errorcode-useriam.md#12500002-common-error-code-of-the-identity-authentication-system) | General operation error. |

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
  const userAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
  console.info('get userAuth instance successfully.');
  userAuthInstance.off('authTip', (authTipInfo: userAuth.AuthTipInfo) => {
    console.info('userAuthInstance callback');
  });
  console.info('auth off successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`auth failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

## on('result')

```TypeScript
on(type: 'result', callback: IAuthCallback): void
```

Subscribes to the user authentication result. This API is used to obtain the final identity authentication result after the user completes identity authentication interaction with the authentication component. Before the authentication widget disappears, the intermediate authentication failures will not be returned through this API. Only the final authentication result (success or failure) is returned through this API. To perceive each authentication failure and intermediate status during the entire authentication process, use the [on('authTip')](#onauthtip) API for subscription.

> **NOTE:** 

> On PCs/2-in-1 devices, if an application initiates authentication in an application modal dialog (that is, a
> valid **uiContext** is passed when the user API parameter [widgetParam](arkts-userauthentication-userauth-widgetparam-i.md) is
> configured) and receives the authentication result, and if other windows need to be displayed, the application
> needs to obtain the flag message released by the component pop-up window and subscribe to the component release
> message (**authTipInfo.tipCode = UserAuthTipCode.WIDGET_RELEASED**) through the
> [on('authTip')](#onauthtip) API.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'result' | Yes | Event type used to return the authentication result. It is triggered when [start()](#start) is called, identity authentication is initiated, and the authentication interaction is completed. |
| callback | [IAuthCallback](arkts-userauthentication-userauth-iauthcallback-i.md) | Yes | Callback used to return the user authentication result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. <br>3. Parameter verification failed. |
| [12500002](../errorcode-useriam.md#12500002-common-error-code-of-the-identity-authentication-system) | General operation error. |

## on('authTip')

```TypeScript
on(type: 'authTip', callback: AuthTipCallback): void
```

Subscribes to authentication tip information. This API is used to obtain the widget startup and exit messages and each authentication failure. This API uses an asynchronous callback to return the result.

> **NOTE:** 

> On PCs/2-in-1 devices, if an application initiates authentication in an application modal dialog (that is, a
> valid **uiContext** is passed when the user API parameter [widgetParam](arkts-userauthentication-userauth-widgetparam-i.md) is
> configured) and receives the authentication result, and if other windows need to be displayed, the application
> needs to obtain the flag message released by the component pop-up window and subscribe to the component release
> message (**authTipInfo.tipCode = UserAuthTipCode.WIDGET_RELEASED**) through the
> [on('authTip')](#onauthtip) API.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'authTip' | Yes | Event type. The supported event is **'authTip'**. This event is triggered when [start()](#start) is called and authentication is initiated. |
| callback | [AuthTipCallback](arkts-userauthentication-userauth-authtipcallback-t.md) | Yes | Callback used to return the intermediate authentication status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12500002](../errorcode-useriam.md#12500002-common-error-code-of-the-identity-authentication-system) | General operation error. |

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
  const userAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
  console.info('get userAuth instance successfully.');
  // The intermediate authentication status is returned by onAuthTip only after the authentication is started by start() of UserAuthInstance.
  userAuthInstance.on('authTip', (authTipInfo: userAuth.AuthTipInfo) => {
    console.info('userAuthInstance callback.');
  });
  console.info('auth on successfully.');
  userAuthInstance.start();
  console.info('auth start successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`auth failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

## start

```TypeScript
start(): void
```

Starts authentication. This API is commonly used in the following service scenarios: initiating identity authentication when a user taps the payment button; performing authentication when a user logs in to an application; confirming identity when a user accesses sensitive data or performs sensitive operations.

> **NOTE:** 

> Each **UserAuthInstance** can be used for authentication only once. To perform authentication again, you must
> obtain a new **UserAuthInstance**.

**Since:** 10

**Required permissions:** 
- API version 20 and later: ohos.permission.ACCESS_BIOMETRIC or ohos.permission.USER_AUTH_FROM_BACKGROUND
- API versions 10 to 19: ohos.permission.ACCESS_BIOMETRIC

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. Possible causes:<br>1. No permission to access biometric. <br>2. No permission to start authentication from background. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Incorrect parameter types. |
| [12500001](../errorcode-useriam.md#12500001-authentication-failed) | Authentication failed.<br>**Applicable version:** 10 - 19 |
| [12500002](../errorcode-useriam.md#12500002-common-error-code-of-the-identity-authentication-system) | General operation error. |
| [12500003](../errorcode-useriam.md#12500003-authentication-canceled) | Authentication canceled. |
| [12500004](../errorcode-useriam.md#12500004-authentication-timed-out) | Authentication timeout.<br>**Applicable version:** 10 - 19 |
| [12500005](../errorcode-useriam.md#12500005-unsupported-authentication-type) | The authentication type is not supported. |
| [12500006](../errorcode-useriam.md#12500006-unsupported-authentication-trust-level) | The authentication trust level is not supported. |
| [12500007](../errorcode-useriam.md#12500007-authentication-service-is-busy) | Authentication service is busy.<br>**Applicable version:** 10 - 19 |
| [12500009](../errorcode-useriam.md#12500009-authentication-locked) | Authentication is locked out. |
| [12500010](../errorcode-useriam.md#12500010-credential-not-enrolled) | The type of credential has not been enrolled. |
| [12500011](../errorcode-useriam.md#12500011-switched-to-custom-authentication) | Switched to the customized authentication process. |
| [12500013](../errorcode-useriam.md#12500013-password-expired) | Operation failed because of PIN expired.<br>**Applicable version:** 12 and later |

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
  const userAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
  console.info('get userAuth instance successfully.');
  userAuthInstance.start();
  console.info('auth start successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`auth failed. Code is ${err?.code}, message is ${err?.message}`);
}
```
