# @ohos.app.businessAbilityRouter

本模块用于查询当前设备上安装的应用程序的路由Ability信息。系统通过业务路由提供标准化的业务模板和管理能力，允许开发者依据特定业务类别注册标准业务，构建一个庞大且丰富的业务超市。系统应用可以便捷地从业务路由中选取合适的业务进行使 用。同时业务路由还提供统一的跳转管控规则，确保应用与业务之间合理跳转，防止非法前后台跳转，杜绝三方应用通过跳转变相分发，从而保障系统的安全性与良好的用户体验。

**起始版本：** 23

<!--Device-unnamed-declare namespace businessAbilityRouter--><!--Device-unnamed-declare namespace businessAbilityRouter-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { businessAbilityRouter } from '@kit.AbilityKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [queryBusinessAbilityInfo](arkts-ability-businessabilityrouter-querybusinessabilityinfo-f-sys.md) | 通过给定的过滤条件查询Ability信息。使用callback异步回调，成功时返回查询到的路由Ability信息，失败时返回错误信息。 |
| [queryBusinessAbilityInfo](arkts-ability-businessabilityrouter-querybusinessabilityinfo-f-sys.md) | 通过给定的过滤条件查询Ability信息。使用Promise异步回调，成功时返回查询到的路由Ability信息，失败时返回错误信息。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BusinessAbilityFilter](arkts-ability-businessabilityrouter-businessabilityfilter-i-sys.md) | 此过滤值用于过滤查询的Ability类型。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BusinessType](arkts-ability-businessabilityrouter-businesstype-e-sys.md) | 此枚举值用于标识过滤条件类型。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BusinessAbilityInfo](arkts-ability-businessabilityrouter-businessabilityinfo-t-sys.md) | 业务路由信息。 |
<!--DelEnd-->

