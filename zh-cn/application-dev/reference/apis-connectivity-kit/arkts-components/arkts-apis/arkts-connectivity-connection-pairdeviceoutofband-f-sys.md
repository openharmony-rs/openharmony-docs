# pairDeviceOutOfBand（系统接口）

## 导入模块

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## pairDeviceOutOfBand

```TypeScript
function pairDeviceOutOfBand(transport: BluetoothTransport, p192Data: OobData | null,
    p256Data: OobData | null): Promise<void>
```

通过带外（Out of Band, OOB）通信机制发起与对端蓝牙设备的配对流程。本接口所需的OobData可通过[generateLocalOobData](arkts-connectivity-connection-generatelocaloobdata-f-sys.md)生成本机OOB数据并经带外通道传输至本端后使用。使用Promise异步回调。

蓝牙配对状态通过[on('bondStateChange')](arkts-connectivity-connection-on-f.md#onbondstatechange)的回调结果获取。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| transport | [BluetoothTransport](arkts-connectivity-connection-bluetoothtransport-e.md) | 是 | 表示在配对对端设备时使用的传输方式。若使用传统蓝牙（BR/EDR），则传入TRANSPORT_BR_EDR。若使用低功耗蓝牙（BLE），则传入TRANSPORT_LE。不支持其他[BluetoothTransport](arkts-connectivity-connection-bluetoothtransport-e.md)类型。 |
| p192Data | [OobData](arkts-connectivity-connection-oobdata-i-sys.md) &#124; null | 是 | 配对过程中使用的OOB数据。P-192指一种椭圆曲线算法，其密钥长度为192位，在蓝牙4.1及以前的传统配对方案中广泛使用。若不使用该值，需传入null。p192Data与p256Data需至少传入一个有效值，若两者同时传入，则p256Data生效，p192Data不生效。 |
| p256Data | [OobData](arkts-connectivity-connection-oobdata-i-sys.md) &#124; null | 是 | 配对过程中使用的OOB数据。P-256指一种椭圆曲线算法，其密钥长度为256位，自蓝牙4.2开始成为安全连接的核心基础。基于P-256的OOB数据相比基于P -192的OOB数据具有更强的抗攻击能力与保密性。若非必须兼容蓝牙4.1或更早版本的旧设备，推荐使用p256Data。若不使用该值，需传入null。p192Data与p256Data需至少传入一个有效值，若两者同时传入，则p256Data生效，p192Data不生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

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
import { common } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let transport: connection.BluetoothTransport = connection.BluetoothTransport.TRANSPORT_LE;
    let addressInfo: common.BluetoothAddress = {
        "address": "11:22:33:44:55:66",
        "addressType": common.BluetoothAddressType.REAL, // 必须为实际MAC地址类型
        "rawAddressType": common.BluetoothRawAddressType.RANDOM
    };
    let confirmHash: Uint8Array = new Uint8Array([0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x0A, 0x0B, 0x0C, 0x0D, 0x0E, 0x0F, 0x10]);
    let randomHash: Uint8Array = new Uint8Array([0x11, 0x22, 0x33, 0x44, 0x55, 0x66, 0x77, 0x88, 0x99, 0xAA, 0xBB, 0xCC, 0xDD, 0xEE, 0xFF, 0x11]);
    let oobData: connection.OobData = {
        "deviceId": addressInfo,
        "confirmationHash": confirmHash,
        "randomizerHash": randomHash,
        "deviceName": "testName",
        "deviceRole": connection.DeviceRole.DEVICE_ROLE_PERIPHERAL_ONLY
    }
    connection.pairDeviceOutOfBand(transport, null, oobData).then(() => {
        console.info('pairDeviceOufOfBand');
    }, (err: BusinessError) => {
        console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
    });
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```
