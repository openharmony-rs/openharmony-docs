# createHidDeviceProfile

## 导入模块

```TypeScript
import { hid } from '@kit.ConnectivityKit';
```

## createHidDeviceProfile

```TypeScript
function createHidDeviceProfile(): HidDeviceProfile
```

创建蓝牙HID Device实例。通过该实例可使用本端作为HID Device的接口，如：获取和其他设备间的蓝牙HID连接状态。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [HidDeviceProfile](arkts-connectivity-hid-hiddeviceprofile-i.md) | 返回HID Device实例。该类继承于[BaseProfile](arkts-connectivity-hid-baseprofile-t.md)，因此可以使用其父类中的方法。和该实例角色相对应的是HID Host角色。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

```TypeScript
try {
    let hidDeviceProfile = hid.createHidDeviceProfile();
    console.info('hidDevice success');
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```
