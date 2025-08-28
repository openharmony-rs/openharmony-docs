# MultiAppMode (系统接口)

定义应用是否支持多开模式。

> **说明：**
> 
> 本模块首批接口从API version 12 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 本模块接口仅可在Stage模型下使用。
> 本模块接口为系统接口。

## 使用说明

通过appManager的[getRunningMultiAppInfo](js-apis-app-ability-appManager-sys.md#appmanagergetrunningmultiappinfo12)来获取MultiAppMode属性。

## MultiAppMode

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称 | 值 |说明 | 
| -------- |----|-------- |
| NOT_SUPPORTED | 0 | 应用不支持多开模式。 |
| MULTI_INSTANCE<sup>14+</sup>  | 1 | 应用支持多实例模式。<br>**说明：** 只支持2in1设备。  |
| APP_CLONE | 2 | 应用支持分身模式。 |