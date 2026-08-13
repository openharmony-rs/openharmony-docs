# ColorResponse（系统接口）

颜色传感器数据，继承于[Response](arkts-sensorservice-sensor-response-i.md#Response)。用于表示颜色传感器上报的响应数据，包含光照强度和色温信息。

**继承/实现关系：** ColorResponse extends [Response](arkts-sensorservice-sensor-response-i.md#Response)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-sensor-interface ColorResponse--><!--Device-sensor-interface ColorResponse-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**系统接口：** 此接口为系统接口。

## colorTemperature

```TypeScript
colorTemperature: double
```

表示色温。单位：开尔文（K）。取值范围：取值为实际上报物理量，由硬件传感器决定。典型值：暖白光约2700-3000K，正白光约4000-5000K，冷白光约6500K以上。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ColorResponse-colorTemperature: double--><!--Device-ColorResponse-colorTemperature: double-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**系统接口：** 此接口为系统接口。

## lightIntensity

```TypeScript
lightIntensity: double
```

表示光的强度。单位：勒克斯（lux）。取值范围：取值为实际上报物理量，由硬件传感器决定。典型室内环境光强度约为300-500 lux，户外阳光可达10000 lux以上。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ColorResponse-lightIntensity: double--><!--Device-ColorResponse-lightIntensity: double-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**系统接口：** 此接口为系统接口。

