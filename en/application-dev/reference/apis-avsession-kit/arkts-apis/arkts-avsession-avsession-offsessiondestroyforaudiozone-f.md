# offSessionDestroyForAudioZone

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## offSessionDestroyForAudioZone

```TypeScript
function offSessionDestroyForAudioZone(userId: number, callback?: Callback<AVSessionDescriptor>): void
```

Unregister session destroy callback for a specific audio zone.

**Since:** 26.1.0

**Required permissions:** ohos.permission.MANAGE_MEDIA_RESOURCES

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.Manager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | The userid which belongs to an audio zone.<br>The value should be an integer. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AVSessionDescriptor](arkts-avsession-avsession-avsessiondescriptor-i.md)&gt; | No | Used to unregister listener for ('sessionDestroy') command. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | permission denied. |
| 6700101 | Session service is not running. |
