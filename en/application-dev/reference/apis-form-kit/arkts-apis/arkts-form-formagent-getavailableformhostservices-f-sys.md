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

**Since:** 26.0.1

**Required permissions:** ohos.permission.AGENT_REQUIRE_FORM

**Model restriction:** This API can be used only in the stage model.

<!--Device-formAgent-function getAvailableFormHostServices(): Promise<Array<formInfo.PeerFormHostServiceInfo>>--><!--Device-formAgent-function getAvailableFormHostServices(): Promise<Array<formInfo.PeerFormHostServiceInfo>>-End-->

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

<!--Del-->
**Examples**

```TypeScript
import { formAgent, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formAgent.getAvailableFormHostServices().then((data: formInfo.PeerFormHostServiceInfo[]) => {
    console.info(`formAgent getAvailableFormHostServices success, service count: ${data.length}`);
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

<!--DelEnd-->
