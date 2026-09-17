# GattClientDevice

GATT客户端类，提供了和服务端进行连接和数据传输等操作方法。

使用该类的方法前，需通过[createGattClientDevice](arkts-connectivity-ble-creategattclientdevice-f.md)方法构造该类的实例。通过创建不同的该类实例，可以管理多路GATT连接。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## writeCharacteristicValueWithContext

```TypeScript
writeCharacteristicValueWithContext(
      characteristic: BLECharacteristic, writeType: GattWriteType): Promise<GattRspContext>
```

client端向指定的server端特征值写入数据，适用于需要获取server端写入响应信息的应用场景（如设备配置指令下发、健康数据同步等）。使用Promise异步回调。

与writeCharacteristicValue接口不同，此接口新增了返回server端响应信息的功能。在完成特征值写入操作后，调用方可以获取本端接收到server端回复消息的时间戳等信息。为获取server端的响应信息，此接口仅支持writeType为[WRITE](arkts-connectivity-ble-gattwritetype-e.md)的写入模式。需要先调用[getServices](arkts-connectivity-ble-gattclientdevice-i.md#getservices)，获取到server端所有支持的能力，且这些能力中需包含指定的入参特征值UUID；否则会写入失败。异步回调结果返回后，才能调用下一次读取或者写入操作，如readCharacteristicValue、[readDescriptorValue](arkts-connectivity-ble-gattclientdevice-i.md#readdescriptorvalue)、writeCharacteristicValue、[writeDescriptorValue](arkts-connectivity-ble-gattclientdevice-i.md#writedescriptorvalue)、setCharacteristicChangeNotification和setCharacteristicChangeIndication。应用单次可写入的特征值数据长度限制为（MTU-3）字节。调用方可根据实际需要通过[setBLEMtuSize](arkts-connectivity-ble-gattclientdevice-i.md#setblemtusize)接口指定MTU大小，进而修改单次可写入的特征值数据长度。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| characteristic | [BLECharacteristic](arkts-connectivity-ble-blecharacteristic-i.md) | 是 | 需要写入的特征值，包含写入的数据内容。单次可写入的数据长度限制为（MTU-3）字节，可通过setBLEMtuSize接口调整。 |
| writeType | [GattWriteType](arkts-connectivity-ble-gattwritetype-e.md) | 是 | 写入特征值的方式，当前仅支持WRITE类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[GattRspContext](arkts-connectivity-ble-gattrspcontext-i-sys.md)&gt; | Promise对象，返回GattRspContext对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900011](../errorcode-bluetoothManager.md#2900011-操作频繁) | The operation is busy. The last operation is not complete. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
| [2901001](../errorcode-bluetoothManager.md#2901001-禁止写操作) | Write forbidden. |
| [2901003](../errorcode-bluetoothManager.md#2901003-gatt未连接) | The connection is not established. |
| [2901004](../errorcode-bluetoothManager.md#2901004-gatt传输拥塞) | The connection is congested. |
| [2901005](../errorcode-bluetoothManager.md#2901005-gatt未加密) | The connection is not encrypted. |
| [2901006](../errorcode-bluetoothManager.md#2901006-gatt未认证) | The connection is not authenticated. |
| [2901007](../errorcode-bluetoothManager.md#2901007-gatt未授权) | The connection is not authorized. |

**示例**

```TypeScript
let descriptors: Array<ble.BLEDescriptor>  = [];
let bufferDesc = new ArrayBuffer(2);
let descV = new Uint8Array(bufferDesc);
descV[0] = 0; // 以Client Characteristic Configuration描述符为例，表示bit0、bit1均为0，notification和indication均不开启
let descriptor: ble.BLEDescriptor = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
  characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
  descriptorUuid: '00002902-0000-1000-8000-00805F9B34FB', descriptorValue: bufferDesc};
descriptors[0] = descriptor;

let bufferCCC = new ArrayBuffer(8);
let cccV = new Uint8Array(bufferCCC);
cccV[0] = 1;
let characteristic: ble.BLECharacteristic = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
  characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
  characteristicValue: bufferCCC, descriptors:descriptors};
try {
    let device: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
    device.writeCharacteristicValueWithContext(characteristic, ble.GattWriteType.WRITE).then((rspContext: ble.GattRspContext) => {
        console.info('timestamp is: ' + rspContext.timestamp);
    });
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```
