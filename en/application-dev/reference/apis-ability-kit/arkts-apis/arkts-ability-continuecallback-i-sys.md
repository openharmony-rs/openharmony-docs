# ContinueCallback (System API)

ContinueCallback registered for notify continue result.

@interface ContinueCallback

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## onContinueDone

```TypeScript
onContinueDone: OnContinueDoneCallback
```

Called by system when continue mission done.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Examples**

```TypeScript
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
