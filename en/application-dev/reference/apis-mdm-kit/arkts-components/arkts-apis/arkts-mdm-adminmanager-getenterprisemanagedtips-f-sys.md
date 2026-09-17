# getEnterpriseManagedTips (System API)

## Modules to Import

```TypeScript
import { adminManager } from '@kit.MDMKit';
```

## getEnterpriseManagedTips

```TypeScript
function getEnterpriseManagedTips(): Promise<string>
```

Gets enterprise message tips.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | returns the enterprise message tips. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
