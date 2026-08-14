# setPortRoles（系统接口）

## setPortRoles

```TypeScript
function setPortRoles(portId: number, powerRole: PowerRoleType, dataRole: DataRoleType): Promise<void>
```

设置指定的端口支持的角色模式，包含充电角色、数据传输角色。使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

**替代接口：** [setPortRoleTypes](arkts-basicservices-usbmanager-setportroletypes-f-sys.md#setPortRoleTypes)(portId: int, powerRole: PowerRoleType, dataRole: DataRoleType)

<!--Device-usbManager-function setPortRoles(portId: number, powerRole: PowerRoleType, dataRole: DataRoleType): Promise<void>--><!--Device-usbManager-function setPortRoles(portId: number, powerRole: PowerRoleType, dataRole: DataRoleType): Promise<void>-End-->

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| portId | number | 是 | 端口号。 |
| powerRole | PowerRoleType | 是 | 充电的角色。 |
| dataRole | DataRoleType | 是 | 数据传输的角色。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  &lt;br&gt;1.Mandatory parameters are left unspecified.  &lt;br&gt;2.Incorrect parameter types. |

