# 获取/设置环境变量

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wkljy; @xuzhihao666-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

环境变量涵盖了所有可能影响应用运行时的环境配置信息，包括应用可指定的内部环境变量（字体大小、外观、语言等）和应用可感知的外部环境变量（屏幕方向等）。

通常条件下，环境变量会跟随系统设置变化。

## 使用场景
|  场景   |  说明       |  约束限制  | 场景举例   |
|------------|-------------------|-------------|-----------------|
| [获取环境变量](#获取环境变量) | 开发者可以使用[getConfigurationSync](../reference/apis-localization-kit/js-apis-resource-manager.md#getconfigurationsync10)主动获取当前环境变量，包括深浅色模式、屏幕方向、语言地区、屏幕密度、设备类型等。        | 当前仅支持同步获取，使用方式参考[ResourceManager.getConfigurationSync](../reference/apis-localization-kit/js-apis-resource-manager.md#getconfigurationsync10)。  |应用运行过程中，可以主动获取当前应用深浅色模式，以更新用户界面显示。  |
| [设置环境变量](#设置环境变量) | 当前仅支持应用自定义字体大小、深浅色、语言。<br>- [设置字体大小](#设置字体大小)<br>- [设置深浅色模式](#设置深浅色模式)<br>- [设置应用语言](#设置应用语言) |  当应用设置环境变量后，应用将无法通过订阅感知到对应的环境变量在系统中的变化。   |  应用自定义字体大小，以提升用户体验。 |
| [订阅环境变量](#订阅环境变量) | 通过订阅环境变量，及时感知系统环境变化 。支持订阅的环境变量包括语言、深浅色、屏幕方向等，详见[Configuration](../reference/apis-ability-kit/js-apis-app-ability-configuration.md)。                   |    - 如果开发者将环境变量配置为不跟随系统变化（即[configuration标签](../quick-start/app-configuration-file.md#configuration标签)中的对应字段取值为“nonFollowSystem”），应用将无法通过订阅感知对应的环境变量在系统中的变化。<br>- 应用订阅环境变量后，当应用处于后台时，环境变量发生变更，应用将无法实时收到订阅通知。相关通知推送会被延迟处理，待应用切换回前台时，才会收到订阅通知。 | 当用户旋转设备屏幕时，应用可以通过订阅环境变量感知环境变化重新布局用户界面，以适应屏幕方向和尺寸。 |


## 获取环境变量

开发者可以使用[getConfigurationSync](../../application-dev/reference/apis-localization-kit/js-apis-resource-manager.md#getconfigurationsync10)主动获取当前[环境变量](../../application-dev/reference/apis-localization-kit/js-apis-resource-manager.md#configuration)，包括深浅色模式、屏幕方向、语言地区、屏幕密度、设备类型等，对应用程序作出相应处理，提供更好的用户体验。

  <!-- @[quick_start0](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/EnvConfig/entry/src/main/ets/EnvAbility/EnvAbility0.ets) -->

## 设置环境变量

支持应用自定义的环境变量包括[字体大小](#设置字体大小)、[深浅色模式](#设置深浅色模式)、[应用语言](#设置应用语言)，其他环境变量（例如屏幕方向等）均不支持直接设置。

### 设置字体大小

应用字体大小默认不跟随系统变化，开发者可以通过将[configuration标签](../quick-start/app-configuration-file.md#configuration标签)中fontSizeScale的值配置为followSystem，使得应用字体大小跟随系统变化。

开发者可以使用[setFontSizeScale](../reference/apis-ability-kit/js-apis-inner-application-applicationContext.md#applicationcontextsetfontsizescale13)设置应用字体大小。设置后，应用字体将不跟随系统变化，不再支持订阅系统字体大小变化。

<!-- @[quick_start0](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/EnvConfig/entry/src/main/ets/EnvAbility/EnvAbility1.ets) -->

### 设置深浅色模式

应用深浅色模式默认跟随系统。开发者可以设置应用或组件的深浅色模式。设置后，不再支持订阅系统的深浅色模式变化。

配置生效的优先级为：UIAbility/UIExtensionAbility的深浅色模式 > 应用的深浅色模式 > 系统的深浅色模式。

- **设置应用的深浅色模式：** 使用ApplicationContext的[setColorMode](../reference/apis-ability-kit/js-apis-inner-application-applicationContext.md#applicationcontextsetcolormode11)接口，可以设置应用深浅色模式。

    <!-- @[quick_start0](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/EnvConfig/entry/src/main/ets/EnvAbility/EnvAbility2.ets) -->

- **设置UIAbility的深浅色模式：** 使用UIAbilityContext的[setColorMode](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#setcolormode18)，可以设置UIAbility的深浅色模式。

    <!-- @[quick_start0](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/EnvConfig/entry/src/main/ets/EnvAbility/EnvAbility3.ets) -->

- **设置UIExtensionAbility的深浅色模式：** 使用UIExtensionContext的[setColorMode](../reference/apis-ability-kit/js-apis-inner-application-uiExtensionContext.md#setcolormode18)，可以设置UIExtensionAbility的深浅色模式。

    <!-- @[quick_start0](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/EnvConfig/entry/src/main/ets/EnvAbility/EnvAbility4.ets) -->

### 设置应用语言

应用语言默认跟随系统语言变化。开发者可以使用[setLanguage](../reference/apis-ability-kit/js-apis-inner-application-applicationContext.md#applicationcontextsetlanguage11)设置应用语言。设置后，不再支持订阅系统语言变化。

<!-- @[quick_start0](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/EnvConfig/entry/src/main/ets/EnvAbility/EnvAbility5.ets) -->

## 订阅环境变量

系统配置的变化通常由“设置”中的选项或“控制中心”中的图标触发。订阅环境变量变化，可以使应用程序更加智能地响应系统环境变化，从而提供更好的用户体验。查看当前支持订阅变化的环境变量，参见[Configuration](../reference/apis-ability-kit/js-apis-app-ability-configuration.md)。

基于当前的应用模型，可以通过以下几种方式来实现订阅环境变量的变化。

- [使用ApplicationContext订阅回调](#使用applicationcontext订阅回调)
- [在AbilityStage组件管理器中订阅回调](#在abilitystage组件管理器中订阅回调)
- [在UIAbility组件中订阅回调](#在uiability组件中订阅回调)
- [在ExtensionAbility组件中订阅回调](#在extensionability组件中订阅回调)

### 使用ApplicationContext订阅回调

[ApplicationContext](../reference/apis-ability-kit/js-apis-inner-application-applicationContext.md)提供了注册回调函数以订阅环境变量的变化，并且可以通过调用相应的方法来撤销该回调。这有助于在资源不再需要时释放相关资源，从而提高系统的可靠性和性能。

1. 使用[on](../reference/apis-ability-kit/js-apis-inner-application-applicationContext.md#applicationcontextonenvironment)方法，应用程序可以通过在非应用组件模块中订阅环境变量的变化来动态响应这些变化。例如，使用该方法在页面中监测系统语言的变化。

    <!-- @[quick_start0](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/EnvConfig/entry/src/main/ets/pages/EnvAbilityPage6.ets) -->

2. 在资源使用完成之后，可以通过调用[off](../reference/apis-ability-kit/js-apis-inner-application-applicationContext.md#applicationcontextoffenvironment-1)方法释放相关资源。

    <!-- @[quick_start0](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/EnvConfig/entry/src/main/ets/pages/EnvAbilityPage7.ets) -->

### 在AbilityStage组件管理器中订阅回调

使用[AbilityStage.onConfigurationUpdate()](../reference/apis-ability-kit/js-apis-app-ability-abilityStage.md#onconfigurationupdate)回调方法订阅环境变量的变化。当环境变量发生变化时，会调用该回调方法。在该方法中，通过[Configuration](../reference/apis-ability-kit/js-apis-app-ability-configuration.md)对象获取最新的环境变量信息。可以进行相应的界面适配等操作，从而提高系统的灵活性和可维护性。

> **说明：**
>
> - DevEco Studio默认工程中未自动生成[AbilityStage](../reference/apis-ability-kit/js-apis-app-ability-abilityStage.md)，AbilityStage文件的创建参见[AbilityStage开发步骤](abilitystage.md#开发步骤)。
> - 当使用回调方法订阅系统环境变量的变化时，该回调方法会随着AbilityStage的生命周期而存在，在Module销毁时一并销毁。

例如，在[AbilityStage.onConfigurationUpdate()](../reference/apis-ability-kit/js-apis-app-ability-abilityStage.md#onconfigurationupdate)回调方法中实现监测系统语言的变化。

<!-- @[quick_start0](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/EnvConfig/entry/src/main/ets/EnvAbility/EnvAbility8.ets) -->

### 在UIAbility组件中订阅回调

[UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md)组件提供了[UIAbility.onConfigurationUpdate()](../reference/apis-ability-kit/js-apis-app-ability-ability.md#abilityonconfigurationupdate)回调方法用于订阅环境变量的变化。当环境变量发生变化时，会调用该回调方法。在该方法中，通过[Configuration](../reference/apis-ability-kit/js-apis-app-ability-configuration.md)对象获取最新的环境变量信息，而无需重启UIAbility。

> **说明：**
>
> - 当应用通过回调方法订阅环境变量变化时，该订阅会随着所在UIAbility的生命周期持续有效。一旦UIAbility被销毁，之前注册的所有回调订阅将自动失效，同时应用将不会再收到订阅的回调信息。
> - 如果使用该接口监听屏幕方向变化，需要在module.json5配置文件的[abilities标签](../quick-start/module-configuration-file.md#abilities标签)中将orientation字段配置为auto_rotation。

例如，在[onConfigurationUpdate()](../reference/apis-ability-kit/js-apis-app-ability-ability.md#abilityonconfigurationupdate)回调方法中实现监测系统语言的变化。

<!-- @[quick_start0](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/EnvConfig/entry/src/main/ets/EnvAbility/EnvAbility9.ets) -->

### 在ExtensionAbility组件中订阅回调

[ExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-extensionAbility.md)组件提供了[onConfigurationUpdate()](../reference/apis-ability-kit/js-apis-app-ability-ability.md#abilityonconfigurationupdate)回调方法用于订阅环境变量的变化。当环境变量发生变化时，会调用该回调方法。在该方法中，通过[Configuration](../reference/apis-ability-kit/js-apis-app-ability-configuration.md)对象获取最新的环境变量信息。

> **说明：**
>
> 当应用通过回调方法订阅环境变量变化时，该订阅会随着所在ExtensionAbility的生命周期持续有效。一旦ExtensionAbility被销毁，之前注册的所有回调订阅将自动失效，同时应用将不会再收到订阅的回调信息。

以[FormExtensionAbility](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md)为例说明。例如，在[onConfigurationUpdate()](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonconfigurationupdate)回调方法中实现环境变量的变化。

<!-- @[quick_start0](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/EnvConfig/entry/src/main/ets/EnvAbility/EnvAbility10.ets) -->
