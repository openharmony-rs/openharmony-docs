# offFoldStatusChange

## 导入模块

```TypeScript
import { display } from '@kit.ArkUI';
```

## offFoldStatusChange

```TypeScript
function offFoldStatusChange(callback?: Callback<FoldStatus>): void
```

Unregister the callback for fold status changes.

**起始版本：** 23

<!--Device-display-function offFoldStatusChange(callback?: Callback<FoldStatus>): void--><!--Device-display-function offFoldStatusChange(callback?: Callback<FoldStatus>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;FoldStatus&gt; | 否 | Unregister the callback function. If not provided, all callbacks for the given event type will be removed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例**

```TypeScript
// 如果通过on注册多个callback，同时关闭所有callback监听
display.offFoldStatusChange();

let callback: Callback<display.FoldStatus> = (data: display.FoldStatus) => {
  console.info(`unregistering FoldStatus changes callback. Data: ${data}`);
};
// 关闭传入的callback监听
display.offFoldStatusChange(callback);
```

