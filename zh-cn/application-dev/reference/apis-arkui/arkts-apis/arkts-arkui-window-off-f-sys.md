# off（系统接口）

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## off('systemBarTintChange')

```TypeScript
function off(type: 'systemBarTintChange', callback?: Callback<SystemBarTintState>): void
```

关闭状态栏、导航栏属性变化的监听。

**起始版本：** 8

<!--Device-window-function off(type: 'systemBarTintChange', callback?: Callback<SystemBarTintState>): void--><!--Device-window-function off(type: 'systemBarTintChange', callback?: Callback<SystemBarTintState>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'systemBarTintChange' | 是 | 监听事件，固定为'systemBarTintChange'，即导航栏、状态栏属性变化事件。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<SystemBarTintState> | 否 | 回调函数。返回当前的状态栏、导航栏信息集合。如果传入参数，则关闭该监听。如果未传入参数，则关闭所有状态栏、导航栏属性变化的监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Incorrect parameter types;2. Parameter verification failed. |

**示例：**

```TypeScript
const callback = (systemBarTintState: window.SystemBarTintState) => {
  // ...
}
try {
  window.on('systemBarTintChange', callback);

  window.off('systemBarTintChange', callback);
  // 如果通过on开启多个callback进行监听，同时关闭所有监听：
  window.off('systemBarTintChange');
} catch (exception) {
  console.error(`Failed to enable or disable the listener for systemBarTint changes. Cause code: ${exception.code}, message: ${exception.message}`);
}

```


## off('gestureNavigationEnabledChange')

```TypeScript
function off(type: 'gestureNavigationEnabledChange', callback?: Callback<boolean>): void
```

移除手势导航启用状态变化的监听。

**起始版本：** 10

<!--Device-window-function off(type: 'gestureNavigationEnabledChange', callback?: Callback<boolean>): void--><!--Device-window-function off(type: 'gestureNavigationEnabledChange', callback?: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'gestureNavigationEnabledChange' | 是 | 监听事件，固定为'gestureNavigationEnabledChange'，即手势导航启用状态变化事件。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<boolean> | 否 | 已注册的回调函数。如果传入参数，则关闭该监听。如果未传入参数，则关闭所有手势导航启用状态变化的监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Incorrect parameter types;2. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |

**示例：**

```TypeScript
const callback = (bool: boolean) => {
  // ...
}
try {
  window.on('gestureNavigationEnabledChange', callback);
  window.off('gestureNavigationEnabledChange', callback);
  // 如果通过on开启多个callback进行监听，同时关闭所有监听：
  window.off('gestureNavigationEnabledChange');
} catch (exception) {
  console.error(`Failed to enable or disable the listener for gesture navigation status changes. Cause code: ${exception.code}, message: ${exception.message}`);
}

```


## off('waterMarkFlagChange')

```TypeScript
function off(type: 'waterMarkFlagChange', callback?: Callback<boolean>): void
```

移除水印启用状态变化的监听。

**起始版本：** 10

<!--Device-window-function off(type: 'waterMarkFlagChange', callback?: Callback<boolean>): void--><!--Device-window-function off(type: 'waterMarkFlagChange', callback?: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'waterMarkFlagChange' | 是 | 监听事件，固定为'waterMarkFlagChange'，即水印启用状态变化事件。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<boolean> | 否 | 已注册的回调函数。如果传入参数，则关闭该监听。如果未传入参数，则关闭所有水印启用状态变化的监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Incorrect parameter types;<br>2. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |

**示例：**

```TypeScript
const callback = (bool: boolean) => {
  // ...
}
try {
  window.on('waterMarkFlagChange', callback);
  window.off('waterMarkFlagChange', callback);
  // 如果通过on开启多个callback进行监听，同时关闭所有监听：
  window.off('waterMarkFlagChange');
} catch (exception) {
  console.error(`Failed to enable or disable the listener for watermark flag changes. Cause code: ${exception.code}, message: ${exception.message}`);
}

```

