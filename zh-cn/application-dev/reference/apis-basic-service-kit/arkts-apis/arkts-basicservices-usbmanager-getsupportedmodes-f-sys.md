# getSupportedModes（系统接口）

## getSupportedModes

```TypeScript
function getSupportedModes(portId: number): PortModeType
```

获取指定的端口支持的模式列表的组合掩码。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

**替代接口：** [getPortSupportModes](arkts-basicservices-usbmanager-getportsupportmodes-f-sys.md#getPortSupportModes)(portId: int)

<!--Device-usbManager-function getSupportedModes(portId: number): PortModeType--><!--Device-usbManager-function getSupportedModes(portId: number): PortModeType-End-->

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| portId | number | 是 | 端口号。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PortModeType | 支持的模式列表的组合掩码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  &lt;br&gt;1.Mandatory parameters are left unspecified.  &lt;br&gt;2.Incorrect parameter types. |

