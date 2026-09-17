# createHidHostProfile

## 导入模块

```TypeScript
import { hid } from '@kit.ConnectivityKit';
```

## createHidHostProfile

```TypeScript
function createHidHostProfile(): HidHostProfile
```

创建蓝牙HID Host实例。通过该实例可使用本端作为HID Host的接口，如：获取和其他设备间的蓝牙HID连接状态。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [HidHostProfile](arkts-connectivity-bluetoothmanager-hidhostprofile-i.md) | 返回HID Host实例。该类继承于[BaseProfile](arkts-connectivity-hid-baseprofile-t.md)，因此可以使用其父类中的方法。和该实例角色相对应的是HID Device角色。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

```TypeScript
try {
    let hidHostProfile = hid.createHidHostProfile();
    console.info('hidHost success');
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```
