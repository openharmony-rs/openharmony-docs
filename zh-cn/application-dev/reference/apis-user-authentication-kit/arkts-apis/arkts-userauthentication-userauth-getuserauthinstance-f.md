# getUserAuthInstance

## 导入模块

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## getUserAuthInstance

```TypeScript
function getUserAuthInstance(authParam: AuthParam, widgetParam: WidgetParam): UserAuthInstance
```

获取[UserAuthInstance](arkts-userauthentication-userauth-userauthinstance-i.md)对象，执行用户身份认证，并支持使用统一用户身份认证控件。该接口用于创建一个用户认证实例，配置认证参数和界面参数后，可通过返回的实例对象启动认证、订阅认证结果等。

> **说明：**  
>  
> 每个UserAuthInstance只能进行一次认证，需要再次认证时，必须重新获取UserAuthInstance。认证完成后（无论成功或失败），该实例将无法再次使用。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-userAuth-function getUserAuthInstance(authParam: AuthParam, widgetParam: WidgetParam): UserAuthInstance--><!--Device-userAuth-function getUserAuthInstance(authParam: AuthParam, widgetParam: WidgetParam): UserAuthInstance-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| authParam | [AuthParam](arkts-userauthentication-userauth-authparam-i.md) | 是 | 用户认证相关参数。包含挑战值、认证类型列表、认证可信等级、认证结果复用配置等。挑战值建议使用加密框架生成的随机数，认证类型可指定多种供用户选择，认证可信等级应根据业务场景安全需求选择。 |
| widgetParam | [WidgetParam](arkts-userauthentication-userauth-widgetparam-i.md) | 是 | 用户认证界面配置相关参数。包含界面标题、导航按钮文本、窗口模式（系统API）、模应用弹窗上下文等。标题建议设置为认证目的，导航按钮文本可用于自定义认证跳转。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [UserAuthInstance](arkts-userauthentication-userauth-userauthinstance-i.md) | 支持用户界面的认证器对象。获取实例后，需调用[on('result')](arkts-userauthentication-userauth-userauthinstance-i.md#on-1)订阅认证结果，再调用[start](arkts-userauthentication-userauth-userauthinstance-i.md#start-1)启动认证。认证完成后，可通过回调获取认证结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types.<br>3. Parameter verification failed. |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |
| [12500005](../errorcode-useriam.md#12500005-认证类型不支持) | The authentication type is not supported. |
| [12500006](../errorcode-useriam.md#12500006-认证信任等级不支持) | The authentication trust level is not supported. |

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
    title: '请输入密码',
  };
  let userAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
  console.info('get userAuth instance successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`auth failed. Code is ${err?.code}, message is ${err?.message}`);
}

```

