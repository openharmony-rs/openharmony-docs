# terminateSelf

## Modules to Import

```TypeScript
import { featureAbility } from '@kit.AbilityKit';
```

## terminateSelf

```TypeScript
function terminateSelf(callback: AsyncCallback<void>): void
```

Terminates this ability. This API uses an asynchronous callback to return the result.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { featureAbility } from '@kit.AbilityKit';

// Stop the current Ability.
featureAbility.terminateSelf(
  (error) => {
    console.error(`error: ${JSON.stringify(error)}`);
  }
)
```


<a id="terminateself-1"></a>

## terminateSelf

```TypeScript
function terminateSelf(): Promise<void>
```

Terminates this ability. This API uses a promise to return the result.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { featureAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Stop the current Ability.
featureAbility.terminateSelf().then(() => {
  console.info('==========================>terminateSelf=======================>');
}).catch((error: BusinessError) => {
  console.error(`terminateSelf failed, error.code: ${error.code}, error.message: ${error.message}`);
});
```
