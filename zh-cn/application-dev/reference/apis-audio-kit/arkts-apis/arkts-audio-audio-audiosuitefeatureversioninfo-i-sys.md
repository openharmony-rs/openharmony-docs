# AudioSuiteFeatureVersionInfo（系统接口）

```TypeScript
interface AudioSuiteFeatureVersionInfo
```

定义音频编创套件特性的版本信息。

**起始版本：** 26.0.1

<!--Device-audio-interface AudioSuiteFeatureVersionInfo--><!--Device-audio-interface AudioSuiteFeatureVersionInfo-End-->

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## errorCode

```TypeScript
errorCode: AudioErrors
```

特性进入异常状态后的错误码。<br>如果错误码为6800301，表示系统内部数据库异常或io异常，与应用调用无关。

**类型：** [AudioErrors](arkts-audio-audio-audioerrors-e.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSuiteFeatureVersionInfo-errorCode: AudioErrors--><!--Device-AudioSuiteFeatureVersionInfo-errorCode: AudioErrors-End-->

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**系统接口：** 此接口为系统接口。

## featureType

```TypeScript
featureType: AudioSuiteFeatureType
```

特性模块类型。

**类型：** [AudioSuiteFeatureType](arkts-audio-audio-audiosuitefeaturetype-e-sys.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSuiteFeatureVersionInfo-featureType: AudioSuiteFeatureType--><!--Device-AudioSuiteFeatureVersionInfo-featureType: AudioSuiteFeatureType-End-->

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**系统接口：** 此接口为系统接口。

## size

```TypeScript
size: number
```

特性模块占用空间大小。单位为：字节。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSuiteFeatureVersionInfo-size: long--><!--Device-AudioSuiteFeatureVersionInfo-size: long-End-->

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**系统接口：** 此接口为系统接口。

## status

```TypeScript
status: AudioSuiteFeatureStatus
```

特性模块状态。

**类型：** [AudioSuiteFeatureStatus](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSuiteFeatureVersionInfo-status: AudioSuiteFeatureStatus--><!--Device-AudioSuiteFeatureVersionInfo-status: AudioSuiteFeatureStatus-End-->

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**系统接口：** 此接口为系统接口。

## version

```TypeScript
version: string
```

特性版本。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSuiteFeatureVersionInfo-version: string--><!--Device-AudioSuiteFeatureVersionInfo-version: string-End-->

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**系统接口：** 此接口为系统接口。
