# @ohos.app.ability.contextConstant

ContextConstant提供Context相关的枚举，包含文件加密分区等级、UIAbility启动后的进程模式等。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 汇总

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AreaMode](arkts-ability-contextconstant-areamode-e.md) | 文件加密分区等级，保证应用在不同场景下的数据安全。开发者可以根据应用的具体需求选择合适的加密等级，以保护用户的数据安全。<br/> |
| [ContextType](arkts-ability-contextconstant-contexttype-e.md) | 上下文类型<br/> |
| <!--DelRow-->[ContextType](arkts-ability-contextconstant-contexttype-e-sys.md) | 上下文类型<br/> |
| [ProcessMode](arkts-ability-contextconstant-processmode-e.md) | UIAbility启动后的进程模式。<br/>ProcessMode作为[StartOptions](@ohos.app.ability.StartOptions:StartOptions)的一个属性，仅在<br/>[UIAbilityContext.startAbility](./application/UIAbilityContext:UIAbilityContext.startAbility(want: Want, options: StartOptions, callback: AsyncCallback&lt;void&gt;))<br/>中生效，用来指定目标UIAbility的进程模式。<br/>该功能仅在2in1和Tablet设备上生效，在其他设备中返回801错误码。<br/> |
| [Scenarios](arkts-ability-contextconstant-scenarios-e.md) | 表示不触发[onNewWant](arkts-ability-uiability-c.md#onNewWant-1)生命周期回调场景的枚举，用于<br/>[setOnNewWantSkipScenarios](arkts-ability-uiabilitycontext-c.md#setOnNewWantSkipScenarios-1)接口。<br/> |
| [StartupVisibility](arkts-ability-contextconstant-startupvisibility-e.md) | UIAbility启动后是否可见。<br/>当用户设置目标UIAbility为不可见时，目标UIAbility的窗口不会显示在前台，dock栏也不会有图标，同时目标UIAbility的onForeground生命周期不会被调用。<br/>StartupVisibility作为[StartOptions](@ohos.app.ability.StartOptions:StartOptions)的一个属性，仅在<br/>[UIAbilityContext.startAbility](./application/UIAbilityContext:UIAbilityContext.startAbility(want: Want, options: StartOptions, callback: AsyncCallback&lt;void&gt;))<br/>中生效，用来指定目标UIAbility启动后的可见性。<br/>该功能仅在2in1和Tablet设备上生效，在其他设备中返回801错误码。<br/> |

