# getAppMemorySize

## Modules to Import

```TypeScript
```

## getAppMemorySize

```TypeScript
function getAppMemorySize(): Promise<number>
```

Obtains the maximum memory (RAM allocation) available to the current application. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getAppMemorySize](arkts-ability-appmanager-getappmemorysize-f.md)

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the maximum memory (RAM allocation) size, in MB. You can perform error processing or other custom processing based on the size. |

**Examples**

```TypeScript
import appManager from '@ohos.application.appManager';
import { BusinessError } from '@ohos.base';

appManager.getAppMemorySize().then((data) => {
  console.info(`The size of app memory is: ${JSON.stringify(data)}`);
}).catch((error: BusinessError) => {
  console.error(`error: ${JSON.stringify(error)}`);
});
```


<a id="getappmemorysize-1"></a>

## getAppMemorySize

```TypeScript
function getAppMemorySize(callback: AsyncCallback<number>): void
```

Obtains the maximum memory (RAM allocation) available to the current application. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getAppMemorySize](arkts-ability-appmanager-getappmemorysize-f.md)

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the maximum memory (RAM allocation) size, in MB. You can perform error processing or other custom processing based on the size. |

**Examples**

```TypeScript
import appManager from '@ohos.application.appManager';

appManager.getAppMemorySize((error, data) => {
  if (error && error.code !== 0) {
    console.error(`getAppMemorySize fail, error: ${JSON.stringify(error)}`);
  } else {
    console.info(`The size of app memory is: ${JSON.stringify(data)}`);
  }
});
```
