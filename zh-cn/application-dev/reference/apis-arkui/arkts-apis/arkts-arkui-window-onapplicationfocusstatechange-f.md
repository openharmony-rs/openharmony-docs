# onApplicationFocusStateChange

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

<a id="onapplicationfocusstatechange"></a>
## onApplicationFocusStateChange

```TypeScript
function onApplicationFocusStateChange(callback: Callback<boolean>): void
```

开启应用进程获焦状态变化的监听。此监听针对应用间的获焦状态变化，若同应用内窗口间的获焦状态发生变化，则不会触发回调函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-window-function onApplicationFocusStateChange(callback: Callback<boolean>): void--><!--Device-window-function onApplicationFocusStateChange(callback: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回当前应用进程获焦状态的变化。true表示当前应用进程变为获焦状态；false表示当前应用进程变为失焦状态。 |

**示例：**

```TypeScript
import { window } from '@kit.ArkUI';

try {
  window.onApplicationFocusStateChange((data) =>{
      console.info(`Succeeded in enabling the listener for application focus state changes. Data: ${data}`);
  })
} catch(exception){
  console.error(`Failed to enable the listener for application focus state changes. Cause code: ${exception.code}, message: ${exception.message}`);
}

```

