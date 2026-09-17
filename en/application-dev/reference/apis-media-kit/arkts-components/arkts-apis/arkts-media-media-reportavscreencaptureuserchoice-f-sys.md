# reportAVScreenCaptureUserChoice (System API)

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## reportAVScreenCaptureUserChoice

```TypeScript
function reportAVScreenCaptureUserChoice(sessionId: number, choice: string): Promise<void>
```

Reports the user selection result in the screen capture privacy dialog box to the AVScreenCapture server to determine whether to start screen capture. Screen capture starts only when the user touches a button to continue the operation. This API is called by the system application that creates the dialog box.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Media.AVScreenCapture

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sessionId | number | Yes | Session ID of the AVScreenCapture service, which is sent to the application when the AVScreenCapture server starts the privacy dialog box. |
| choice | string | Yes | User choice, including whether screen capture is agreed, selected display ID, and window ID. For details, see JsonData in the example below. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| [5400101](../errorcode-media.md#5400101-memory-allocation-failed) | No memory. Return by promise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

class JsonData {
  public choice: string = 'true';
  public displayId: number | null = -1;
  public missionId: number | null = -1;
  public checkBoxSelected: string = 'true';
  public isInnerAudioBoxSelected: string = 'true';
}
let sessionId: number = 0; // Use the ID of the session that starts the process.

try {
  const jsonData: JsonData = {
    choice: 'true',  // Replace it with the user choice.
    displayId: -1, // Replace it with the ID of the display selected by the user.
    missionId: -1,   // Replace it with the ID of the window selected by the user.
    checkBoxSelected: 'true',   // Replace it with whether the user has enabled screen protection.
    isInnerAudioBoxSelected: 'true',   // Replace it with whether the user has enabled internal audio recording.
  }
  await media.reportAVScreenCaptureUserChoice(sessionId, JSON.stringify(jsonData));
} catch (error: BusinessError) {
  console.error(`reportAVScreenCaptureUserChoice error, error message: ${error.message}`);
}
```
