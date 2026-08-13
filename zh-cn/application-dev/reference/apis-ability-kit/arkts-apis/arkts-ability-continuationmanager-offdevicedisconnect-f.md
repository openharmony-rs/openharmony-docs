# off_deviceDisconnect

## off_deviceDisconnect

```TypeScript
function off(type: 'deviceDisconnect', callback?: Callback<string>): void
```

异步方法，取消监听设备断开状态，使用Callback形式返回连接的设备信息。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [off](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#off_deviceStateChange)(type: 'deviceStateChange', callback?: Callback&lt;{ action: DeviceStateChange; device: DeviceBasicInfo; }&gt;)

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-continuationManager-function off(type: 'deviceDisconnect', callback?: Callback<string>): void--><!--Device-continuationManager-function off(type: 'deviceDisconnect', callback?: Callback<string>): void-End-->

**系统能力：** SystemCapability.Ability.DistributedAbilityManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceDisconnect' | 是 | 取消监听的事件类型，固定值"deviceDisconnect"。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;string&gt; | 否 | 当用户从设备选择模块中断开设备时调用，返回设备ID供开发者使用。 |

## 示例

```TypeScript
import { continuationManager } from '@kit.AbilityKit';

continuationManager.off("deviceDisconnect", (data) => {
  console.info('onDeviceDisconnect deviceId: ' + JSON.stringify(data));
});
```

