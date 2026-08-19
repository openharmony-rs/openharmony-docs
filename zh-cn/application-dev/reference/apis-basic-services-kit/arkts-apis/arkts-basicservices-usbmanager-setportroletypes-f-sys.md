# setPortRoleTypes（系统接口）

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';
```

## setPortRoleTypes

```TypeScript
function setPortRoleTypes(portId: int, powerRole: PowerRoleType, dataRole: DataRoleType): Promise<void>
```

设置指定端口当前的角色类型，包含电源角色、数据传输角色。使用Promise异步回调。调用成功后端口的电源角色和数据传输角色将切换为指定的角色。适用于系统应用需要动态切换USB端口角色的场景。开发者模式关闭时，如果没有设备接入，操作 可能会失败，调用失败时抛出异常。角色约束详情参见[USBPortStatus](arkts-basicservices-usbmanager-usbportstatus-i-sys.md)。 **使用建议：** - 建议先调用getPortList获取端口列表，得到有效的portId - 建议调用[getPortSupportModes](arkts-basicservices-usbmanager-getportsupportmodes-f-sys.md)查询端口支持的模式，确保设置的角色配置在支持范围内 - 如果设置的角色不被端口支持，调用会失败并返回错误码14400003

**起始版本：** 23

**需要权限：** ohos.permission.MANAGE_USB_CONFIG

<!--Device-usbManager-function setPortRoleTypes(portId: int, powerRole: PowerRoleType, dataRole: DataRoleType): Promise<void>--><!--Device-usbManager-function setPortRoleTypes(portId: int, powerRole: PowerRoleType, dataRole: DataRoleType): Promise<void>-End-->

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| portId | int | 是 | 端口号，可通过[getPortList](arkts-basicservices-usbmanager-getportlist-f-sys.md)获取端口列表后得到。 |
| powerRole | PowerRoleType | 是 | 电源角色类型，可选值包括：NONE（无）、SOURCE（对外提供电源）、SINK（需要外部供电）。 |
| dataRole | DataRoleType | 是 | 数据传输角色类型，可选值包括：NONE（无）、HOST（主机角色）、DEVICE（设备角色）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。调用成功时无返回值，调用失败时抛出异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  <br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |
| [14400003](../errorcode-usb.md#14400003-不支持的端口角色切换) | Unsupported operation. The current device does not support port role switching. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API.<br>**适用版本：** 18+ |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied. Normal application do not have permission to use system api. |

