# toggleShownStateForAllAppWindows（系统接口）

## toggleShownStateForAllAppWindows

```TypeScript
function toggleShownStateForAllAppWindows(callback: AsyncCallback<void>): void
```

多窗口快速切换时隐藏或者恢复应用窗口。

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a systemAPI.<br>**适用版本：** 12+ |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited devicecapabilities.<br>**适用版本：** 12+ |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

window.toggleShownStateForAllAppWindows((err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to toggle shown state for all app windows. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in toggling shown state for all app windows.');
});

```


## toggleShownStateForAllAppWindows

```TypeScript
function toggleShownStateForAllAppWindows(): Promise<void>
```

多窗口快速切换时隐藏或者恢复应用窗口，使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a systemAPI.<br>**适用版本：** 12+ |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited devicecapabilities.<br>**适用版本：** 12+ |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let promise = window.toggleShownStateForAllAppWindows();
promise.then(() => {
  console.info('Succeeded in toggling shown state for all app windows.');
}).catch((err: BusinessError) => {
  console.error(`Failed to toggle shown state for all app windows. Cause code: ${err.code}, message: ${err.message}`);
});

```

