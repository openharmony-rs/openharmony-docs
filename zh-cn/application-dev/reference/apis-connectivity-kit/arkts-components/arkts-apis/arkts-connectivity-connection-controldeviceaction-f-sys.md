# controlDeviceAction（系统接口）

## 导入模块

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## controlDeviceAction

```TypeScript
function controlDeviceAction(controlDeviceActionParams: ControlDeviceActionParams): Promise<void>
```

查找蓝牙耳机设备时，向耳机发送控制命令。使用Promise异步回调。

**起始版本：** 15

**需要权限：** ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| controlDeviceActionParams | [ControlDeviceActionParams](arkts-connectivity-connection-controldeviceactionparams-i-sys.md) | 是 | 控制蓝牙外设的相关信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let controlDeviceActionParams: connection.ControlDeviceActionParams = {
        deviceId: '40:DC:A5:E5:75:C3',
        type: connection.ControlType.PLAY,
        typeValue: connection.ControlTypeValue.ENABLE,
        controlObject: connection.ControlObject.LEFT_EAR
    };
    connection.controlDeviceAction(controlDeviceActionParams).then(() => {
        console.info('controlDeviceAction success');
    }, (err: BusinessError) => {
        console.error('controlDeviceAction: errCode' + err.code + ', errMessage: ' + err.message);
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
