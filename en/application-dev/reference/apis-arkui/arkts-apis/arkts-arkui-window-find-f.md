# find

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## find

```TypeScript
function find(id: string, callback: AsyncCallback<Window>): void
```

Finds a window based on the ID. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [findWindow](arkts-arkui-window-findwindow-f.md)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | Window name, that is, the value of name in [Configuration](arkts-arkui-window-configuration-i.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Window](arkts-arkui-window-window-i.md)&gt; | Yes | Callback used to return the window found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let windowClass: window.Window | undefined = undefined;
window.find('test', (err: BusinessError, data) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to find the Window. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  windowClass = data;
  console.info('Succeeded in finding the window. Data: ' + JSON.stringify(data));
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let windowClass: window.Window | undefined = undefined;
let promise = window.find('test');
promise.then((data) => {
  windowClass = data;
  console.info('Succeeded in finding the window. Data: ' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error(`Failed to find the Window. Cause code: ${err.code}, message: ${err.message}`);
});
```


## find

```TypeScript
function find(id: string): Promise<Window>
```

Finds a window based on the ID. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [findWindow](arkts-arkui-window-findwindow-f.md)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | Window name, that is, the value of name in [Configuration](arkts-arkui-window-configuration-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Window](arkts-arkui-window-window-i.md)&gt; | Promise used to return the window found. |

**Examples**

See [find](#find)
