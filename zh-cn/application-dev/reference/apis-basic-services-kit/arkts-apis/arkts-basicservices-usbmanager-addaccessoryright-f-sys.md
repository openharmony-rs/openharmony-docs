# addAccessoryRight（系统接口）

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';
```

## addAccessoryRight

```TypeScript
function addAccessoryRight(tokenId: int, accessory: USBAccessory): void
```

为应用添加访问USB配件权限。适用于系统应用需要为第三方应用授权访问USB配件的场景。usbManager.requestAccessoryRight会触发弹窗请求用户授权；addAccessoryRight不会触发弹窗，而是直接 添加应用访问USB配件的权限。授权立即生效并持久化存储，设备重启后仍然有效。授权范围为指定的USB配件实例，多个应用可以同时获得同一配件的访问权限。与requestAccessoryRight相比， addAccessoryRight不需要用户交互，适用于系统应用自动授权场景。

**起始版本：** 23

**需要权限：** ohos.permission.MANAGE_USB_CONFIG

<!--Device-usbManager-function addAccessoryRight(tokenId: int, accessory: USBAccessory): void--><!--Device-usbManager-function addAccessoryRight(tokenId: int, accessory: USBAccessory): void-End-->

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenId | int | 是 | 应用程序的唯一标识符，可通过 [bundleManager.getBundleInfoForSelf](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfoforself-f.md)获取。 |
| accessory | [USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md) | 是 | USB配件对象，包含配件的标识和属性信息。可通过[getAccessoryList](arkts-basicservices-usbmanager-getaccessorylist-f.md)获取 配件列表后获得。详细字段定义参见[USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md)接口。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  <br>1. Mandatory parameters are left unspecified.  <br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permission check failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied. Normal application do not have permission to use system api. |
| [14400005](../errorcode-usb.md#14400005-数据库操作异常) | Database operation exception. |
| [14400004](../errorcode-usb.md#14400004-服务异常) | Service exception. Possible causes:  <br>1. No accessory is plugged in. |

