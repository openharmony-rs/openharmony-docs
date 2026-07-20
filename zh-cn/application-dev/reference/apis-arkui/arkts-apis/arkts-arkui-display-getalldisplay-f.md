# getAllDisplay

## 导入模块

```TypeScript
import { display } from '@kit.ArkUI';
```

<a id="getalldisplay"></a>
## getAllDisplay

```TypeScript
function getAllDisplay(callback: AsyncCallback<Array<Display>>): void
```

获取当前所有的Display对象，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getAllDisplays(callback:](arkts-arkui-display-getalldisplays-f.md#getalldisplays-1)

<!--Device-display-function getAllDisplay(callback: AsyncCallback<Array<Display>>): void--><!--Device-display-function getAllDisplay(callback: AsyncCallback<Array<Display>>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;Display&gt;&gt; | 是 | 回调函数。返回当前所有的Display对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

display.getAllDisplay((err: BusinessError, data: Array<display.Display>) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to obtain all the display objects. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in obtaining the default display objects. Data: ${JSON.stringify(data)}`);
});

```


<a id="getalldisplay-1"></a>
## getAllDisplay

```TypeScript
function getAllDisplay(): Promise<Array<Display>>
```

获取当前所有的Display对象，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getAllDisplays()](arkts-arkui-display-getalldisplays-f.md#getalldisplays-1)

<!--Device-display-function getAllDisplay(): Promise<Array<Display>>--><!--Device-display-function getAllDisplay(): Promise<Array<Display>>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Display&gt;&gt; | Promise对象。返回当前所有的Display对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let promise: Promise<Array<display.Display>> = display.getAllDisplay();
promise.then((data: Array<display.Display>) => {
  console.info(`Succeeded in obtaining the default display objects. Data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain all the display objects. Code: ${err.code}, message: ${err.message}`);
});

```

