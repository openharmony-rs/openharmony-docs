# Display

屏幕实例。描述Display对象的属性和方法。

下列API示例中都需先使用[getAllDisplays()](arkts-arkui-display-getalldisplays-f.md#getAllDisplays-1)、
[getDefaultDisplaySync()](arkts-arkui-display-getdefaultdisplaysync-f.md#getDefaultDisplaySync-1)中的任一方法获取到Display实例，再通过此实例调用对应方法。

**起始版本：** 7

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## hasImmersiveWindow

```TypeScript
hasImmersiveWindow(callback: AsyncCallback<boolean>): void
```

判断当前屏幕是否包含沉浸式窗口，使用callback异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数。返回true表示当前屏幕包含沉浸式窗口，false表示不包含。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. Failed to call the API due to limited device<br/>capabilities. |
| [1400001](../../errorcode-universal.md#1400001-Invalid) | Invalid display or screen. |
| [1400003](../../errorcode-universal.md#1400003-This) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { display } from '@kit.ArkUI';

let displayClass: display.Display | null = null;
displayClass = display.getDefaultDisplaySync();
displayClass.hasImmersiveWindow((err: BusinessError, data) => {
    const errCode: number = err.code;
    if (errCode) {
      console.error(`Failed to check whether there is immersive window. Code: ${err.code} , message : ${err.message}`);
      return;
    }
    console.info(`Succeeded in checking whether there is immersive window. data: ${data}`);
});

```

## hasImmersiveWindow

```TypeScript
hasImmersiveWindow(): Promise<boolean>
```

判断当前屏幕是否包含沉浸式窗口，使用Promise异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示当前屏幕包含沉浸式窗口，false表示不包含。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. Failed to call the API due to limited device<br/>capabilities. |
| [1400001](../../errorcode-universal.md#1400001-Invalid) | Invalid display or screen. |
| [1400003](../../errorcode-universal.md#1400003-This) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { display } from '@kit.ArkUI';

let displayClass: display.Display | null = null;
displayClass = display.getDefaultDisplaySync();
let promise = displayClass.hasImmersiveWindow();
promise.then((data) => {
  console.info(`Succeeded in checking whether there is immersive window. data: ${data}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to check whether there is immersive window. Code: ${err.code} , message: ${err.message}`);
})

```

