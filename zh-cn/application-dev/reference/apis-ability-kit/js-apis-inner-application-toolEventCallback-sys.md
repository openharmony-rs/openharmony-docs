# ToolEventCallback (系统接口)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @littlejerry1-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

ToolEventCallback用于接收CLI工具进程运行期间产生的会话事件。

**起始版本：** 26.0.0

> **说明：**
>
> 本模块仅适用于ArkTS-Dyn。
>
> 本模块接口为系统接口。
>
> 本模块接口仅可在Stage模型下使用。

## 导入模块

```ts
import { common } from '@kit.AbilityKit';
```

## ToolEventCallback

CLI工具会话事件的回调接口。

**起始版本：** 26.0.0

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 名称    | 类型                                                 | 只读 | 可选 | 说明                      |
| ------- | ---------------------------------------------------- | ---- | ---- | ------------------------- |
| onEvent | (event: [CliToolEvent](js-apis-inner-application-cliToolEvent-sys.md#clitoolevent)) => void | 否   | 否   | CLI工具会话事件回调函数。 |

**示例：**

```ts
import { common } from '@kit.AbilityKit';

let callback: common.ToolEventCallback = {
  onEvent: (event: common.CliToolEvent) => {
    console.info('tool event type: ' + event.toolEventType + ', data: ' + event.data);
  }
};
```
