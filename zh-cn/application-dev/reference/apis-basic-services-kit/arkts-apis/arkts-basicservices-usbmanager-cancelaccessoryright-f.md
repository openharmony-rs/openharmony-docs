# cancelAccessoryRight

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';
```

## cancelAccessoryRight

```TypeScript
function cancelAccessoryRight(accessory: USBAccessory): void
```

取消当前应用访问USB配件的权限。与requestAccessoryRight()方法配合使用，用于取消此前通过requestAccessoryRight()申请的配件访问权限。 需要调用[usbManager.getAccessoryList](arkts-basicservices-usbmanager-getaccessorylist-f.md)获取配件列表，得到 [USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md)作为参数。

**起始版本：** 23

<!--Device-usbManager-function cancelAccessoryRight(accessory: USBAccessory): void--><!--Device-usbManager-function cancelAccessoryRight(accessory: USBAccessory): void-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accessory | [USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md) | 是 | USB配件，需要通过[getAccessoryList](arkts-basicservices-usbmanager-getaccessorylist-f.md)获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  <br>1. Mandatory parameters are left unspecified.  <br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |
| [14401001](../errorcode-usb.md#14401001-目标usb配件未匹配) | The target USBAccessory not matched. |
| [14400005](../errorcode-usb.md#14400005-数据库操作异常) | Database operation exception. |
| [14400004](../errorcode-usb.md#14400004-服务异常) | Service exception. Possible causes:  <br>1. No accessory is plugged in. |

**示例**

```TypeScript
async function cancelAccessoryRight() {
  try {
    let accList: usbManager.USBAccessory[] = usbManager.getAccessoryList();
    let flag = await usbManager.requestAccessoryRight(accList?.[0]);
    if (!flag) {
      return;
    }
    usbManager.cancelAccessoryRight(accList?.[0]);
    console.info(`cancelAccessoryRight success`);
  } catch (error) {
    console.error(`cancelAccessoryRight error ${error.code}, message is ${error.message}`);
  }
}
```

