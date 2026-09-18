# getAvailableFormHostServices (System API)

## Modules to Import

```TypeScript
import { formAgent } from '@kit.FormKit';
```

## getAvailableFormHostServices

```TypeScript
function getAvailableFormHostServices(): Promise<Array<formInfo.PeerFormHostServiceInfo>>
```

Get available form host service info list.

**Since:** 26.1.0

**Required permissions:** ohos.permission.AGENT_REQUIRE_FORM

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[formInfo.PeerFormHostServiceInfo](arkts-form-forminfo-peerformhostserviceinfo-i-sys.md)&gt;&gt; | Promise used to return the peer form host service info list. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permissions denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | IPC connection error. |
| [16501000](../errorcode-form.md#16501000-internal-function-error) | An internal functional error occurred. |
