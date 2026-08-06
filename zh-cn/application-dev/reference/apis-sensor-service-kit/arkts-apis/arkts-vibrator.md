# @system.vibrator

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [Vibrator](arkts-sensorservice-vibrator-vibrator-c.md) |  |

### 接口

| 名称 | 说明 |
| --- | --- |
| [VibrateOptions](arkts-sensorservice-vibrator-vibrateoptions-i.md) | 定义触发设备振动的配置参数，包括振动模式及接口调用的回调函数。开发者调用 \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_时，通过 VibrateOptions指定振动模式（短振动或长振动）以及监听振动触发成功、失败和完成的回调函数。传入VibrateOptions后，设备将按指定的mode执行相应振动模式，并在振动触发成功时回调success函数，失败时回调 fail函数，接口调用结束时回调complete函数。 |

