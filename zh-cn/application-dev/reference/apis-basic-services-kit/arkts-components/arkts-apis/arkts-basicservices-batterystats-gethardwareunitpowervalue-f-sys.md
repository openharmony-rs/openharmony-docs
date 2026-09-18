# getHardwareUnitPowerValue（系统接口）

## 导入模块

```TypeScript
import { batteryStats } from '@kit.BasicServicesKit';
```

## getHardwareUnitPowerValue

```TypeScript
function getHardwareUnitPowerValue(type: ConsumptionType): number
```

根据耗电类型获取硬件单元的耗电量，单位毫安时。适用于需要精确耗电数值的场景。如需比较不同硬件单元耗电占比，请使用[getHardwareUnitPowerPercent](arkts-basicservices-batterystats-gethardwareunitpowerpercent-f-sys.md)获取相对百分比。

**起始版本：** 8

**系统能力：** SystemCapability.PowerManager.BatteryStatistics

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [ConsumptionType](arkts-basicservices-batterystats-consumptiontype-e-sys.md) | 是 | 电量消耗类型，用于指定要查询的硬件单元耗电类型。可选值参见[ConsumptionType](arkts-basicservices-batterystats-consumptiontype-e-sys.md)，如CONSUMPTION_TYPE_SCREEN用于查询屏幕耗电、CONSUMPTION_TYPE_BLUETOOTH用于查询蓝牙耗电、CONSUMPTION_TYPE_WIFI用于查询无线网耗电等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 电量消耗类型对应硬件的耗电量，单位毫安时。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [4600101](../errorcode-batteryStatistics.md#4600101-连接服务失败) | Failed to connect to the service. |

**示例**

```TypeScript
try {
    let powerValue = batteryStats.getHardwareUnitPowerValue(batteryStats.ConsumptionType.CONSUMPTION_TYPE_SCREEN);
    console.info('battery statistics value of hardware is: ' + powerValue);
} catch (err) {
    console.error(`Failed to get battery statistics value of hardware. Code: ${err.code}, message: ${err.message}`);
}
```
