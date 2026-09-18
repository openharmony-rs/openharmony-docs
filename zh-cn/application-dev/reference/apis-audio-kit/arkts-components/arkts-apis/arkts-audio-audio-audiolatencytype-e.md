# AudioLatencyType

表示音频时延类型的枚举。

**起始版本：** 23

**系统能力：** SystemCapability.Multimedia.Audio.Core

## LATENCY_TYPE_ALL

```TypeScript
LATENCY_TYPE_ALL = 0
```

输入以获取所有音频处理单元（包括软件和硬件）的延迟。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

## LATENCY_TYPE_SOFTWARE

```TypeScript
LATENCY_TYPE_SOFTWARE = 1
```

输入以获取软件部分的延迟，包括软件中的音频效果。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

## LATENCY_TYPE_HARDWARE

```TypeScript
LATENCY_TYPE_HARDWARE = 2
```

输入以获取硬件部分的延迟，包括HAL、驱动程序和硬件中的音频效果。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core
