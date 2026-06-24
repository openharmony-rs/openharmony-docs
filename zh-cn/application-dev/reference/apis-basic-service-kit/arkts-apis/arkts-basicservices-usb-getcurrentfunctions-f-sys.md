# getCurrentFunctions（系统接口）

## getCurrentFunctions

```TypeScript
function getCurrentFunctions(): FunctionType
```

在设备模式下，获取当前的USB功能列表的数字组合掩码。

**起始版本：** 9

**废弃版本：** 9

**替代接口：** [getCurrentFunctions](arkts-basicservices-usbmanager-getcurrentfunctions-f-sys.md#getCurrentFunctions-1)

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| FunctionType | 当前的USB功能列表的数字组合掩码。 |

**示例：**

```TypeScript
let ret = usb.getCurrentFunctions();

```

