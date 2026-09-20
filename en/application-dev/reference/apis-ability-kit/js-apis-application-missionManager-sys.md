# @ohos.application.missionManager (missionManager) (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @littlejerry1-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=1e2bfcc9b4f85d9126c23f626a7a73b4bb891227 translatedAt=2026-09-03T11:03:17.007Z pushedAt=2026-09-05T10:47:30.520Z -->

The missionManager module provides APIs to lock, unlock, and clear missions, and switch a mission to the foreground.

> **NOTE**
> 
> The APIs of this module are supported since API version 8 and deprecated since API version 9. You are advised to use [@ohos.app.ability.missionManager](js-apis-app-ability-missionManager-sys.md) instead. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module are system APIs and cannot be called by third-party applications.

## Modules to Import

```ts
import missionManager from '@ohos.application.missionManager';
```

## Required Permissions

ohos.permission.MANAGE_MISSIONS

## missionManager.registerMissionListener

registerMissionListener(listener: MissionListener): number

Registers a listener to observe the mission status.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | listener | [MissionListener](js-apis-inner-application-missionListener-sys.md) | Yes | System mission listener used to listen for system mission status changes, including mission creation, destruction, and switching. |

**Return value**

  | Type| Description|
  | -------- | -------- |
  | number | Index of the listener, which is created by the system and assigned when the system mission status listener is registered. It has a one-to-one correspondence with the listener. |

**Example**

```ts
import missionManager from '@ohos.application.missionManager';

console.info('registerMissionListener');
// Register a system mission status listener.
let listenerId = missionManager.registerMissionListener({
  onMissionCreated: (mission) => {
    console.info('--------onMissionCreated-------');
  },
  onMissionDestroyed: (mission) => {
    console.info('--------onMissionDestroyed-------');
  },
  onMissionSnapshotChanged: (mission) => {
    console.info('--------onMissionSnapshotChanged-------');
  },
  onMissionMovedToFront: (mission) => {
    console.info('--------onMissionMovedToFront-------');
  },
  onMissionIconUpdated: (mission, icon) => {
    console.info('--------onMissionIconUpdated-------');
  },
  onMissionClosed: (mission) => {
    console.info('--------onMissionClosed-------');
  },
  onMissionLabelUpdated: (mission) => {
    console.info('--------onMissionLabelUpdated-------');
  }
});
```


## missionManager.unregisterMissionListener

unregisterMissionListener(listenerId: number, callback: AsyncCallback&lt;void&gt;): void

Unregisters a mission status listener. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | listenerId | number | Yes| Index of the mission status listener to unregister. It is returned by **registerMissionListener()**.|
  | callback | AsyncCallback&lt;void&gt; | Yes | Callback for the unregistration result. If the unregistration is successful, err is undefined and data is undefined. If the unregistration fails, err is an error object. |

**Example**

```ts
import missionManager from '@ohos.application.missionManager';
import { BusinessError } from '@ohos.base';

console.info('registerMissionListener');
let listenerId = missionManager.registerMissionListener({
  onMissionCreated: (mission) => {
    console.info('--------onMissionCreated-------');
  },
  onMissionDestroyed: (mission) => {
    console.info('--------onMissionDestroyed-------');
  },
  onMissionSnapshotChanged: (mission) => {
    console.info('--------onMissionSnapshotChanged-------');
  },
  onMissionMovedToFront: (mission) => {
    console.info('--------onMissionMovedToFront-------');
  },
  onMissionIconUpdated: (mission, icon) => {
    console.info('--------onMissionIconUpdated-------');
  },
  onMissionClosed: (mission) => {
    console.info('--------onMissionClosed-------');
  },
  onMissionLabelUpdated: (mission) => {
    console.info('--------onMissionLabelUpdated-------');
  }
});

// Unregister a system mission status listener.
missionManager.unregisterMissionListener(listenerId, (error) => {
  let err = error as BusinessError;
  console.error(`unregisterMissionListener failed. Code: ${err.code}, message: ${err.message}.`);
});
```


