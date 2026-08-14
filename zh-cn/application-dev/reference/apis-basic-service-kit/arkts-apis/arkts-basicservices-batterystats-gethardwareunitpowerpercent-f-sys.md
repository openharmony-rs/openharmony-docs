# getHardwareUnitPowerPercent（系统接口）

## getHardwareUnitPowerPercent

```TypeScript
function getHardwareUnitPowerPercent(type: ConsumptionType): double
```

根据耗电类型获取硬件单元的耗电百分比。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-batteryStats-function getHardwareUnitPowerPercent(type: ConsumptionType): double--><!--Device-batteryStats-function getHardwareUnitPowerPercent(type: ConsumptionType): double-End-->

**系统能力：** SystemCapability.PowerManager.BatteryStatistics

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [ConsumptionType](arkts-basicservices-batterystats-consumptiontype-e-sys.md) | 是 | 电量消耗类型；该参数类型是枚举类。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 电量消耗类型对应硬件的耗电百分比，取值范围是[0.00，1.00]。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Parameter verification failed. |
| [4600101](../../apis-basic-services-kit/errorcode-batteryStatistics.md#4600101-连接服务失败) | Failed to connect to the service. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## 示例

```TypeScript
try {
    let percent = batteryStats.getHardwareUnitPowerPercent(batteryStats.ConsumptionType.CONSUMPTION_TYPE_SCREEN);
    console.info('battery statistics percent of hardware is: ' + percent);
} catch(err) {
    console.error('get battery statistics percent of hardware failed, err: ' + err);
}
```

