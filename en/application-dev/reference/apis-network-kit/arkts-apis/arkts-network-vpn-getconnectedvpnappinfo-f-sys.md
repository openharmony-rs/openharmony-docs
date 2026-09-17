# getConnectedVpnAppInfo (System API)

## Modules to Import

```TypeScript
import { vpn } from '@kit.NetworkKit';
```

## getConnectedVpnAppInfo

```TypeScript
function getConnectedVpnAppInfo(): Promise<Array<string>>
```

Get the connected VPN App Info.

**Since:** 20

**Required permissions:** ohos.permission.MANAGE_VPN

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | The promise returned by the connected VPN App Info. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [19900001](../errorcode-net-vpn.md#19900001-invalid-parameter) | Invalid parameter value. |
| [19900002](../errorcode-net-vpn.md#19900002-system-internal-error) | System internal error. |
