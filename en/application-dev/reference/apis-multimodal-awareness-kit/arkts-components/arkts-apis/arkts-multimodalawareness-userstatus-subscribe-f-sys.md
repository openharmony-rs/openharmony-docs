# subscribe (System API)

## Modules to Import

```TypeScript
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## subscribe

```TypeScript
function subscribe(featureId: UserStatusFeature, callback: Callback<UserStatusData>,
    deviceInfo?: DeviceInfo[]): number
```

Subscribes to user status monitoring.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| featureId | [UserStatusFeature](arkts-multimodalawareness-userstatus-userstatusfeature-e-sys.md) | Yes | Indicates the feature to be subscribed to. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[UserStatusData](arkts-multimodalawareness-userstatus-userstatusdata-i-sys.md)&gt; | Yes | Callback used to return user status data. |
| deviceInfo | [DeviceInfo](arkts-multimodalawareness-userstatus-deviceinfo-i-sys.md)[] | No | List of devices to enable user status monitoring. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the registered callback ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited<br> device capabilities. |
| [33900001](../errorcode-userStatus.md#33900001-service-exception) | Service exception. Possible causes:<br>1. System error, such as null pointer and container-related exception. <br>2. Node-API invocation exception, such as a invalid Node-API status. |
| [33900002](../errorcode-userStatus.md#33900002-subscription-failed) | Subscription failed. Possible causes:<br>1. Callback registration failed. <br>2. Failed to bind the native object to the JS wrapper. <br>3. Node-API invocation exception, such as invalid Node-API status. <br>4. IPC request exception. |
