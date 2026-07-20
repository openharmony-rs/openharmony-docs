# on（系统接口）

## 导入模块

```TypeScript
import { cooperate } from '@kit.DistributedServiceKit';
```

<a id="on"></a>
## on('cooperate')

```TypeScript
function on(type: 'cooperate', callback: Callback<{ networkId: string, msg: CooperateMsg }>): void
```

注册监听键鼠穿越状态。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [on(type:](../../apis-test-kit/arkts-apis/arkts-test-uitest-on-c.md)

<!--Device-cooperate-function on(type: 'cooperate', callback: Callback<{ networkId: string, msg: CooperateMsg }>): void--><!--Device-cooperate-function on(type: 'cooperate', callback: Callback<{ networkId: string, msg: CooperateMsg }>): void-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Cooperate

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cooperate' | 是 | 监听类型，取值为'cooperate' |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;{ networkId: string, msg: CooperateMsg }&gt; | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types.<br>3. Parameter verification failed. |

**示例：**

```TypeScript
import { cooperate } from '@kit.DistributedServiceKit';
class Data {
  networkId: string = "networkId";
  msg: cooperate.CooperateMsg = 0;
}

try {
  cooperate.on('cooperate', (data: Data) => {
    console.info(`Keyboard mouse crossing event: ${JSON.stringify(data)}`);
  });
} catch (error) {
  console.error(`Register failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}

```


<a id="on-1"></a>
## on('cooperateMessage')

```TypeScript
function on(type: 'cooperateMessage', callback: Callback<CooperateMessage>): void
```

注册监听键鼠穿越状态。

**起始版本：** 11

**需要权限：** ohos.permission.COOPERATE_MANAGER

<!--Device-cooperate-function on(type: 'cooperateMessage', callback: Callback<CooperateMessage>): void--><!--Device-cooperate-function on(type: 'cooperateMessage', callback: Callback<CooperateMessage>): void-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Cooperate

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cooperateMessage' | 是 | 监听类型，取值为'cooperateMessage' |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;CooperateMessage&gt; | 是 | 回调函数，异步返回键鼠穿越状态消息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types.<br>3. Parameter verification failed. |

**示例：**

```TypeScript
function callback(msg: cooperate.CooperateMessage) {
  console.info(`Keyboard mouse crossing event: ${JSON.stringify(msg)}`);
  return false;
}

try {
  cooperate.on('cooperateMessage', callback);
} catch (error) {
  console.error(`Register failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}

```


<a id="on-2"></a>
## on('cooperateMouse')

```TypeScript
function on(type: 'cooperateMouse', networkId: string, callback: Callback<MouseLocation>): void
```

注册监听指定设备鼠标光标位置。

**起始版本：** 12

**需要权限：** ohos.permission.COOPERATE_MANAGER

<!--Device-cooperate-function on(type: 'cooperateMouse', networkId: string, callback: Callback<MouseLocation>): void--><!--Device-cooperate-function on(type: 'cooperateMouse', networkId: string, callback: Callback<MouseLocation>): void-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Cooperate

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cooperateMouse' | 是 | 监听类型，取值为'cooperateMouse' |
| networkId | string | 是 | 目标设备描述符 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;MouseLocation&gt; | 是 | 回调函数，异步返回指定监听设备鼠标光标位置信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2.Incorrect parameter types.<br>3.Parameter verification failed. |

**示例：**

```TypeScript
function callback(data: cooperate.MouseLocation) {
  console.info('displayX:' + data.displayX + 'displayY:' + data.displayY + 'displayWidth:' +
  data.displayWidth + 'displayHeight:' + data.displayHeight);
}

try {
  let networkId: string = 'Default';
  cooperate.on('cooperateMouse', networkId, callback);
} catch (error) {
  console.error(`Register failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}

```

