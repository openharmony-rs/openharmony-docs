# moveMissionToFront (System API)

## Modules to Import

```TypeScript
```

## moveMissionToFront

```TypeScript
function moveMissionToFront(missionId: number, callback: AsyncCallback<void>): void
```

Switches a given mission to the foreground. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [moveMissionToFront](arkts-ability-missionmanager-movemissiontofront-f-sys.md)

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| missionId | number | Yes | Mission ID. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the mission is switched to the foreground, **err** is **undefined**. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
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


<a id="movemissiontofront-1"></a>

## moveMissionToFront

```TypeScript
function moveMissionToFront(missionId: number, options: StartOptions, callback: AsyncCallback<void>): void
```

Switches a given mission to the foreground, with the startup parameters for the switching specified. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [moveMissionToFront](arkts-ability-missionmanager-movemissiontofront-f-sys.md)

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| missionId | number | Yes | Mission ID. |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md) | Yes | Startup parameters, which are used to specify the window mode and device ID for switching the mission to the foreground. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the mission is switched to the foreground, **err** is **undefined**. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
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


<a id="movemissiontofront-2"></a>

## moveMissionToFront

```TypeScript
function moveMissionToFront(missionId: number, options?: StartOptions): Promise<void>
```

Switches a given mission to the foreground, with the startup parameters for the switching specified. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [moveMissionToFront](arkts-ability-missionmanager-movemissiontofront-f-sys.md)

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| missionId | number | Yes | Mission ID. |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md) | No | Startup parameters, which are used to specify the window mode and device ID for switching the mission to the foreground. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
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
