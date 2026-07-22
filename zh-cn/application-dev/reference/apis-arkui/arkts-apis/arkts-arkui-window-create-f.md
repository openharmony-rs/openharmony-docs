# create

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## create

```TypeScript
function create(id: string, type: WindowType, callback: AsyncCallback<Window>): void
```

创建子窗口，使用callback异步回调。

子窗口创建后默认是[沉浸式布局](../../../windowmanager/window-terminology.md#沉浸式布局)。
> **说明：**  
>  
> 从API version 7开始支持，从API version 9开始废弃，参数id传入null或undefined时，可能会导致callback无法得到执行，建议使用  
> [createWindow()](arkts-arkui-window-createwindow-f.md#createwindow)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [createWindow(config:](arkts-arkui-window-createwindow-f.md#createwindow)

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-window-function create(id: string, type: WindowType, callback: AsyncCallback<Window>): void--><!--Device-window-function create(id: string, type: WindowType, callback: AsyncCallback<Window>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 窗口名字，即[Configuration](arkts-arkui-window-configuration-i.md)中的name。 |
| type | [WindowType](../../apis-accessibility-kit/arkts-apis/arkts-accessibility-windowtype-t.md) | 是 | 窗口类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Window&gt; | 是 | 回调函数。返回当前创建的子窗口对象。 |

**示例：**

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


## create

```TypeScript
function create(id: string, type: WindowType): Promise<Window>
```

创建子窗口，使用Promise异步回调。

子窗口创建后默认是[沉浸式布局](../../../windowmanager/window-terminology.md#沉浸式布局)。
> **说明：**  
>  
> 从API version 7开始支持，从API version 9开始废弃，建议使用[createWindow()](arkts-arkui-window-createwindow-f.md#createwindow)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [createWindow(config:](arkts-arkui-window-createwindow-f.md#createwindow)

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-window-function create(id: string, type: WindowType): Promise<Window>--><!--Device-window-function create(id: string, type: WindowType): Promise<Window>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 窗口名字，即[Configuration](arkts-arkui-window-configuration-i.md)中的name。 |
| type | [WindowType](../../apis-accessibility-kit/arkts-apis/arkts-accessibility-windowtype-t.md) | 是 | 窗口类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Window&gt; | Promise对象。返回当前创建的子窗口对象。 |

**示例：**

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


## create

```TypeScript
function create(ctx: BaseContext, id: string, type: WindowType): Promise<Window>
```

创建系统窗口，使用Promise异步回调。
> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[createWindow()](arkts-arkui-window-createwindow-f.md#createwindow)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [createWindow(config:](arkts-arkui-window-createwindow-f.md#createwindow)

<!--Device-window-function create(ctx: BaseContext, id: string, type: WindowType): Promise<Window>--><!--Device-window-function create(ctx: BaseContext, id: string, type: WindowType): Promise<Window>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ctx | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 当前应用上下文信息。 |
| id | string | 是 | 窗口名字，即[Configuration](arkts-arkui-window-configuration-i.md)中的name。 |
| type | [WindowType](../../apis-accessibility-kit/arkts-apis/arkts-accessibility-windowtype-t.md) | 是 | 窗口类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Window&gt; | Promise对象。返回当前创建的子窗口对象。 |

**示例：**

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


## create

```TypeScript
function create(ctx: BaseContext, id: string, type: WindowType, callback: AsyncCallback<Window>): void
```

创建系统窗口，使用callback异步回调。
> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [createWindow()](arkts-arkui-window-createwindow-f.md#createwindow)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [createWindow(config:](arkts-arkui-window-createwindow-f.md#createwindow)

<!--Device-window-function create(ctx: BaseContext, id: string, type: WindowType, callback: AsyncCallback<Window>): void--><!--Device-window-function create(ctx: BaseContext, id: string, type: WindowType, callback: AsyncCallback<Window>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ctx | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 当前应用上下文信息。 |
| id | string | 是 | 窗口名字，即[Configuration](arkts-arkui-window-configuration-i.md)中的name。 |
| type | [WindowType](../../apis-accessibility-kit/arkts-apis/arkts-accessibility-windowtype-t.md) | 是 | 窗口类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Window&gt; | 是 | 回调函数。返回当前创建的子窗口对象。 |

**示例：**

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

