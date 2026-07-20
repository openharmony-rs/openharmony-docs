# find

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

<a id="find"></a>
## find

```TypeScript
function find(id: string, callback: AsyncCallback<Window>): void
```

查找id所对应的窗口，使用callback异步回调。

> **说明：**  
>  
> 从API version 7开始支持，从API version 9开始废弃，建议使用[findWindow()](arkts-arkui-window-findwindow-f.md#findwindow-1)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [findWindow](arkts-arkui-window-findwindow-f.md#findwindow-1)

<!--Device-window-function find(id: string, callback: AsyncCallback<Window>): void--><!--Device-window-function find(id: string, callback: AsyncCallback<Window>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 窗口名字，即[Configuration](arkts-arkui-window-configuration-i.md)中的name。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Window&gt; | 是 | 回调函数。返回当前查找到的窗口对象。 |

**示例：**

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


<a id="find-1"></a>
## find

```TypeScript
function find(id: string): Promise<Window>
```

查找id所对应的窗口，使用Promise异步回调。

> **说明：**  
>  
> 从API version 7开始支持，从API version 9开始废弃，建议使用[findWindow()](arkts-arkui-window-findwindow-f.md#findwindow-1)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [findWindow](arkts-arkui-window-findwindow-f.md#findwindow-1)

<!--Device-window-function find(id: string): Promise<Window>--><!--Device-window-function find(id: string): Promise<Window>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 窗口名字，即[Configuration](arkts-arkui-window-configuration-i.md)中的name。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Window&gt; | Promise对象。返回当前查找的窗口对象。 |

**示例：**

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

