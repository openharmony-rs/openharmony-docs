# off（系统接口）

## 导入模块

```TypeScript
import { cooperate } from '@kit.DistributedServiceKit';
```

## off('cooperate')

```TypeScript
function off(type: 'cooperate', callback?: Callback<void>): void
```

取消监听键鼠穿越状态。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** off(type:

<!--Device-cooperate-function off(type: 'cooperate', callback?: Callback<void>): void--><!--Device-cooperate-function off(type: 'cooperate', callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Cooperate

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cooperate' | 是 | 监听类型，取值为'cooperate'。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;void&gt; | 否 | 需要取消注册的回调函数，若无此参数，则取消当前应用注册的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types.<br>3. Parameter verification failed. |

**示例：**

```TypeScript
// 取消注册单个回调函数
class Data {
  networkId: string = "networkId";
  msg: cooperate.CooperateMsg = 0;
}

function callbackOff() {
  console.info(`Keyboard mouse crossing event`);
  return false;
}

try {
  cooperate.on('cooperate', (data: Data) => {
    console.info(`Keyboard mouse crossing event: ${JSON.stringify(data)}`);
  });
  cooperate.off('cooperate', callbackOff);
} catch (error) {
  console.error(`Register failed, error: ${JSON.stringify(error)}`);
}

```

```TypeScript
// 取消注册所有回调函数
class Data {
  networkId: string = "networkId";
  msg: cooperate.CooperateMsg = 0;
}

try {
  cooperate.on('cooperate', (data: Data) => {
    console.info(`Keyboard mouse crossing event: ${JSON.stringify(data)}`);
  });
  cooperate.off('cooperate');
} catch (error) {
  console.error(`Execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}

```


## off('cooperateMessage')

```TypeScript
function off(type: 'cooperateMessage', callback?: Callback<CooperateMessage>): void
```

取消监听键鼠穿越状态。

**起始版本：** 11

**需要权限：** ohos.permission.COOPERATE_MANAGER

<!--Device-cooperate-function off(type: 'cooperateMessage', callback?: Callback<CooperateMessage>): void--><!--Device-cooperate-function off(type: 'cooperateMessage', callback?: Callback<CooperateMessage>): void-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Cooperate

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cooperateMessage' | 是 | 监听类型，取值为'cooperate'。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;CooperateMessage&gt; | 否 | 需要取消注册的回调函数，若无此参数，则取消当前应用注册的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types.<br>3. Parameter verification failed. |

**示例：**

```TypeScript
// 取消注册单个回调函数
function callbackOn(msgOn: cooperate.CooperateMessage) {
  console.info(`Keyboard mouse crossing event: ${JSON.stringify(msgOn)}`);
  return false;
}

function callbackOff(msgOff: cooperate.CooperateMessage) {
  console.info(`Keyboard mouse crossing event: ${JSON.stringify(msgOff)}`);
  return false;
}

try {
  cooperate.on('cooperateMessage', callbackOn);
  cooperate.off('cooperateMessage', callbackOff);
} catch (error) {
  console.error(`Execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}

```

```TypeScript
// 取消注册所有回调函数
import { cooperate } from '@kit.DistributedServiceKit';
function callbackOn(msg: cooperate.CooperateMessage) {
  console.info(`Keyboard mouse crossing event: ${JSON.stringify(msg)}`);
  return false;
}

try {
  cooperate.on('cooperateMessage', callbackOn);
  cooperate.off('cooperateMessage');
} catch (error) {
  console.error(`Execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}

```


## off('cooperateMouse')

```TypeScript
function off(type: 'cooperateMouse', networkId: string, callback?: Callback<MouseLocation>): void
```

取消监听指定设备鼠标光标位置。

**起始版本：** 12

**需要权限：** ohos.permission.COOPERATE_MANAGER

<!--Device-cooperate-function off(type: 'cooperateMouse', networkId: string, callback?: Callback<MouseLocation>): void--><!--Device-cooperate-function off(type: 'cooperateMouse', networkId: string, callback?: Callback<MouseLocation>): void-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Cooperate

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cooperateMouse' | 是 | 监听类型，取值为'cooperateMouse'。 |
| networkId | string | 是 | 目标设备描述符 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;MouseLocation&gt; | 否 | 需要取消注册的回调函数，若无此参数，则取消当前应用注册的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types.<br>3. Parameter verification failed. |

**示例：**

```TypeScript
// 取消注册单个回调函数
function callbackOn(data: cooperate.MouseLocation) {
  console.info('Register mouse location listener');
  return false;
}

function callbackOff(data: cooperate.MouseLocation) {
  console.info('Unregister mouse location listener');
  return false;
}

try {
  let networkId: string = 'Default';
  cooperate.on('cooperateMouse', networkId, callbackOn);
  cooperate.off('cooperateMouse', networkId, callbackOff);
} catch (error) {
  console.error(`Execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}

```

```TypeScript
// 取消注册所有回调函数
function callbackOn(data: cooperate.MouseLocation) {
  console.info('Register mouse location listener');
}

try {
  let networkId: string = 'Default';
  cooperate.on('cooperateMouse', networkId, callbackOn);
  cooperate.off('cooperateMouse', networkId);
} catch (error) {
  console.error(`Execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}

```

