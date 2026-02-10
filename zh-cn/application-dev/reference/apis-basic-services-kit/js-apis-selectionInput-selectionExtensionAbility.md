# @ohos.selectionInput.SelectionExtensionAbility (划词扩展能力)

<!--Kit: Basic Services Kit-->
<!--Subsystem: SelectionInput-->
<!--Owner: @no86-->
<!--Designer: @mmwwbb-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->

本模块提供划词扩展功能，用于用户通过鼠标、触控板等方式选择文本后的搜索、翻译等场景。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 24开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本模块仅支持PC/2in1设备。

## 导入模块

```ts
import SelectionExtensionAbility from '@ohos.selectionInput.SelectionExtensionAbility';
```
## SelectionExtensionAbility

**系统能力：** SystemCapability.SelectionInput.Selection

**模型约束：** 此接口仅可在Stage模式下使用。

**ArkTS-Dyn起始版本**：24

**ArkTS-Sta起始版本**：24

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| context | [SelectionExtensionContext](js-apis-selectionInput-selectionExtensionContext.md) | 否 | 否 | SelectionExtensionAbility的上下文环境，继承自[ExtensionContext](../apis-ability-kit/js-apis-inner-application-extensionContext.md)。 |

### onConnect

onConnect(want: Want): rpc.RemoteObject

当[SelectionExtensionAbility](#selectionextensionability)实例完成创建时，系统会触发该回调，开发者可在该回调中执行初始化逻辑（如定义变量、加载资源、监听划词事件等）。

**系统能力：** SystemCapability.SelectionInput.Selection

**模型约束：** 此接口仅可在Stage模式下使用。

**ArkTS-Dyn起始版本**：24

**ArkTS-Sta起始版本**：24

**参数：**

| 参数名 | 类型          | 必填 | 说明                             |
| ------ | ----------- | ---- | ------------------------------- |
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md#want) | 是 | 当前SelectionExtensionAbility的Want类型信息，包括Ability名称、Bundle名称等。 |

**返回值：**
| 类型   | 说明                                                                 |
| ------- | ------------------------------------------------------------------ |
| [rpc.RemoteObject](../apis-ipc-kit/js-apis-rpc.md#iremoteobject) | RemoteObject对象，用于客户端和服务端通信。  |

**示例：**

```ts
import SelectionExtensionAbility from '@ohos.selectionInput.SelectionExtensionAbility';
import rpc from '@ohos.rpc';
import { Want } from '@kit.AbilityKit';
import hilog from '@ohos.hilog';

const TAG: string = '[SelectionExtensionAbility]';

class StubTest extends rpc.RemoteObject {
  constructor(des: string) {
    super(des);
  }
  onConnect(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence, option: rpc.MessageOption) {
  }
}

class ServiceExtAbility extends SelectionExtensionAbility {
  onConnect(want: Want): rpc.RemoteObject {
    hilog.info(0x0000, TAG, `onConnect, want: ${want.abilityName}`);
    return new StubTest('test');
  }
}
```

### onDisconnect

onDisconnect(): void

当[SelectionExtensionAbility](#selectionextensionability)实例被销毁（例如用户关闭划词开关或切换划词应用）时，系统触发该回调。开发者可以在该生命周期中执行资源清理、数据保存等相关操作。使用同步回调或Promise异步回调。

在执行完[onDisconnect](#ondisconnect)生命周期回调后，应用可能会退出，从而可能导致[onDisconnect](#ondisconnect)中的异步函数未能正确执行，比如异步写入数据库。推荐使用Promise异步回调，避免因应用退出导致[onDisconnect](#ondisconnect)中的异步函数（比如异步写入数据库）未能正确执行。

仅当[SelectionExtensionAbility](#selectionextensionability)正常退出时会触发该回调，异常退出场景（例如低内存终止进程）不会触发该回调。

**系统能力：** SystemCapability.SelectionInput.Selection

**模型约束：** 此接口仅可在Stage模式下使用。

**ArkTS-Dyn起始版本**：24

**ArkTS-Sta起始版本**：24

**示例：**

```ts
import SelectionExtensionAbility from '@ohos.selectionInput.SelectionExtensionAbility';
import hilog from '@ohos.hilog';

const TAG: string = '[SelectionExtensionAbility]';

class ServiceExtAbility extends SelectionExtensionAbility {
  onDisconnect(): void {
    hilog.info(0x0000, TAG, `onDisconnect`);
  }
}
```
