# getAllDisplay

## Modules to Import

```TypeScript
import { display } from '@kit.ArkUI';
```

## getAllDisplay

```TypeScript
function getAllDisplay(callback: AsyncCallback<Array<Display>>): void
```

Obtains all Display objects. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getAllDisplays](arkts-arkui-display-getalldisplays-f.md)(callback: AsyncCallback&lt;Array&lt;Display&gt;&gt;)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[Display](arkts-arkui-display-display-i.md)&gt;&gt; | Yes | Callback used to return all the Display objects. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

display.getAllDisplay((err: BusinessError, data: Array<display.Display>) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to obtain all the display objects. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in obtaining all the display objects. Data: ${JSON.stringify(data)}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let promise: Promise<Array<display.Display>> = display.getAllDisplay();
promise.then((data: Array<display.Display>) => {
  console.info(`Succeeded in obtaining all the display objects. Data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain all the display objects. Code: ${err.code}, message: ${err.message}`);
});
```


## getAllDisplay

```TypeScript
function getAllDisplay(): Promise<Array<Display>>
```

Obtains all Display objects. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getAllDisplays](arkts-arkui-display-getalldisplays-f.md)()

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[Display](arkts-arkui-display-display-i.md)&gt;&gt; | Promise used to return all the Display objects. |

**Examples**

See [getAllDisplay](#getalldisplay)
