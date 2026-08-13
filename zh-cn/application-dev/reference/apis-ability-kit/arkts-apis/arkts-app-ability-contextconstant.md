# @ohos.app.ability.contextConstant

/*
 Copyright (c) 2022-2024 Huawei Device Co., Ltd.
 Licensed under the Apache License, Version 2.0 (the "License");
 you may not use this file except in compliance with the License.
 You may obtain a copy of the License at
 http://www.apache.org/licenses/LICENSE-2.0
 Unless required by applicable law or agreed to in writing, software
 distributed under the License is distributed on an "AS IS" BASIS,
 WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 See the License for the specific language governing permissions and
 limitations under the License.
 /


**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace contextConstant--><!--Device-unnamed-declare namespace contextConstant-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 汇总

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AreaMode](arkts-ability-contextconstant-areamode-e.md) | 文件加密分区等级，保证应用在不同场景下的数据安全。开发者可以根据应用的具体需求选择合适的加密等级，以保护用户的数据安全。 |
| [ContextType](arkts-ability-contextconstant-contexttype-e.md) | 上下文类型 |
| [ProcessMode](arkts-ability-contextconstant-processmode-e.md) | UIAbility启动后的进程模式。 ProcessMode作为[StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md#StartOptions)的一个属性，仅在 [UIAbilityContext.startAbility](arkts-ability-uiabilitycontext-c.md#startAbility) 中生效，用来指定目标UIAbility的进程模式。 该功能仅在2in1和Tablet设备上生效，在其他设备中返回801错误码。 |
| [Scenarios](arkts-ability-contextconstant-scenarios-e.md) | 表示不触发[onNewWant](arkts-ability-app-ability-uiability-uiability-c.md#onNewWant)生命周期回调场景的枚举，用于 [setOnNewWantSkipScenarios](arkts-ability-uiabilitycontext-c.md#setOnNewWantSkipScenarios)接口。 |
| [StartupVisibility](arkts-ability-contextconstant-startupvisibility-e.md) | UIAbility启动后是否可见。 当用户设置目标UIAbility为不可见时，目标UIAbility的窗口不会显示在前台，dock栏也不会有图标，同时目标UIAbility的onForeground生命周期不会被调用。 StartupVisibility作为[StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md#StartOptions)的一个属性，仅在 [UIAbilityContext.startAbility](arkts-ability-uiabilitycontext-c.md#startAbility) 中生效，用来指定目标UIAbility启动后的可见性。 该功能仅在2in1和Tablet设备上生效，在其他设备中返回801错误码。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ContextType](arkts-ability-contextconstant-contexttype-e-sys.md) | 上下文类型 |
<!--DelEnd-->

