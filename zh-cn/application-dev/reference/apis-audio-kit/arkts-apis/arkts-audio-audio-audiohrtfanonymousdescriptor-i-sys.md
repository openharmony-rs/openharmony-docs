# AudioHRTFAnonymousDescriptor（系统接口）

匿名的HRTF文件描述符，用于跨进程传输。

**起始版本：** 26.0.0

<!--Device-audio-interface AudioHRTFAnonymousDescriptor--><!--Device-audio-interface AudioHRTFAnonymousDescriptor-End-->

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

个人化HRTF的文件描述符。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioHRTFAnonymousDescriptor-fd: int--><!--Device-AudioHRTFAnonymousDescriptor-fd: int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

## length

```TypeScript
length: number
```

个人化HRTF数据的总大小（以字节为单位）。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioHRTFAnonymousDescriptor-length: long--><!--Device-AudioHRTFAnonymousDescriptor-length: long-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

