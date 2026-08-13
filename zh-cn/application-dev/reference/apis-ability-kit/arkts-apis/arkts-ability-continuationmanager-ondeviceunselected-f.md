# on_deviceUnselected

## on_deviceUnselected

```TypeScript
function on(type: 'deviceUnselected', token: number, callback: Callback<Array<ContinuationResult>>): void
```

异步方法，监听设备断开状态，使用Callback形式返回断开的设备信息。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 22

**替代接口：** [on](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#on_deviceStateChange)(type: 'deviceStateChange', callback: Callback&lt;{ action: DeviceStateChange; device: DeviceBasicInfo; }&gt;)

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-continuationManager-function on(type: 'deviceUnselected', token: number, callback: Callback<Array<ContinuationResult>>): void--><!--Device-continuationManager-function on(type: 'deviceUnselected', token: number, callback: Callback<Array<ContinuationResult>>): void-End-->

**系统能力：** SystemCapability.Ability.DistributedAbilityManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceUnselected' | 是 | 监听的事件类型，固定值"deviceUnselected"。 |
| token | number | 是 | 注册后的token。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;Array&lt;ContinuationResult&gt;&gt; | 是 | 当用户从设备选择模块中断开设备时调用，返回设备ID、设备类型和设备名称供开发者使用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [16600004](../errorcode-DistributedSchedule.md#16600004-指定的callback已注册) | The specified callback has been registered. |
| [16600001](../errorcode-DistributedSchedule.md#16600001-系统服务工作异常) | The system ability works abnormally. |
| [16600002](../errorcode-DistributedSchedule.md#16600002-指定的token或callback未注册) | The specified token or callback is not registered. |

## 示例

```TypeScript
import { continuationManager } from '@kit.AbilityKit';

let token: number = 1;
try {
  continuationManager.on("deviceUnselected", token, (data) => {
    console.info('onDeviceUnselected len: ' + data.length);
    for (let i = 0; i < data.length; i++) {
      console.info('onDeviceUnselected deviceId: ' + JSON.stringify(data[i].id));
      console.info('onDeviceUnselected deviceType: ' + JSON.stringify(data[i].type));
      console.info('onDeviceUnselected deviceName: ' + JSON.stringify(data[i].name));
    }
    console.info('onDeviceUnselected finished.');
  });
} catch (err) {
  console.error('on failed, cause: ' + JSON.stringify(err));
}
```

