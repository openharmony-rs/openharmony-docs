# getRemoteDeviceType（系统接口）

## 导入模块

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## getRemoteDeviceType

```TypeScript
function getRemoteDeviceType(deviceId: string): Promise<DeviceType>
```

获取通过setRemoteDeviceType设置的蓝牙远端设备自定义类型。使用Promise异步回调。从API version 18开始不再校验ohos.permission.ACCESS_BLUETOOTH权限。

**起始版本：** 12

**需要权限：** 
- API版本18+：N/A
- API版本12-17：ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 表示远端设备MAC地址，例如："XX:XX:XX:XX:XX:XX"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[DeviceType](arkts-connectivity-connection-devicetype-e-sys.md)&gt; | 以Promise形式返回获取蓝牙远端设备类型的结果，返回值为设备类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied.<br>**适用版本：** 12 - 17 |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs.<br>**适用版本：** 18+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// promise
try {
    connection.getRemoteDeviceType('11:22:33:44:55:66').then((data: connection.DeviceType) => {
        console.info('getRemoteDeviceType success, DeviceType:' + JSON.stringify(data));
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
