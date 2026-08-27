# InputMethodExtensionAbility

@ohos.InputMethodExtensionAbility模块提供输入法ExtensionAbility（扩展能力基类）的基础类定义，是开发输入法应用的入口和生命周期管理框架。 本模块是输入法ExtensionAbility的核心类模块，定义了`InputMethodExtensionAbility`类，作为输入法应用的Extension基类。开发者需继承该类并实现`onCreate`和`onDestroy`生命周期回调， 系统在拉起和销毁输入法Extension时自动调用这些回调。 本模块提供两大核心能力：1）通过`onCreate(want)`回调实现输入法应用的初始化——系统拉起输入法Extension时调用，开发者在此完成资源加载、面板创建等初始化工作；2）通过`onDestroy()` 回调实现输入法应用的资源清理——系统销毁输入法Extension时调用，开发者在此释放资源。此外，通过`context`属性提供`InputMethodExtensionContext`上下文对象，供开发者在生命周期内执行销毁自身、 拉起其他应用等上下文级操作。 当开发输入法应用时必须使用本模块。开发者通过继承`InputMethodExtensionAbility` → 在module.json5中配置ExtensionAbility信息 → 系统拉起时触发`onCreate`（初始化） → 系统销毁或开发者主动调用`context.destroy()`时触发`onDestroy`（清理）。   
> **说明：**
   
> 
   
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
   
> 
   
> `InputMethodExtensionAbility`仅定义了基础的`onCreate`和`onDestroy`两个生命周期回调。输入法的核心交互能力（如面板创建/销毁、键盘事件监听、客户端绑定等） 需在`onCreate`回调中通过`@ohos.inputMethodEngine`模块获取`InputMethodAbility`对象来实现。`onCreate`是所有关键对象获取和面板创建的唯一入口，必须在该回调中完成初始化。
   
> 
   
> `InputMethodExtensionAbility`的`context`属性类型为`InputMethodExtensionContext`（来自`@ohos.InputMethodExtensionContext`模块）， 属于关联关系——`InputMethodExtensionAbility`拥有`InputMethodExtensionContext`的上下文能力。
 | Class | 说明 | |---|---| | InputMethodExtensionAbility | 输入法ExtensionAbility基类，提供输入法应用的生命周期管理框架。关键成员包括：`context`属性（`InputMethodExtensionContext`上下文对象）、 `onCreate(want)`方法（初始化回调）、`onDestroy()`方法（销毁回调）。开发者需继承此类并重写生命周期方法。 |

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## 导入模块

```TypeScript
import { InputMethodExtensionAbility } from '@kit.IMEKit';
```

## onCreate

```TypeScript
onCreate(want: Want): void
```

生命周期回调，在拉起输入法Extension时调用，用于初始化输入法应用。   
- 含义/功能：系统拉起输入法ExtensionAbility时触发的初始化回调。开发者在该回调中完成输入法应用的所有关键初始化工作，包括获取核心能力对象、创建输入法面板、订阅事件等。   
- 使用场景：当系统根据module.json5配置拉起输入法ExtensionAbility时自动触发。这是输入法应用初始化的唯一入口，所有关键对象的获取和面板创建必须在此回调中完成。   
- 使用后效果：回调执行完成后，输入法应用进入正常运行状态。系统将随后触发键盘显示/隐藏请求、客户端绑定等事件，输入法应用需在此之前完成初始化（如已订阅`on('inputStart')`事件、已创建面板等）， 否则后续事件可能无法正常响应。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 当前Extension相关的Want类型信息，包括Ability名称、bundle名称等。 |

**示例**

```TypeScript
import { InputMethodExtensionAbility, InputMethodAbility, KeyboardDelegate, PanelInfo, PanelType, PanelFlag, inputMethodEngine } from '@kit.IMEKit';
import { Want } from '@kit.AbilityKit';

class InputMethodExt extends InputMethodExtensionAbility {
  onCreate(want: Want): void {
    console.info(`onCreate, want: ${want.abilityName}`);

    // 获取输入法能力对象
    let ability: InputMethodAbility = inputMethodEngine.getInputMethodAbility();

    // 获取键盘代理对象
    let keyboardDelegate: KeyboardDelegate = inputMethodEngine.getKeyboardDelegate();

    // 创建面板
    let panelInfo: PanelInfo = {
      type: PanelType.SOFT_KEYBOARD,
      flag: PanelFlag.FLG_FIXED
    };
    ability.createPanel(this.context, panelInfo, (err, panel) => {
      if (err) {
        console.error(`Failed to create panel: ${err.code}`);
        return;
      }
      console.info('Succeeded in creating panel.');
    });

    // 订阅输入法绑定事件
    ability.on('inputStart', (kbController, inputClient) => {
      console.info('Input method bound to client.');
    });
  }
}
```

## onDestroy

```TypeScript
onDestroy(): void
```

生命周期回调，在销毁输入法应用时调用，用于资源清理。   
- 含义/功能：系统销毁输入法ExtensionAbility时触发的清理回调。开发者在该回调中释放面板、取消事件订阅等资源清理工作。   
- 使用场景：当系统主动销毁输入法ExtensionAbility（如系统回收资源、用户切换到其他输入法）或开发者主动调用`context.destroy()`触发销毁时自动触发。 注意：`onDestroy`回调执行后，`context`将不可用，不应在回调中或回调后继续使用`context`对象。   
- 使用后效果：回调执行完成后，输入法ExtensionAbility进程终止，所有资源应已释放。调用后再进行其他操作将不起效。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**示例**

```TypeScript
import { InputMethodExtensionAbility } from '@kit.IMEKit';

class InputMethodExt extends InputMethodExtensionAbility {
  onDestroy(): void {
    // 销毁面板、取消事件订阅等清理工作
    console.info('onDestroy');
  }
}
```

## context

```TypeScript
context: InputMethodExtensionContext
```

InputMethodExtensionAbility的上下文环境，继承于ExtensionContext。

**类型：** [InputMethodExtensionContext](arkts-ime-inputmethodextensioncontext-c.md)

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework
