# off (System API)

## Modules to Import

```TypeScript
import { missionManager } from '@kit.AbilityKit';
```

## off('mission')

```TypeScript
function off(type: 'mission', listenerId: number, callback: AsyncCallback<void>): void
```

Deregisters a mission status listener. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'mission' | Yes | Name of the target mission. The value is fixed at **'mission'**, indicating the system mission status listener. |
| listenerId | number | Yes | Index of the mission status listener to deregister. It is returned by **on()**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result and the task ID array. If the mission status listener is deregistered successfully, err is undefined; otherwise, err is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16300002](../errorcode-ability.md#16300002-nonexistent-mission-listener) | The specified mission listener does not exist. |

**Examples**

```TypeScript
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


## off('mission')

```TypeScript
function off(type: 'mission', listenerId: number): Promise<void>
```

Unregisters a mission status listener. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'mission' | Yes | Name of the target mission. The value is fixed at **'mission'**, indicating the system mission status listener. |
| listenerId | number | Yes | Index of the mission status listener to deregister. It is returned by **on()**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16300002](../errorcode-ability.md#16300002-nonexistent-mission-listener) | The specified mission listener does not exist. |

**Examples**

```TypeScript
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


## off('missionEvent')

```TypeScript
function off(type: 'missionEvent', listenerId: number, callback: AsyncCallback<void>): void
```

Deregisters a mission status listener. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** off(type: 'mission', listenerId: number, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'missionEvent' | Yes | Name of the target mission. The value is fixed at **'mission'**, indicating the system mission status listener. |
| listenerId | number | Yes | Index of the mission status listener to deregister. It is returned by **on()**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the API call is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16300002](../errorcode-ability.md#16300002-nonexistent-mission-listener) | The specified mission listener does not exist. |

**Examples**

```TypeScript
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


## off('missionEvent')

```TypeScript
function off(type: 'missionEvent', listenerId: number): Promise<void>
```

Unregisters a mission status listener. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** off(type: 'mission', listenerId: number)

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'missionEvent' | Yes | Name of the target mission. The value is fixed at **'missionEvent'**, indicating the system mission status listener. |
| listenerId | number | Yes | Index of the mission status listener to deregister. It is returned by **on()**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16300002](../errorcode-ability.md#16300002-nonexistent-mission-listener) | The specified mission listener does not exist. |

**Examples**

```TypeScript
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
