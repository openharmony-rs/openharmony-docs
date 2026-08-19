# onGestureNavigationEnabledChange（系统接口）

## 导入模块

```TypeScript
import { floatingBall } from '@kit.ArkUI';
import { floatView } from '@kit.ArkUI';
import { window } from '@kit.ArkUI';
```

## onGestureNavigationEnabledChange

```TypeScript
function onGestureNavigationEnabledChange(callback: Callback<boolean>): void
```

添加手势导航启用状态变化的监听。

**起始版本：** 23

<!--Device-window-function onGestureNavigationEnabledChange(callback: Callback<boolean>): void--><!--Device-window-function onGestureNavigationEnabledChange(callback: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回当前手势导航的启用状态。true表示手势导航状态变化为启用；false表示手势导航状态变化为禁用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

```TypeScript
try {
  window.onGestureNavigationEnabledChange((data) => {
    console.info(`Succeeded in enabling the listener for gesture navigation status changes. Data: ${data}`);
  });
} catch (exception) {
  let error = exception as BusinessError;
  console.error(`Failed to enable the listener for gesture navigation status changes. Cause code: ${error.code}, message: ${error.message}`);
}
```

