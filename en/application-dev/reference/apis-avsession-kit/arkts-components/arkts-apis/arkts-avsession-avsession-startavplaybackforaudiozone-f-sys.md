# startAVPlaybackForAudioZone (System API)

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## startAVPlaybackForAudioZone

```TypeScript
function startAVPlaybackForAudioZone(userId: number, bundleName: string, assetId: string, info?: CommandInfo): Promise<void>
```

Start an application for media playback with command info for an specific audio zone.

**Since:** 26.1.0

**Required permissions:** ohos.permission.MANAGE_MEDIA_RESOURCES

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.Manager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | The userid which belongs to an audio zone.<br>The value should be an integer. |
| bundleName | string | Yes | Specifies the bundleName which to be started. |
| assetId | string | Yes | Specifies the assetId to be started. |
| info | [CommandInfo](arkts-avsession-avsession-commandinfo-i.md) | No | Specifies the specified command information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that return |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. |
| 6700101 | Session service is not running. |
