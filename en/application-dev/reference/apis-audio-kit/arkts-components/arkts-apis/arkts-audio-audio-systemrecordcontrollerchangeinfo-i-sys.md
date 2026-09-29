# SystemRecordControllerChangeInfo (System API)

```TypeScript
interface SystemRecordControllerChangeInfo
```

Defines the information carried when the system recording controller state changes. It includes the enable status, application UID and expected audio source type.

**Since:** 26.0.0

<!--Device-audio-interface SystemRecordControllerChangeInfo--><!--Device-audio-interface SystemRecordControllerChangeInfo-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## enabled

```TypeScript
enabled: boolean
```

Whether the system recording controller panel is enabled. The value true means the panel is enabled, and false means disabled.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SystemRecordControllerChangeInfo-enabled: boolean--><!--Device-SystemRecordControllerChangeInfo-enabled: boolean-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

## sourceType

```TypeScript
sourceType?: SourceType
```

The expected audio source type configured by the application when enabling the recording controller. It is used to match the corresponding recording scenario and noise reduction mode.

**Type:** [SourceType](arkts-audio-audio-sourcetype-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SystemRecordControllerChangeInfo-sourceType?: SourceType--><!--Device-SystemRecordControllerChangeInfo-sourceType?: SourceType-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

## uid

```TypeScript
uid?: number
```

The UID of the application that triggers the system recording controller state change. The value range is all integers.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SystemRecordControllerChangeInfo-uid?: int--><!--Device-SystemRecordControllerChangeInfo-uid?: int-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.
