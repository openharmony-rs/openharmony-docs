# hasWindowFocus

## Modules to Import

```TypeScript
import { featureAbility } from '@kit.AbilityKit';
```

## hasWindowFocus

```TypeScript
function hasWindowFocus(callback: AsyncCallback<boolean>): void
```

Checks whether the main window of this ability has the focus. This API uses an asynchronous callback to return the result.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result.<br>If the main window has the focus, **true** is returned. Otherwise, **false** is returned. |

**Examples**

```TypeScript
import { featureAbility } from '@kit.AbilityKit';

// Check whether the main window of the Ability has window focus.
featureAbility.hasWindowFocus((error, data) => {
  if (error && error.code !== 0) {
    console.error(`hasWindowFocus fail, error: ${JSON.stringify(error)}`);
  } else {
    console.info(`hasWindowFocus success, data: ${JSON.stringify(data)}`);
  }
});
```

```TypeScript
import { featureAbility } from '@kit.AbilityKit';

// Check whether the main window of the Ability has window focus.
featureAbility.hasWindowFocus().then((data) => {
  console.info(`hasWindowFocus data: ${JSON.stringify(data)}`);
});
```


## hasWindowFocus

```TypeScript
function hasWindowFocus(): Promise<boolean>
```

Checks whether the main window of this ability has the focus. This API uses a promise to return the result.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. If the main window has the focus, **true** is returned. Otherwise, **false** is returned. |

**Examples**

See [hasWindowFocus](#haswindowfocus)
