# on_deviceConnect

## on_deviceConnect

```TypeScript
function on(type: 'deviceConnect', callback: Callback<ContinuationResult>): void
```

异步方法，监听设备连接状态，使用Callback形式返回连接的设备信息。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [on](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#on_deviceStateChange)(type: 'deviceStateChange', callback: Callback&lt;{ action: DeviceStateChange; device: DeviceBasicInfo; }&gt;)

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-continuationManager-function on(type: 'deviceConnect', callback: Callback<ContinuationResult>): void--><!--Device-continuationManager-function on(type: 'deviceConnect', callback: Callback<ContinuationResult>): void-End-->

**系统能力：** SystemCapability.Ability.DistributedAbilityManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceConnect' | 是 | 监听的事件类型，固定值"deviceConnect"。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;ContinuationResult&gt; | 是 | 当用户从设备选择模块中选择设备时调用，返回设备ID、设备类型和设备名称供开发者使用。 |

## 示例

```TypeScript
import { continuationManager } from '@kit.AbilityKit';

continuationManager.on("deviceConnect", (data) => {
  console.info('onDeviceConnect deviceId: ' + JSON.stringify(data.id));
  console.info('onDeviceConnect deviceType: ' + JSON.stringify(data.type));
  console.info('onDeviceConnect deviceName: ' + JSON.stringify(data.name));
});
```

