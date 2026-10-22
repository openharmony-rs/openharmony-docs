# ContinueCallback (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: DistributedSched-->
<!--Owner: @hobbycao-->
<!--Designer: @gsxiaowen-->
<!--Tester: @hanjiawei-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=116689016d259349eb0a38a801fc8824a3ec9bca translatedAt=2026-09-03T11:54:51.969Z pushedAt=2026-09-05T10:47:30.719Z -->

The ContinueCallback module defines the callback function that indicates the result of mission continuation. For details about mission continuation, see [continueMission](js-apis-distributedMissionManager-sys.md#distributedmissionmanagercontinuemission).

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> The APIs provided by this module are system APIs.
> The APIs of this module can be used only in the stage model.

## ContinueCallback.onContinueDone

onContinueDone(result: number): void;

Called when the mission continuation is complete. The callback parameter **result** returns the continuation result. After the target device successfully receives and starts the mission, the system triggers this callback to notify the source device of the continuation result. The developer should determine whether the continuation is successful based on the **result** parameter and perform the corresponding operations, such as prompting the user, retrying, or terminating the task. For details about the continuation process and mechanism, see [continueMission API](js-apis-distributedMissionManager-sys.md#distributedmissionmanagercontinuemission).

**Device behavior difference:** This API does not take effect on wearable devices that do not support distributed services.

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| result | number | Yes | Result of the migration task. The value **0** indicates that the migration is successful, and a non-zero value indicates that the migration fails. For details about the specific error codes and their meanings, possible causes, and solutions, see the error code description of the [continueMission API](js-apis-distributedMissionManager-sys.md#distributedmissionmanagercontinuemission). |

**Example**

```ts
import { distributedMissionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Call the continueMission method to initiate mission migration.
distributedMissionManager.continueMission(
  {
    srcDeviceId: '123', // Source device ID, obtained through APIs such as deviceManager.
    dstDeviceId: '456', // Target device ID, obtained through APIs such as deviceManager.
    missionId: 123, // Mission ID, obtained through distributedMissionManager or returned by other APIs.
    wantParam: {
      'key': 'value' // Migration data.
    }
  },
  {
    // Callback invoked when the migration is complete to receive the migration result.
    onContinueDone(result: number) {
      console.info(`onContinueDone, result: ${JSON.stringify(result)}`);
    }
  }, (error: BusinessError) => {
  // Callback for error handling.
  // Check whether there is an error and the error code.
  if (error) {
    console.error(`continueMission failed, error.code: ${error.code}, error.message: ${error.message}`);
  }
  console.info(`continueMission finished`);
});
```
