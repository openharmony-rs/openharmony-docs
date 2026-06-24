# hasRight

## hasRight

```TypeScript
function hasRight(deviceName: string): boolean
```

判断是否有权访问该设备。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [hasRight](arkts-basicservices-usbmanager-hasright-f.md#hasRight-1)

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceName | string | 是 | 设备名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示有访问设备的权限，false表示没有访问设备的权限。 |

**示例：**

```TypeScript
let devicesName= "1-1";
let bool = usb.hasRight(devicesName);
console.info(`hasRight = ${bool}`);

```

