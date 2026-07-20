# getAllDisplays

## 导入模块

```TypeScript
import { display } from '@kit.ArkUI';
```

<a id="getalldisplays"></a>
## getAllDisplays

```TypeScript
function getAllDisplays(callback: AsyncCallback<Array<Display>>): void
```

获取当前所有的Display对象，使用callback异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-display-function getAllDisplays(callback: AsyncCallback<Array<Display>>): void--><!--Device-display-function getAllDisplays(callback: AsyncCallback<Array<Display>>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;Display&gt;&gt; | 是 | 回调函数。返回当前所有的Display对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let displayClass: Array<display.Display> = [];
display.getAllDisplays((err: BusinessError, data: Array<display.Display>) => {
  displayClass = data;
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to obtain all the display objects. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in obtaining all the display objects. Data: ${JSON.stringify(data)}`);
});

```


<a id="getalldisplays-1"></a>
## getAllDisplays

```TypeScript
function getAllDisplays(): Promise<Array<Display>>
```

获取当前所有的Display对象，使用Promise异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-display-function getAllDisplays(): Promise<Array<Display>>--><!--Device-display-function getAllDisplays(): Promise<Array<Display>>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Display&gt;&gt; | Promise对象。返回当前所有的Display对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let displayClass: Array<display.Display> =[];
let promise: Promise<Array<display.Display>> = display.getAllDisplays();
promise.then((data: Array<display.Display>) => {
  displayClass = data;
  console.info(`Succeeded in obtaining all the display objects. Data:  ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain all the display objects. Code: ${err.code}, message: ${err.message}`);
});

```

