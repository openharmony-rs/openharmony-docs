# connectAllowedProfiles

## 导入模块

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## connectAllowedProfiles

```TypeScript
function connectAllowedProfiles(deviceId: string, callback: AsyncCallback<void>): void
```

连接对端设备支持的Profile（只包括A2DP、HFP和HID）。使用Callback异步回调。

API版本26.0.0之前，需先调用[connection.pairDevice](arkts-connectivity-connection-pairdevice-f.md)发起配对，且仅允许在每次发起配对后30秒内调用此接口一次。从API版本26.0.0开始，针对A2DP和HFP，调用接口无时间限制，可以在调用[connection.pairDevice](arkts-connectivity-connection-pairdevice-f.md)发起配对后任意时间内进行调用。针对HID，仍需在每次发起配对后30秒内调用此接口。当配对成功后，建议先调用[getRemoteProfileUuids](arkts-connectivity-connection-getremoteprofileuuids-f.md)主动查询目标设备支持的Profile能力。若存在应用需要的能力，才调用此接口。需要与接口[connection.disconnectAllowedProfiles](arkts-connectivity-connection-disconnectallowedprofiles-f.md)配合使用。从API version 21开始，此接口支持使用对端设备的实际MAC地址进行Profile连接。

**起始版本：** 16

**需要权限：** 
- API版本16+：ohos.permission.ACCESS_BLUETOOTH
- API版本11-15：ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 表示需要连接的对端设备MAC地址，例如："XX:XX:XX:XX:XX:XX"。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当发起连接成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs.<br>**适用版本：** 11 - 15 |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
  connection.connectAllowedProfiles('68:13:24:79:4C:8C', (err: BusinessError) => {
    if (err) {
      console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
      return;
    }
    console.info('connectAllowedProfiles');
  });
} catch (err) {
  console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
  connection.connectAllowedProfiles('68:13:24:79:4C:8C').then(() => {
      console.info('connectAllowedProfiles');
    }, (err: BusinessError) => {
      console.error('connectAllowedProfiles:errCode' + err.code + ', errMessage: ' + err.message);
  });
} catch (err) {
  console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## connectAllowedProfiles

```TypeScript
function connectAllowedProfiles(deviceId: string): Promise<void>
```

连接对端设备支持的Profile（只包括A2DP、HFP和HID）。使用Promise异步回调。

API版本26.0.0之前，需先调用[connection.pairDevice](arkts-connectivity-connection-pairdevice-f.md)发起配对，且仅允许在每次发起配对后30秒内调用此接口一次。从API版本26.0.0开始，针对A2DP和HFP，调用接口无时间限制，可以在调用[connection.pairDevice](arkts-connectivity-connection-pairdevice-f.md)发起配对后任意时间内进行调用。针对HID，仍需在每次发起配对后30秒内调用此接口。当配对成功后，建议先调用[getRemoteProfileUuids](arkts-connectivity-connection-getremoteprofileuuids-f.md)主动查询目标设备支持的Profile能力。若存在应用需要的能力，才调用此接口。需要与接口[connection.disconnectAllowedProfiles](arkts-connectivity-connection-disconnectallowedprofiles-f.md)配合使用。从API version 21开始，此接口支持使用对端设备的实际MAC地址进行Profile连接。

**起始版本：** 16

**需要权限：** 
- API版本16+：ohos.permission.ACCESS_BLUETOOTH
- API版本11-15：ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 表示需要连接的对端设备MAC地址，例如："XX:XX:XX:XX:XX:XX"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs.<br>**适用版本：** 11 - 15 |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

参见 [connectAllowedProfiles](#connectallowedprofiles)
