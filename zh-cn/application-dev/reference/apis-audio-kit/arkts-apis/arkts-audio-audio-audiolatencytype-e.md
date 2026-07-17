# AudioLatencyType

表示音频时延类型的枚举。

| 名称 | 值 | 说明 |  
| ---- | -- | ---- |  
| LATENCY_TYPE_ALL | 0 | 计算包含软件和硬件在内的整体音频处理链路时延。 |  
| LATENCY_TYPE_SOFTWARE | 1 | 计算软件侧时延，包含软件音效。 |  
| LATENCY_TYPE_HARDWARE | 2 | 计算硬件侧时延，包含HAL、驱动和硬件。 |

**起始版本：** 23

<!--Device-audio-enum AudioLatencyType--><!--Device-audio-enum AudioLatencyType-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## LATENCY_TYPE_ALL

```TypeScript
LATENCY_TYPE_ALL = 0
```

Type to get latency of all audio processing units, including software and hardware.

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioLatencyType-LATENCY_TYPE_ALL = 0--><!--Device-AudioLatencyType-LATENCY_TYPE_ALL = 0-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## LATENCY_TYPE_SOFTWARE

```TypeScript
LATENCY_TYPE_SOFTWARE = 1
```

Type to get latency of software part, including audio effects in software.

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioLatencyType-LATENCY_TYPE_SOFTWARE = 1--><!--Device-AudioLatencyType-LATENCY_TYPE_SOFTWARE = 1-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## LATENCY_TYPE_HARDWARE

```TypeScript
LATENCY_TYPE_HARDWARE = 2
```

Type to get latency of hardware part, including audio effects in hal, driver and hardware.

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioLatencyType-LATENCY_TYPE_HARDWARE = 2--><!--Device-AudioLatencyType-LATENCY_TYPE_HARDWARE = 2-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

