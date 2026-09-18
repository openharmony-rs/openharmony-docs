# AudioHRTFAnonymousDescriptor（系统接口）

用于跨进程传输的匿名个性化HRTF文件描述符。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## fd

```TypeScript
fd: number
```

个性化HRTF的文件描述符。取值限定为整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

## length

```TypeScript
length: number
```

个性化HRTF数据的总大小（以字节为单位）。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。
