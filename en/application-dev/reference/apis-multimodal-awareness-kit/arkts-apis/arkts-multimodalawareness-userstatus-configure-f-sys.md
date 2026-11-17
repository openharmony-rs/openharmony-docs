# configure (System API)

## Modules to Import

```TypeScript
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## configure

```TypeScript
function configure(featureId: UserStatusFeature, detail: string): number
```

Configures feature parameters. After a successful call, the configuration parameters of the specified feature are updated, affecting the subsequent detection behavior of the feature, such as detection sensitivity, sampling frequency, and enabled detection items. It is recommended to call configure() to configure feature parameters before subscribe() to ensure that the configuration takes effect upon subscription. For features that require specific configuration (such as the real-time/non-real-time mode of USER_MOOD), it is recommended to call configure() before subscribe().

**detail Definition**

| featureId | description | value | Description |  
| --- | --- | --- | --- |  
| USER_MOOD | isRealTime | [ ] | **isRealTime** takes the value **0** or **1**, where **0** indicates non-real-time and **1** indicates real-time. Obtaining data in real-time mode increases performance overhead. It is recommended to select an appropriate mode based on business needs to optimize performance. |  
| - | atomicCapabilities | [ ] | **atomicCapabilities** can contain one or more values, and duplicate values are automatically deduplicated. Enabling multiple capabilities increases the computational load. It is recommended to select capabilities on demand based on business requirements to optimize performance.<br>5=atomic gravity sensor<br>8=atomic linear acceleration sensor<br>12=atomic emotion capability |  
| GESTURES_RECOGNITION<br>QUICK_GESTURES_RECOGNITION | dynamicGestureTypes | [ ] | **dynamicGestureTypes** can contain one or more values, and duplicate values are invalid. Enabling multiple gesture types increases the recognition computational load. It is recommended to select them on demand to optimize performance.<br>0=grab<br>1=swipe down<br>2=initial flip-up gesture<br>3=initial flip-down gesture<br>4=swipe up<br>5=fist to open palm<br>6=disappear |  
| - | staticGestureTypes | [ ] | **staticGestureTypes** can contain one or more values, and duplicate values are invalid. Enabling multiple gesture types increases the recognition computational load. It is recommended to select them on demand to optimize performance.<br>7=palm<br>8=scissors hand<br>9=fist<br>10=heart gesture |  
| USER_BLOWING_STATUS | atomicCapabilities | [ ] | **atomicCapabilities** can contain one or more values, and duplicate values are automatically deduplicated. Enabling multiple capabilities increases the computational load. It is recommended to select capabilities on demand based on business requirements to optimize performance.<br>5=atomic gravity sensor<br>8=atomic linear acceleration sensor<br>11=atomic blowing capability<br>12=atomic emotion capability<br>15=atomic screen gaze capability |

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-userStatus-function configure(featureId: UserStatusFeature, detail: string): int--><!--Device-userStatus-function configure(featureId: UserStatusFeature, detail: string): int-End-->

**System capability:** SystemCapability.MultimodalAwareness.UserStatus

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| featureId | [UserStatusFeature](arkts-multimodalawareness-userstatus-userstatusfeature-e-sys.md) | Yes | Feature to configure. |
| detail | string | Yes | Configuration parameter, a JSON format string. It contains a params array, where each parameter contains the description (parameter name) and value (parameter value array) fields. For the specific format and value range, see the detail definition table below. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Configuration execution result. The value 0 indicates that the operation is successful, and a non-zero value indicates that the operation fails. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [33900001](../errorcode-userStatus.md#33900001-service-exception) | Service exception. Possible causes: <br>1. System error, such as a null pointer and container-related exception. <br>2. Node-API invocation exception, such as invalid Node-API status. |