## missionManager.unregisterMissionListener

unregisterMissionListener(listenerId: number): Promise&lt;void&gt;

Unregisters a mission status listener. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | listenerId | number | Yes| Index of the mission status listener to unregister. It is returned by **registerMissionListener()**.|

**Return value**

  | Type| Description| 
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise that returns no value.| 

**Example**

```ts
import missionManager from '@ohos.application.missionManager';
import { BusinessError } from '@ohos.base';

console.info('registerMissionListener');
let listenerId = missionManager.registerMissionListener({
  onMissionCreated: (mission) => {
    console.info('--------onMissionCreated-------');
  },
  onMissionDestroyed: (mission) => {
    console.info('--------onMissionDestroyed-------');
  },
  onMissionSnapshotChanged: (mission) => {
    console.info('--------onMissionSnapshotChanged-------');
  },
  onMissionMovedToFront: (mission) => {
    console.info('--------onMissionMovedToFront-------');
  },
  onMissionIconUpdated: (mission, icon) => {
    console.info('--------onMissionIconUpdated-------');
  },
  onMissionClosed: (mission) => {
    console.info('--------onMissionClosed-------');
  },
  onMissionLabelUpdated: (mission) => {
    console.info('--------onMissionLabelUpdated-------');
  }
});

// Unregister the system mission status listener.
missionManager.unregisterMissionListener(listenerId)
  .then(() => {
    console.info(`UnregisterMissionListener success.`)
  })
  .catch((error: BusinessError) => {
    console.error(`unregisterMissionListener failed. Code: ${error.code}, message: ${error.message}.`);
  });
```


## missionManager.getMissionInfo

getMissionInfo(deviceId: string, missionId: number, callback: AsyncCallback&lt;MissionInfo&gt;): void

Obtains the information about a given mission. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | deviceId | string | Yes| Device ID. It is a null string by default for the local device.|
  | missionId | number | Yes| Mission ID.|
  | callback | AsyncCallback&lt;[MissionInfo](js-apis-inner-application-missionInfo-sys.md)&gt; | Yes | Callback invoked to return the mission information. If the operation is successful, err is undefined and data is the mission snapshot information. If the operation fails, err is an error object. |

**Example**

  ```ts
  import missionManager from '@ohos.application.missionManager';

  let missionId: number = 0;

  // Obtain information about the specified mission.
  missionManager.getMissionInfo('', missionId, (error, mission) => {
    if (error.code) {
      console.error(`getMissionInfo failed, error.code: ${error.code}, error.message: ${error.message}`);
      return;
    }

    console.info(`mission.missionId = ${mission.missionId}`);
    console.info(`mission.runningState = ${mission.runningState}`);
    console.info(`mission.lockedState = ${mission.lockedState}`);
    console.info(`mission.timestamp = ${mission.timestamp}`);
    console.info(`mission.label = ${mission.label}`);
    console.info(`mission.iconPath = ${mission.iconPath}`);
  });
  ```


## missionManager.getMissionInfo

getMissionInfo(deviceId: string, missionId: number): Promise&lt;MissionInfo&gt;

Obtains the information about a given mission. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | deviceId | string | Yes| Device ID. It is a null string by default for the local device.|
  | missionId | number | Yes| Mission ID.|

**Return value**

  | Type| Description|
  | -------- | -------- |
  | Promise&lt;[MissionInfo](js-apis-inner-application-missionInfo-sys.md)&gt; | Promise used to return the mission information obtained.|

