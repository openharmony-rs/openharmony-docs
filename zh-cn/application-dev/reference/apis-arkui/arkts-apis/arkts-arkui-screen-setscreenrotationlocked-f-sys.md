# setScreenRotationLocked（系统接口）

## 导入模块

```TypeScript
import { screen } from '@kit.ArkUI';
```

## setScreenRotationLocked

```TypeScript
function setScreenRotationLocked(isLocked:boolean, callback: AsyncCallback<void>): void
```

设置自动转屏开关是否锁定，使用callback异步回调。

**起始版本：** 9

<!--Device-screen-function setScreenRotationLocked(isLocked:boolean, callback: AsyncCallback<void>): void--><!--Device-screen-function setScreenRotationLocked(isLocked:boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isLocked | boolean | 是 | 自动转屏开关是否锁定。true为锁定，false为未锁定。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当设置自动转屏是否锁定成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let isLocked: boolean = false;
// 设置自动转屏开关为未锁定
screen.setScreenRotationLocked(isLocked, (err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to unlock auto rotate. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in unlocking auto rotate.');
});

```


## setScreenRotationLocked

```TypeScript
function setScreenRotationLocked(isLocked:boolean): Promise<void>
```

设置自动转屏开关是否锁定，使用Promise异步回调。

**起始版本：** 9

<!--Device-screen-function setScreenRotationLocked(isLocked:boolean): Promise<void>--><!--Device-screen-function setScreenRotationLocked(isLocked:boolean): Promise<void>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isLocked | boolean | 是 | 自动转屏开关是否锁定。true为锁定，false为未锁定。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let isLocked: boolean = false;
// 设置自动转屏开关为未锁定
screen.setScreenRotationLocked(isLocked).then(() => {
  console.info('Succeeded in unlocking auto rotate');
}).catch((err: BusinessError) => {
  console.error(`Failed to unlock auto rotate. Code: ${err.code}, message: ${err.message}`);
});

```

