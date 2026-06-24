# getSupportedModes（系统接口）

## getSupportedModes

```TypeScript
function getSupportedModes(portId: number): PortModeType
```

获取指定的端口支持的模式列表的组合掩码。

**起始版本：** 9

**废弃版本：** 9

**替代接口：** [getSupportedModes](arkts-basicservices-usbmanager-getsupportedmodes-f-sys.md#getSupportedModes-1)

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

**示例：**

```TypeScript
let ret = usb.getSupportedModes(0);

```