**Example**

  ```ts
  import missionManager from '@ohos.application.missionManager';
  import { BusinessError } from '@ohos.base';

  let testMissionId = 1;
  try {
    // Obtain information about the specified mission.
    missionManager.getMissionInfo('', testMissionId).then((data) => {
      console.info(`getMissionInfo successfully. Data: ${JSON.stringify(data)}`);
    }).catch((error: BusinessError) => {
      console.error(`getMissionInfo failed. Cause: ${error.message}`);
    });
  } catch (error) {
    console.error(`getMissionInfo failed. Cause: ${error.message}`);
  }
  ```


## missionManager.getMissionInfos

getMissionInfos(deviceId: string, numMax: number, callback: AsyncCallback&lt;Array&lt;MissionInfo&gt;&gt;): void

Obtains information about all missions. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | deviceId | string | Yes| Device ID. It is a null string by default for the local device.|
  | numMax | number | Yes| Maximum number of missions whose information can be obtained.|
  | callback | AsyncCallback&lt;Array&lt;[MissionInfo](js-apis-inner-application-missionInfo-sys.md)&gt;&gt; | Yes | Callback invoked to return an array of mission information. If the operation is successful, err is undefined and data is the mission snapshot information. If the operation fails, err is an error object. |

**Example**

  ```ts
  import missionManager from '@ohos.application.missionManager';

  // Obtain all mission information.
  missionManager.getMissionInfos('', 10, (error, missions) => {
    if (error.code) {
      console.error(`getMissionInfos failed, error.code: ${error.code}, error.message: ${error.message}`);
      return;
    }
    console.info(`size = ${missions.length}`);
    console.info(`missions = ${JSON.stringify(missions)}`);
  });
  ```


## missionManager.getMissionInfos

getMissionInfos(deviceId: string, numMax: number): Promise&lt;Array&lt;MissionInfo&gt;&gt;

Obtains information about all missions. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | deviceId | string | Yes| Device ID. It is a null string by default for the local device.|
  | numMax | number | Yes| Maximum number of missions whose information can be obtained.|

**Return value**

  | Type| Description|
  | -------- | -------- |
  | Promise&lt;Array&lt;[MissionInfo](js-apis-inner-application-missionInfo-sys.md)&gt;&gt; | Promise used to return the array of mission information obtained.|

**Example**

  ```ts
  import missionManager from '@ohos.application.missionManager';
  import { BusinessError } from '@ohos.base';

  try {
    // Obtain all mission information.
    missionManager.getMissionInfos('', 10).then((data) => {
      console.info(`getMissionInfos successfully. Data: ${JSON.stringify(data)}`);
    }).catch((error: BusinessError) => {
      console.error(`getMissionInfos failed. Cause: ${error.message}`);
    });
  } catch (error) {
    console.error(`getMissionInfos failed. Cause: ${error.message}`);
  }
  ```


## missionManager.getMissionSnapShot

getMissionSnapShot(deviceId: string, missionId: number, callback: AsyncCallback&lt;MissionSnapshot&gt;): void

Obtains the snapshot of a given mission. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | deviceId | string | Yes| Device ID. It is a null string by default for the local device.|
  | missionId | number | Yes| Mission ID.|
  | callback | AsyncCallback&lt;[MissionSnapshot](js-apis-inner-application-missionSnapshot-sys.md)&gt; | Yes | Callback function used to return the mission snapshot information. If the operation is successful, err is undefined and data is the mission snapshot information. If the operation fails, err is an error object. |

**Example**

  ```ts
  import missionManager from '@ohos.application.missionManager';
  import { BusinessError } from '@ohos.base';

  let testMissionId = 2;
  try {
    // Obtain the mission snapshot.
    missionManager.getMissionSnapShot('', testMissionId, (err, data) => {
      if (err) {
        console.error(`getMissionSnapShot failed. Code: ${err.code}, message: ${err.message}.`);
      } else {
        console.info(`getMissionSnapShot successfully. Data: ${JSON.stringify(data)}`);
      }
    });
  } catch (err) {
    let error = err as BusinessError;
    console.error(`getMissionSnapShot sync failed. Code: ${error.code}, message: ${error.message}.`);
  }
  ```


