# getPortList（系统接口）

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';
```

## getPortList

```TypeScript
function getPortList(): Array<USBPort>
```

获取所有物理USB端口描述信息。适用于需要枚举USB端口、进行端口管理、设备连接诊断、或查询端口配置信息的场景。开发者模式关闭时，如果没有设备接入，接口返回`undefined`，注意需要对接口返回值做判空处理。

**起始版本：** 23

**需要权限：** ohos.permission.MANAGE_USB_CONFIG

<!--Device-usbManager-function getPortList(): Array<USBPort>--><!--Device-usbManager-function getPortList(): Array<USBPort>-End-->

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;USBPort&gt; | USB端口描述信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API.<br>**适用版本：** 18+ |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied. Normal application do not have permission to use system api. |
| [14400004](../errorcode-usb.md#14400004-服务异常) |  |

