# stopMirror（系统接口）

## 导入模块

```TypeScript
import { screen } from '@kit.ArkUI';
```

<a id="stopmirror"></a>
## stopMirror

```TypeScript
function stopMirror(mirrorScreen:Array<number>, callback: AsyncCallback<void>): void
```

停止屏幕的镜像模式，使用callback异步回调。

**起始版本：** 10

<!--Device-screen-function stopMirror(mirrorScreen:Array<long>, callback: AsyncCallback<void>): void--><!--Device-screen-function stopMirror(mirrorScreen:Array<long>, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mirrorScreen | Array&lt;number&gt; | 是 | 镜像屏幕ID集合，其中ID应为整数。 mirrorScreen数组大小不应超过1000。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当停止屏幕镜像模式成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3. Parameter verification failed. |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 屏幕ID需通过getAllScreens()获取
let mirrorScreenIds: Array<number> = [1, 2, 3]; // 镜像屏ID集合
// 停止屏幕镜像模式
screen.stopMirror(mirrorScreenIds, (err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to stop mirror screens. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in stopping mirror screens.');
});

```


<a id="stopmirror-1"></a>
## stopMirror

```TypeScript
function stopMirror(mirrorScreen:Array<number>): Promise<void>
```

停止屏幕的镜像模式，使用Promise异步回调。

**起始版本：** 10

<!--Device-screen-function stopMirror(mirrorScreen:Array<long>): Promise<void>--><!--Device-screen-function stopMirror(mirrorScreen:Array<long>): Promise<void>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mirrorScreen | Array&lt;number&gt; | 是 | 镜像屏幕ID集合，其中ID应为整数。mirrorScreen数组大小不应超过1000。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 屏幕ID需通过getAllScreens()获取
let mirrorScreenIds: Array<number> = [1, 2, 3]; // 镜像屏ID集合
// 停止屏幕镜像模式
screen.stopMirror(mirrorScreenIds).then(() => {
  console.info('Succeeded in stopping mirror screens.');
}).catch((err: BusinessError) => {
  console.error(`Failed to stop mirror screens. Code: ${err.code}, message: ${err.message}`);
});

```

