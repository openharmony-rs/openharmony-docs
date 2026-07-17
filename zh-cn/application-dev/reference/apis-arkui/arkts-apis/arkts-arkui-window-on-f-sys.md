# on（系统接口）

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## on('systemBarTintChange')

```TypeScript
function on(type: 'systemBarTintChange', callback: Callback<SystemBarTintState>): void
```

开启状态栏、导航栏属性变化的监听。

**起始版本：** 8

<!--Device-window-function on(type: 'systemBarTintChange', callback: Callback<SystemBarTintState>): void--><!--Device-window-function on(type: 'systemBarTintChange', callback: Callback<SystemBarTintState>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'systemBarTintChange' | 是 | 监听事件，固定为'systemBarTintChange'，即导航栏、状态栏属性变化事件。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<SystemBarTintState> | 是 | 回调函数。返回当前的状态栏、导航栏信息集合。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

**示例：**

```TypeScript
try {
  window.on('systemBarTintChange', (data) => {
    console.info('Succeeded in enabling the listener for systemBarTint changes. Data: ' + JSON.stringify(data));
  });
} catch (exception) {
  console.error(`Failed to enable the listener for systemBarTint changes. Cause code: ${exception.code}, message: ${exception.message}`);
}

```


## on('gestureNavigationEnabledChange')

```TypeScript
function on(type: 'gestureNavigationEnabledChange', callback: Callback<boolean>): void
```

添加手势导航启用状态变化的监听。

**起始版本：** 10

<!--Device-window-function on(type: 'gestureNavigationEnabledChange', callback: Callback<boolean>): void--><!--Device-window-function on(type: 'gestureNavigationEnabledChange', callback: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'gestureNavigationEnabledChange' | 是 | 监听事件，固定为'gestureNavigationEnabledChange'，即手势导航启用状态变化事件。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<boolean> | 是 | 回调函数。返回当前手势导航的启用状态。true表示手势导航状态变化为启用；false表示手势导航状态变化为禁用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types.3. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |

**示例：**

```TypeScript
try {
  window.on('gestureNavigationEnabledChange', (data) => {
    console.info(`Succeeded in enabling the listener for gesture navigation status changes. Data: ${data}`);
  });
} catch (exception) {
  console.error(`Failed to enable the listener for gesture navigation status changes. Cause code: ${exception.code}, message: ${exception.message}`);
}

```


## on('waterMarkFlagChange')

```TypeScript
function on(type: 'waterMarkFlagChange', callback: Callback<boolean>): void
```

添加水印启用状态变化的监听。

**起始版本：** 10

<!--Device-window-function on(type: 'waterMarkFlagChange', callback: Callback<boolean>): void--><!--Device-window-function on(type: 'waterMarkFlagChange', callback: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'waterMarkFlagChange' | 是 | 监听事件，固定为'waterMarkFlagChange'，即水印启用状态变化事件。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<boolean> | 是 | 回调函数。返回当前水印的启用状态。true表示当前已启用水印；false表示当前未启用水印。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |

**示例：**

```TypeScript
try {
  window.on('waterMarkFlagChange', (data) => {
    console.info(`Succeeded in enabling the listener for watermark flag changes. Data: ${data}`);
  });
} catch (exception) {
  console.error(`Failed to enable the listener for watermark flag changes. Cause code: ${exception.code}, message: ${exception.message}`);
}

```

