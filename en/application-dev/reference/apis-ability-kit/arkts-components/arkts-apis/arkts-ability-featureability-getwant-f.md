# getWant

## Modules to Import

```TypeScript
import { featureAbility } from '@kit.AbilityKit';
```

## getWant

```TypeScript
function getWant(callback: AsyncCallback<Want>): void
```

Obtains the Want corresponding to the ability to start. This API uses an asynchronous callback to return the result.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Want](arkts-ability-app-ability-want-want-c.md)&gt; | Yes | Callback used to return the Want. |

**Examples**

```TypeScript
import { featureAbility } from '@kit.AbilityKit';

// Obtain the Want corresponding to the Ability to be started.
featureAbility.getWant((error, data) => {
  if (error && error.code !== 0) {
    console.error(`getWant fail, error: ${JSON.stringify(error)}`);
  } else {
    console.info(`getWant success, data: ${JSON.stringify(data)}`);
  }
});
```

```TypeScript
import { featureAbility } from '@kit.AbilityKit';

// Obtain the Want corresponding to the Ability to be started.
featureAbility.getWant().then((data) => {
  console.info(`getWant data: ${JSON.stringify(data)}`);
});
```


## getWant

```TypeScript
function getWant(): Promise<Want>
```

Obtains the Want corresponding to the ability to start. This API uses a promise to return the result.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Want](arkts-ability-app-ability-want-want-c.md)&gt; | Promise used to return the Want. |

**Examples**

See [getWant](#getwant)
