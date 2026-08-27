# AVRecorderConfig

表示音视频录制的参数设置。通过audioSourceType和videoSourceType区分纯音频录制、纯视频录制或音视频录制。纯音频录制时，仅需要设置audioSourceType；纯视频录制时，仅需要设置videoSourceType； 音视频录制时，audioSourceType和videoSourceType均需要设置。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## metaSourceTypes

```TypeScript
metaSourceTypes?: Array<MetaSourceType>
```

元数据源类型，详见MetaSourceType。

**类型：** Array&lt;[MetaSourceType](arkts-media-media-metasourcetype-e-sys.md)&gt;

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**系统接口：** 此接口为系统接口。
