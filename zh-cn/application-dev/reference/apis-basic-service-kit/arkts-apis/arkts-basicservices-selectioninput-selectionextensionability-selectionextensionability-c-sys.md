# SelectionExtensionAbility（系统接口）

本模块提供划词扩展能力，支持开发者通过继承SelectionExtensionAbility实现自定义的划词扩展服务，适用于在用户通过鼠标、触控板选中文本后提供搜索、翻译等扩展交互的场景。开发者需在工程配置中声明该 ExtensionAbility。具体的配置请参见 [实现一个划词扩展能力](../../../basic-services/selectionInput/selection-services-application-guide.md)。本模块提供的具体能力包括： - 生命周期管理：通过[onConnect](#onConnect)和 [onDisconnect](#onDisconnect)回调处理连接与断开逻辑。 - 提供context属性：开发者可通过context调用 [startAbility](arkts-basicservices-selectioninput-selectionextensioncontext-selectionextensioncontext-c-sys.md#startAbility)拉起同应用内的目标 Ability，或将context作为[createPanel](arkts-basicservices-selectionmanager-createpanel-f-sys.md#createPanel（系统接口）)的入参创建划词面板。 > **说明：** > > - 本模块仅支持PC/2in1设备。开发者可通过canIUse('SystemCapability.SelectionInput.Selection')判断当前设备是否支持该能力。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

<!--Device-unnamed-declare class SelectionExtensionAbility--><!--Device-unnamed-declare class SelectionExtensionAbility-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

## onConnect

```TypeScript
onConnect(want: Want): rpc.RemoteObject
```

当客户端连接到SelectionExtensionAbility时，系统会触发该回调，开发者可在该回调中返回RPC通信对象，用于客户端与服务端建立IPC通信连接。开发者需返回一个继承了rpc.RemoteObject的通信桩对象， 系统将该桩对象传递给客户端，客户端通过该桩对象与SelectionExtensionAbility进行IPC通信。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SelectionExtensionAbility-onConnect(want: Want): rpc.RemoteObject--><!--Device-SelectionExtensionAbility-onConnect(want: Want): rpc.RemoteObject-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 连接SelectionExtensionAbility时系统传入的Want对象，包含当前Ability的名称、Bundle名称等描述信息，用于在onConnect回调中获取 Ability连接配置，以便据此执行相应的初始化逻辑。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| rpc.RemoteObject | RemoteObject通信桩对象，开发者需实现该对象的远程消息处理方法（如onRemoteMessageRequest），系统将此对象传递给客户端用于IPC通信。 |

## 示例

```TypeScript
import SelectionExtensionAbility from '@ohos.selectionInput.SelectionExtensionAbility';
import rpc from '@ohos.rpc';
import { Want } from '@kit.AbilityKit';
import hilog from '@ohos.hilog';

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

## onDisconnect

```TypeScript
onDisconnect(): void
```

当客户端断开与SelectionExtensionAbility的连接（例如用户关闭划词开关或切换划词应用）时，系统会触发该回调。开发者可在该回调中执行与onConnect对应的清理操作，如调用 [destroyPanel](arkts-basicservices-selectionmanager-destroypanel-f-sys.md#destroyPanel（系统接口）)销毁已创建的面板、调用 [off('selectionCompleted')](arkts-basicservices-selectionmanager-offselectioncompleted-f-sys.md#off_selectionCompleted) 取消订阅的划词完成事件等。 仅当SelectionExtensionAbility正常断开连接时会触发该回调，异常断开场景（例如低内存终止进程）不会触发该回调。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SelectionExtensionAbility-onDisconnect(): void--><!--Device-SelectionExtensionAbility-onDisconnect(): void-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

## 示例

```TypeScript
import SelectionExtensionAbility from '@ohos.selectionInput.SelectionExtensionAbility';
import hilog from '@ohos.hilog';

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

SelectionExtensionAbility的上下文环境，继承自[ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md#ExtensionContext)。开发者可通过 context调用 [startAbility](arkts-basicservices-selectioninput-selectionextensioncontext-selectionextensioncontext-c-sys.md#startAbility)拉起同应用内的目 标Ability，或将context作为[createPanel](arkts-basicservices-selectionmanager-createpanel-f-sys.md#createPanel（系统接口）)的入参创建划词面 板。

**类型：** [SelectionExtensionContext](arkts-basicservices-selectioninput-selectionextensioncontext-selectionextensioncontext-c-sys.md)

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SelectionExtensionAbility-context: SelectionExtensionContext--><!--Device-SelectionExtensionAbility-context: SelectionExtensionContext-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

