# makeMirrorWithRegion (System API)

## Modules to Import

```TypeScript
import { screen } from '@kit.ArkUI';
```

## makeMirrorWithRegion

```TypeScript
function makeMirrorWithRegion(mainScreen: number, mirrorScreen: Array<number>, mainScreenRegion: Rect): Promise<number>
```

Sets a rectangle on the screen to mirror mode. This API uses a promise to return the result. After this API is called, you are advised not to rotate or fold the screen further. Otherwise, the mirrored content may be abnormal.

**Since:** 19

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mainScreen | number | Yes | ID of the primary screen. The ID must be a non-negative integer. |
| mirrorScreen | Array&lt;number&gt; | Yes | Array of IDs of secondary screens. Each ID must be a positive integer. |
| mainScreenRegion | Rect | Yes | Rectangle on the primary screen to be mirrored. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the group ID of the secondary screens, where the ID is a positive integer. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [1400001](../errorcode-display.md#1400001-invalid-display-or-screen) | Invalid display or screen. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the screen ID using getAllScreens().
let mainScreenId: number = 0; // Main screen ID.
let mirrorScreenIds: Array<number> = [1, 2, 3]; // ID array of mirrored screens.
// Rectangle on the main screen to be mirrored.
let mainScreenRegion: screen.Rect = {
  left: 0,
  top: 0,
  width: 1920,
  height: 1080
};
// Set a rectangle on the screen to mirror mode.
screen.makeMirrorWithRegion(mainScreenId, mirrorScreenIds, mainScreenRegion).then((data: number) => {
  console.info(`Succeeded in setting screen mirroring. Data: ${data}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set screen area mirroring. Code: ${err.code}, message: ${err.message}`);
});
```
