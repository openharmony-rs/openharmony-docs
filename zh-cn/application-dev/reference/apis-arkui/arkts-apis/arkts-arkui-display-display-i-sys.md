# Display

屏幕实例。描述Display对象的属性和方法。

下列API示例中都需先使用[getAllDisplays()](arkts-arkui-display-getalldisplays-f.md#getalldisplays-1)、[getDefaultDisplaySync()](arkts-arkui-display-getdefaultdisplaysync-f.md#getdefaultdisplaysync-1)中的任一方法获取到Display实例，再通过此实例调用对应方法。

**起始版本：** 7

<!--Device-display-interface Display--><!--Device-display-interface Display-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## 导入模块

```TypeScript
import { display } from '@kit.ArkUI';
```

## hasImmersiveWindow

```TypeScript
hasImmersiveWindow(callback: AsyncCallback<boolean>): void
```

判断当前屏幕是否包含沉浸式窗口，使用callback异步回调。

**起始版本：** 11

<!--Device-Display-hasImmersiveWindow(callback: AsyncCallback<boolean>): void--><!--Device-Display-hasImmersiveWindow(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<boolean> | 是 | 回调函数。返回true表示当前屏幕包含沉浸式窗口，false表示不包含。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { display } from '@kit.ArkUI';

let displayClass: display.Display | null = null;
// 获取默认Display对象
displayClass = display.getDefaultDisplaySync();
// 查询是否包含沉浸式窗口
displayClass.hasImmersiveWindow((err: BusinessError, data: boolean) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to check whether there is immersive window. Code: ${err.code}, message: ${err.message}`);
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

<!--Device-Display-hasImmersiveWindow(): Promise<boolean>--><!--Device-Display-hasImmersiveWindow(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<boolean> | Promise对象。返回true表示当前屏幕包含沉浸式窗口，false表示不包含。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1400001](../errorcode-display.md#1400001-无效的显示设备) | Invalid display or screen. |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { display } from '@kit.ArkUI';

let displayClass: display.Display | null = null;
// 获取默认Display对象
displayClass = display.getDefaultDisplaySync();
// 查询是否包含沉浸式窗口
let promise = displayClass.hasImmersiveWindow();
promise.then((data) => {
  console.info(`Succeeded in checking whether there is immersive window. data: ${data}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to check whether there is immersive window. Code: ${err.code}, message: ${err.message}`);
});

```

