# onPrivateModeChange（系统接口）

## onPrivateModeChange

```TypeScript
function onPrivateModeChange(callback: Callback<boolean>): void
```

Register the callback for private mode changes.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-display-function onPrivateModeChange(callback: Callback<boolean>): void--><!--Device-display-function onPrivateModeChange(callback: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;boolean&gt; | 是 | Callback used to return the result whether display is on private mode or not |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## 示例

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let callback: Callback<boolean> = (data: boolean) => {
  console.info(`Listening enabled. Data: ${data}`);
};
try {
  display.onPrivateModeChange(callback);
} catch (exception) {
  let error = exception as BusinessError;
  console.error(`Failed to register callback. Code: ${error.code} , message: ${error.message}`);
}
```

