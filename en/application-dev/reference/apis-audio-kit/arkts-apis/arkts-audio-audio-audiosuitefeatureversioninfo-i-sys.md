# AudioSuiteFeatureVersionInfo (System API)

```TypeScript
interface AudioSuiteFeatureVersionInfo
```

Defines the audio suite feature version information.

**Since:** 26.0.1

<!--Device-audio-interface AudioSuiteFeatureVersionInfo--><!--Device-audio-interface AudioSuiteFeatureVersionInfo-End-->

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

Error code when the feature enters the error state. <br>If the error code is 6800301, it indicates that the internal database or I/O of the system is abnormal, which is irrelevant to application invoking.

**Type:** [AudioErrors](arkts-audio-audio-audioerrors-e.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioSuiteFeatureVersionInfo-errorCode: AudioErrors--><!--Device-AudioSuiteFeatureVersionInfo-errorCode: AudioErrors-End-->

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

<!--Device-AudioSuiteFeatureVersionInfo-featureType: AudioSuiteFeatureType--><!--Device-AudioSuiteFeatureVersionInfo-featureType: AudioSuiteFeatureType-End-->

**System capability:** SystemCapability.Multimedia.Audio.SuiteEngine

**System API:** This is a system API.

## size

```TypeScript
size: number
```

Storage size of feature module. Unit: Bytes.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioSuiteFeatureVersionInfo-size: long--><!--Device-AudioSuiteFeatureVersionInfo-size: long-End-->

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

<!--Device-AudioSuiteFeatureVersionInfo-status: AudioSuiteFeatureStatus--><!--Device-AudioSuiteFeatureVersionInfo-status: AudioSuiteFeatureStatus-End-->

**System capability:** SystemCapability.Multimedia.Audio.SuiteEngine

**System API:** This is a system API.

## version

```TypeScript
version: string
```

Feature version.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioSuiteFeatureVersionInfo-version: string--><!--Device-AudioSuiteFeatureVersionInfo-version: string-End-->

**System capability:** SystemCapability.Multimedia.Audio.SuiteEngine

**System API:** This is a system API.
