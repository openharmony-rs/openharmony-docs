# VibratorPattern

马达振动序列，每个events代表一个振动事件。通过[VibratorPatternBuilder.build](arkts-sensorservice-vibrator-vibratorpatternbuilder-c.md#build)方法生成，作为 [VibrateFromPattern](arkts-sensorservice-vibrator-vibratefrompattern-i.md)的pattern参数传入 [startVibration](arkts-sensorservice-vibrator-startvibration-f.md) 接口触发振动。

**起始版本：** 23

<!--Device-vibrator-interface VibratorPattern--><!--Device-vibrator-interface VibratorPattern-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## 导入模块

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
```

## events

```TypeScript
events: Array<VibratorEvent>
```

振动事件数组。由[VibratorPatternBuilder](arkts-sensorservice-vibrator-vibratorpatternbuilder-c.md)的addContinuousEvent和addTransientEvent方法添加后 通过build方法生成。同一VibratorPattern中多个VibratorEvent的time值不能重叠。

**类型：** Array&lt;[VibratorEvent](arkts-sensorservice-vibrator-vibratorevent-i.md)&gt;

**起始版本：** 23

<!--Device-VibratorPattern-events: Array<VibratorEvent>--><!--Device-VibratorPattern-events: Array<VibratorEvent>-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## time

```TypeScript
time: int
```

振动绝对起始时间。单位：ms（毫秒）。

**类型：** int

**起始版本：** 23

<!--Device-VibratorPattern-time: int--><!--Device-VibratorPattern-time: int-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

