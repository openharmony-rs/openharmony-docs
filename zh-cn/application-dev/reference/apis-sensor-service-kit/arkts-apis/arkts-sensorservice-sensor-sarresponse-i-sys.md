# SarResponse（系统接口）

吸收比率传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md)。用于表示吸收比率传感器上报的响应数据，包含电磁波吸收率信息。

**继承/实现关系：** SarResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**起始版本：** 10

**系统能力：** SystemCapability.Sensors.Sensor

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## absorptionRatio

```TypeScript
absorptionRatio: number
```

表示具体的吸收率。单位：W/kg。取值范围：取值为实际上报物理量，由硬件传感器决定。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.Sensors.Sensor

**系统接口：** 此接口为系统接口。
