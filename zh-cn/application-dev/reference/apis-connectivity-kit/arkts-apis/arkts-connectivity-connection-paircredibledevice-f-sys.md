# pairCredibleDevice（系统接口）

## 导入模块

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## pairCredibleDevice

```TypeScript
function pairCredibleDevice(deviceId: string, transport: BluetoothTransport, callback: AsyncCallback<void>): void
```

向可信的远端设备发起蓝牙配对。通过非蓝牙扫描的方式（例如NFC等）获取到外设的地址，可以通过该接口发起配对。使用Callback异步回调。蓝牙配对状态通过on('bondStateChange')的回调结果获取。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 表示配对的远端设备地址，例如："XX:XX:XX:XX:XX:XX"。 |
| transport | [BluetoothTransport](arkts-connectivity-connection-bluetoothtransport-e.md) | 是 | 表示在配对远端设备时使用的传输方式。若明确使用传统蓝牙（BR/EDR）或者低功耗蓝牙（BLE）方式，则传入TRANSPORT_BR_EDR或TRANSPORT_LE。若不确定使用哪种传输方式，则传入TRANSPORT_DUAL&lt;sup&gt;20+&lt;/sup&gt;或TRANSPORT_UNKNOWN&lt;sup&gt;20+&lt;/sup&gt;，蓝牙子系统会决策传输方式。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当发起配对成功，err为undefined，否则为错误对象。 |

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
    connection.pairCredibleDevice('68:13:24:79:4C:8C', connection.BluetoothTransport
        .TRANSPORT_BR_EDR, (err: BusinessError) => {
        if (err) {
            console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
            return;
        }
        console.info('pairCredibleDevice, err: ' + JSON.stringify(err));
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


<a id="paircredibledevice-1"></a>

## pairCredibleDevice

```TypeScript
function pairCredibleDevice(deviceId: string, transport: BluetoothTransport): Promise<void>
```

向可信的远端设备发起蓝牙配对。通过非蓝牙扫描的方式（例如NFC等）获取到外设的地址，可以通过该接口发起配对。使用Promise异步回调。蓝牙配对状态通过on('bondStateChange')的回调结果获取。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 表示配对的远端设备地址，例如："XX:XX:XX:XX:XX:XX"。 |
| transport | [BluetoothTransport](arkts-connectivity-connection-bluetoothtransport-e.md) | 是 | 表示在配对远端设备时使用的传输方式。若明确使用传统蓝牙（BR/EDR）或者低功耗蓝牙（BLE）方式，则传入TRANSPORT_BR_EDR或TRANSPORT_LE。若不确定使用哪种传输方式，则传入TRANSPORT_DUAL&lt;sup&gt;20+&lt;/sup&gt;或TRANSPORT_UNKNOWN&lt;sup&gt;20+&lt;/sup&gt;，蓝牙子系统会决策传输方式。 |

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
    connection.pairCredibleDevice('68:13:24:79:4C:8C', 0).then(() => {
        console.info('PairCredibleDevice');
    }, (err: BusinessError) => {
        console.error('PairCredibleDevice:errCode' + err.code + ', errMessage: ' + err.message);
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
