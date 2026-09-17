# isAlwaysOnVpnEnabled (System API)

## Modules to Import

```TypeScript
import { vpnExtension } from '@kit.NetworkKit';
```

## isAlwaysOnVpnEnabled

```TypeScript
function isAlwaysOnVpnEnabled(bundleName: string): Promise<boolean>
```

Obtains the status of the **always on** mode. This API uses a promise to return the result.

**Since:** 11

**Required permissions:** ohos.permission.MANAGE_VPN

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the application (generally a third-party application). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the **always on** mode is enabled, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
