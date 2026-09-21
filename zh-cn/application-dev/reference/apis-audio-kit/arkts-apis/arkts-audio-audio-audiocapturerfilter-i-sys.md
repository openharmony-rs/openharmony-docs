# AudioCapturerFilter（系统接口）

```TypeScript
interface AudioCapturerFilter
```

过滤条件类。在调用selectInputDeviceByFilter接口前，需要先创建AudioCapturerFilter实例。

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## capturerInfo

```TypeScript
capturerInfo?: AudioCapturerInfo
```

表示采集器信息。不填写时表示不按采集器信息过滤。

**类型：** [AudioCapturerInfo](arkts-audio-audio-audiocapturerinfo-i.md)

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## uid

```TypeScript
uid?: number
```

表示应用ID。不填写时表示不按应用ID过滤。

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。
