# UserAuthInstance

用于执行用户身份认证，并支持使用统一用户身份认证控件。该接口提供了完整的用户认证能力，包括订阅认证结果、订阅认证中间状态、启动认证和取消认证等操作。通过统一认证控件，可以为用户提供标准化的认证界面和一致的认证体验。

使用以下接口前，需先通过[getUserAuthInstance](arkts-userauthentication-getuserauthinstance-f.md#getuserauthinstance-1)方法获取UserAuthInstance对象。

> **说明：**
>
> 每个UserAuthInstance实例只能用于一次认证过程。若需要再次认证，必须重新获取UserAuthInstance实例。

**起始版本：** 10

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## cancel

```TypeScript
cancel(): void
```

取消认证。

> **说明：**
>
> 此时UserAuthInstance必须是正在进行认证的对象。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BIOMETRIC

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Incorrect parameter types. |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { userAuth } from '@kit.UserAuthenticationKit';

try {
  const rand = cryptoFramework.createRandom();
  const len: number = 16;
  let randData: Uint8Array | null = null;
  let retryCount = 0;
  while(retryCount < 3){
    randData = rand?.generateRandomSync(len)?.data;
    if(randData){
      break;
    }
    retryCount++;
  }
  if(!randData){
    return;
  }
  const authParam : userAuth.AuthParam = {
    challenge: randData,
    authType: [userAuth.UserAuthType.PIN],
    authTrustLevel: userAuth.AuthTrustLevel.ATL3,
  };
  const widgetParam: userAuth.WidgetParam = {
    title: '请输入密码',
  };
  const userAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
  console.info('get userAuth instance successfully.');
  // 需要调用UserAuthInstance的start()接口，启动认证后，才能调用cancel()接口。
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

取消订阅用户身份认证的结果。

> **说明：**
>
> 需要使用已经成功订阅事件的[UserAuthInstance](arkts-userauthentication-userauthinstance-i.md)对象调用该接口进行取消订阅。

**起始版本：** 10

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'result' | 是 | 订阅事件类型，表明该事件用来返回认证结果。 |
| callback | IAuthCallback | 否 | 认证接口的回调函数，用于返回认证结果。当不传该参数时默认值为调用[on('result')](arkts-userauthentication-userauthinstance-i.md#on-1)接口时传递的参数值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types.<br>3. Parameter verification failed. |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { userAuth } from '@kit.UserAuthenticationKit';

try {
  const rand = cryptoFramework.createRandom();
  const len: number = 16;
  let randData: Uint8Array | null = null;
  let retryCount = 0;
  while(retryCount < 3){
    randData = rand?.generateRandomSync(len)?.data;
    if(randData){
      break;
    }
    retryCount++;
  }
  if(!randData){
    return;
  }
  const authParam: userAuth.AuthParam = {
    challenge: randData,
    authType: [userAuth.UserAuthType.PIN],
    authTrustLevel: userAuth.AuthTrustLevel.ATL3,
  };
  const widgetParam: userAuth.WidgetParam = {
    title: '请输入密码',
  };
  const userAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
  console.info('get userAuth instance successfully.');
  userAuthInstance.off('result', {
    onResult (result) {
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

取消订阅用户身份认证中间状态。

> **说明：**
>
> 需要使用已经成功订阅事件的[UserAuthInstance](arkts-userauthentication-userauthinstance-i.md)对象调用该接口进行取消订阅。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'authTip' | 是 | 取消订阅的事件类型，支持的事件为'authTip'，当[start()](arkts-userauthentication-userauthinstance-i.md#start-1)调用完成，发起身份认证并调用[on('authTip')](arkts-userauthentication-userauthinstance-i.md#on-2)订阅该事件后，调用该方法可取消订阅，不会再触发该事件。 |
| callback | AuthTipCallback | 否 | 认证接口的回调函数，用于返回认证中间状态。 当不传该参数时默认值为调用[on('authTip')](arkts-userauthentication-userauthinstance-i.md#on-2)接口时传递的参数值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { userAuth } from '@kit.UserAuthenticationKit';

try {
  const rand = cryptoFramework.createRandom();
  const len: number = 16;
  let randData: Uint8Array | null = null;
  let retryCount = 0;
  while(retryCount < 3){
    randData = rand?.generateRandomSync(len)?.data;
    if(randData){
      break;
    }
    retryCount++;
  }
  if(!randData){
    return;
  }
  const authParam: userAuth.AuthParam = {
    challenge: randData,
    authType: [userAuth.UserAuthType.PIN],
    authTrustLevel: userAuth.AuthTrustLevel.ATL3,
  };
  const widgetParam: userAuth.WidgetParam = {
    title: '请输入密码',
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

订阅用户身份认证的最终结果。通过该接口获取到的是用户在认证控件完成身份认证交互后的最终身份认证结果。认证控件消失前，用户中间的认证不通过尝试并不会通过该接口返回，只有最终的认证结果（成功或最终失败）会通过此接口返回。如果需要感
知整个认证过程中用户的每一次认证不通过尝试和中间状态，请通过
[on('authTip')](arkts-userauthentication-userauthinstance-i.md#on-2)接口订阅。

> **说明：**
>
> 在PC/2in1设备上，应用如果使用模应用弹窗方式发起认证（即配置用户界面参数[widgetParam](arkts-userauthentication-widgetparam-i.md)时传入了有效的uiContext），收到认证结果后，若需弹出其
> 他窗口，应先获取控件弹窗释放的标志消息，通过
> [on('authTip')](arkts-userauthentication-userauthinstance-i.md#on-2)接口订阅控件释放消息（
> authTipInfo.tipCode = UserAuthTipCode.WIDGET_RELEASED）。

**起始版本：** 10

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'result' | 是 | 订阅事件类型，表明该事件用来返回认证结果。 |
| callback | IAuthCallback | 是 | 认证接口的回调函数，用于返回认证结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types.<br>3. Parameter verification failed. |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |

## on('authTip')

```TypeScript
on(type: 'authTip', callback: AuthTipCallback): void
```

订阅身份认证过程中的提示信息。通过该接口可以获取到认证过程中控件的拉起和退出提示，以及认证过程中用户的每一次认证不通过尝试。使用callback异步回调。

> **说明：**
>
> 在PC/2in1设备上，应用如果使用模应用弹窗方式发起认证（即配置用户界面参数[widgetParam](arkts-userauthentication-widgetparam-i.md)时传入了有效的uiContext），收到认证结果后，若需弹出其
> 他窗口，应先获取控件弹窗释放的标志消息，通过
> [on('authTip')](arkts-userauthentication-userauthinstance-i.md#on-2)接口订阅控件释放消息（
> authTipInfo.tipCode = UserAuthTipCode.WIDGET_RELEASED）。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'authTip' | 是 | 订阅事件类型，支持的事件为'authTip'，当[start()](arkts-userauthentication-userauthinstance-i.md#start-1)调用完成，发起身份认证，触发该事件。 |
| callback | AuthTipCallback | 是 | 认证接口的回调函数，用于返回认证中间状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { userAuth } from '@kit.UserAuthenticationKit';

try {
  const rand = cryptoFramework.createRandom();
  const len: number = 16;
  let randData: Uint8Array | null = null;
  let retryCount = 0;
  while(retryCount < 3){
    randData = rand?.generateRandomSync(len)?.data;
    if(randData){
      break;
    }
    retryCount++;
  }
  if(!randData){
    return;
  }
  const authParam: userAuth.AuthParam = {
    challenge: randData,
    authType: [userAuth.UserAuthType.PIN],
    authTrustLevel: userAuth.AuthTrustLevel.ATL3,
  };
  const widgetParam: userAuth.WidgetParam = {
    title: '请输入密码',
  };
  const userAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
  console.info('get userAuth instance successfully.');
  // 需要调用UserAuthInstance的start()接口，启动认证后，才能通过onAuthTip获取到认证中间状态。
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

开始认证。

> **说明：**
>
> 每个UserAuthInstance只能进行一次认证，需要再次认证时，必须重新获取UserAuthInstance。

**起始版本：** 10

**需要权限：** 
- API版本20+：ohos.permission.ACCESS_BIOMETRIC or ohos.permission.USER_AUTH_FROM_BACKGROUND
- API版本10 - 19：ohos.permission.ACCESS_BIOMETRIC

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Possible causes:<br>1. No permission to access biometric.<br>2. No permission to start authentication from background. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Incorrect parameter types. |
| [12500001](../errorcode-useriam.md#12500001-认证不通过) | Authentication failed.<br>**适用版本：** 10 - 19 |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |
| [12500003](../errorcode-useriam.md#12500003-认证被取消) | Authentication canceled. |
| [12500004](../errorcode-useriam.md#12500004-认证操作超时) | Authentication timeout.<br>**适用版本：** 10 - 19 |
| [12500005](../errorcode-useriam.md#12500005-认证类型不支持) | The authentication type is not supported. |
| [12500006](../errorcode-useriam.md#12500006-认证信任等级不支持) | The authentication trust level is not supported. |
| [12500007](../errorcode-useriam.md#12500007-认证服务繁忙) | Authentication service is busy.<br>**适用版本：** 10 - 19 |
| [12500009](../errorcode-useriam.md#12500009-认证被锁定) | Authentication is locked out. |
| [12500010](../errorcode-useriam.md#12500010-该类型的凭据没有录入) | The type of credential has not been enrolled. |
| [12500011](../errorcode-useriam.md#12500011-提示通知切换自定义认证) | Switched to the customized authentication process. |
| [12500013](../errorcode-useriam.md#12500013-密码过期) | Operation failed because of PIN expired.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { userAuth } from '@kit.UserAuthenticationKit';

try {
  const rand = cryptoFramework.createRandom();
  const len: number = 16;
  let randData: Uint8Array | null = null;
  let retryCount = 0;
  while(retryCount < 3){
    randData = rand?.generateRandomSync(len)?.data;
    if(randData){
      break;
    }
    retryCount++;
  }
  if(!randData){
    return;
  }
  const authParam: userAuth.AuthParam = {
    challenge: randData,
    authType: [userAuth.UserAuthType.PIN],
    authTrustLevel: userAuth.AuthTrustLevel.ATL3,
  };
  const widgetParam: userAuth.WidgetParam = {
    title: '请输入密码',
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

