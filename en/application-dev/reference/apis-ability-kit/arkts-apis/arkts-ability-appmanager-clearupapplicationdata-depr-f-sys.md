# clearUpApplicationData (System API)

## Modules to Import

```TypeScript
```

## clearUpApplicationData

```TypeScript
function clearUpApplicationData(bundleName: string): Promise<void>
```

Clear up application data by bundle name

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [clearUpApplicationData](arkts-ability-appmanager-clearupapplicationdata-f-sys.md)

**Required permissions:** ohos.permission.CLEAN_APPLICATION_DATA

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | bundle name. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Examples**

```TypeScript
import appManager from '@ohos.application.appManager';
import { BusinessError } from '@ohos.base';

let bundleName = 'bundleName';

function clearUpApplicationDataCallback(err: BusinessError, data: void) {
  if (err) {
    console.error(`ClearUpApplicationDataCallback failed, error code: ${err.code}, error msg: ${err.message}.`);
  } else {
    console.info(`ClearUpApplicationDataCallback success, data: ${JSON.stringify(data)}.`);
  }
}

appManager.clearUpApplicationData(bundleName, clearUpApplicationDataCallback);
```

```TypeScript
import appManager from '@ohos.application.appManager';
import { BusinessError } from '@ohos.base';

let bundleName = 'bundleName';
appManager.clearUpApplicationData(bundleName)
  .then((data) => {
    console.info(`ClearUpApplicationData success, data: ${JSON.stringify(data)}.`);
  })
  .catch((err: BusinessError) => {
    console.error(`ClearUpApplicationData failed, error code: ${err.code}, error msg: ${err.message}.`);
  });
```


## clearUpApplicationData

```TypeScript
function clearUpApplicationData(bundleName: string, callback: AsyncCallback<void>)
```

Clear up application data by bundle name

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [clearUpApplicationData](arkts-ability-appmanager-clearupapplicationdata-f-sys.md)

**Required permissions:** ohos.permission.CLEAN_APPLICATION_DATA

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | bundle name. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Represents the specified callback method. |

**Examples**

See [clearUpApplicationData](#clearupapplicationdata)
