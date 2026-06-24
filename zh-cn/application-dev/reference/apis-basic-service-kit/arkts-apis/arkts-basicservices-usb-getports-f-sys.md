# getPorts（系统接口）

## getPorts

```TypeScript
function getPorts(): Array<USBPort>
```

获取所有物理USB端口描述信息。

**起始版本：** 9

**废弃版本：** 9

**替代接口：** [getPorts](arkts-basicservices-usbmanager-getports-f-sys.md#getPorts-1)

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;USBPort&gt; | USB端口描述信息列表。 |

**示例：**

```TypeScript
let ret = usb.getPorts();

```

