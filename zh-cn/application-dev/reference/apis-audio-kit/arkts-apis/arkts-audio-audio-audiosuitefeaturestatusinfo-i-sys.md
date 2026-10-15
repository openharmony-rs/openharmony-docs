# AudioSuiteFeatureStatusInfo（系统接口）

```TypeScript
interface AudioSuiteFeatureStatusInfo
```

定义音频编创套件特性的状态信息。

**起始版本：** 26.0.1

<!--Device-audio-interface AudioSuiteFeatureStatusInfo--><!--Device-audio-interface AudioSuiteFeatureStatusInfo-End-->

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

特性进入异常状态后的错误码。<br>如果错误码为6800301，表示系统内部数据库异常或IO异常，与应用调用无关。

**类型：** [AudioErrors](arkts-audio-audio-audioerrors-e.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSuiteFeatureStatusInfo-errorCode: AudioErrors--><!--Device-AudioSuiteFeatureStatusInfo-errorCode: AudioErrors-End-->

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

<!--Device-AudioSuiteFeatureStatusInfo-featureType: AudioSuiteFeatureType--><!--Device-AudioSuiteFeatureStatusInfo-featureType: AudioSuiteFeatureType-End-->

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**系统接口：** 此接口为系统接口。

## installPath

```TypeScript
installPath: string
```

安装路径。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSuiteFeatureStatusInfo-installPath: string--><!--Device-AudioSuiteFeatureStatusInfo-installPath: string-End-->

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**系统接口：** 此接口为系统接口。

## progress

```TypeScript
progress: number
```

下载进度，取值范围从0到100。取值限定为整数。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSuiteFeatureStatusInfo-progress: int--><!--Device-AudioSuiteFeatureStatusInfo-progress: int-End-->

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

<!--Device-AudioSuiteFeatureStatusInfo-status: AudioSuiteFeatureStatus--><!--Device-AudioSuiteFeatureStatusInfo-status: AudioSuiteFeatureStatus-End-->

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**系统接口：** 此接口为系统接口。
