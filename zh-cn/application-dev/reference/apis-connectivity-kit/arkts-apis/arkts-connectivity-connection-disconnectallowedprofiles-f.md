# disconnectAllowedProfiles

## 导入模块

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

<a id="disconnectallowedprofiles-1"></a>

## disconnectAllowedProfiles

```TypeScript
function disconnectAllowedProfiles(deviceId: string): Promise<void>
```

断开对端设备支持的Profile（只包括A2DP和HFP）。

需要与接口[connection.connectAllowedProfiles](arkts-connectivity-connection-connectallowedprofiles-f.md)配合使用。

**起始版本：** 26.0.0

**需要权限：** 
- API版本26+：ohos.permission.ACCESS_BLUETOOTH
- API版本25：N/A
- API版本11-24：ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 表示需要断开连接的对端设备MAC地址，例如："XX:XX:XX:XX:XX:XX"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Non-system applications are not allowed to use system APIs.<br>**适用版本：** 11 - 24 |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.<br>**适用版本：** 11 - 24 |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Failed to call the API when the short-range chip is not inserted on 2in1 device. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
try {
  await connection.disconnectAllowedProfiles('68:13:24:79:4C:8C');
} catch (err) {
  console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
    connection.disconnectAllowedProfiles('68:13:24:79:4C:8C').then(() => {
        console.info('disconnectAllowedProfiles');
    }, (err: BusinessError) => {
        console.error('disconnectAllowedProfiles:errCode' + err.code + ', errMessage: ' + err.message);
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
