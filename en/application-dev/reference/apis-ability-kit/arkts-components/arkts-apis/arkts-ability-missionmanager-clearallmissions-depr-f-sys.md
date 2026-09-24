# clearAllMissions (System API)

## Modules to Import

```TypeScript
```

## clearAllMissions

```TypeScript
function clearAllMissions(callback: AsyncCallback<void>): void
```

Clears all unlocked missions. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [clearAllMissions](arkts-ability-missionmanager-clearallmissions-f-sys.md)

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If all the unlocked missions are cleared, **err** is **undefined**. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
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


<a id="clearallmissions-1"></a>

## clearAllMissions

```TypeScript
function clearAllMissions(): Promise<void>
```

Clears all unlocked missions. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [clearAllMissions](arkts-ability-missionmanager-clearallmissions-f-sys.md)

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
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
