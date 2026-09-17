# notifyDialogResult（系统接口）

## 导入模块

```TypeScript
import { access } from '@kit.ConnectivityKit';
```

## notifyDialogResult

```TypeScript
function notifyDialogResult(notifyDialogResultParams: NotifyDialogResultParams): Promise<void>
```

将用户操作蓝牙对话框的行为通知给蓝牙服务。使用Promise异步回调。

与API version 20开始支持的[access.enableBluetoothAsync](arkts-connectivity-access-enablebluetoothasync-f.md)搭配使用，应用申请开启蓝牙，调用该接口会将用户操作开关蓝牙对话框的行为通知给蓝牙服务。与API version 20开始支持的[access.disableBluetoothAsync](arkts-connectivity-access-disablebluetoothasync-f.md)搭配使用，应用申请关闭蓝牙，调用该接口会将用户操作开关蓝牙对话框的行为通知给蓝牙服务。

**起始版本：** 20

**需要权限：** ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| notifyDialogResultParams | [NotifyDialogResultParams](arkts-connectivity-access-notifydialogresultparams-i-sys.md) | 是 | 用户操作对话框的行为。 |

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
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let notifyDialogResultParams: access.NotifyDialogResultParams = {
        "dialogType": 0,
        "dialogResult": true,
    };
    access.notifyDialogResult(notifyDialogResultParams);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
