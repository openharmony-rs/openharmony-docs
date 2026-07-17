# off

## 导入模块

```TypeScript
import { continuationManager } from '@kit.AbilityKit';
```

## off('deviceSelected')

```TypeScript
function off(type: 'deviceSelected', token: number): void
```

取消监听设备连接状态。

**起始版本：** 9

**废弃版本：** 22

**替代接口：** off(type:

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-continuationManager-function off(type: 'deviceSelected', token: number): void--><!--Device-continuationManager-function off(type: 'deviceSelected', token: number): void-End-->

**系统能力：** SystemCapability.Ability.DistributedAbilityManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceSelected' | 是 | 取消监听的事件类型，固定值"deviceSelected"。 |
| token | number | 是 | 注册后的token。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [16600001](../errorcode-DistributedSchedule.md#16600001-系统服务工作异常) | The system ability works abnormally. |
| [16600002](../errorcode-DistributedSchedule.md#16600002-指定的token或callback未注册) | The specified token or callback is not registered. |
| [16600004](../errorcode-DistributedSchedule.md#16600004-指定的callback已注册) | The specified callback has been registered. |

**示例：**

```TypeScript
import { continuationManager } from '@kit.AbilityKit';

let token: number = 1;
try {
  continuationManager.off("deviceSelected", token);
} catch (err) {
  console.error('off failed, cause: ' + JSON.stringify(err));
}

```


## off('deviceUnselected')

```TypeScript
function off(type: 'deviceUnselected', token: number): void
```

取消监听设备断开状态。

**起始版本：** 9

**废弃版本：** 22

**替代接口：** off(type:

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-continuationManager-function off(type: 'deviceUnselected', token: number): void--><!--Device-continuationManager-function off(type: 'deviceUnselected', token: number): void-End-->

**系统能力：** SystemCapability.Ability.DistributedAbilityManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceUnselected' | 是 | 取消监听的事件类型，固定值"deviceUnselected"。 |
| token | number | 是 | 注册后的token。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [16600001](../errorcode-DistributedSchedule.md#16600001-系统服务工作异常) | The system ability works abnormally. |
| [16600002](../errorcode-DistributedSchedule.md#16600002-指定的token或callback未注册) | The specified token or callback is not registered. |
| [16600004](../errorcode-DistributedSchedule.md#16600004-指定的callback已注册) | The specified callback has been registered. |

**示例：**

```TypeScript
import { continuationManager } from '@kit.AbilityKit';

let token: number = 1;
try {
  continuationManager.off("deviceUnselected", token);
} catch (err) {
  console.error('off failed, cause: ' + JSON.stringify(err));
}

```


## off('deviceConnect')

```TypeScript
function off(type: 'deviceConnect', callback?: Callback<ContinuationResult>): void
```

异步方法，取消监听设备连接状态，使用Callback形式返回连接的设备信息。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** off(type:

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-continuationManager-function off(type: 'deviceConnect', callback?: Callback<ContinuationResult>): void--><!--Device-continuationManager-function off(type: 'deviceConnect', callback?: Callback<ContinuationResult>): void-End-->

**系统能力：** SystemCapability.Ability.DistributedAbilityManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceConnect' | 是 | 取消监听的事件类型，固定值"deviceConnect"。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<ContinuationResult> | 否 | 当用户从设备选择模块中选择设备时调用，返回设备ID、设备类型和设备名称供开发者使用。 |

**示例：**

```TypeScript
import { continuationManager } from '@kit.AbilityKit';

continuationManager.off("deviceConnect", (data) => {
  console.info('onDeviceConnect deviceId: ' + JSON.stringify(data.id));
  console.info('onDeviceConnect deviceType: ' + JSON.stringify(data.type));
  console.info('onDeviceConnect deviceName: ' + JSON.stringify(data.name));
});

```


## off('deviceDisconnect')

```TypeScript
function off(type: 'deviceDisconnect', callback?: Callback<string>): void
```

异步方法，取消监听设备断开状态，使用Callback形式返回连接的设备信息。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** off(type:

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-continuationManager-function off(type: 'deviceDisconnect', callback?: Callback<string>): void--><!--Device-continuationManager-function off(type: 'deviceDisconnect', callback?: Callback<string>): void-End-->

**系统能力：** SystemCapability.Ability.DistributedAbilityManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceDisconnect' | 是 | 取消监听的事件类型，固定值"deviceDisconnect"。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<string> | 否 | 当用户从设备选择模块中断开设备时调用，返回设备ID供开发者使用。 |

**示例：**

```TypeScript
import { continuationManager } from '@kit.AbilityKit';

continuationManager.off("deviceDisconnect", (data) => {
  console.info('onDeviceDisconnect deviceId: ' + JSON.stringify(data));
});

```

