# setInterfaceUp (System API)

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## setInterfaceUp

```TypeScript
function setInterfaceUp(ifaceName: string): Promise<void>
```

Set a specific interface up.

**Since:** 26.0.0

**Required permissions:** ohos.permission.CONNECTIVITY_INTERNAL

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ifaceName | string | Yes | the name of the interface to set up.<br>Value range:(0,1024] <br>Name of the actual network adapter to be started If the network adapter exists, try to up the network adapter. If the network adapter does not exist or does not meet the up condition, the network adapter fails to be up. The network adapter exists in the kernel, and the network adapter meets the up condition. None None |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |
