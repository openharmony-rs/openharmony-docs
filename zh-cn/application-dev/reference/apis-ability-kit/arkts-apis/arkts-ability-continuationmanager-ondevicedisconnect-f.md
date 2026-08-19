# on_deviceDisconnect

## 导入模块

```TypeScript
import { continuationManager } from '@kit.AbilityKit';
```

## on('deviceDisconnect')

```TypeScript
function on(type: 'deviceDisconnect', callback: Callback<string>): void
```

异步方法，监听设备断开状态，使用Callback形式返回断开的设备信息。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [on](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#ondevicestatechange)(type: 'deviceStateChange', callback: Callback&lt;{ action: DeviceStateChange; device: DeviceBasicInfo; }&gt;)

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-continuationManager-function on(type: 'deviceDisconnect', callback: Callback<string>): void--><!--Device-continuationManager-function on(type: 'deviceDisconnect', callback: Callback<string>): void-End-->

**系统能力：** SystemCapability.Ability.DistributedAbilityManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceDisconnect' | 是 | 监听的事件类型，固定值"deviceDisconnect"。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;string&gt; | 是 | 当用户从设备选择模块中断开设备时调用，返回设备ID供开发者使用。 |

**示例**

```TypeScript
import { continuationManager } from '@kit.AbilityKit';

continuationManager.on("deviceDisconnect", (data) => {
  console.info('onDeviceDisconnect deviceId: ' + JSON.stringify(data));
});
```

