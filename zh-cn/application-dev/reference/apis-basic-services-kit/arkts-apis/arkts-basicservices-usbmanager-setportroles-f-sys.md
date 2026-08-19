# setPortRoles（系统接口）

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';
```

## setPortRoles

```TypeScript
function setPortRoles(portId: number, powerRole: PowerRoleType, dataRole: DataRoleType): Promise<void>
```

设置指定端口当前的角色模式，包含电源角色、数据传输角色。使用Promise异步回调。调用成功后端口角色将切换为指定的角色。适用于系统应用需要动态切换USB端口角色的场景。开发者模式关闭时，如果没有设备接入，操作可能会失败，调用失败 时抛出异常。

**起始版本：** 9

**废弃版本：** 12

**替代接口：** [setPortRoleTypes](arkts-basicservices-usbmanager-setportroletypes-f-sys.md)(portId: int, powerRole: PowerRoleType, dataRole: DataRoleType)

<!--Device-usbManager-function setPortRoles(portId: number, powerRole: PowerRoleType, dataRole: DataRoleType): Promise<void>--><!--Device-usbManager-function setPortRoles(portId: number, powerRole: PowerRoleType, dataRole: DataRoleType): Promise<void>-End-->

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| portId | number | 是 | USB端口号，取值范围为非负整数，可通过[getPortList](arkts-basicservices-usbmanager-getportlist-f-sys.md)获取端口列表后得到。 |
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