## missionManager.getMissionSnapShot

getMissionSnapShot(deviceId: string, missionId: number): Promise&lt;MissionSnapshot&gt;

Obtains the snapshot of a given mission. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | deviceId | string | Yes| Device ID. It is a null string by default for the local device.|
  | missionId | number | Yes| Mission ID.|

**Return value**

  | Type| Description|
  | -------- | -------- |
  | Promise&lt;[MissionSnapshot](js-apis-inner-application-missionSnapshot-sys.md)&gt; | Promise used to return the snapshot information obtained.|

**Example**

  ```ts
  import missionManager from '@ohos.application.missionManager';
  import { BusinessError } from '@ohos.base';

  let testMissionId = 2;
  try {
    // Obtain the mission snapshot.
    missionManager.getMissionSnapShot('', testMissionId).then((data) => {
      console.info(`getMissionSnapShot successfully. Data: ${JSON.stringify(data)}`);
    }).catch((error: BusinessError) => {
      console.error(`getMissionSnapShot failed. Cause: ${error.message}`);
    });
  } catch (error) {
    console.error(`getMissionSnapShot failed. Cause: ${error.message}`);
  }
  ```

## missionManager.lockMission

lockMission(missionId: number, callback: AsyncCallback&lt;void&gt;): void

Locks a given mission. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | missionId | number | Yes| Mission ID.|
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the mission is locked, **err** is **undefined**. Otherwise, **err** is an error object.|

**Example**

  ```ts
  import missionManager from '@ohos.application.missionManager';
  import { BusinessError } from '@ohos.base';

  let testMissionId = 2;
  try {
    // Lock the specified mission.
    missionManager.lockMission(testMissionId, (err, data) => {
      if (err) {
        console.error(`lockMission failed. Code: ${err.code}, message: ${err.message}.`);
      } else {
        console.info(`lockMission successfully. Data: ${JSON.stringify(data)}`);
      }
    });
  } catch (err) {
    let error = err as BusinessError;
    console.error(`lockMission sync failed. Code: ${error.code}, message: ${error.message}.`);
  }
  ```


## missionManager.lockMission

lockMission(missionId: number): Promise&lt;void&gt;

Locks a given mission. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | missionId | number | Yes| Mission ID.|

**Return value**

  | Type| Description| 
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise that returns no value.| 

**Example**

  ```ts
  import missionManager from '@ohos.application.missionManager';
  import { BusinessError } from '@ohos.base';

  let testMissionId = 2;
  try {
    // Lock the specified mission.
    missionManager.lockMission(testMissionId).then((data) => {
      console.info(`lockMission successfully. Data: ${JSON.stringify(data)}`);
    }).catch((error: BusinessError) => {
      console.error(`lockMission failed. Code: ${error.code}, message: ${error.message}.`);
    });
  } catch (error) {
    let err = error as BusinessError;
    console.error(`lockMission sync failed. Code: ${err.code}, message: ${err.message}.`);
  }
  ```


## missionManager.unlockMission

unlockMission(missionId: number, callback: AsyncCallback&lt;void&gt;): void

Unlocks a given mission. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| missionId | number | Yes| Mission ID.|
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the mission is unlocked, **err** is **undefined**. Otherwise, **err** is an error object.|

**Example**

  ```ts
  import missionManager from '@ohos.application.missionManager';
  import { BusinessError } from '@ohos.base';

  let testMissionId = 2;
  try {
    // Unlock the specified mission.
    missionManager.unlockMission(testMissionId, (err, data) => {
      if (err) {
        console.error(`unlockMission failed. Code: ${err.code}, message: ${err.message}.`);
      } else {
        console.info(`unlockMission successfully. Data: ${JSON.stringify(data)}`);
      }
    });
  } catch (err) {
    let error = err as BusinessError;
    console.error(`unlockMission sync failed. Code: ${error.code}, message: ${error.message}.`);
  }
  ```


