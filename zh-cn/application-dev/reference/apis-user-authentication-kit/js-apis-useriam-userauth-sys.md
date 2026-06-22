# @ohos.userIAM.userAuth (用户认证)(系统接口)

<!--Kit: User Authentication Kit-->
<!--Subsystem: UserIAM-->
<!--Owner: @WALL_EYE-->
<!--Designer: @lichangting518-->
<!--Tester: @jane_lz-->
<!--Adviser: @zengyawen-->

## 模块简介

**userAuth**模块是OpenHarmony系统中用于用户身份认证的核心模块，提供了设备解锁、支付验证、应用登录等场景下的身份认证能力。

当前页面仅包含本模块中面向系统应用和认证组件开发者的高级能力。这些API提供了认证组件管理、自定义通知发送、认证结果复用查询、隐私密码认证等系统级功能。

主要用于以下场景：

- 系统应用需要管理自定义认证组件的生命周期。
- 认证组件需要与认证框架进行双向通信。
- 需要发送认证组件相关的系统通知。
- 需要查询可复用的认证结果以实现无感认证。
- 需要使用隐私密码进行认证。
- 需要指定特定用户或特定凭据进行认证。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 6开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.userIAM.userAuth (用户认证)](js-apis-useriam-userauth.md)。

## 导入模块

```ts
import { userAuth } from '@kit.UserAuthenticationKit';
```

## AuthParam<sup>10+</sup>

用户认证相关参数。该接口用于配置用户认证的各项参数，包括挑战值、认证类型列表、认证信任等级等。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

| 名称           | 类型                               | 只读 | 可选 | 说明                                                         |
| -------------- | ---------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| userId<sup>18+</sup> | ArkTS-Dyn: number<br>ArkTS-Sta: int | 否   | 是   |待认证的目标用户ID，值为非负整数，用于指定需要认证的用户。默认值为当前用户的ID。<br>**ArkTS-Dyn起始版本：** 18 <br> **ArkTS-Sta起始版本：** 23 <br>**系统接口：** 此接口为系统接口。|
| credentialIdList<sup>23+</sup> | Uint8Array[] | 否 | 是 |凭据ID列表。若凭据ID列表不为空，则会认证指定的凭据ID，而非用户的所有凭据。适用于需要精确控制认证凭据的场景。<br>**ArkTS-Dyn起始版本：** 23 <br> **ArkTS-Sta起始版本：** 23 <br>**系统接口：**此接口为系统接口。<br>**模型约束：**此接口仅可在Stage模型下使用。|

## WindowModeType<sup>10+</sup>

用户认证界面的显示类型。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**系统接口：** 此接口为系统接口。

| 名称       | 值   | 说明       |
| ---------- | ---- | ---------- |
| DIALOG_BOX | 1    | 对话框类型。身份认证界面以对话框形式显示，适用于大多数认证场景，用户体验较好。 |
| FULLSCREEN | 2    | 全屏类型。身份认证界面以全屏形式显示，适用于需要沉浸式认证体验或认证信息较多需要更大展示空间的场景。 |

## WidgetParam<sup>10+</sup>

用户认证界面配置相关参数。该接口用于配置认证界面的显示样式和交互方式，包括标题、导航按钮文本、窗口模式等。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

