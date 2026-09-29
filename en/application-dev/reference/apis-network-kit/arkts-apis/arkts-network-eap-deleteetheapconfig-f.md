# deleteEthEapConfig

## Modules to Import

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## deleteEthEapConfig

```TypeScript
function deleteEthEapConfig(): Promise<void>
```

Deletes the persisted 802.1X EAP configuration and stops any ongoing auto-authentication. Idempotent: resolves successfully even if no configuration has been stored.

**Since:** 26.2.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_EAP

**Model restriction:** This API can be used only in the stage model.

<!--Device-eap-function deleteEthEapConfig(): Promise<void>--><!--Device-eap-function deleteEthEapConfig(): Promise<void>-End-->

**System capability:** SystemCapability.Communication.NetManager.Eap

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
