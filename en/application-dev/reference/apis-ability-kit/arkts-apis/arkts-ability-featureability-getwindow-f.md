# getWindow

## Modules to Import

```TypeScript
import { featureAbility } from '@kit.AbilityKit';
```

## getWindow

```TypeScript
function getWindow(callback: AsyncCallback<window.Window>): void
```

Obtains the window corresponding to this ability. This API uses an asynchronous callback to return the result.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[window.Window](../../apis-arkui/arkts-apis/arkts-arkui-window-window-i.md)&gt; | Yes | Callback used to return the window. |

**Examples**

```TypeScript
import { featureAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the window corresponding to the current Ability.
featureAbility.getWindow((error: BusinessError, data: window.Window) => {
  if (error && error.code !== 0) {
    console.error(`getWindow fail, error: ${JSON.stringify(error)}`);
  } else {
    console.info(`getWindow success, data: ${typeof(data)}`);
  }
});
```


<a id="getwindow-1"></a>

## getWindow

```TypeScript
function getWindow(): Promise<window.Window>
```

Obtains the window corresponding to this ability. This API uses a promise to return the result.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[window.Window](../../apis-arkui/arkts-apis/arkts-arkui-window-window-i.md)&gt; | Promise used to return the window. |

**Examples**

```TypeScript
import { featureAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

// Get the window corresponding to the current Ability.
featureAbility.getWindow().then((data: window.Window) => {
  console.info(`getWindow success, data: ${typeof(data)}`);
}).catch((error: BusinessError)=>{
  console.error(`getWindow fail, error: ${JSON.stringify(error)}`);
});
```
