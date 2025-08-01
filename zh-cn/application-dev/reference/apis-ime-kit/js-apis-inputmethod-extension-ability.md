# @ohos.InputMethodExtensionAbility (InputMethodExtensionAbility)

本模块支持开发者自行开发输入法应用，以及管理输入法应用的生命周期。

> **说明：**
>
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 本模块接口仅可在Stage模型下使用。

## 导入模块

```ts
import { InputMethodExtensionAbility } from '@kit.IMEKit';
```

## InputMethodExtensionAbility

输入法Extension ability类。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

### 属性

输入法Extension ability的上下文信息。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| context | [InputMethodExtensionContext](js-apis-inputmethod-extension-context.md) | 否 | 否 | InputMethodExtension的上下文环境，继承于ExtensionContext。 |

### onCreate

onCreate(want: Want): void

Extension生命周期回调，在拉起Extension输入法应用时调用，执行初始化输入法应用操作。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型          | 必填 | 说明                             |
| ------ | ----------- | ---- | ------------------------------- |
| want   | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 当前Extension相关的Want类型信息，包括ability名称、bundle名称等。 |

**示例：**

```ts
import { InputMethodExtensionAbility } from '@kit.IMEKit';
import { Want } from '@kit.AbilityKit';
class InputMethodExt extends InputMethodExtensionAbility {
  onCreate(want: Want): void {
    console.info('onCreate, want:' + want.abilityName);
  }
}
```

### onDestroy

onDestroy(): void

Extension生命周期回调，在销毁输入法应用时回调，执行资源清理等操作。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**示例：**

```ts
import { InputMethodExtensionAbility } from '@kit.IMEKit';
class InputMethodExt extends InputMethodExtensionAbility {
  onDestroy(): void {
    console.info('onDestroy');
  }
}
```
