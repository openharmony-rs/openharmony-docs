# getThermalLevel

## getThermalLevel

```TypeScript
function getThermalLevel(): ThermalLevel
```

获取当前热档位信息。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getLevel](arkts-basicservices-getlevel-f.md#getlevel-1)

**系统能力：** SystemCapability.PowerManager.ThermalManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ThermalLevel | 热档位信息。 |

**示例：**

```TypeScript
let level = thermal.getThermalLevel();
console.info('thermal level is: ' + level);

```

