# destroyVirtualScreen（系统接口）

## destroyVirtualScreen

```TypeScript
function destroyVirtualScreen(screenId:long, callback: AsyncCallback<void>): void
```

销毁虚拟屏幕，使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-screen-function destroyVirtualScreen(screenId:long, callback: AsyncCallback<void>): void--><!--Device-screen-function destroyVirtualScreen(screenId:long, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| screenId | long | 是 | 屏幕的id，该参数仅支持整数输入。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当销毁虚拟屏幕成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. |
| [1400002](../errorcode-display.md#1400002-无权限操作) | Unauthorized operation. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 屏幕ID需通过getAllScreens()获取或从createVirtualScreen()返回值获取
let screenId: number = 1; // 虚拟屏ID
// 销毁虚拟屏幕
screen.destroyVirtualScreen(screenId, (err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to destroy the virtual screen. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in destroying the virtual screen.');
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let screenId: long = 1;
screen.destroyVirtualScreen(screenId, (err: BusinessError | null) => {
  const errCode = err?.code;
  if (errCode) {
    console.error(`Failed to destroy the virtual screen. Code: ${err?.code}, message: ${err?.message}`);
    return;
  }
  console.info('Succeeded in destroying the virtual screen.');
});
```


## destroyVirtualScreen

```TypeScript
function destroyVirtualScreen(screenId:long): Promise<void>
```

销毁虚拟屏幕，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-screen-function destroyVirtualScreen(screenId:long): Promise<void>--><!--Device-screen-function destroyVirtualScreen(screenId:long): Promise<void>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| screenId | long | 是 | 屏幕的id，该参数仅支持整数输入。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. |
| [1400002](../errorcode-display.md#1400002-无权限操作) | Unauthorized operation. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 屏幕ID需通过getAllScreens()获取或从createVirtualScreen()返回值获取
let screenId: number = 1; // 虚拟屏ID
// 销毁虚拟屏幕
screen.destroyVirtualScreen(screenId).then(() => {
  console.info('Succeeded in destroying the virtual screen.');
}).catch((err: BusinessError) => {
  console.error(`Failed to destroy the virtual screen. Code: ${err.code}, message: ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let screenId: long = 1;
screen.destroyVirtualScreen(screenId).then(() => {
  console.info('Succeeded in destroying the virtual screen.');
}).catch((err: Error) => {
  console.error(`Failed to destroy the virtual screen. Code: ${err?.code}, message: ${err?.message}`);
});
```

