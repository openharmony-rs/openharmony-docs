# AudioRecordingManager

Provides recording strategy management, including collaborative recording and recording control capabilities.

**Since:** 26.0.0

**System capability:** SystemCapability.Multimedia.Audio.Capturer

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## offSystemRecordControllerEnabledChange

```TypeScript
offSystemRecordControllerEnabledChange(callback?: Callback<SystemRecordControllerChangeInfo>): void
```

Unsubscribes from the system recording controller panel enabled state change event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SystemRecordControllerChangeInfo](arkts-audio-audio-systemrecordcontrollerchangeinfo-i-sys.md)&gt; | No | The Callback used in subscription function for unsubscribing. If not using this parameter, all callbacks subscribed in current process before will be unsubscribed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio service error occurs like service died. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';

audioRecordingManager.offSystemRecordControllerEnabledChange();
```

## onSystemRecordControllerEnabledChange

```TypeScript
onSystemRecordControllerEnabledChange(callback: Callback<SystemRecordControllerChangeInfo>): void
```

Subscribes to the system recording controller panel enabled state change event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SystemRecordControllerChangeInfo](arkts-audio-audio-systemrecordcontrollerchangeinfo-i-sys.md)&gt; | Yes | Callback used to listen whether the system recording controller panel enabled state change event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800102](../errorcode-audio.md#6800102-memory-allocation-failure) | Memory allocation failed. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio service error occurs like service died. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';

audioRecordingManager.onSystemRecordControllerEnabledChange((changeInfo: audio.SystemRecordControllerChangeInfo) => {
  console.info(`System record controller enabled state changed: ${changeInfo.enabled}, uid: ${changeInfo.uid}, sourceType: ${changeInfo.sourceType}`);
});
```
