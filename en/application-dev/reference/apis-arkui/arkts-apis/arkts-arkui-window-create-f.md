# create

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## create

```TypeScript
function create(id: string, type: WindowType, callback: AsyncCallback<Window>): void
```

Creates a child window. This API uses an asynchronous callback to return the result.

The child window created uses an [immersive layout](../../../windowmanager/window-terminology.md#immersive-layout) by default.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [createWindow](arkts-arkui-window-createwindow-f.md)(config: Configuration, callback: AsyncCallback&lt;Window&gt;)

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | Window name, that is, the value of name in [Configuration](arkts-arkui-window-configuration-i.md). |
| type | [WindowType](arkts-arkui-window-windowtype-e.md) | Yes | Window type. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Window](arkts-arkui-window-window-i.md)&gt; | Yes | Callback used to return the child window created. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let windowClass: window.Window | undefined = undefined;
window.create('test', window.WindowType.TYPE_APP, (err: BusinessError, data) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to create the subWindow. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  windowClass = data;
  console.info('Succeeded in creating the subWindow. Data: ' + JSON.stringify(data));
});
```


<a id="create-1"></a>

## create

```TypeScript
function create(id: string, type: WindowType): Promise<Window>
```

Creates a child window. This API uses a promise to return the result.

The child window created uses an [immersive layout](../../../windowmanager/window-terminology.md#immersive-layout) by default.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [createWindow](arkts-arkui-window-createwindow-f.md#createwindow-1)(config: Configuration)

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | Window name, that is, the value of name in [Configuration](arkts-arkui-window-configuration-i.md). |
| type | [WindowType](arkts-arkui-window-windowtype-e.md) | Yes | Window type. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Window](arkts-arkui-window-window-i.md)&gt; | Promise used to return the child window created. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let windowClass: window.Window | undefined = undefined;
let promise = window.create('test', window.WindowType.TYPE_APP);
promise.then((data) => {
  windowClass = data;
  console.info('Succeeded in creating the subWindow. Data: ' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error(`Failed to create the subWindow. Cause code: ${err.code}, message: ${err.message}`);
});
```


<a id="create-2"></a>

## create

```TypeScript
function create(ctx: BaseContext, id: string, type: WindowType): Promise<Window>
```

Creates a system window. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [createWindow](arkts-arkui-window-createwindow-f.md#createwindow-1)(config: Configuration)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ctx | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-basecontext-c.md) | Yes | Current application context. |
| id | string | Yes | Window name, that is, the value of name in [Configuration](arkts-arkui-window-configuration-i.md). |
| type | [WindowType](arkts-arkui-window-windowtype-e.md) | Yes | Window type. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Window](arkts-arkui-window-window-i.md)&gt; | Promise used to return the child window created. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let windowClass: window.Window | undefined = undefined;
let promise = window.create(globalThis.getContext(), 'test', window.WindowType.TYPE_SYSTEM_ALERT);
promise.then((data) => {
  windowClass = data;
  console.info('Succeeded in creating the window. Data:' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error(`Failed to create the Window. Cause code: ${err.code}, message: ${err.message}`);
});
```


<a id="create-3"></a>

## create

```TypeScript
function create(ctx: BaseContext, id: string, type: WindowType, callback: AsyncCallback<Window>): void
```

Creates a system window. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [createWindow](arkts-arkui-window-createwindow-f.md)(config: Configuration, callback: AsyncCallback&lt;Window&gt;)

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ctx | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-basecontext-c.md) | Yes | Current application context. |
| id | string | Yes | Window name, that is, the value of name in [Configuration](arkts-arkui-window-configuration-i.md). |
| type | [WindowType](arkts-arkui-window-windowtype-e.md) | Yes | Window type. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Window](arkts-arkui-window-window-i.md)&gt; | Yes | Callback used to return the child window created. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let windowClass: window.Window | undefined = undefined;
window.create(globalThis.getContext(), 'test', window.WindowType.TYPE_SYSTEM_ALERT, (err: BusinessError, data) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to create the window. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  windowClass = data;
  console.info('Succeeded in creating the window. Data: ' + JSON.stringify(data));
  windowClass.resetSize(500, 1000);
});
```
