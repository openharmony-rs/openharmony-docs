# off_deviceUnselected

## 导入模块

```TypeScript
import { continuationManager } from '@kit.AbilityKit';
```

## off('deviceUnselected')

```TypeScript
function off(type: 'deviceUnselected', token: number): void
```

取消监听设备断开状态。

**起始版本：** 9

**废弃版本：** 22

**替代接口：** [off](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#offdevicestatechange)(type: 'deviceStateChange', callback?: Callback&lt;{ action: DeviceStateChange; device: DeviceBasicInfo; }&gt;)

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [16600004](../errorcode-DistributedSchedule.md#16600004-指定的callback已注册) | The specified callback has been registered. |
| [16600001](../errorcode-DistributedSchedule.md#16600001-系统服务工作异常) | The system ability works abnormally. |
| [16600002](../errorcode-DistributedSchedule.md#16600002-指定的token或callback未注册) | The specified token or callback is not registered. |

**示例**

```TypeScript
import { continuationManager } from '@kit.AbilityKit';

let token: number = 1;
try {
  continuationManager.off("deviceUnselected", token);
} catch (err) {
  console.error('off failed, cause: ' + JSON.stringify(err));
}
```

