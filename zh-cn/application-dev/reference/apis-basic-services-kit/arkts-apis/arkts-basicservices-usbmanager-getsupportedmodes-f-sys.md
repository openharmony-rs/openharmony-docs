# getSupportedModes（系统接口）

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';
```

## getSupportedModes

```TypeScript
function getSupportedModes(portId: number): PortModeType
```

获取指定的端口支持的模式列表的组合掩码。适用于系统应用需要查询USB-C端口能力判断是否支持特定模式（如UFP、DFP或DRP模式）的场景。返回值为PortModeType的组合掩码，可通过位运算判断端口是否支持特定模式。 PortModeType包括：NONE（0，无模式）、UFP（1，上行端口模式，dataRole为DEVICE）、DFP（2，下行端口模式，dataRole为HOST）、DRP（3，双角色模式，可在UFP和DFP间切换）、 NUM_MODES（4，当前不支持）。开发者可根据返回值判断端口是否支持所需的电源角色和数据传输角色组合。

**起始版本：** 9

**废弃版本：** 12

**替代接口：** [getPortSupportModes](arkts-basicservices-usbmanager-getportsupportmodes-f-sys.md)(portId: int)

<!--Device-usbManager-function getSupportedModes(portId: number): PortModeType--><!--Device-usbManager-function getSupportedModes(portId: number): PortModeType-End-->

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| portId | number | 是 | USB端口号，取值范围为非负整数，可通过[getPortList](arkts-basicservices-usbmanager-getportlist-f-sys.md)获取端口列表后得到。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PortModeType | 支持的模式列表的组合掩码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  <br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |

