# onFoldDisplayModeChange

## 导入模块

```TypeScript
import { display } from '@kit.ArkUI';
```

## onFoldDisplayModeChange

```TypeScript
function onFoldDisplayModeChange(callback: Callback<FoldDisplayMode>): void
```

Register the callback for fold display mode changes.

**起始版本：** 23

<!--Device-display-function onFoldDisplayModeChange(callback: Callback<FoldDisplayMode>): void--><!--Device-display-function onFoldDisplayModeChange(callback: Callback<FoldDisplayMode>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[FoldDisplayMode](arkts-arkui-display-folddisplaymode-e.md)&gt; | 是 | Callback used to return the current fold display mode |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

/**
 * 注册监听的callback参数要采用对象传递.
 * 若使用匿名函数注册，每次调用会创建一个新的底层对象，引起内存泄漏问题。
 */
let callback: Callback<display.FoldDisplayMode> = (data: display.FoldDisplayMode) => {
  console.info(`Listening enabled. Data: ${data}`);
}; 
display.onFoldDisplayModeChange(callback);
```

