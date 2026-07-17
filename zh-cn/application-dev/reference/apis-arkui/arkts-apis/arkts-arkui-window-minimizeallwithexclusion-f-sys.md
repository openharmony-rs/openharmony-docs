# minimizeAllWithExclusion（系统接口）

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## minimizeAllWithExclusion

```TypeScript
function minimizeAllWithExclusion(displayId: number, excludeWindowId: number): Promise<void>
```

最小化指定ID的屏幕中除指定窗口之外的所有主窗口，使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-window-function minimizeAllWithExclusion(displayId: long, excludeWindowId: int): Promise<void>--><!--Device-window-function minimizeAllWithExclusion(displayId: long, excludeWindowId: int): Promise<void>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayId | number | 是 | 屏幕ID，该参数仅支持整数输入，输入浮点数会向下取整。 |
| excludeWindowId | number | 是 | 窗口ID。可通过[getWindowProperties](arkts-arkui-window-window-i.md#getwindowproperties-1)接口获取到相关窗口属性，其中属性id即对应为窗口ID。窗口ID小于等于0，或窗口ID为null或者undefined时，会抛出[401错误码](../../../../reference/errorcode-universal.md#401-参数检查失败)；窗口ID大于0但是不存在会抛出1300002错误码；窗口ID大于0且窗口存在但是不在该屏幕，最小化指定屏幕上的所有主窗口。该参数仅支持整数输入，输入浮点数会向下取整。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A nonsystem application calls a system API. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal.Possible cause: 1. Window is nullptr;2. Failed to find specified window by id. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |

**示例：**

```TypeScript
import { display, window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

let displayClass: display.Display | null = null;
displayClass = display.getDefaultDisplaySync();
let excludeWindowId = 1;

try {
  let promise = window.minimizeAllWithExclusion(displayClass.id, excludeWindowId);
  promise.then(() => {
    console.info('Succeeded in minimizing all windows.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to minimize all windows. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to minimize all windows. Cause code: ${exception.code}, message: ${exception.message}`);
}

```

