# @ohos.selectionInput.SelectionExtensionAbility (划词扩展能力)

<!--Kit: Basic Services Kit-->
<!--Subsystem: SelectionInput-->
<!--Owner: @no86-->
<!--Designer: @mmwwbb-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->

本模块提供划词扩展能力，支持开发者通过继承SelectionExtensionAbility实现自定义的划词扩展服务（如监听划词事件、创建划词面板、显示划词面板等）。适用于需要在用户通过鼠标、触控板选中文本后提供搜索、翻译等扩展交互的场景，帮助开发者快速接入划词扩展能力，为用户提供更丰富的文本交互体验。

> **说明：**
>
> - 本模块首批接口从API version 24开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本模块仅支持PC/2in1设备。开发者可通过canIUse('SystemCapability.SelectionInput.Selection')判断当前设备是否支持该能力。

## 导入模块

```ts
import { SelectionExtensionAbility } from '@kit.BasicServicesKit';
```
## SelectionExtensionAbility

**系统能力：** SystemCapability.SelectionInput.Selection

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| context | [SelectionExtensionContext](./js-apis-selectionInput-selectionExtensionContext.md) | 否 | 否 | SelectionExtensionAbility的上下文环境，继承自[ExtensionContext](../apis-ability-kit/js-apis-inner-application-extensionContext.md)。 |

### onConnect

onConnect(want: Want): rpc.RemoteObject

当客户端连接到SelectionExtensionAbility时，系统会触发该回调，开发者可在该回调中返回RPC通信对象，用于客户端与服务端建立IPC通信连接。开发者需返回一个实现了rpc.RemoteObject的通信桩对象，系统将该桩对象传递给客户端，客户端通过该桩对象与SelectionExtensionAbility进行IPC通信。

**系统能力：** SystemCapability.SelectionInput.Selection

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型          | 必填 | 说明                             |
| ------ | ----------- | ---- | ------------------------------- |
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md#want) | 是 | 连接SelectionExtensionAbility时系统传入的Want对象，包含当前Ability的名称、Bundle名称等描述信息，用于在onConnect回调中获取Ability连接配置，以便据此执行相应的初始化逻辑。 |

**返回值：**
| 类型   | 说明                                                                 |
| ------- | ------------------------------------------------------------------ |
| [rpc.RemoteObject](../apis-ipc-kit/js-apis-rpc.md#iremoteobject) | RemoteObject通信桩对象，开发者需实现该对象的远程消息处理方法（如onRemoteMessageRequest），系统将此对象传递给客户端用于IPC通信。  |

**示例：**

```ts
import { SelectionExtensionAbility } from '@kit.BasicServicesKit';
import { rpc } from '@kit.IPCKit';
import { Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG: string = '[SelectionExtensionAbility]';

// 定义RPC通信桩类，用于客户端和服务端之间的IPC通信
class StubTest extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteMessageRequest(
    code: number,
    data: rpc.MessageSequence,
    reply: rpc.MessageSequence,
    options: rpc.MessageOption
  ): boolean | Promise<boolean> {
    return true;
  }
}

class ServiceExtAbility extends SelectionExtensionAbility {
  // 实现onConnect生命周期回调，在客户端连接到SelectionExtensionAbility时返回RPC通信对象
  onConnect(want: Want): rpc.RemoteObject {
    hilog.info(0x0000, TAG, `onConnect, want: ${want.abilityName}`);
    // 返回RPC通信桩对象，用于客户端与服务端建立IPC通信
    return new StubTest('test');
  }
}
```

### onDisconnect

onDisconnect(): void

当客户端断开与SelectionExtensionAbility的连接（例如用户关闭划词开关或切换划词应用）时，系统触发该回调。开发者可以在该回调中执行与连接断开相关的清理操作。

仅当SelectionExtensionAbility正常断开连接时会触发该回调，异常断开场景（例如低内存终止进程）不会触发该回调。

**系统能力：** SystemCapability.SelectionInput.Selection

**模型约束：** 此接口仅可在Stage模型下使用。

**示例：**

```ts
import { SelectionExtensionAbility } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG: string = '[SelectionExtensionAbility]';

class ServiceExtAbility extends SelectionExtensionAbility {
  // 实现onDisconnect生命周期回调，在客户端断开与SelectionExtensionAbility的连接时执行相关清理操作
  onDisconnect(): void {
    hilog.info(0x0000, TAG, `onDisconnect`);
  }
}
```
