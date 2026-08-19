# UserAuthWidgetMgr（系统接口）

身份认证组件管理器。用于将自定义身份认证控件注册到UserAuthWidgetMgr中进行统一管理和调度。自定义身份认证控件可接收来自用户认证框架的命令并执行相应操作。

**起始版本：** 23

<!--Device-userAuth-interface UserAuthWidgetMgr--><!--Device-userAuth-interface UserAuthWidgetMgr-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
import { UserAuthIcon } from '@kit.UserAuthenticationKit';
```

## offCommand

```TypeScript
offCommand(callback?: IAuthWidgetCallback): void
```

身份认证控件取消订阅来自用户认证框架的命令。

**起始版本：** 23

<!--Device-UserAuthWidgetMgr-offCommand(callback?: IAuthWidgetCallback): void--><!--Device-UserAuthWidgetMgr-offCommand(callback?: IAuthWidgetCallback): void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [IAuthWidgetCallback](arkts-userauthentication-userauth-iauthwidgetcallback-i-sys.md) | 否 | Callback to unregister. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. <br>3. Parameter verification failed. |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |

**示例**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@ohos.base';

const userAuthWidgetMgrVersion: int = 1;
try {
  let userAuthWidgetMgr = userAuth.getUserAuthWidgetMgr(userAuthWidgetMgrVersion);
  console.info('get userAuthWidgetMgr instance successfully.');
  userAuthWidgetMgr.offCommand({
    sendCommand: (cmdData: string) => {
      console.info(`The cmdData is ${cmdData}`);
    }
  })
  console.info('cancel subscribe authentication event successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`userAuth widgetMgr failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

## off('command')

```TypeScript
off(type: 'command', callback?: IAuthWidgetCallback): void
```

取消订阅来自用户认证框架的命令事件。身份认证控件通过此接口取消对用户认证框架命令的订阅。

**起始版本：** 10

<!--Device-UserAuthWidgetMgr-off(type: 'command', callback?: IAuthWidgetCallback): void--><!--Device-UserAuthWidgetMgr-off(type: 'command', callback?: IAuthWidgetCallback): void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'command' | 是 | 订阅事件类型。值为'command'，表明取消订阅用户认证框架向身份认证控件发送命令的事件。 |
| callback | [IAuthWidgetCallback](arkts-userauthentication-userauth-iauthwidgetcallback-i-sys.md) | 否 | 回调函数。指定取消注册的回调函数，需与on方法注册时传入的回调一致；若不传入此参数，则取消所有已注册的回调。使用前需确保已通过 [on](#oncommand)方法注册过相应回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. <br>3. Parameter verification failed. |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |

**示例**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

const userAuthWidgetMgrVersion = 1;
try {
  let userAuthWidgetMgr = userAuth.getUserAuthWidgetMgr(userAuthWidgetMgrVersion);
  console.info('get userAuthWidgetMgr instance successfully.');
  userAuthWidgetMgr.off('command', {
    sendCommand: (cmdData) => {
      console.info(`The cmdData is ${cmdData}`);
    }
  })
  console.info('cancel subscribe authentication event successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`userAuth widgetMgr failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

## onCommand

```TypeScript
onCommand(callback: IAuthWidgetCallback): void
```

身份认证控件订阅来自用户认证框架的命令。使用callback异步回调。

**起始版本：** 23

<!--Device-UserAuthWidgetMgr-onCommand(callback: IAuthWidgetCallback): void--><!--Device-UserAuthWidgetMgr-onCommand(callback: IAuthWidgetCallback): void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [IAuthWidgetCallback](arkts-userauthentication-userauth-iauthwidgetcallback-i-sys.md) | 是 | 组件管理接口的回调函数，用于用户认证框架向身份认证控件发送命令。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. <br>3. Parameter verification failed. |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |

**示例**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@ohos.base';

const userAuthWidgetMgrVersion: int = 1;
try {
  let userAuthWidgetMgr = userAuth.getUserAuthWidgetMgr(userAuthWidgetMgrVersion);
  console.info('get userAuthWidgetMgr instance successfully.');
  userAuthWidgetMgr.onCommand({
    sendCommand: (cmdData: string) => {
      console.info(`The cmdData is ${cmdData}`);
    }
  })
  console.info('subscribe authentication event successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`userAuth widgetMgr failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

## on('command')

```TypeScript
on(type: 'command', callback: IAuthWidgetCallback): void
```

订阅来自用户认证框架的命令事件。身份认证控件通过此接口订阅来自用户认证框架的命令，以便根据命令执行相应的认证操作。

**起始版本：** 10

<!--Device-UserAuthWidgetMgr-on(type: 'command', callback: IAuthWidgetCallback): void--><!--Device-UserAuthWidgetMgr-on(type: 'command', callback: IAuthWidgetCallback): void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'command' | 是 | 订阅事件类型。值为'command'，表明该事件用于用户认证框架向身份认证控件发送命令。 |
| callback | [IAuthWidgetCallback](arkts-userauthentication-userauth-iauthwidgetcallback-i-sys.md) | 是 | 回调函数。用于接收来自用户认证框架的命令，身份认证控件需在回调中解析命令并执行相应操作。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. <br>3. Parameter verification failed. |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |

**示例**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

const userAuthWidgetMgrVersion = 1;
try {
  let userAuthWidgetMgr = userAuth.getUserAuthWidgetMgr(userAuthWidgetMgrVersion);
  console.info('get userAuthWidgetMgr instance successfully.');
  userAuthWidgetMgr.on('command', {
    sendCommand: (cmdData) => {
      console.info(`The cmdData is ${cmdData}`);
    }
  })
  console.info('subscribe authentication event successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`userAuth widgetMgr failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

