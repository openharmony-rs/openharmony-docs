# AudioSuiteFeatureStatusInfo (System API)

```TypeScript
interface AudioSuiteFeatureStatusInfo
```

Defines the audio suite feature status information.

**Since:** 26.0.1

<!--Device-audio-interface AudioSuiteFeatureStatusInfo--><!--Device-audio-interface AudioSuiteFeatureStatusInfo-End-->

**System capability:** SystemCapability.Multimedia.Audio.SuiteEngine

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## errorCode

```TypeScript
errorCode: AudioErrors
```

Error code when the feature enters the error status. <br>If the error code is 6800301, the internal database or I/O of the system is abnormal, which is irrelevant to application invoking.

**Type:** [AudioErrors](arkts-audio-audio-audioerrors-e.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioSuiteFeatureStatusInfo-errorCode: AudioErrors--><!--Device-AudioSuiteFeatureStatusInfo-errorCode: AudioErrors-End-->

**System capability:** SystemCapability.Multimedia.Audio.SuiteEngine

**System API:** This is a system API.

## featureType

```TypeScript
featureType: AudioSuiteFeatureType
```

Type of the feature module.

**Type:** [AudioSuiteFeatureType](arkts-audio-audio-audiosuitefeaturetype-e-sys.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioSuiteFeatureStatusInfo-featureType: AudioSuiteFeatureType--><!--Device-AudioSuiteFeatureStatusInfo-featureType: AudioSuiteFeatureType-End-->

**System capability:** SystemCapability.Multimedia.Audio.SuiteEngine

**System API:** This is a system API.

## installPath

```TypeScript
installPath: string
```

Installation path.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioSuiteFeatureStatusInfo-installPath: string--><!--Device-AudioSuiteFeatureStatusInfo-installPath: string-End-->

**System capability:** SystemCapability.Multimedia.Audio.SuiteEngine

**System API:** This is a system API.

## progress

```TypeScript
progress: number
```

Download progress. The value ranges from 0 to 100. The value should be an integer.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioSuiteFeatureStatusInfo-progress: int--><!--Device-AudioSuiteFeatureStatusInfo-progress: int-End-->

**System capability:** SystemCapability.Multimedia.Audio.SuiteEngine

**System API:** This is a system API.

## status

```TypeScript
status: AudioSuiteFeatureStatus
```

Status of the feature module.

**Type:** [AudioSuiteFeatureStatus](arkts-audio-audio-audiosuitefeaturestatus-e-sys.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioSuiteFeatureStatusInfo-status: AudioSuiteFeatureStatus--><!--Device-AudioSuiteFeatureStatusInfo-status: AudioSuiteFeatureStatus-End-->

**System capability:** SystemCapability.Multimedia.Audio.SuiteEngine

**System API:** This is a system API.
