# AudioRecordingManager

Provides recording strategy management, including collaborative recording and recording control capabilities.

**Since:** 26.0.0

**System capability:** SystemCapability.Multimedia.Audio.Capturer

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## enableSystemRecordController

```TypeScript
enableSystemRecordController(show: boolean, config: SystemRecordControllerConfig): Promise<void>
```

Enables or disables the system recording controller panel. The application can call this API to pull up the recording controller panel before starting the recording stream, allowing the user to finish selecting the recording device or audio effect parameters. The recording service can then be started to avoid inconsistent audio effects caused by switching during the recording process. The application must be in the foreground to enable the panel; the enable operation does not take effect if the application is in the background. Disabling the panel is not restricted by the application's foreground or background status. The API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| show | boolean | Yes | A boolean value indicating whether to show (true) or hide (false) the system recording controller panel. |
| config | [SystemRecordControllerConfig](arkts-audio-audio-systemrecordcontrollerconfig-i.md) | Yes | Configuration for the system recording controller panel. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio service error occurs like service died. |