## missionManager.unlockMission

unlockMission(missionId: number): Promise&lt;void&gt;

Unlocks a given mission. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | missionId | number | Yes| Mission ID.|

**Return value**

  | Type| Description| 
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise that returns no value.| 

**Example**

  ```ts
  import missionManager from '@ohos.application.missionManager';
  import { BusinessError } from '@ohos.base';

  let testMissionId = 2;
  try {
    // Unlock the specified mission.
    missionManager.unlockMission(testMissionId).then((data) => {
      console.info(`unlockMission successfully. Data: ${JSON.stringify(data)}`);
    }).catch((error: BusinessError) => {
      console.error(`unlockMission failed. Code: ${error.code}, message: ${error.message}.`);
    });
  } catch (error) {
    let err = error as BusinessError;
    console.error(`unlockMission sync failed. Code: ${err.code}, message: ${err.message}.`);
  }
  ```


## missionManager.clearMission

clearMission(missionId: number, callback: AsyncCallback&lt;void&gt;): void

Clears a given mission, regardless of whether it is locked. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | missionId | number | Yes| Mission ID.|
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the mission is cleared, **err** is **undefined**. Otherwise, **err** is an error object.|

**Example**

  ```ts
  import missionManager from '@ohos.application.missionManager';
  import { BusinessError } from '@ohos.base';

  let testMissionId = 2;
  try {
    // Clear the specified mission.
    missionManager.clearMission(testMissionId, (err, data) => {
      if (err) {
        console.error(`clearMission failed. Code: ${err.code}, message: ${err.message}.`);
      } else {
        console.info(`clearMission successfully. Data: ${JSON.stringify(data)}`);
      }
    });
  } catch (err) {
    let error = err as BusinessError;
    console.error(`clearMission sync failed. Code: ${error.code}, message: ${error.message}.`);
  }
  ```


## missionManager.clearMission

clearMission(missionId: number): Promise&lt;void&gt;

Clears a given mission, regardless of whether it is locked. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | missionId | number | Yes| Mission ID.|

**Return value**

  | Type| Description| 
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise that returns no value.| 

**Example**

  ```ts
  import missionManager from '@ohos.application.missionManager';
  import { BusinessError } from '@ohos.base';

  let testMissionId = 2;
  try {
    // Clear the specified mission.
    missionManager.clearMission(testMissionId).then((data) => {
      console.info(`clearMission successfully. Data: ${JSON.stringify(data)}`);
    }).catch((error: BusinessError) => {
      console.error(`clearMission failed. Code: ${error.code}, message: ${error.message}.`);
    });
  } catch (error) {
    let err = error as BusinessError;
    console.error(`clearMission sync failed. Code: ${err.code}, message: ${err.message}.`);
  }
  ```


## missionManager.clearAllMissions

clearAllMissions(callback: AsyncCallback&lt;void&gt;): void

Clears all unlocked missions. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If all the unlocked missions are cleared, **err** is **undefined**. Otherwise, **err** is an error object.|

**Example**

  ```ts
  import missionManager from '@ohos.application.missionManager';
  import { BusinessError } from '@ohos.base';

  try {
    // Clear all unlocked missions.
    missionManager.clearAllMissions(err => {
      if (err) {
        console.error(`clearAllMissions failed: ${err.message}`);
      } else {
        console.info('clearAllMissions successfully.');
      }
    });
  } catch (err) {
    let error = err as BusinessError;
    console.error(`clearAllMissions sync failed. Code: ${error.code}, message: ${error.message}.`);
  }
  ```


## missionManager.clearAllMissions

clearAllMissions(): Promise&lt;void&gt;

Clears all unlocked missions. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Return value**

  | Type| Description| 
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise that returns no value.| 

