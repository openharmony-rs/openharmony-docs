# off（系统接口）

## 导入模块

```TypeScript
import { screen } from '@kit.ArkUI';
```

## off

```TypeScript
function off(eventType: 'connect' | 'disconnect' | 'change', callback?: Callback<number>): void
```

关闭屏幕状态变化的监听。

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventType | 'connect' \| 'disconnect' \| 'change' | 是 | 监听事件。   -eventType为"connect"表示屏幕连接事件。   -eventType为"disconnect"表示断开屏幕连接事件。   -eventType为"change"表示屏幕状态改变事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | 回调函数。返回屏幕的id，该参数为整数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.  2. Incorrect parameter types. |

**示例**

```TypeScript
let callback: Callback<number> = (data: number) => {
  console.info(`Succeeded in unregistering the callback for screen changes. Data: ${data}`);
};
// 关闭传入的callback监听
screen.off('connect', callback);
// 如果通过on注册多个callback，同时关闭所有callback监听
screen.off('connect');
```


## off

```TypeScript
function off(eventType: 'connect' | 'disconnect' | 'change', callback?: Callback<number>): void
```

关闭屏幕状态变化的监听。

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventType | 'connect' \| 'disconnect' \| 'change' | 是 | 监听事件。   -eventType为"connect"表示屏幕连接事件。   -eventType为"disconnect"表示断开屏幕连接事件。   -eventType为"change"表示屏幕状态改变事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | 回调函数。返回屏幕的id，该参数为整数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.  2. Incorrect parameter types. |

**示例**

参见 [off](#off)


## off

```TypeScript
function off(eventType: 'connect' | 'disconnect' | 'change', callback?: Callback<number>): void
```

关闭屏幕状态变化的监听。

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventType | 'connect' \| 'disconnect' \| 'change' | 是 | 监听事件。   -eventType为"connect"表示屏幕连接事件。   -eventType为"disconnect"表示断开屏幕连接事件。   -eventType为"change"表示屏幕状态改变事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | 回调函数。返回屏幕的id，该参数为整数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.  2. Incorrect parameter types. |

**示例**

参见 [off](#off)
