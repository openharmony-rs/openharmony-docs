# setRemoteDeviceType（系统接口）

## 导入模块

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## setRemoteDeviceType

```TypeScript
function setRemoteDeviceType(deviceId: string, type: DeviceType): Promise<void>
```

设置蓝牙远端设备自定义类型，适用于蓝牙设置或设备管理应用中按设备类型（如汽车、耳机、助听器等）进行分类展示或差异化处理的场景。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 表示远端设备MAC地址，例如："XX:XX:XX:XX:XX:XX"。 |
| type | [DeviceType](arkts-connectivity-connection-devicetype-e-sys.md) | 是 | 表示设备类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 以Promise形式返回设置蓝牙远端设备类型的结果，设置失败时返回错误码信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// promise
try {
    connection.setRemoteDeviceType('11:22:33:44:55:66', connection.DeviceType.DEVICE_TYPE_HEADSET).then(() => {
        console.info('setRemoteDeviceType success');
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
