# updateConnectStatus

## updateConnectStatus

```TypeScript
function updateConnectStatus(
    token: number,
    deviceId: string,
    status: DeviceConnectState,
    callback: AsyncCallback<void>
  ): void
```

通知设备选择模块，更新当前的连接状态，使用AsyncCallback方式作为异步方法。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [@ohos.distributedDeviceManager:distributedDeviceManager.DeviceManager.getAvailableDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelistsync)

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-continuationManager-function updateConnectStatus(    token: number,    deviceId: string,    status: DeviceConnectState,    callback: AsyncCallback<void>  ): void--><!--Device-continuationManager-function updateConnectStatus(    token: number,    deviceId: string,    status: DeviceConnectState,    callback: AsyncCallback<void>  ): void-End-->

**系统能力：** SystemCapability.Ability.DistributedAbilityManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| token | number | 是 | 注册后的token。 |
| deviceId | string | 是 | 设备ID。 |
| status | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 设备连接状态。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当通知设备成功，err为undefined，否则返回错误对象。 |

**示例：**

```TypeScript
import { continuationManager } from '@kit.AbilityKit';

let token: number = -1;
let deviceId: string = "test deviceId";
continuationManager.updateConnectStatus(token, deviceId, continuationManager.DeviceConnectState.CONNECTED, (err) => {
  if (err.code != 0) {
    console.error('updateConnectStatus failed, cause: ' + JSON.stringify(err));
    return;
  }
  console.info('updateConnectStatus finished. ');
});
```


## updateConnectStatus

```TypeScript
function updateConnectStatus(token: number, deviceId: string, status: DeviceConnectState): Promise<void>
```

通知设备选择模块，更新当前的连接状态，使用Promise方式作为异步方法。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [@ohos.distributedDeviceManager:distributedDeviceManager.DeviceManager.getAvailableDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelistsync)

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-continuationManager-function updateConnectStatus(token: number, deviceId: string, status: DeviceConnectState): Promise<void>--><!--Device-continuationManager-function updateConnectStatus(token: number, deviceId: string, status: DeviceConnectState): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.DistributedAbilityManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| token | number | 是 | 注册后的token。 |
| deviceId | string | 是 | 设备ID。 |
| status | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 设备连接状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise形式返回接口调用结果。 |

**示例：**

```TypeScript
import { continuationManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let token: number = 1;
let deviceId: string = "test deviceId";
continuationManager.updateConnectStatus(token, deviceId, continuationManager.DeviceConnectState.CONNECTED)
  .then(() => {
    console.info('updateConnectStatus finished. ');
  })
  .catch((err: BusinessError) => {
    console.error('updateConnectStatus failed, cause: ' + JSON.stringify(err));
});
```

