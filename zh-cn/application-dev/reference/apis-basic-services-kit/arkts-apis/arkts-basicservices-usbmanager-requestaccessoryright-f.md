# requestAccessoryRight

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';
```

## requestAccessoryRight

```TypeScript
function requestAccessoryRight(accessory: USBAccessory): Promise<boolean>
```

为指定应用申请访问USB配件的访问权限。使用Promise异步回调。 需要调用[usbManager.getAccessoryList](arkts-basicservices-usbmanager-getaccessorylist-f.md)获取配件列表，得到 [USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md)作为参数。

**起始版本：** 23

<!--Device-usbManager-function requestAccessoryRight(accessory: USBAccessory): Promise<boolean>--><!--Device-usbManager-function requestAccessoryRight(accessory: USBAccessory): Promise<boolean>-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accessory | [USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md) | 是 | USB配件，需要通过[getAccessoryList](arkts-basicservices-usbmanager-getaccessorylist-f.md)获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回应用访问配件权限的申请结果。返回true表示权限申请成功；返回false表示权限申请失败。 |

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
async function requestAccessoryRight() {
  try {
    let accList: usbManager.USBAccessory[] = usbManager.getAccessoryList();
    let flag = await usbManager.requestAccessoryRight(accList?.[0]);
    console.info(`requestAccessoryRight success, ret:${flag}`);
  } catch (error) {
    console.error(`requestAccessoryRight error ${error.code}, message is ${error.message}`);
  }
}
```