| 名称                 | 类型                                | 只读 | 可选 | 说明                                                         |
| -------------------- | ----------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| windowMode           | [WindowModeType](#windowmodetype10) | 否   | 是   | 用户认证界面的显示类型。用于控制系统身份认证组件的窗口样式，可选择对话框模式（DIALOG_BOX）或全屏模式（FULLSCREEN）。默认值为WindowModeType.DIALOG_BOX。<br>**系统接口：** 此接口为系统接口。 |

## NoticeType<sup>10+</sup>

用户身份认证的通知类型枚举。该枚举定义了系统支持的通知类型，用于标识通知的来源。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**系统接口：** 此接口为系统接口。

| 名称          | 值   | 说明                 |
| ------------- | ---- | -------------------- |
| WIDGET_NOTICE | 1    | 表示该通知由系统统一身份认证控件发出，用于通知用户认证框架相关事件。 |

## userAuth.sendNotice<sup>10+</sup>

sendNotice(noticeType: NoticeType, eventData: string): void

发送来自身份认证组件的通知。在使用统一身份认证控件进行用户身份认证时，该接口用于接收来自统一身份认证组件的通知，并将通知发送给用户认证框架。

**需要权限：** ohos.permission.SUPPORT_USER_AUTH

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名     | 类型                        | 必填 | 说明       |
| ---------- | --------------------------- | ---- | ---------- |
| noticeType | [NoticeType](#noticetype10) | 是   | 通知类型。用于标识通知的来源，当前支持WIDGET_NOTICE（1），表示来自身份认证组件的通知。 |
| eventData  | string                | 是   | 事件数据。JSON格式的字符串，包含通知的具体内容，如认证类型就绪事件等。数据长度范围为(0, 65536)字节。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[用户认证错误码](errorcode-useriam.md)。

| 错误码ID | 错误信息                                |
| -------- | --------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission denied. Called by non-system application. |
| 401      | Parameter error. Possible causes: <br>1.Mandatory parameters are left unspecified. <br>2.Incorrect parameter types. <br>3.Parameter verification failed.    |
| 12500002 | General operation error.                |

**示例：**

```ts
import { userAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

interface  EventData {
  widgetContextId: number;
  event: string;
  version: string;
  payload: PayLoad;
}
interface PayLoad {
  type: string[];
}
try {
  const eventData : EventData = {
    widgetContextId: 123456,
    event: 'EVENT_AUTH_TYPE_READY',
    version: '1',
    payload: {
      type: ['pin']
    } as PayLoad,
  };
  const jsonEventData = JSON.stringify(eventData);
  let noticeType = userAuth.NoticeType.WIDGET_NOTICE;
  userAuth.sendNotice(noticeType, jsonEventData);
  console.info('sendNotice successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`sendNotice failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

## UserAuthWidgetMgr<sup>10+</sup>

身份认证组件管理器。用于将自定义身份认证控件注册到UserAuthWidgetMgr中，由UserAuthWidgetMgr进行统一管理和调度。通过该接口，自定义身份认证控件可以接收来自用户认证框架的命令并执行相应操作。

### on<sup>10+</sup>

on(type: 'command', callback: IAuthWidgetCallback): void

订阅来自用户认证框架的命令事件。身份认证控件通过此接口订阅来自用户认证框架的命令，以便根据命令执行相应的认证操作。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onCommand](#oncommand23)。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**ArkTS-Dyn起始版本：** 10

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名   | 类型                                          | 必填 | 说明                                                         |
| -------- | --------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | 'command'                                     | 是   | 订阅事件类型。值为'command'，表明该事件用于用户认证框架向身份认证控件发送命令。 |
| callback | [IAuthWidgetCallback](#iauthwidgetcallback10) | 是   | 回调函数。用于接收来自用户认证框架的命令，身份认证控件需在回调中解析命令并执行相应操作。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[用户认证错误码](errorcode-useriam.md)。

| 错误码ID | 错误信息                 |
| -------- | ------------------------ |
| 401      | Parameter error. Possible causes: <br>1.Mandatory parameters are left unspecified. <br>2.Incorrect parameter types. <br>3.Parameter verification failed. |
| 12500002 | General operation error. |

**示例：**

```ts
import { userAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

const userAuthWidgetMgrVersion = 1;
try {
  let userAuthWidgetMgr = userAuth.getUserAuthWidgetMgr(userAuthWidgetMgrVersion);
  console.info('get userAuthWidgetMgr instance successfully.');
  userAuthWidgetMgr.on('command', {
    sendCommand(cmdData) {
      console.info(`The cmdData is ${cmdData}`);
    }
  })
  console.info('subscribe authentication event successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`userAuth widgetMgr failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

### onCommand<sup>23+</sup>

onCommand(callback: IAuthWidgetCallback): void

身份认证控件订阅来自用户认证框架的命令。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on](#on10)。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**ArkTS-Sta起始版本：** 23

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名   | 类型                                          | 必填 | 说明                                                         |
| -------- | --------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | [IAuthWidgetCallback](#iauthwidgetcallback10) | 是   | 组件管理接口的回调函数，用于用户认证框架向身份认证控件发送命令。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[用户认证错误码](errorcode-useriam.md)。

| 错误码ID | 错误信息                 |
| -------- | ------------------------ |
| 401      | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. <br>3. Parameter verification failed. |
| 12500002 | General operation error. |

**示例：**

```ts
import { userAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@ohos.base';

const userAuthWidgetMgrVersion = 1;
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

### off<sup>10+</sup>

off(type: 'command', callback?: IAuthWidgetCallback): void

取消订阅来自用户认证框架的命令事件。身份认证控件通过此接口取消对用户认证框架命令的订阅。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offCommand](#offcommand23)。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**ArkTS-Dyn起始版本：** 10

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名   | 类型                                          | 必填 | 说明                                                         |
| -------- | --------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | 'command'                                     | 是   | 订阅事件类型。值为'command'，表明取消订阅用户认证框架向身份认证控件发送命令的事件。 |
| callback | [IAuthWidgetCallback](#iauthwidgetcallback10) | 否   | 回调函数。指定取消注册的回调函数，若不传入此参数，则取消所有已注册的回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[用户认证错误码](errorcode-useriam.md)。

| 错误码ID | 错误信息                 |
| -------- | ------------------------ |
| 401      | Parameter error. Possible causes: <br>1.Mandatory parameters are left unspecified. <br>2.Incorrect parameter types. <br>3.Parameter verification failed. |
| 12500002 | General operation error. |

**示例：**

```ts
import { userAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

const userAuthWidgetMgrVersion = 1;
try {
  let userAuthWidgetMgr = userAuth.getUserAuthWidgetMgr(userAuthWidgetMgrVersion);
  console.info('get userAuthWidgetMgr instance successfully.');
  userAuthWidgetMgr.off('command', {
    sendCommand(cmdData) {
      console.info(`The cmdData is ${cmdData}`);
    }
  })
  console.info('cancel subscribe authentication event successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`userAuth widgetMgr failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

### offCommand<sup>23+</sup>

offCommand(callback?: IAuthWidgetCallback): void

身份认证控件取消订阅来自用户认证框架的命令。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off](#off10)。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**ArkTS-Sta起始版本：** 23

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名   | 类型                                          | 必填 | 说明                                                         |
| -------- | --------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | [IAuthWidgetCallback](#iauthwidgetcallback10) | 否   | 组件管理接口的回调函数，用于用户认证框架向身份认证控件发送命令。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[用户认证错误码](errorcode-useriam.md)。

| 错误码ID | 错误信息                 |
| -------- | ------------------------ |
| 401      | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. <br>3. Parameter verification failed. |
| 12500002 | General operation error. |

**示例：**

```ts
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

## userAuth.getUserAuthWidgetMgr<sup>10+</sup>

ArkTS-Dyn: getUserAuthWidgetMgr(version: number): UserAuthWidgetMgr

ArkTS-Sta: getUserAuthWidgetMgr(version: int): UserAuthWidgetMgr

获取身份认证组件管理器对象。用于获取UserAuthWidgetMgr实例，通过该实例可将自定义身份认证控件注册到系统进行统一管理。

> **说明：**
>
> 每个UserAuthWidgetMgr实例可管理一个身份认证控件，若需要管理多个控件则需获取多个实例。

**需要权限：** ohos.permission.SUPPORT_USER_AUTH

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名  | 类型   | 必填 | 说明                 |
| ------- | ------ | ---- | -------------------- |
| version | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 身份认证组件的版本号。用于指定组件的版本，目前支持版本1。组件版本决定了组件与框架之间的通信协议和功能支持范围。 |

**返回值：**

| 类型                                      | 说明         |
| ----------------------------------------- | ------------ |
| [UserAuthWidgetMgr](#userauthwidgetmgr10) | 身份认证组件管理器对象。可用于订阅和取消订阅来自用户认证框架的命令。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[用户认证错误码](errorcode-useriam.md)。

| 错误码ID | 错误信息                                |
| -------- | --------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission denied. Called by non-system application. |
| 401      | Parameter error. Possible causes: <br>1.Mandatory parameters are left unspecified. <br>2.Incorrect parameter types. |
| 12500002 | General operation error.                |

**示例：**

```ts
import { userAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let userAuthWidgetMgrVersion = 1;
try {
  let userAuthWidgetMgr = userAuth.getUserAuthWidgetMgr(userAuthWidgetMgrVersion);
  console.info('get userAuthWidgetMgr instance successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`userAuth widgetMgr failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

## AuthWidgetCallbackSendCommandFunc<sup>23+</sup>

type AuthWidgetCallbackSendCommandFunc = (cmdData: string) => void

回调函数，身份认证框架向控件发送命令。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型   | 必填 | 说明                               |
| ------- | ------ | ---- | ---------------------------------- |
| cmdData | string | 是   | 用户身份认证框架向控件发送的命令。 |

## IAuthWidgetCallback<sup>10+</sup>

身份认证组件回调接口。认证组件通过该回调接口获取用户认证框架发送的命令，并根据命令内容执行相应的认证操作。

### 属性

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**ArkTS-Sta起始版本：** 23

| 名称         | 类型   | 只读 | 可选 | 说明                 |
| ------------ | ---------- | ---- | ---- | -------------------- |
| sendCommand<sup>23+</sup> | [AuthWidgetCallbackSendCommandFunc](#authwidgetcallbacksendcommandfunc23) | 否 | 否   | 用于用户认证框架向组件发送命令。  |

### sendCommand<sup>10+</sup>

sendCommand(cmdData: string): void

回调函数，用于接收来自用户认证框架的命令。用户认证框架通过此回调向身份认证组件发送命令，控件需解析命令内容并执行相应操作。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**ArkTS-Dyn起始版本：** 10

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名  | 类型   | 必填 | 说明                               |
| ------- | ------ | ---- | ---------------------------------- |
| cmdData | string | 是   | 命令数据。JSON格式的字符串，包含用户认证框架向身份认证控件发送的具体命令内容，如认证类型切换、认证结果返回等指令。控件需解析此数据并执行相应操作。 |

**示例：**

ArkTS-Dyn示例：

```ts
import { userAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

const userAuthWidgetMgrVersion = 1;
try {
  let userAuthWidgetMgr = userAuth.getUserAuthWidgetMgr(userAuthWidgetMgrVersion);
  console.info('get userAuthWidgetMgr instance successfully.');
  userAuthWidgetMgr.on('command', {
    sendCommand(cmdData) {
      console.info(`The cmdData is ${cmdData}`);
    }
  })
  console.info('subscribe authentication event successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`userAuth widgetMgr failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

ArkTS-Sta示例：

```ts
import { userAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@ohos.base';

const userAuthWidgetMgrVersion = 1;
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

## UserAuthType<sup>8+</sup>

表示身份认证的凭据类型枚举。该枚举定义了系统支持的认证类型，包括生物特征认证（人脸、指纹）和密码认证（PIN）等。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

| 名称        | 值   | 说明       |
| ----------- | ---- | ---------- |
| PRIVATE_PIN<sup>14+</sup>  | 16   | 隐私密码。一种特殊的PIN认证类型，一般用于解锁后的用户二次访问控制。例如用户可以选择使用隐私密码保护应用锁，从而阻止知道锁屏密码的家人访问自己的某些应用。<br> **ArkTS-Dyn起始版本：** 14 <br> **ArkTS-Sta起始版本：** 23 <br>**系统接口：** 此接口为系统接口。 |

**示例：**

发起用户认证，采用认证可信等级≥ATL3的隐私密码认证，获取认证结果。

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { userAuth } from '@kit.UserAuthenticationKit';

try {
  const rand = cryptoFramework.createRandom();
  const len: number = 16;
  const randData: Uint8Array = rand?.generateRandomSync(len)?.data;
  const authParam: userAuth.AuthParam = {
    challenge: randData,
    authType: [userAuth.UserAuthType.PRIVATE_PIN],
    authTrustLevel: userAuth.AuthTrustLevel.ATL3,
  };
  const widgetParam: userAuth.WidgetParam = {
    title: '请输入密码',
  };

  const userAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
  console.info('get userAuth instance successfully.');
  // 需要调用UserAuthInstance的start()接口，启动认证后，才能通过onResult获取到认证结果。
  userAuthInstance.on('result', {
    onResult (result) {
      console.info(`userAuthInstance callback result = ${result.result}`);
    }
  });
  console.info('auth on successfully.');
  userAuthInstance.start();
  console.info('auth start successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`auth failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { userAuth } from '@kit.UserAuthenticationKit';

try {
  const rand = cryptoFramework.createRandom();
  const len: int = 16;
  const randData: Uint8Array = rand?.generateRandomSync(len)?.data;
  const authParam: userAuth.AuthParam = {
    challenge: randData,
    authType: [userAuth.UserAuthType.PRIVATE_PIN],
    authTrustLevel: userAuth.AuthTrustLevel.ATL3,
  };
  const widgetParam: userAuth.WidgetParam = {
    title: '请输入密码',
  };

  const userAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
  console.info('get userAuth instance successfully.');
  // 需要调用UserAuthInstance的start()接口，启动认证后，才能通过onResult获取到认证结果。
  userAuthInstance.onResult({
    onResult: (result) => {
      console.info(`userAuthInstance callback result = ${result.result}`);
    }
  });
  console.info('auth on successfully.');
  userAuthInstance.start();
  console.info('auth start successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`auth failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

## userAuth.queryReusableAuthResult<sup>20+</sup>

queryReusableAuthResult(authParam: AuthParam): Uint8Array

查询是否有可复用的身份认证结果。该接口用于在发起认证前查询是否存在满足复用条件的认证结果，若存在则直接返回可复用的AuthToken，无需用户再次进行认证交互。

**需要权限：** ohos.permission.ACCESS_USER_AUTH_INTERNAL

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 23

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名  | 类型   | 必填 | 说明                 |
| ------- | ------ | ---- | -------------------- |
| authParam | [AuthParam](js-apis-useriam-userauth.md#authparam10) | 是 | 用户认证相关参数。包含挑战值（challenge）、认证类型列表（authType）、认证信任等级（authTrustLevel）以及认证结果复用配置（reuseUnlockResult）。系统会根据这些参数判断是否存在满足条件的可复用认证结果。|

**返回值：**

| 类型        | 说明                                 |
| ---------- | ------------------------------------ |
| Uint8Array | 可复用的认证令牌（AuthToken）。若存在满足条件的可复用认证结果，返回AuthToken数据，最大长度为1024字节；若不存在，则抛出相应错误码。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[用户认证错误码](errorcode-useriam.md)。

| 错误码ID | 错误信息                                |
| -------- | --------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission denied. Called by non-system application. |
| 12500002 | General operation error.                |
| 12500008 | The parameter is out of range.          |
| 12500017 | Failed to reuse authentication result.       |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { userAuth } from '@kit.UserAuthenticationKit';

try {
  const rand = cryptoFramework.createRandom();
  const len = 16;
  const randData: Uint8Array = rand?.generateRandomSync(len)?.data;
  const reuseUnlockResult: userAuth.ReuseUnlockResult = {
    reuseMode: userAuth.ReuseMode.AUTH_TYPE_RELEVANT,
    reuseDuration: userAuth.MAX_ALLOWABLE_REUSE_DURATION,
  }
  const authParam: userAuth.AuthParam = {
    challenge: randData,
    authType: [userAuth.UserAuthType.PIN],
    authTrustLevel: userAuth.AuthTrustLevel.ATL3,
    reuseUnlockResult: reuseUnlockResult,
  };
  let authToken = userAuth.queryReusableAuthResult(authParam);
  console.info('query reuse auth result successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`query reuse auth result failed. Code is ${err?.code}, message is ${err?.message}`);
}
```

## UserAuthResultCode<sup>9+</sup>

表示返回码的枚举。该枚举定义了用户认证操作可能返回的所有结果码，包括成功码和各类错误码。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**系统接口：** 此接口为系统接口。

| 名称                    |   值   | 说明                 |
| ----------------------- | ------ | -------------------- |
| AUTH_TOKEN_CHECK_FAILED<sup>18+</sup> | 12500015      | AuthToken校验失败。verifyAuthToken系统接口错误码，表示验证的AuthToken完整性校验失败，令牌可能被篡改或损坏。<br/> **ArkTS-Dyn起始版本：** 18 <br> **ArkTS-Sta起始版本：** 23|
| AUTH_TOKEN_EXPIRED<sup>18+</sup>       | 12500016      | AuthToken已过期。verifyAuthToken系统接口错误码，表示AuthToken的签发时间至发起验证时的时间间隔超过传入的最大有效时长（allowableDuration）。<br> **ArkTS-Dyn起始版本：** 18 <br> **ArkTS-Sta起始版本：** 23|
| REUSE_AUTH_RESULT_FAILED<sup>20+</sup>| 12500017      | 复用认证结果失败。queryReusableAuthResult系统接口错误码，表示查询可复用的身份认证结果失败，可能原因包括：不存在满足复用条件的认证结果、认证结果已失效或凭据已变更。<br> **ArkTS-Dyn起始版本：** 20 <br> **ArkTS-Sta起始版本：** 23|