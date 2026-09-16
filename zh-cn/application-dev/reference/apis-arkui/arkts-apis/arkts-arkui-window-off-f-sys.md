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

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'systemBarTintChange' | 是 | 监听事件，固定为'systemBarTintChange'，即导航栏、状态栏属性变化事件。 |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;[SystemBarTintState](arkts-arkui-window-systembartintstate-i-sys.md)&gt; | 否 | 回调函数。返回当前的状态栏、导航栏信息集合。如果传入参数，则关闭该监听。如果未传入参数，则关闭所有状态栏、导航栏属性变化的监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible cause: 1. Incorrect parameter types; 2. Parameter verification failed. |


## off('gestureNavigationEnabledChange')

```TypeScript
function off(type: 'gestureNavigationEnabledChange', callback?: Callback<boolean>): void
```

移除手势导航启用状态变化的监听。

**起始版本：** 10

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'gestureNavigationEnabledChange' | 是 | 监听事件，固定为'gestureNavigationEnabledChange'，即手势导航启用状态变化事件。 |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;boolean&gt; | 否 | 已注册的回调函数。如果传入参数，则关闭该监听。如果未传入参数，则关闭所有手势导航启用状态变化的监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible cause: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |


## off('waterMarkFlagChange')

```TypeScript
function off(type: 'waterMarkFlagChange', callback?: Callback<boolean>): void
```

移除水印启用状态变化的监听。

**起始版本：** 10

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'waterMarkFlagChange' | 是 | 监听事件，固定为'waterMarkFlagChange'，即水印启用状态变化事件。 |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;boolean&gt; | 否 | 已注册的回调函数。如果传入参数，则关闭该监听。如果未传入参数，则关闭所有水印启用状态变化的监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible cause: 1. Incorrect parameter types;<br>2. Parameter verification failed. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
