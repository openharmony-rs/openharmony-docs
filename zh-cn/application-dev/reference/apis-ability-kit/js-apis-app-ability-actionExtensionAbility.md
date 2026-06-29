# @ohos.app.ability.ActionExtensionAbility (支持业务操作自定义的ExtensionAbility组件)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

ActionExtensionAbility是为开发者提供的自定义操作业务模板，继承自[UIExtensionAbility](js-apis-app-ability-uiExtensionAbility.md)。

开发者通过实现ActionExtensionAbility，为其他应用提供内容查看与处理功能。例如，开发者使用ActionExtensionAbility实现了文本翻译功能。其他应用可以通过调用该ActionExtensionAbility来处理需要翻译的内容，并获取到处理后的翻译内容。

各类Ability的继承关系详见[继承关系说明](./js-apis-app-ability-ability.md#ability的继承关系说明)。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 10 开始支持，从API version 26.0.0开始废弃，暂无替代接口。
>
> - 本模块接口仅可在Stage模型下使用。

## 导入模块

```ts
import { ActionExtensionAbility } from '@kit.AbilityKit';
```

## ActionExtensionAbility<sup>(deprecated)</sup>

ActionExtensionAbility是为开发者提供的自定义操作业务模板，继承自[UIExtensionAbility](js-apis-app-ability-uiExtensionAbility.md)。

ActionExtensionAbility主要用于实现宿主应用的内容查看及交互处理功能。例如，添加一个书签、将选中的文本翻译成其他语言、在当前页面编辑图像等。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**废弃版本：** 26.0.0

**替代接口：** 暂无替代接口
