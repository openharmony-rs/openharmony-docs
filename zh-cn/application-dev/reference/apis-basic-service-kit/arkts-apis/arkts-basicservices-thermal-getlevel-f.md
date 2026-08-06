# getLevel

## getLevel

```TypeScript
function getLevel(): ThermalLevel
```

获取当前热档位信息。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-thermal-function getLevel(): ThermalLevel--><!--Device-thermal-function getLevel(): ThermalLevel-End-->

**系统能力：** SystemCapability.PowerManager.ThermalManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 热档位信息。 |

**示例：**

```TypeScript
let level = thermal.getLevel();
console.info('thermal level is: ' + level);
```

