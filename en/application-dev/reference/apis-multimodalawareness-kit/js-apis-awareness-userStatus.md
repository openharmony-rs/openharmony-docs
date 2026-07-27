# @ohos.multimodalAwareness.userStatus (User Status Awareness)

<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @zou_ye-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=d18790e6ef1247c1fd8194f3838e7698bf6e9bf2 translatedAt=2026-06-24T06:30:17.391Z pushedAt=2026-06-25T01:35:11.434Z -->

The **UserStatus** module, designed for user state awareness, empowers the system to perceive specific conditions of users, such as determining their age group.

> **NOTE**
>
> The initial APIs of this module are supported since API version 20. This API is deprecated since API version 24. No substitute API is provided.

## Modules to Import

```ts
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## UserAgeGroup<sup>(deprecated)</sup>

Enumerates the user age groups, for example, child or adult.

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

| Name               | Value | Description                  |
| ------------------- | ---- | ---------------------- |
| OTHERS  | 0    | Adult.|
| CHILD  | 1    | Child.|

## UserClassification<sup>(deprecated)</sup>

Defines the user age group detection result.

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

| Name               | Type  |Read-Only|Optional| Description                  |
| ------------------- | ---- |----|----| ---------------------- |
| ageGroup  | [UserAgeGroup](#useragegroupdeprecated)   |No|Yes| User age group, for example, child or adult.|
| confidence  | float    |No|Yes| Confidence of the detection result. The value is a floating point number ranging from 0 to 1. A larger value indicates a higher confidence.|

## userStatus.on('userAgeGroupDetected')<sup>(deprecated)</sup>

 on(type: 'userAgeGroupDetected', callback: Callback&lt;UserClassification&gt;): void

Enables the age group detection function.

When the function is enabled, the application can recommend content based on the age group detection result.

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**Device behavior differences**: This API can be called on phones. If it is called on other devices, error code **801** is returned.

> **NOTE**
>
> This API is supported only on some phones. Error code **801** is returned if it is called on unsupported phones.

**Parameters**

| Name  | Type                            | Mandatory| Description                                                        |
| -------- | -------------------------------- | ---- |------------------------------------------------------------ |
| type     | string                           | Yes  | Event type. The value **userAgeGroupDetected** indicates the event of enabling age group detection.|
| callback | Callback&lt;[UserClassification](#userclassificationdeprecated)&gt; | Yes  | Callback used to return the detection result.|

**Error codes**

For details about the error codes, see [User Status Awareness Error Codes](errorcode-userStatus.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 33900001 | Service exception. Possible causes: <br>1. System error, such as a null pointer and container-related exception. <br>2. Node-API invocation exception, such as invalid Node-API status.|
| 33900002 | Subscription failed. Possible causes: <br>1. Callback registration failed. <br>2. Failed to bind the native object to the JS wrapper. <br>3. Node-API invocation exception, such as invalid Node-API status. <br>4. IPC request exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
    userStatus.on('userAgeGroupDetected', (data: userStatus.UserClassification) => {
        console.info('callback succeeded, ageGroup:' + data.ageGroup + ", confidence:" + data.confidence);
    });
    console.info("on succeeded");
} catch (err) {
    let error = err as BusinessError;
    console.error("Failed on and err code is " + error.code);
}
```

## userStatus.off('userAgeGroupDetected')<sup>(deprecated)</sup>

off(type: 'userAgeGroupDetected', callback?: Callback&lt;UserClassification&gt;): void

Disables the age group detection function.

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**Device behavior differences**: This API can be called on phones. If it is called on other devices, error code **33900003** is returned.

> **NOTE**
>
> This API is supported only on some phones. Error code **33900003** is returned if it is called on unsupported phones.

**Parameters**

| Name  | Type                            | Mandatory| Description                                                        |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                           | Yes  | Event type. The value **userAgeGroupDetected** indicates the event of enabling age group detection.|
| callback | Callback&lt;[UserClassification](#userclassificationdeprecated)&gt; | No  | Callback used to return the detection result. The callback to be unsubscribed must be the same as the one passed in during subscription. If not specified, all callbacks currently listening for this event will be unsubscribed. |

**Error codes**

For details about the error codes, see [User Status Awareness Error Codes](errorcode-userStatus.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 33900001 | Service exception. Possible causes: <br>1. System error, such as a null pointer and container-related exception. <br>2. Node-API invocation exception, such as invalid Node-API status. |
| 33900003 | Unsubscription failed. Possible causes: <br>1. Callback failure. <br>2. Node-API invocation exception, such as invalid Node-API status. <br>3. IPC request exception.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
    userStatus.off('userAgeGroupDetected');
    console.info("off succeeded");
} catch (err) {
    let error = err as BusinessError;
    console.error("Failed off and err code is " + error.code);
}
```