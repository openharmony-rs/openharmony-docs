# offApplicationFocusStateChange

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## offApplicationFocusStateChange

```TypeScript
function offApplicationFocusStateChange(callback?: Callback<boolean>): void
```

关闭应用进程获焦状态变化的监听。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-window-function offApplicationFocusStateChange(callback?: Callback<boolean>): void--><!--Device-window-function offApplicationFocusStateChange(callback?: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;boolean&gt; | 否 | 已注册的回调函数。如果传入参数，则关闭该监听。如果未传入参数，则关闭所有应用进程焦点状态变化的监听。 |

**示例**

```TypeScript
import { window } from '@kit.ArkUI';

const callback = (bool: boolean) => {
  // ...
}
try {
  window.onApplicationFocusStateChange(callback);
  window.offApplicationFocusStateChange(callback);
  // 如果通过on开启多个callback进行监听，同时关闭所有监听：
  window.offApplicationFocusStateChange(); 
} catch (exception) {
  console.error(`Failed to disable the listener for application focus state changes. Cause code: ${exception.code}, message: ${exception.message}`);
}
```
