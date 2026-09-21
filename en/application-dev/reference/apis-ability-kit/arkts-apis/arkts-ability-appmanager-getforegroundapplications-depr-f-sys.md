# getForegroundApplications (System API)

## Modules to Import

```TypeScript
```

## getForegroundApplications

```TypeScript
function getForegroundApplications(callback: AsyncCallback<Array<AppStateData>>): void
```

getForegroundApplications.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getForegroundApplications](arkts-ability-appmanager-getforegroundapplications-f-sys.md)

**Required permissions:** ohos.permission.GET_RUNNING_INFO

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[AppStateData](arkts-ability-appstatedata-c.md)&gt;&gt; | Yes | Return all application information currently in the foreground in the form of callback. |

**Examples**

```TypeScript
import appManager from '@ohos.application.appManager';

appManager.getForegroundApplications((err, data) => {
  if (err) {
    console.error(`GetForegroundApplications failed, error code: ${err.code}, error msg: ${err.message}.`);
  } else {
    console.info(`GetForegroundApplications success, data: ${JSON.stringify(data)}.`);
  }
});
```


<a id="getforegroundapplications-1"></a>

## getForegroundApplications

```TypeScript
function getForegroundApplications(): Promise<Array<AppStateData>>
```

getForegroundApplications.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getForegroundApplications](arkts-ability-appmanager-getforegroundapplications-f-sys.md)

**Required permissions:** ohos.permission.GET_RUNNING_INFO

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[AppStateData](arkts-ability-appstatedata-c.md)&gt;&gt; | Returns the list of AppStateData. |

**Examples**

```TypeScript
import appManager from '@ohos.application.appManager';
import { BusinessError } from '@ohos.base';

appManager.getForegroundApplications()
  .then((data) => {
    console.info(`GetForegroundApplications success, data: ${JSON.stringify(data)}.`);
  })
  .catch((err: BusinessError) => {
    console.error(`GetForegroundApplications failed, error code: ${err.code}, error msg: ${err.message}.`);
  });
```
