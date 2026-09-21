# off

## 导入模块

```TypeScript
import { access } from '@kit.ConnectivityKit';
```

## off('stateChange')

```TypeScript
function off(type: 'stateChange', callback?: Callback<BluetoothState>): void
```

取消订阅本端蓝牙开关状态变化事件。从API18开始不再校验ohos.permission.ACCESS_BLUETOOTH权限。

**起始版本：** 10

**需要权限：** 
- API版本18+：N/A
- API版本10-17：ohos.permission.ACCESS_BLUETOOTH

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'stateChange' | 是 | 事件回调类型，支持的事件为'stateChange'，表示蓝牙开关状态变化事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BluetoothState](arkts-connectivity-access-bluetoothstate-e.md)&gt; | 否 | 指定取消订阅的回调函数通知。若传参，则需与[access.on('stateChange')](arkts-connectivity-access-on-f.md#onstatechange)中的回调函数一致；若无传参，则取消订阅该type对应的所有回调函数通知。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied.<br>**适用版本：** 10 - 17 |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function onReceiveEvent(data: access.BluetoothState) {
    console.info('bluetooth state = '+ JSON.stringify(data));
}
try {
    access.on('stateChange', onReceiveEvent);
    access.off('stateChange', onReceiveEvent);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
