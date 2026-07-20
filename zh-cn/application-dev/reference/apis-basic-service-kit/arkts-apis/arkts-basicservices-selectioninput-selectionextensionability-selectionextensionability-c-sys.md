# SelectionExtensionAbility（系统接口）

本模块提供划词扩展功能，用于用户通过鼠标、触控板等方式选择文本后的搜索、翻译等场景。

> **说明：**  
> - 本模块仅支持PC/2in1设备。

**起始版本：** 24

<!--Device-unnamed-declare class SelectionExtensionAbility--><!--Device-unnamed-declare class SelectionExtensionAbility-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { SelectionExtensionAbility } from '@kit.BasicServicesKit';
```

<a id="onconnect"></a>
## onConnect

```TypeScript
onConnect(want: Want): rpc.RemoteObject
```

当SelectionExtensionAbility实例完成创建时，系统会触发该回调，开发者可在该回调中执行初始化逻辑（如定义变量、加载资源、监听划词事件等）。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SelectionExtensionAbility-onConnect(want: Want): rpc.RemoteObject--><!--Device-SelectionExtensionAbility-onConnect(want: Want): rpc.RemoteObject-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 当前SelectionExtensionAbility的Want类型信息，包括Ability名称、Bundle名称等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| rpc.RemoteObject | RemoteObject对象，用于客户端和服务端通信。 |

**示例：**

```TypeScript
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

<a id="ondisconnect"></a>
## onDisconnect

```TypeScript
onDisconnect(): void
```

当SelectionExtensionAbility实例被销毁（例如用户关闭划词开关或切换划词应用）时，系统触发该回调。开发者可以在该生命周期中执行资源清理、数据保存等相关操作。使用同步回调或Promise异步回调。在执行完onDisconnect生命周期回调后，应用可能会退出，从而可能导致onDisconnect中的异步函数未能正确执行，比如异步写入数据库。推荐使用Promise异步回调，避免因应用退出导致onDisconnect中的异步函数（比如异步写入数据库）未能正确执行。仅当SelectionExtensionAbility正常退出时会触发该回调，异常退出场景（例如低内存终止进程）不会触发该回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SelectionExtensionAbility-onDisconnect(): void--><!--Device-SelectionExtensionAbility-onDisconnect(): void-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

**示例：**

```TypeScript
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

## context

```TypeScript
context: SelectionExtensionContext
```

SelectionExtensionAbility的上下文环境，继承自[ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)。

**类型：** SelectionExtensionContext

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SelectionExtensionAbility-context: SelectionExtensionContext--><!--Device-SelectionExtensionAbility-context: SelectionExtensionContext-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

