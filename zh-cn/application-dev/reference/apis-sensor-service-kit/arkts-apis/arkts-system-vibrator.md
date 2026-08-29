# @system.vibrator

户注意力。
 适用于Lite Wearable轻量穿戴设备。对于其他设备类型，自API version 8起该模块不再维护。
 与[@ohos.vibrator (振动)](arkts-vibrator.md)模块相比，本模块功能较为简单，不支持振动效果查询、振动器列表查询、自定义振动文件等高级功能。对于Lite Wearable设备，
 本模块持续维护；对于其他设备类型，从API version 8起不再维护，推荐使用[@ohos.vibrator (振动)](arkts-vibrator.md)模块的
 [vibrator.startVibration()](arkts-sensorservice-vibrator-startvibration-f.md)
 接口，该替代接口支持更丰富的振动效果（包括指定时长振动[VibrateTime](arkts-sensorservice-vibrator-vibratetime-i.md)、预置效果振动
 [VibratePreset](arkts-sensorservice-vibrator-vibratepreset-i.md)、自定义文件振动
 [VibrateFromFile](arkts-sensorservice-vibrator-vibratefromfile-i.md)等），适用于更多设备类型。
 > **说明：**
 > - 模块维护策略：
 >  >   - 对于Lite Wearable设备类型，该模块长期维护，正常使用。
 >  >   - 对于支持该模块的其他设备类型，该模块从API version 8开始不再维护，推荐使用新接口[@ohos.vibrator (振动)](arkts-vibrator.md)。
 > - 该功能使用需要对应硬件支持，仅支持真机调试。可通过系统设备信息或相关接口查询设备是否支持振动功能。


## 导入模块

```TypeScript
import { Vibrator, VibrateOptions } from '@kit.SensorServiceKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [Vibrator](arkts-sensorservice-system-vibrator-vibrator-c.md) |  |

### 接口

| 名称 | 说明 |
| --- | --- |
| [VibrateOptions](arkts-sensorservice-system-vibrator-vibrateoptions-i.md) | 定义触发设备振动的配置参数，包括振动模式及接口调用的回调函数。开发者调用 Vibrator.vibrate()时，通过 VibrateOptions指定振动模式（短振动或长振动）以及监听振动触发成功、失败和完成的回调函数。传入VibrateOptions后，设备将按指定的mode执行相应振动模式，并在振动触发成功时回调success函数，失败时回调 fail函数，接口调用结束时回调complete函数。 |
