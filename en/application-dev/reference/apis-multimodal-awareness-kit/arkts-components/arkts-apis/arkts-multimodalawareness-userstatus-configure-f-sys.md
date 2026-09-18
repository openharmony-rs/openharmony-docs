# configure (System API)

## Modules to Import

```TypeScript
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## configure

```TypeScript
function configure(featureId: UserStatusFeature, detail: string): number
```

Configures feature parameters.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| featureId | [UserStatusFeature](arkts-multimodalawareness-userstatus-userstatusfeature-e-sys.md) | Yes | Feature to configure. |
| detail | string | Yes | Detailed feature parameters in JSON format. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns 0 if the operation succeeds; otherwise, returns a non-zero value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [33900001](../errorcode-userStatus.md#33900001-service-exception) | Service exception. Possible causes:<br>1. System error, such as a null pointer and container-related exception. <br>2. Node-API invocation exception, such as invalid Node-API status. |
