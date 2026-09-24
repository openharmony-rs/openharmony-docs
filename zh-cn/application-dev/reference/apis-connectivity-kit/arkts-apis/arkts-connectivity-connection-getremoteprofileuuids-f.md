# getRemoteProfileUuids

## 导入模块

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## getRemoteProfileUuids

```TypeScript
function getRemoteProfileUuids(deviceId: string, callback: AsyncCallback<Array<ProfileUuids>>): void
```

获取对端蓝牙设备的Profile协议能力，通过UUID区分。使用Callback异步回调。

建议仅对已配对的设备调用该方法。从API version 21开始，此接口支持使用对端设备的实际MAC地址获取Profile协议能力。

**起始版本：** 12

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 表示对端设备地址，例如："XX:XX:XX:XX:XX:XX"。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[ProfileUuids](arkts-connectivity-connection-profileuuids-t.md)&gt;&gt; | 是 | 回调函数。当获取UUID成功，err为undefined，获取到的是Profile协议能力集合；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Non-system applications are not allowed to use system APIs.<br>**适用版本：** 10 - 11 |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Invalid parameter. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
    connection.getRemoteProfileUuids('XX:XX:XX:XX:XX:XX', (err: BusinessError, data: Array<connection.ProfileUuids>) => {
        console.info('getRemoteProfileUuids, err: ' + JSON.stringify(err) + ', data: ' + JSON.stringify(data));
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


<a id="getremoteprofileuuids-1"></a>

## getRemoteProfileUuids

```TypeScript
function getRemoteProfileUuids(deviceId: string): Promise<Array<ProfileUuids>>
```

获取对端蓝牙设备的Profile协议能力，通过UUID区分。使用Promise异步回调。

建议仅对已配对的设备调用该方法。从API version 21开始，此接口支持使用对端设备的实际MAC地址获取Profile协议能力。

**起始版本：** 12

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 表示对端设备地址，例如："XX:XX:XX:XX:XX:XX"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[ProfileUuids](arkts-connectivity-connection-profileuuids-t.md)&gt;&gt; | Promise对象，返回支持的Profile协议能力集合。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Non-system applications are not allowed to use system APIs.<br>**适用版本：** 10 - 11 |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Invalid parameter. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
    connection.getRemoteProfileUuids('XX:XX:XX:XX:XX:XX').then(() => {
        console.info('getRemoteProfileUuids');
    }, (err: BusinessError) => {
        console.error('getRemoteProfileUuids: errCode' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
