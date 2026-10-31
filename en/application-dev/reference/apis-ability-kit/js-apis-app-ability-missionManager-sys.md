# @ohos.app.ability.missionManager (missionManager) (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @littlejerry1-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=c729316c7132777446bc2bf258a399ce6ac24a11 translatedAt=2026-09-03T10:28:13.111Z pushedAt=2026-09-05T10:47:30.428Z -->

The missionManager module provides APIs to lock, unlock, and clear missions, and switch a mission to the foreground.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module are system APIs and cannot be called by third-party applications.

## Modules to Import

```ts
import { missionManager } from '@kit.AbilityKit';
```

## Required Permissions

ohos.permission.MANAGE_MISSIONS

## missionManager.on('mission')

on(type:'mission', listener: MissionListener): number

Registers a listener to observe the mission status.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type     | string   | Yes      | Name of the target mission. The value is fixed at **'mission'**, indicating the system mission status listener.|
  | listener | [MissionListener](js-apis-inner-application-missionListener-sys.md) | Yes| Mission status listener to register.|

**Return value**

  | Type| Description|
  | -------- | -------- |
  | number | Index of the mission status listener, which is created by the system and allocated when the listener is registered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { missionManager, UIAbility, AbilityConstant, common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';

let listener: missionManager.MissionListener = {
  onMissionCreated: (mission: number) => {console.info('--------onMissionCreated-------');},
  onMissionDestroyed: (mission: number) => {console.info('--------onMissionDestroyed-------');},
  onMissionSnapshotChanged: (mission: number) => {console.info('--------onMissionSnapshotChanged-------');},
  onMissionMovedToFront: (mission: number) => {console.info('--------onMissionMovedToFront-------');},
  onMissionIconUpdated: (mission: number, icon: image.PixelMap) => {console.info('--------onMissionIconUpdated-------');},
  onMissionClosed: (mission: number) => {console.info('--------onMissionClosed-------');},
  onMissionLabelUpdated: (mission: number) => {console.info('--------onMissionLabelUpdated-------');}
};

let listenerId = -1;
let abilityWant: Want;
let context: common.UIAbilityContext;

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    console.info('[Demo] EntryAbility onCreate');
    abilityWant = want;
    context = this.context;
  }

  onDestroy() {
    try {
      if (listenerId !== -1) {
        missionManager.off('mission', listenerId).catch((error: BusinessError) => {
          console.error(`MissionManager.off failed. Code: ${error.code}, message: ${error.message}`);
        });
      }
    } catch (paramError) {
      let code = (paramError as BusinessError).code;
      let message = (paramError as BusinessError).message;
      console.error(`error: ${code}, ${message} `);
    }
    console.info('[Demo] EntryAbility onDestroy');
  }

  onWindowStageCreate(windowStage: window.WindowStage) {
    // The main window is created. Set a main page for this ability.
    console.info('[Demo] EntryAbility onWindowStageCreate');
    try {
      // Register System Mission State Listener
      listenerId = missionManager.on('mission', listener);
    } catch (paramError) {
      let code = (paramError as BusinessError).code;
      let message = (paramError as BusinessError).message;
      console.error(`error: ${code}, ${message} `);
    }

    windowStage.loadContent('pages/index', (err, data) => {
      if (err.code) {
        console.error(`Failed to load the content. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info(`Succeeded in loading the content. Data: ${JSON.stringify(data)}`);
    });
  }
}
```


## missionManager.off('mission')

off(type: 'mission', listenerId: number, callback: AsyncCallback&lt;void&gt;): void

Deregisters a mission status listener. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type     | string   | Yes      | Name of the target mission. The value is fixed at **'mission'**, indicating the system mission status listener.|
  | listenerId | number | Yes | Index of the system mission state listener, which has a one-to-one correspondence with the listener and is returned by the on method. Before using it, call [missionManager.on('mission')](#missionmanageronmission) to obtain a valid listenerId. |
  | callback | AsyncCallback&lt;void&gt; | Yes | Callback for the mission state listener unregistration event. Returns an array of mission IDs. If the mission state listener is unregistered successfully, err is undefined; otherwise, err is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16300002 | The specified mission listener does not exist. |

**Example**

```ts
import { missionManager, UIAbility, AbilityConstant, common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';

let listener: missionManager.MissionListener = {
  onMissionCreated: (mission: number) => {
    console.info('--------onMissionCreated-------');
  },
  onMissionDestroyed: (mission: number) => {
    console.info('--------onMissionDestroyed-------');
  },
  onMissionSnapshotChanged: (mission: number) => {
    console.info('--------onMissionSnapshotChanged-------');
  },
  onMissionMovedToFront: (mission: number) => {
    console.info('--------onMissionMovedToFront-------');
  },
  onMissionIconUpdated: (mission: number, icon: image.PixelMap) => {
    console.info('--------onMissionIconUpdated-------');
  },
  onMissionClosed: (mission: number) => {
    console.info('--------onMissionClosed-------');
  },
  onMissionLabelUpdated: (mission: number) => {
    console.info('--------onMissionLabelUpdated-------');
  }
};

// Index value of the listener, created by the system and assigned when the system mission state listener is registered.
let listenerId = -1;
let abilityWant: Want;
let context: common.UIAbilityContext;

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    console.info('[Demo] EntryAbility onCreate');
    abilityWant = want;
    context = this.context;
  }

  onDestroy() {
    try {
      if (listenerId !== -1) {
        // Unregister the system mission state listener.
        missionManager.off('mission', listenerId, (error: BusinessError) => {
          if (error) {
            console.error(`MissionManager.off failed, error code: ${error.code}, error msg: ${error.message}`);
            return;
          }
          console.info(`MissionManager.off success.`);
        });
      }
    } catch (paramError) {
      let code = (paramError as BusinessError).code;
      let message = (paramError as BusinessError).message;
      console.error(`error: ${code}, ${message} `);
    }
    console.info('[Demo] EntryAbility onDestroy');
  }

  onWindowStageCreate(windowStage: window.WindowStage) {
    // The main window is created. Set a main page for this ability.
    console.info('[Demo] EntryAbility onWindowStageCreate');
    try {
      // Register the system mission state listener.
      listenerId = missionManager.on('mission', listener);
    } catch (paramError) {
      let code = (paramError as BusinessError).code;
      let message = (paramError as BusinessError).message;
      console.error(`error: ${code}, ${message} `);
    }

    windowStage.loadContent('pages/index', (err: BusinessError, data) => {
      if (err.code) {
        console.error(`Failed to load the content. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info(`Succeeded in loading the content. Data: ${JSON.stringify(data)}`);
    });
  }
}
```


## missionManager.off('mission')

off(type: 'mission', listenerId: number): Promise&lt;void&gt;

Unregisters a mission status listener. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type     | string   | Yes      | Name of the target mission. The value is fixed at **'mission'**, indicating the system mission status listener.|
  | listenerId | number | Yes | Index of the system mission state listener, which has a one-to-one correspondence with the listener and is returned by the on method. Before using it, call [missionManager.on('mission')](#missionmanageronmission) to obtain a valid listenerId. |

**Return value**

  | Type| Description|
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16300002 | The specified mission listener does not exist. |

**Example**

```ts
import { missionManager, UIAbility, AbilityConstant, common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';

let listener: missionManager.MissionListener = {
  onMissionCreated: (mission: number) => {
    console.info('--------onMissionCreated-------');
  },
  onMissionDestroyed: (mission: number) => {
    console.info('--------onMissionDestroyed-------');
  },
  onMissionSnapshotChanged: (mission: number) => {
    console.info('--------onMissionSnapshotChanged-------');
  },
  onMissionMovedToFront: (mission: number) => {
    console.info('--------onMissionMovedToFront-------');
  },
  onMissionIconUpdated: (mission: number, icon: image.PixelMap) => {
    console.info('--------onMissionIconUpdated-------');
  },
  onMissionClosed: (mission: number) => {
    console.info('--------onMissionClosed-------');
  },
  onMissionLabelUpdated: (mission: number) => {
    console.info('--------onMissionLabelUpdated-------');
  }
};

let listenerId = -1;
let abilityWant: Want;
let context: common.UIAbilityContext;

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    console.info('[Demo] EntryAbility onCreate');
    abilityWant = want;
    context = this.context;
  }

  onDestroy() {
    try {
      if (listenerId !== -1) {
        missionManager.off('mission', listenerId).catch((error: BusinessError) => {
          console.error(`MissionManager.off failed, Code: ${error.code}, message: ${error.message}.`);
        });
      }
    } catch (paramError) {
      let code = (paramError as BusinessError).code;
      let message = (paramError as BusinessError).message;
      console.error(`error: ${code}, ${message} `);
    }
    console.info('[Demo] EntryAbility onDestroy');
  }

  onWindowStageCreate(windowStage: window.WindowStage) {
    // The main window is created. Set a main page for this ability.
    console.info('[Demo] EntryAbility onWindowStageCreate');
    try {
      // Register System Mission State Listener
      listenerId = missionManager.on('mission', listener);
    } catch (paramError) {
      let code = (paramError as BusinessError).code;
      let message = (paramError as BusinessError).message;
      console.error(`error: ${code}, ${message} `);
    }

    windowStage.loadContent('pages/index', (err: BusinessError, data) => {
      if (err.code) {
        console.error(`Failed to load the content. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info(`Succeeded in loading the content. Data: ${JSON.stringify(data)}`);
    });
  }
}
```

## missionManager.getMissionInfo

getMissionInfo(deviceId: string, missionId: number, callback: AsyncCallback&lt;MissionInfo&gt;): void

Obtains the mission information. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | deviceId | string | Yes| Device ID. It is a null string by default for the local device.|
  | missionId | number | Yes| Mission ID.|
  | callback | AsyncCallback&lt;[MissionInfo](js-apis-inner-application-missionInfo-sys.md)&gt; | Yes| Callback used to return the mission information obtained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let testMissionId = 1;

// Get all mission information.
missionManager.getMissionInfos('', 10)
  .then((allMissions: Array<missionManager.MissionInfo>) => {
    try {
      if (allMissions && allMissions.length > 0) {
        testMissionId = allMissions[0].missionId;
      }

      missionManager.getMissionInfo('', testMissionId, (error: BusinessError, mission: missionManager.MissionInfo) => {
        if (error) {
          console.error(`getMissionInfo failed, error.code: ${error.code}, error.message: ${error.message}`);
        } else {
          console.info(`mission.missionId = ${mission.missionId}`);
          console.info(`mission.runningState = ${mission.runningState}`);
          console.info(`mission.lockedState = ${mission.lockedState}`);
          console.info(`mission.timestamp = ${mission.timestamp}`);
          console.info(`mission.label = ${mission.label}`);
          console.info(`mission.iconPath = ${mission.iconPath}`);
        }
      });
    } catch (paramError) {
      let code = (paramError as BusinessError).code;
      let message = (paramError as BusinessError).message;
      console.error(`error: ${code}, ${message} `);
    }
  })
  .catch((error: BusinessError) => {
    console.error(`getMissionInfos failed, Code: ${error.code}, message: ${error.message}.`);
  });
```

## missionManager.getMissionInfo

getMissionInfo(deviceId: string, missionId: number): Promise&lt;MissionInfo&gt;

Obtains the mission information. This API uses a promise to return the result.

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

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let testMissionId = 1;

try {
  missionManager.getMissionInfo('', testMissionId)
    .then((data: missionManager.MissionInfo) => {
      console.info(`getMissionInfo successfully. Data: ${JSON.stringify(data)}`);
    })
    .catch((error: BusinessError) => {
      console.error(`getMissionInfo failed. Code: ${error.code}, message: ${error.message}`);
    });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`getMissionInfo failed. Code: ${err.code}, message: ${err.message}`);
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
  | callback | AsyncCallback&lt;Array&lt;[MissionInfo](js-apis-inner-application-missionInfo-sys.md)&gt;&gt; | Yes| Callback used to return the array of mission information obtained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Obtain all mission information.
  missionManager.getMissionInfos('', 10, (error: BusinessError, missions: Array<missionManager.MissionInfo>) => {
    if (error) {
      console.error(`getMissionInfos failed, error.code: ${error.code}, error.message: ${error.message}`);
    } else {
      console.info(`size = ${missions.length}`);
      console.info(`missions = ${JSON.stringify(missions)}`);
    }
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`getMissionInfos failed, error code: ${code}, error msg: ${message}.`);
}
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

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Get all mission information.
  missionManager.getMissionInfos('', 10).then((data: Array<missionManager.MissionInfo>) => {
    console.info(`getMissionInfos successfully. Data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`getMissionInfos failed. Code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`getMissionInfos failed. Code: ${err.code}, message: ${err.message}`);
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
  | callback | AsyncCallback&lt;[MissionSnapshot](js-apis-inner-application-missionSnapshot-sys.md)&gt; | Yes| Callback used to return the snapshot information obtained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**
```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// testMissionId is the mission ID, which can be obtained through the getMissionInfos API to get a real and valid mission ID.
let testMissionId = 2;

try {
  missionManager.getMissionSnapShot('', testMissionId, (err: BusinessError, data: missionManager.MissionSnapshot) => {
    if (err) {
      console.error(`getMissionSnapShot failed. Code: ${err.code}, message: ${err.message}.`);
    } else {
      console.info(`getMissionSnapShot successfully: ${JSON.stringify(data)}`);
    }
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`getMissionSnapShot failed. Code: ${err.code}, message: ${err.message}.`);
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

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**
```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// testMissionId is the mission ID, which can be obtained through the getMissionInfos API.
let testMissionId = 2;

try {
  missionManager.getMissionSnapShot('', testMissionId).then((data: missionManager.MissionSnapshot) => {
    console.info(`getMissionSnapShot successfully. Data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`getMissionSnapShot failed. Code: ${error.code}, message: ${error.message}.`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`getMissionSnapShot failed. Code: ${err.code}, message: ${err.message}.`);
}
```

## missionManager.getLowResolutionMissionSnapShot

getLowResolutionMissionSnapShot(deviceId: string, missionId: number, callback: AsyncCallback\<MissionSnapshot>): void

Obtains the low-resolution snapshot of a given mission. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | deviceId | string | Yes| Device ID. It is a null string by default for the local device.|
  | missionId | number | Yes| Mission ID.|
  | callback | AsyncCallback&lt;[MissionSnapshot](js-apis-inner-application-missionSnapshot-sys.md)&gt; | Yes| Callback used to return the snapshot information obtained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**
```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// testMissionId is the mission ID. You can obtain a valid mission ID through the getMissionInfos API.
let testMissionId = 2;

try {
  missionManager.getLowResolutionMissionSnapShot('', testMissionId,
    (err: BusinessError, data: missionManager.MissionSnapshot) => {
      if (err) {
        console.error(`getLowResolutionMissionSnapShot failed. Code: ${err.code}, message: ${err.message}.`);
      } else {
        console.info(`getLowResolutionMissionSnapShot successfully: ${JSON.stringify(data)}`);
      }
    });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`getLowResolutionMissionSnapShot failed. Code: ${err.code}, message: ${err.message}.`);
}
```

## missionManager.getLowResolutionMissionSnapShot

getLowResolutionMissionSnapShot(deviceId: string, missionId: number): Promise\<MissionSnapshot>

Obtains the low-resolution snapshot of a given mission. This API uses a promise to return the result.

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

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// testMissionId is the mission ID, which can be obtained through the getMissionInfos API.
let testMissionId = 2;

try {
  missionManager.getLowResolutionMissionSnapShot('', testMissionId).then((data: missionManager.MissionSnapshot) => {
    console.info(`getLowResolutionMissionSnapShot successfully. Data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`getLowResolutionMissionSnapShot failed. Code: ${error.code}, message: ${error.message}.`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`getLowResolutionMissionSnapShot failed. Code: ${err.code}, message: ${err.message}.`);
}
```


## missionManager.lockMission

lockMission(missionId: number, callback: AsyncCallback&lt;void&gt;): void

Locks the mission with the specified mission ID. This API is applicable to scenarios where a mission needs to be kept from being cleared, for example, a system management application locks a key mission when it needs to keep running in the background. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | missionId | number | Yes| Mission ID.|
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16300001 | Mission not found. |

**Example**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// testMissionId is the mission ID, which can be obtained through the getMissionInfos API to get a real and valid mission ID.
let testMissionId = 2;

try {
  missionManager.lockMission(testMissionId, (err: BusinessError, data: void) => {
    if (err) {
      console.error(`lockMission failed. Code: ${err.code}, message: ${err.message}.`);
    } else {
      console.info(`lockMission successfully: ${JSON.stringify(data)}`);
    }
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`lockMission failed. Code: ${err.code}, message: ${err.message}.`);
}
```

## missionManager.lockMission

lockMission(missionId: number): Promise&lt;void&gt;

Locks the mission with the specified mission ID. This API is applicable to scenarios where a mission needs to be kept from being cleared, for example, a system management application locks a key mission when it needs to keep running in the background. This API uses a promise to return the result.

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

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16300001 | Mission not found. |

**Example**
```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// testMissionId is the mission ID, which can be obtained through the getMissionInfos API.
let testMissionId = 2;

try {
  missionManager.lockMission(testMissionId).then((data: void) => {
    console.info(`lockMission successfully. Data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`lockMission failed. Code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`lockMission failed. Code: ${err.code}, message: ${err.message}`);
}
```

## missionManager.unlockMission

unlockMission(missionId: number, callback: AsyncCallback&lt;void&gt;): void

Unlocks the mission with the specified mission ID. This API is applicable to scenarios where a locked mission is allowed to be cleared by the system normally, for example, a system management application unlocks a mission when it no longer needs to keep the mission running in the background. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| missionId | number | Yes| Mission ID.|
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16300001 | Mission not found. |

**Example**
```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// testMissionId is the mission ID, which can be obtained through the getMissionInfos API.
let testMissionId = 2;

try {
  missionManager.unlockMission(testMissionId, (err: BusinessError, data: void) => {
    if (err) {
      console.error(`unlockMission failed. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info(`unlockMission successfully: ${JSON.stringify(data)}`);
    }
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`unlockMission failed. Code: ${err.code}, message: ${err.message}`);
}
```

## missionManager.unlockMission

unlockMission(missionId: number): Promise&lt;void&gt;

Unlocks the mission with the specified mission ID. This API is applicable to scenarios where a locked mission is allowed to be cleared by the system normally, for example, a system management application unlocks a mission when it no longer needs to keep the mission running in the background. This API uses a promise to return the result.

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

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16300001 | Mission not found. |

**Example**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// testMissionId is the mission ID, which can be obtained through the getMissionInfos API.
let testMissionId = 2;

try {
  missionManager.unlockMission(testMissionId).then((data: void) => {
    console.info(`unlockMission successfully. Data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`unlockMission failed. Code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`unlockMission failed. Code: ${err.code}, message: ${err.message}`);
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
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// testMissionId is the mission ID, which can be obtained through the getMissionInfos API to get a real and valid mission ID.
let testMissionId = 2;

try {
  missionManager.clearMission(testMissionId, (err: BusinessError, data: void) => {
    if (err) {
      console.error(`clearMission failed. Code: ${err.code}, message: ${err.message}.`);
    } else {
      console.info(`clearMission successfully: ${JSON.stringify(data)}`);
    }
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`clearMission failed. Code: ${err.code}, message: ${err.message}.`);
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

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// testMissionId is the mission ID, which can be obtained through the getMissionInfos API.
let testMissionId = 2;

try {
  missionManager.clearMission(testMissionId).then((data: void) => {
    console.info(`clearMission successfully. Data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`clearMission failed. Code: ${error.code}, message: ${error.message}.`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`clearMission failed. Code: ${err.code}, message: ${err.message}.`);
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
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  missionManager.clearAllMissions((err: BusinessError) => {
    if (err) {
      console.error(`clearAllMissions failed. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('clearAllMissions successfully.');
    }
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`clearAllMissions failed. Code: ${err.code}, message: ${err.message}`);
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

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201 | Permission denied. |
| 202 | Not system application. |

**Example**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  missionManager.clearAllMissions().then((data: void) => {
    console.info(`clearAllMissions successfully. Data: ${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
    console.error(`clearAllMissions failed. Code: ${err.code}, message: ${err.message}.`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`clearAllMissions failed. Code: ${err.code}, message: ${err.message}.`);
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
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |

**Example**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// testMissionId is the mission ID. Obtain a valid mission ID through the getMissionInfos API.
let testMissionId = 2;

try {
  missionManager.moveMissionToFront(testMissionId, (err: BusinessError, data: void) => {
    if (err) {
      console.error(`moveMissionToFront failed. Code: ${err.code}, message: ${err.message}.`);
    } else {
      console.info(`moveMissionToFront successfully: ${JSON.stringify(data)}`);
    }
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`moveMissionToFront failed. Code: ${err.code}, message: ${err.message}.`);
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
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |

**Example**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// testMissionId is the mission ID, which can be obtained through the getMissionInfos API.
let testMissionId = 2;

try {
  missionManager.moveMissionToFront(testMissionId, { windowMode: 101 }, (err: BusinessError, data: void) => {
    if (err) {
      console.error(`moveMissionToFront failed. Code: ${err.code}, message: ${err.message}.`);
    } else {
      console.info(`moveMissionToFront successfully: ${JSON.stringify(data)}`);
    }
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`moveMissionToFront failed. Code: ${err.code}, message: ${err.message}.`);
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
  | options | [StartOptions](js-apis-app-ability-startOptions.md) | No| Startup parameters, which are used to specify the window mode and device ID for switching the mission to the foreground. By default, no value is passed in, indicating that the default startup parameters are used.|

**Return value**

  | Type| Description|
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |

**Example**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// testMissionId is the mission ID. Obtain a valid mission ID through the getMissionInfos API.
let testMissionId = 2;

try {
  missionManager.moveMissionToFront(testMissionId).then((data: void) => {
    console.info(`moveMissionToFront successfully. Data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`moveMissionToFront failed. Code: ${error.code}, message: ${error.message}.`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`moveMissionToFront failed. Code: ${err.code}, Cause: ${err.message}.`);
}
```

## missionManager.moveMissionsToForeground<sup>10+</sup>

moveMissionsToForeground(missionIds: Array&lt;number&gt;, callback: AsyncCallback&lt;void&gt;): void

Switches a batch of missions to the foreground. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | missionIds | Array&lt;number&gt; | Yes| Array holding the mission IDs.|
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
import { abilityManager, missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  missionManager.getMissionInfos("", 10, (error: BusinessError, missionInfos: Array<missionManager.MissionInfo>) => {
    if (error.code) {
      console.error(`getMissionInfos failed, Code: ${error.code}, message: ${error.message}.`);
      return;
    }
    if (missionInfos.length < 1) {
      return;
    }

    let toShows = new Array<number>();
    for (let missionInfo of missionInfos) {
      if (missionInfo.abilityState == abilityManager.AbilityState.BACKGROUND) {
        toShows.push(missionInfo.missionId);
      }
    }
    // Move the specified missions to the foreground in batches.
    missionManager.moveMissionsToForeground(toShows, (err: BusinessError, data: void) => {
      if (err) {
        console.error(`moveMissionsToForeground failed. Code: ${err.code}, message: ${err.message}.`);
      } else {
        console.info(`moveMissionsToForeground successfully: ${JSON.stringify(data)}`);
      }
    });
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message} `);
}
```

## missionManager.moveMissionsToForeground<sup>10+</sup>

moveMissionsToForeground(missionIds: Array&lt;number&gt;, topMission: number, callback: AsyncCallback&lt;void&gt;): void

Switches a batch of missions to the foreground, and moves the mission with the specified ID to the top. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | missionIds | Array&lt;number&gt; | Yes| Array holding the mission IDs.|
  | topMission | number | Yes | Mission ID of the mission to move to the top. The value -1 indicates that no specific mission is specified, and the system moves the mission to the top based on the default logic. |
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
import { abilityManager, missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  missionManager.getMissionInfos("", 10, (error: BusinessError, missionInfos: Array<missionManager.MissionInfo>) => {
    if (error.code) {
      console.error(`getMissionInfos failed, Code: ${error.code}, message: ${error.message}.`);
      return;
    }
    if (missionInfos.length < 1) {
      return;
    }

    let toShows = new Array<number>();
    for (let missionInfo of missionInfos) {
      if (missionInfo.abilityState == abilityManager.AbilityState.BACKGROUND) {
        toShows.push(missionInfo.missionId);
      }
    }
    // Move the specified missions to the foreground in batches, and move the first mission to the top.
    missionManager.moveMissionsToForeground(toShows, toShows[0], (err: BusinessError, data: void) => {
      if (err) {
        console.error(`moveMissionsToForeground failed. Code: ${err.code}, message: ${err.message}.`);
      } else {
        console.info(`moveMissionsToForeground successfully`);
      }
    });
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message} `);
}
```

## missionManager.moveMissionsToForeground<sup>10+</sup>

moveMissionsToForeground(missionIds: Array&lt;number&gt;, topMission?: number): Promise&lt;void&gt;

Switches a batch of missions to the foreground, and moves the mission with the specified ID to the top. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | missionIds | Array&lt;number&gt; | Yes| Array holding the mission IDs.|
  | topMission | number | No | Mission ID of the mission to move to the top. The default value is -1, which means no specific mission is specified, and the system moves the mission to the top based on the default logic. |

**Return value**

  | Type| Description|
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
import { abilityManager, missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  missionManager.getMissionInfos("", 10, (error: BusinessError, missionInfos: Array<missionManager.MissionInfo>) => {
    if (error.code) {
      console.error(`getMissionInfos failed, error code: ${error.code}, error msg: ${error.message}`);
      return;
    }
    if (missionInfos.length < 1) {
      return;
    }

    let toShows = new Array<number>();
    for (let missionInfo of missionInfos) {
      if (missionInfo.abilityState == abilityManager.AbilityState.BACKGROUND) {
        toShows.push(missionInfo.missionId);
      }
    }
    missionManager.moveMissionsToForeground(toShows, toShows[0]).then(() => {
      console.info(`moveMissionsToForeground is called`);
    });
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message} `);
}
```

## missionManager.moveMissionsToBackground<sup>10+</sup>

moveMissionsToBackground(missionIds: Array&lt;number&gt;, callback: AsyncCallback&lt;Array&lt;number&gt;&gt;): void

Moves the specified missions to the background in batches. The returned mission ID array is sorted by the mission hierarchy at the time the missions are hidden. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | missionIds | Array&lt;number&gt; | Yes| Array holding the mission IDs.|
  | callback | AsyncCallback&lt;Array&lt;number&gt;&gt; | Yes| Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
import { abilityManager, missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  missionManager.getMissionInfos("", 10, (error: BusinessError, missionInfos: Array<missionManager.MissionInfo>) => {
    if (error.code) {
      console.error(`getMissionInfos failed, error code: ${error.code}, error msg: ${error.message}`);
      return;
    }

    let toHides = new Array<number>();
    for (let missionInfo of missionInfos) {
      if (missionInfo.abilityState == abilityManager.AbilityState.FOREGROUND) {
        toHides.push(missionInfo.missionId);
      }
    }
    missionManager.moveMissionsToBackground(toHides, (err: BusinessError, data: Array<number>) => {
      if (err) {
        console.error(`moveMissionsToBackground failed. Code: ${err.code}, message: ${err.message}.`);
      } else {
        console.info(`moveMissionsToBackground successfully: ${JSON.stringify(data)}`);
      }
    });
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message} `);
}
```

## missionManager.moveMissionsToBackground<sup>10+</sup>

moveMissionsToBackground(missionIds : Array&lt;number&gt;): Promise&lt;Array&lt;number&gt;&gt;

Moves the specified missions to the background in batches. The returned mission ID array is sorted by the mission hierarchy at the time the missions are hidden. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | missionIds | Array&lt;number&gt; | Yes| Array holding the mission IDs.|

**Return value**

  | Type| Description|
  | -------- | -------- |
  | Promise&lt;Array&lt;number&gt;&gt; | Promise object that returns an array of mission IDs. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
import { abilityManager, missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  missionManager.getMissionInfos("", 10, (error: BusinessError, missionInfos: Array<missionManager.MissionInfo>) => {
    if (error.code) {
      console.error(`getMissionInfos failed, error code: ${error.code}, error msg: ${error.message}`);
      return;
    }

    let toHides = new Array<number>();
    for (let missionInfo of missionInfos) {
      if (missionInfo.abilityState == abilityManager.AbilityState.FOREGROUND) {
        toHides.push(missionInfo.missionId);
      }
    }
    missionManager.moveMissionsToBackground(toHides).then((hideRes: Array<number>) => {
      console.info(`moveMissionsToBackground is called, res: ${JSON.stringify(hideRes)}`);
    });
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message} `);
}
```

## missionManager.on('missionEvent')<sup>(deprecated)</sup>

on(type:'missionEvent', listener: MissionListener): number

Registers a system mission state listener.

> **NOTE**
>
> Supported since API version 9, deprecated since API version 10. You are advised to use [missionManager.on('mission')](#missionmanageronmission) instead.

**Required permission:** ohos.permission.MANAGE_MISSIONS

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | type     | string   | Yes       | Name of the mission to listen for. Fixed value: 'missionEvent', indicating a system mission state listener. |
  | listener | [MissionListener](js-apis-inner-application-missionListener-sys.md) | Yes | System mission listener. |

**Return value**

  | Type | Description |
  | -------- | -------- |
  | number | Index of the listener, which is created by the system and assigned when the system mission state listener is registered. It has a one-to-one correspondence with the listener&nbsp;. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| ------- | -------------------------------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { missionManager, UIAbility, AbilityConstant, common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';

let listener: missionManager.MissionListener = {
  onMissionCreated: (missionEvent: number) => {console.info('--------onMissionCreated-------');},
  onMissionDestroyed: (missionEvent: number) => {console.info('--------onMissionDestroyed-------');},
  onMissionSnapshotChanged: (missionEvent: number) => {console.info('--------onMissionSnapshotChanged-------');},
  onMissionMovedToFront: (missionEvent: number) => {console.info('--------onMissionMovedToFront-------');},
  onMissionIconUpdated: (missionEvent: number, icon: image.PixelMap) => {console.info('--------onMissionIconUpdated-------');},
  onMissionClosed: (missionEvent: number) => {console.info('--------onMissionClosed-------');},
  onMissionLabelUpdated: (missionEvent: number) => {console.info('--------onMissionLabelUpdated-------');}
};

let listenerId = -1;
let abilityWant: Want;
let context: common.UIAbilityContext;

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    console.info('[Demo] EntryAbility onCreate');
    abilityWant = want;
    context = this.context;
  }

  onDestroy() {
    try {
      if (listenerId !== -1) {
        missionManager.off('missionEvent', listenerId).catch((error: BusinessError) => {
          console.error(`MissionManager.off failed. Code: ${error.code}, message: ${error.message}`);
        });
      }
    } catch (paramError) {
      let code = (paramError as BusinessError).code;
      let message = (paramError as BusinessError).message;
      console.error(`error: ${code}, ${message} `);
    }
    console.info('[Demo] EntryAbility onDestroy');
  }

  onWindowStageCreate(windowStage: window.WindowStage) {
    // Main window is created, set main page for this ability
    console.info('[Demo] EntryAbility onWindowStageCreate');
    try {
      listenerId = missionManager.on('missionEvent', listener);
    } catch (paramError) {
      let code = (paramError as BusinessError).code;
      let message = (paramError as BusinessError).message;
      console.error(`error: ${code}, ${message} `);
    }

    windowStage.loadContent('pages/index', (err, data) => {
      if (err.code) {
        console.error(`Failed to load the content. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info(`Succeeded in loading the content. Data: ${JSON.stringify(data)}`);
    });
  }
}
```


## missionManager.off('missionEvent')<sup>(deprecated)</sup>

off(type: 'missionEvent', listenerId: number, callback: AsyncCallback&lt;void&gt;): void

Unregisters the mission state listener. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. You are advised to use [missionManager.off('mission')](#missionmanageroffmission) instead.

**Required permission**: ohos.permission.MANAGE_MISSIONS

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | type     | string   | Yes       | Name of the mission for which the listener is unregistered. Fixed value: 'missionEvent', which indicates the system mission state listener. |
  | listenerId | number | Yes | Index of the system mission state listener, which has a one-to-one correspondence with the listener and is returned by the on method. |
  | callback | AsyncCallback&lt;void&gt; | Yes | Callback for the mission state listener unregistration event. If the mission state listener is unregistered successfully, err is undefined; otherwise, err is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID | Error Message |
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16300002 | The specified missionEvent listener does not exist. |

**Example**

```ts
import { missionManager, UIAbility, AbilityConstant, common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';

let listener: missionManager.MissionListener = {
  onMissionCreated: (missionEvent: number) => {
    console.info('--------onMissionCreated-------');
  },
  onMissionDestroyed: (missionEvent: number) => {
    console.info('--------onMissionDestroyed-------');
  },
  onMissionSnapshotChanged: (missionEvent: number) => {
    console.info('--------onMissionSnapshotChanged-------');
  },
  onMissionMovedToFront: (missionEvent: number) => {
    console.info('--------onMissionMovedToFront-------');
  },
  onMissionIconUpdated: (missionEvent: number, icon: image.PixelMap) => {
    console.info('--------onMissionIconUpdated-------');
  },
  onMissionClosed: (missionEvent: number) => {
    console.info('--------onMissionClosed-------');
  },
  onMissionLabelUpdated: (missionEvent: number) => {
    console.info('--------onMissionLabelUpdated-------');
  }
};

let listenerId = -1;
let abilityWant: Want;
let context: common.UIAbilityContext;

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    console.info('[Demo] EntryAbility onCreate');
    abilityWant = want;
    context = this.context;
  }

  onDestroy() {
    try {
      if (listenerId !== -1) {
        missionManager.off('missionEvent', listenerId, (error: BusinessError) => {
          if (error) {
            console.error(`MissionManager.off failed, error code: ${error.code}, error msg: ${error.message}`);
            return;
          }
          console.info(`MissionManager.off success.`);
        });
      }
    } catch (paramError) {
      let code = (paramError as BusinessError).code;
      let message = (paramError as BusinessError).message;
      console.error(`error: ${code}, ${message} `);
    }
    console.info('[Demo] EntryAbility onDestroy');
  }

  onWindowStageCreate(windowStage: window.WindowStage) {
    // Main window is created, set main page for this ability
    console.info('[Demo] EntryAbility onWindowStageCreate');
    try {
      listenerId = missionManager.on('missionEvent', listener);
    } catch (paramError) {
      let code = (paramError as BusinessError).code;
      let message = (paramError as BusinessError).message;
      console.error(`error: ${code}, ${message} `);
    }

    windowStage.loadContent('pages/index', (err: BusinessError, data) => {
      if (err.code) {
        console.error(`Failed to load the content. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info(`Succeeded in loading the content. Data: ${JSON.stringify(data)}`);
    });
  }
}
```

## missionManager.off('missionEvent')<sup>(deprecated)</sup>

off(type: 'missionEvent', listenerId: number): Promise&lt;void&gt;

Unregisters the mission state listener. This API uses a promise to return the result asynchronously.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. You are advised to use [missionManager.off('mission')](#missionmanageroffmission-1) instead.

**Required permission:** ohos.permission.MANAGE_MISSIONS

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | type     | string   | Yes       | Name of the mission for which the listener is unregistered. Fixed value: 'missionEvent', which indicates the system mission state listener. |
  | listenerId | number | Yes | Index of the system mission state listener, which has a one-to-one correspondence with the listener and is returned by the on method. |

**Return value**

  | Type | Description |
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID | Error Message |
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16300002 | The specified missionEvent listener does not exist. |

**Example**

```ts
import { missionManager, UIAbility, AbilityConstant, common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';

let listener: missionManager.MissionListener = {
  onMissionCreated: (missionEvent: number) => {
    console.info('--------onMissionCreated-------');
  },
  onMissionDestroyed: (missionEvent: number) => {
    console.info('--------onMissionDestroyed-------');
  },
  onMissionSnapshotChanged: (missionEvent: number) => {
    console.info('--------onMissionSnapshotChanged-------');
  },
  onMissionMovedToFront: (missionEvent: number) => {
    console.info('--------onMissionMovedToFront-------');
  },
  onMissionIconUpdated: (missionEvent: number, icon: image.PixelMap) => {
    console.info('--------onMissionIconUpdated-------');
  },
  onMissionClosed: (missionEvent: number) => {
    console.info('--------onMissionClosed-------');
  },
  onMissionLabelUpdated: (missionEvent: number) => {
    console.info('--------onMissionLabelUpdated-------');
  }
};

let listenerId = -1;
let abilityWant: Want;
let context: common.UIAbilityContext;

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    console.info('[Demo] EntryAbility onCreate');
    abilityWant = want;
    context = this.context;
  }

  onDestroy() {
    try {
      if (listenerId !== -1) {
        missionManager.off('missionEvent', listenerId).catch((error: BusinessError) => {
          console.error(`MissionManager.off failed, Code: ${error.code}, message: ${error.message}.`);
        });
      }
    } catch (paramError) {
      let code = (paramError as BusinessError).code;
      let message = (paramError as BusinessError).message;
      console.error(`error: ${code}, ${message} `);
    }
    console.info('[Demo] EntryAbility onDestroy');
  }

  onWindowStageCreate(windowStage: window.WindowStage) {
    // Main window is created, set main page for this ability
    console.info('[Demo] EntryAbility onWindowStageCreate');
    try {
      listenerId = missionManager.on('missionEvent', listener);
    } catch (paramError) {
      let code = (paramError as BusinessError).code;
      let message = (paramError as BusinessError).message;
      console.error(`error: ${code}, ${message} `);
    }

    windowStage.loadContent('pages/index', (err: BusinessError, data) => {
      if (err.code) {
        console.error(`Failed to load the content. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info(`Succeeded in loading the content. Data: ${JSON.stringify(data)}`);
    });
  }
}
```
## MissionInfo<sup>9+</sup>

type MissionInfo = _MissionInfo

Represents the detailed information about a mission.

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

| Type | Description |
| --- | --- |
| [_MissionInfo](js-apis-inner-application-missionInfo-sys.md) | Represents the detailed information about a mission. |

## MissionListener<sup>9+</sup>

type MissionListener = _MissionListener

System mission state listener.

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

| Type | Description |
| --- | --- |
| [_MissionListener](js-apis-inner-application-missionListener-sys.md) | System mission state listener. |

## MissionSnapshot<sup>9+</sup>

type MissionSnapshot = _MissionSnapshot

Mission snapshot information.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**System API**: This is a system API.

| Type | Description |
| --- | --- |
| [_MissionSnapshot](js-apis-inner-application-missionSnapshot-sys.md) | Mission snapshot information. |
