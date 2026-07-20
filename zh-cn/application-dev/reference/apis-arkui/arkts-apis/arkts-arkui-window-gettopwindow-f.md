# getTopWindow

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

<a id="gettopwindow"></a>
## getTopWindow

```TypeScript
function getTopWindow(callback: AsyncCallback<Window>): void
```

获取当前应用内最后显示的窗口，使用callback异步回调。

> **说明：**  
>  
> 从API version 6开始支持，从API version 9开始废弃，建议使用  
> [getLastWindow()](arkts-arkui-window-getlastwindow-f.md#getlastwindow-1)替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [getLastWindow(ctx:](arkts-arkui-window-getlastwindow-f.md#getlastwindow-1)

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-window-function getTopWindow(callback: AsyncCallback<Window>): void--><!--Device-window-function getTopWindow(callback: AsyncCallback<Window>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Window&gt; | 是 | 回调函数。返回当前应用内最后显示的窗口对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let windowClass: window.Window | undefined = undefined;
window.getTopWindow((err: BusinessError, data) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to obtain the top window. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  windowClass = data;
  console.info('Succeeded in obtaining the top window. Data: ' + JSON.stringify(data));
});

```


<a id="gettopwindow-1"></a>
## getTopWindow

```TypeScript
function getTopWindow(): Promise<Window>
```

获取当前应用内最后显示的窗口，使用Promise异步回调。

> **说明：**  
>  
> 从API version 6开始支持，从API version 9开始废弃，建议使用[getLastWindow()](arkts-arkui-window-getlastwindow-f.md#getlastwindow-1)替代。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [getLastWindow(ctx:](arkts-arkui-window-getlastwindow-f.md#getlastwindow-1)

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-window-function getTopWindow(): Promise<Window>--><!--Device-window-function getTopWindow(): Promise<Window>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Window&gt; | Promise对象。返回当前应用内最后显示的窗口对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let windowClass: window.Window | undefined = undefined;
let promise = window.getTopWindow();
promise.then((data)=> {
    windowClass = data;
    console.info('Succeeded in obtaining the top window. Data: ' + JSON.stringify(data));
}).catch((err: BusinessError)=>{
    console.error(`Failed to obtain the top window. Cause code: ${err.code}, message: ${err.message}`);
});

```


<a id="gettopwindow-2"></a>
## getTopWindow

```TypeScript
function getTopWindow(ctx: BaseContext): Promise<Window>
```

获取当前应用内最后显示的窗口，使用Promise异步回调。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[getLastWindow()](arkts-arkui-window-getlastwindow-f.md#getlastwindow-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getLastWindow(ctx:](arkts-arkui-window-getlastwindow-f.md#getlastwindow-1)

<!--Device-window-function getTopWindow(ctx: BaseContext): Promise<Window>--><!--Device-window-function getTopWindow(ctx: BaseContext): Promise<Window>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ctx | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 当前应用上下文信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Window&gt; | Promise对象。返回当前应用内最后显示的窗口对象。 |

**示例：**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage:window.WindowStage) {
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    let promise = window.getTopWindow(this.context);
    promise.then((data) => {
      windowClass = data;
      console.info('Succeeded in obtaining the top window. Data: ' + JSON.stringify(data));
    }).catch((error: BusinessError) => {
      console.error(`Failed to obtain the top window. Cause code: ${error.code}, message: ${error.message}`);
    });
  }
}

```


<a id="gettopwindow-3"></a>
## getTopWindow

```TypeScript
function getTopWindow(ctx: BaseContext, callback: AsyncCallback<Window>): void
```

获取当前应用内最后显示的窗口，使用callback异步回调。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，参数ctx传入null或undefined时，可能会导致callback无法得到执行，建议使用  
> [getLastWindow()](arkts-arkui-window-getlastwindow-f.md#getlastwindow-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getLastWindow(ctx:](arkts-arkui-window-getlastwindow-f.md#getlastwindow-1)

<!--Device-window-function getTopWindow(ctx: BaseContext, callback: AsyncCallback<Window>): void--><!--Device-window-function getTopWindow(ctx: BaseContext, callback: AsyncCallback<Window>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ctx | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 当前应用上下文信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Window&gt; | 是 | 回调函数。返回当前应用内最后显示的窗口对象。 |

**示例：**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage:window.WindowStage){
    console.info('onWindowStageCreate');
    let windowClass: window.Window | undefined = undefined;
    try {
      window.getTopWindow(this.context, (err: BusinessError, data) => {
        const errCode: number = err.code;
        if(errCode){
          console.error(`Failed to obtain the top window. Cause code: ${err.code}, message: ${err.message}`);
          return ;
        }
        windowClass = data;
        console.info('Succeeded in obtaining the top window. Data: ' + JSON.stringify(data));
      });
    } catch(error){
      console.error(`Failed to obtain the top window. Cause code: ${error.code}, message: ${error.message}`);
    }
  }
}

```

