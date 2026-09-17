# createStream (System API)

## Modules to Import

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## createStream

```TypeScript
function createStream(sessionId: number, param: StreamParam): Promise<number>
```

Creating a Stream.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sessionId | number | Yes | Ability connection Session id. |
| param | [StreamParam](arkts-distributedservice-abilityconnectionmanager-streamparam-i-sys.md) | Yes | Transport Stream Parameters |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | The promise returned by the function, contain the ID of a transport stream. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [32300001](../errorcode-device-manager.md#32300001-transport-stream-repeatedly-created) | Only one stream can be created for the current session. |
| [32300003](../errorcode-device-manager.md#32300003-bit-rate-not-supported) | Bitrate not supported. |
| [32300004](../errorcode-device-manager.md#32300004-color-space-not-supported) | Color space not supported. |

**Examples**

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

hilog.info(0x0000, 'testTag', 'startStream');
let sessionId = 100;
abilityConnectionManager.createStream(sessionId ,{name: 'receive', role: 0}).then(async (streamId) => {
  let surfaceParam: abilityConnectionManager.SurfaceParam = {
    width: 640,
    height: 480,
    format: 1
  }
  let surfaceId = abilityConnectionManager.getSurfaceId(streamId, surfaceParam);
  hilog.info(0x0000, 'testTag', 'surfaceId is'+surfaceId);
  AppStorage.setOrCreate<string>('surfaceId', surfaceId);
  abilityConnectionManager.startStream(streamId);
})
```
