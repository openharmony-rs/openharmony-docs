# createOppServerProfile (System API)

## Modules to Import

```TypeScript
import { opp } from '@kit.ConnectivityKit';
```

## createOppServerProfile

```TypeScript
function createOppServerProfile(): OppServerProfile
```

create the instance of OPP server profile.

**Since:** 16

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [OppServerProfile](arkts-connectivity-opp-oppserverprofile-i-sys.md) | Returns the instance of opp profile. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications are not allowed to use system APIs. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
