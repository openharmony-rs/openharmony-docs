# getDefaultDisplay

## getDefaultDisplay

```TypeScript
function getDefaultDisplay(callback: AsyncCallback<Display>): void
```

获取当前默认的Display对象，使用callback异步回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [getDefaultDisplaySync](arkts-arkui-display-getdefaultdisplaysync-f.md#getDefaultDisplaySync)

<!--Device-display-function getDefaultDisplay(callback: AsyncCallback<Display>): void--><!--Device-display-function getDefaultDisplay(callback: AsyncCallback<Display>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[Display](arkts-arkui-display-display-i.md)&gt; | 是 | 回调函数。返回当前默认的Display对象。 |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let displayClass: display.Display | null = null;
display.getDefaultDisplay((err: BusinessError, data: display.Display) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to obtain the default display object. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in obtaining the default display object. Data: ${JSON.stringify(data)}`);
  displayClass = data;
});
```


## getDefaultDisplay

```TypeScript
function getDefaultDisplay(): Promise<Display>
```

获取当前默认的Display对象，使用Promise异步回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [getDefaultDisplaySync](arkts-arkui-display-getdefaultdisplaysync-f.md#getDefaultDisplaySync)

<!--Device-display-function getDefaultDisplay(): Promise<Display>--><!--Device-display-function getDefaultDisplay(): Promise<Display>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Display](arkts-arkui-display-display-i.md)&gt; | Promise对象。返回当前默认的Display对象。 |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let displayClass: display.Display | null = null;
let promise: Promise<display.Display> = display.getDefaultDisplay();
promise.then((data: display.Display) => {
  displayClass = data;
  console.info(`Succeeded in obtaining the default display object. Data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain the default display object. Code: ${err.code}, message: ${err.message}`);
});
```