**Example**

  ```ts
  import missionManager from '@ohos.application.missionManager';
  import { BusinessError } from '@ohos.base';

  try {
    // Clear all unlocked missions.
    missionManager.clearAllMissions().then((data) => {
      console.info(`clearAllMissions successfully. Data: ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      console.error(`clearAllMissions failed. Code: ${err.code}, message: ${err.message}.`);
    });
  } catch (err) {
    let error = err as BusinessError;
    console.error(`clearAllMissions sync failed. Code: ${error.code}, message: ${error.message}.`);
  }
  ```


## missionManager.moveMissionToFront

moveMissionToFront(missionId: number, callback: AsyncCallback&lt;void&gt;): void

Switches a given mission to the foreground. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | missionId | number | Yes| Mission ID.|
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the mission is switched to the foreground, **err** is **undefined**. Otherwise, **err** is an error object.|

**Example**

  ```ts
  import missionManager from '@ohos.application.missionManager';
  import { BusinessError } from '@ohos.base';

  let testMissionId = 2;
  try {
    // Switch the specified mission to the foreground.
    missionManager.moveMissionToFront(testMissionId, (err, data) => {
      if (err) {
        console.error(`moveMissionToFront failed: ${err.message}`);
      } else {
        console.info(`moveMissionToFront successfully: ${JSON.stringify(data)}`);
      }
    });
  } catch (err) {
    let error = err as BusinessError;
    console.error(`moveMissionToFront failed. Code: ${error.code}, message: ${error.message}.`);
  }
  ```


## missionManager.moveMissionToFront

moveMissionToFront(missionId: number, options: StartOptions, callback: AsyncCallback&lt;void&gt;): void

Switches a given mission to the foreground, with the startup parameters for the switching specified. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | missionId | number | Yes| Mission ID.|
  | options | [StartOptions](js-apis-app-ability-startOptions.md) | Yes| Startup parameters, which are used to specify the window mode and device ID for switching the mission to the foreground.|
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the mission is switched to the foreground, **err** is **undefined**. Otherwise, **err** is an error object.|

**Example**

  ```ts
  import missionManager from '@ohos.application.missionManager';
  import { BusinessError } from '@ohos.base';

  let testMissionId = 2;
  try {
    // Switch the specified mission to the foreground and specify the window mode.
    missionManager.moveMissionToFront(testMissionId, { windowMode: 101 }, (err, data) => {
      if (err) {
        console.error(`moveMissionToFront failed. Code: ${err.code}, message: ${err.message}.`);
      } else {
        console.info(`moveMissionToFront successfully. Data: ${JSON.stringify(data)}`);
      }
    });
  } catch (err) {
    let error = err as BusinessError;
    console.error(`moveMissionToFront sync failed. Code: ${error.code}, message: ${error.message}.`);
  }
  ```


## missionManager.moveMissionToFront

moveMissionToFront(missionId: number, options?: StartOptions): Promise&lt;void&gt;

Switches a given mission to the foreground, with the startup parameters for the switching specified. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | missionId | number | Yes| Mission ID.|
  | options | [StartOptions](js-apis-app-ability-startOptions.md) | No | Startup parameter options, used to specify the window mode and device ID when the mission is switched to the foreground. If not specified, the system default startup parameters are used. |

**Return value**

  | Type| Description| 
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise that returns no value.| 

**Example**

  ```ts
  import missionManager from '@ohos.application.missionManager';
  import { BusinessError } from '@ohos.base';

  let testMissionId = 2;
  try {
    // Switch the specified mission to the foreground.
    missionManager.moveMissionToFront(testMissionId).then((data) => {
      console.info(`moveMissionToFront successfully. Data: ${JSON.stringify(data)}`);
    }).catch((error: BusinessError) => {
      console.error(`moveMissionToFront failed. Cause: ${error.message}`);
    });
  } catch (error) {
    console.error(`moveMissionToFront failed. Cause: ${error.message}`);
  }
  ```