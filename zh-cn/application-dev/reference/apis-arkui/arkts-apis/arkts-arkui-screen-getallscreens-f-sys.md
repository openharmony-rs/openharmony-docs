# getAllScreens（系统接口）

## 导入模块

```TypeScript
import { screen } from '@kit.ArkUI';
```

## getAllScreens

```TypeScript
function getAllScreens(callback: AsyncCallback<Array<Screen>>): void
```

获取所有的屏幕，使用callback异步回调。

**起始版本：** 9

<!--Device-screen-function getAllScreens(callback: AsyncCallback<Array<Screen>>): void--><!--Device-screen-function getAllScreens(callback: AsyncCallback<Array<Screen>>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;Screen&gt;&gt; | 是 | 回调函数。返回当前获取的屏幕对象集合。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let screenClass: screen.Screen | null = null;
// 获取所有屏幕对象
screen.getAllScreens((err: BusinessError, data: Array<screen.Screen>) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to get all screens. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting all screens. Data: ${JSON.stringify(data)}`);
  if (data.length > 0) {
    screenClass = data[0];
  }
});

```


## getAllScreens

```TypeScript
function getAllScreens(): Promise<Array<Screen>>
```

获取所有的屏幕，使用Promise异步回调。

**起始版本：** 9

<!--Device-screen-function getAllScreens(): Promise<Array<Screen>>--><!--Device-screen-function getAllScreens(): Promise<Array<Screen>>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Screen&gt;&gt; | Promise对象。返回当前获取的屏幕对象集合。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let screenClass: screen.Screen | null = null;
// 获取所有屏幕对象
let promise: Promise<Array<screen.Screen>> = screen.getAllScreens();
promise.then((data: Array<screen.Screen>) => {
  if(data.length > 0){
    screenClass = data[0];
  }
  console.info(`Succeeded in getting all screens. Data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get all screens. Code: ${err.code}, message: ${err.message}`);
});

```

