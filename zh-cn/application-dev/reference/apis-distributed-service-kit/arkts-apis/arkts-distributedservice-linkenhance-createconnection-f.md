# createConnection

## 导入模块

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
```

## createConnection

```TypeScript
function createConnection(deviceId: string, name: string): Connection
```

作为客户端的设备创建连接对象。创建Connection对象后，订阅on('connectResult')，然后调用connect()方法向服务端设备发起连接，连接成功后，可通过sendData()发送数据，当连接不需要使用，可调用close()销毁连接对象释放资源。

**起始版本：** 20

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 连接的对端设备的deviceId，即对端设备的BLE MAC地址。BLE MAC的获取方法，请参考[查找设备](../../../connectivity/bluetooth/ble-development-guide.md)。 |
| name | string | 是 | 连接的目标设备的服务名，非空字符串，最大长度255字节。超出长度限制或传入空字符串时返回错误码32390206。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Connection](arkts-distributedservice-linkenhance-connection-i.md) | 创建成功的连接对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the linkEnhance function has been trimmed.<br>**适用版本：** 26.0.0+ |
| [32390206](../errorcode-link-enhance.md#32390206-参数非法) | Invalid parameter. |

**示例**

在客户端设备上，应用需要主动调用createConnection()接口创建连接对象。

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "testDemo";

try {
  let peerDeviceId: string = "00:11:22:33:44:55"; // BLE MAC地址，需通过蓝牙扫描获取，详见参数说明
  hilog.info(0x0000, TAG, 'connection server deviceId = ' + peerDeviceId);
  let connection: linkEnhance.Connection = linkEnhance.createConnection(peerDeviceId, "demo");
} catch (err) {
  hilog.error(0x0000, TAG, 'errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}
```
