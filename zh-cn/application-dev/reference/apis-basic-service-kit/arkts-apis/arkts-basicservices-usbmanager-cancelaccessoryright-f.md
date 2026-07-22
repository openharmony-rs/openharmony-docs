# cancelAccessoryRight

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## cancelAccessoryRight

```TypeScript
function cancelAccessoryRight(accessory: USBAccessory): void
```

取消当前应用程序访问USB配件的权限。需要调用[usbManager.getAccessoryList](arkts-basicservices-usbmanager-getaccessorylist-f.md#getaccessorylist)获取配件列表，得到[USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md)作为参数。

**起始版本：** 14

<!--Device-usbManager-function cancelAccessoryRight(accessory: USBAccessory): void--><!--Device-usbManager-function cancelAccessoryRight(accessory: USBAccessory): void-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accessory | [USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md) | 是 | USB配件，需要通过[getAccessoryList](arkts-basicservices-usbmanager-getaccessorylist-f.md#getaccessorylist)获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:* <br>1. Mandatory parameters are left unspecified.* <br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |
| [14401001](../../apis-basic-services-kit/errorcode-usb.md#14401001-目标usb配件未匹配) | The target USBAccessory not matched. |
| [14400004](../../apis-basic-services-kit/errorcode-usb.md#14400004-服务异常) | Service exception. Possible causes:* <br>1. No accessory is plugged in. |
| [14400005](../../apis-basic-services-kit/errorcode-usb.md#14400005-数据库操作异常) | Database operation exception. |

**示例：**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
try {
  let accList: usbManager.USBAccessory[] = usbManager.getAccessoryList()
  let flag = usbManager.requestAccessoryRight(accList?.[0])
  if (!flag) {
    return
  }
  usbManager.cancelAccessoryRight(accList?.[0])
  hilog.info(0, 'testTag ui', `cancelAccessoryRight success`)
} catch (error) {
  hilog.error(0, 'testTag ui', `cancelAccessoryRight error ${error.code}, message is ${error.message}`)
}

```

