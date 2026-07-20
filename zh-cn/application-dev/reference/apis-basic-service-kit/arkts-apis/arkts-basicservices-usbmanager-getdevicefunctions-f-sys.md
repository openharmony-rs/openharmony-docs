# getDeviceFunctions（系统接口）

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

<a id="getdevicefunctions"></a>
## getDeviceFunctions

```TypeScript
function getDeviceFunctions(): FunctionType
```

在设备模式下，获取当前的USB功能列表的数字组合掩码。开发者模式关闭时，如果没有设备接入，接口可能返回`undefined`，注意需要对接口返回值做判空处理。

**起始版本：** 12

**需要权限：** ohos.permission.MANAGE_USB_CONFIG

<!--Device-usbManager-function getDeviceFunctions(): FunctionType--><!--Device-usbManager-function getDeviceFunctions(): FunctionType-End-->

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FunctionType](arkts-basicservices-usb-functiontype-e-sys.md) | 当前的USB功能列表的数字组合掩码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API.<br>**适用版本：** 18+ |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied. Normal application do not have permission to use system api. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

