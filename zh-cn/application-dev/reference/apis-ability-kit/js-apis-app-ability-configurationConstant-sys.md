# @ohos.app.ability.ConfigurationConstant (环境变量相关的常量定义)(系统接口)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wkljy-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

ConfigurationConstant模块提供[Configuration](js-apis-app-ability-configuration.md)操作相关的系统预置枚举。包括语言、深浅色、字体等环境变量的枚举值，当前文件只包含品牌色枚举。

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.app.ability.ConfigurationConstant (环境变量相关的常量定义)](js-apis-app-ability-configurationConstant.md)。

## 导入模块

```ts
import { ConfigurationConstant } from '@kit.AbilityKit';
```

## BrandColorStrategy

表示品牌色策略的枚举，用于[ConfigurationStrategy](js-apis-app-ability-uiExtensionAbility-sys.md#configurationstrategy)的brandColorStrategy字段，指定[UIExtensionAbility](js-apis-app-ability-uiExtensionAbility.md)组件中品牌色的取值来源。

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityBase

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| BRAND_COLOR_FOLLOW_SYSTEM | 0 | 表示UIExtensionAbility的品牌色跟随系统。系统品牌色发生变化时，组件的品牌色随之变化。未指定品牌色策略时，系统默认使用该值。 |
| BRAND_COLOR_FOLLOW_UEC | 1 | 表示UIExtensionAbility的品牌色跟随宿主UIExtensionComponent控件。组件使用宿主UIExtensionComponent控件传入的品牌色，系统品牌色发生变化时不会覆盖该品牌色。 |
