# onChange（系统接口）

## 导入模块

```TypeScript
import { screen } from '@kit.ArkUI';
import { screenshot } from '@kit.ArkUI';
```

## onChange

```TypeScript
function onChange(callback: Callback<long>): void
```

Register the callback for screen change.

**起始版本：** 23

<!--Device-screen-function onChange(callback: Callback<long>): void--><!--Device-screen-function onChange(callback: Callback<long>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;long&gt; | 是 | Callback used to return the screen ID. This parameter is callable. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

```TypeScript
let callback: Callback<long> = (data: long) => {
  console.info(`Succeeded in registering the callback for screen disconnect. Data: ${data}`)
};
screen.onChange(callback);
```

