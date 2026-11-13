# @ohos.app.ability.UIExtensionAbility (带界面的ExtensionAbility组件)(系统接口)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c; @xuzhihao666-->
<!--Designer: @xhz-sz-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

UIExtensionAbility组件是带界面的ExtensionAbility组件，继承自[ExtensionAbility](js-apis-app-ability-extensionAbility.md)，提供了组件创建、销毁、前后台切换等基础生命周期。和UIAbility组件不同，UIExtensionAbility组件不会作为单独的任务在任务视图中体现。UIExtensionAbility组件被宿主窗口启动，该组件的前后台切换状态、以及是否可见均跟随宿主窗口。

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块接口仅可在Stage模型下使用。
>
> - 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.app.ability.UIExtensionAbility (带界面的ExtensionAbility组件)](js-apis-app-ability-uiExtensionAbility.md)。

## 导入模块

```ts
import { UIExtensionAbility } from '@kit.AbilityKit';
```

## UIExtensionAbility

表示包含UI界面的扩展组件，提供组件创建、销毁、前后台切换等生命周期回调。

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| onGetConfigurationStrategy | [OnGetConfigurationStrategyFn](#ongetconfigurationstrategyfn) | 否 | 是 | 组件的配置策略回调。系统在[onCreate](js-apis-app-ability-uiExtensionAbility.md#oncreate)回调之后、[onSessionCreate](js-apis-app-ability-uiExtensionAbility.md#onsessioncreate)回调之前触发该回调，用于获取组件的配置策略，例如组件中品牌色的取值来源。该生命周期回调为可选事件。组件未实现时，系统使用默认配置策略，例如品牌色会跟随系统。该回调仅对系统应用生效，非系统应用实现该回调后不会被触发。 |

**示例：**

```ts
// UIExtensionAbility组件不支持三方应用直接继承，故以派生类ShareExtensionAbility举例说明。
import { ShareExtensionAbility, ConfigurationConstant, ConfigurationStrategy } from '@kit.AbilityKit';

export default class ShareExtAbility extends ShareExtensionAbility {
  // 返回值类型为ConfigurationStrategy，此处指定品牌色跟随宿主UIExtensionComponent控件。
  onGetConfigurationStrategy = ():ConfigurationStrategy => {
    return { brandColorStrategy: ConfigurationConstant.BrandColorStrategy.BRAND_COLOR_FOLLOW_UEC };
  }
}
```

## ConfigurationStrategy

表示UIExtensionAbility组件的配置策略。

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| brandColorStrategy | [ConfigurationConstant.BrandColorStrategy](js-apis-app-ability-configurationConstant-sys.md#brandcolorstrategy) | 否 | 是 | 表示品牌色策略，默认值为ConfigurationConstant.BrandColorStrategy.BRAND_COLOR_FOLLOW_SYSTEM，即品牌色跟随系统。<br>取值为BRAND_COLOR_FOLLOW_UEC时，组件使用宿主UIExtensionComponent控件传入的品牌色，系统品牌色发生变化时不会覆盖该品牌色。 |

## OnGetConfigurationStrategyFn

type OnGetConfigurationStrategyFn = () => ConfigurationStrategy

UIExtensionAbility组件的配置策略回调函数类型。

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [ConfigurationStrategy](#configurationstrategy) | 组件的配置策略。 |
