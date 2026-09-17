# generateLocalOobData（系统接口）

## 导入模块

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## generateLocalOobData

```TypeScript
function generateLocalOobData(transport: BluetoothTransport): Promise<OobData>
```

获取本机的带外（Out of Band, OOB）通信数据。生成的OOB数据经带外通道传输至对端设备后，对端设备可通过[pairDeviceOutOfBand](arkts-connectivity-connection-pairdeviceoutofband-f-sys.md)使用该数据发起配对流程。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| transport | [BluetoothTransport](arkts-connectivity-connection-bluetoothtransport-e.md) | 是 | 表示在配对对端设备时使用的传输方式。若使用传统蓝牙（BR/EDR），则传入TRANSPORT_BR_EDR。若使用低功耗蓝牙（BLE），则传入TRANSPORT_LE。不支持其他[BluetoothTransport](arkts-connectivity-connection-bluetoothtransport-e.md)类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[OobData](arkts-connectivity-connection-oobdata-i-sys.md)&gt; | Promise对象，返回本机的OOB数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let transport: connection.BluetoothTransport = connection.BluetoothTransport.TRANSPORT_LE;
    connection.generateLocalOobData(transport).then((oobData: connection.OobData) => {
        console.info(`generateLocalOobData: ${JSON.stringify(oobData)}`);
    }, (err: BusinessError) => {
        console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
    });
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```
