# 创建ArkTS卡片
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @cx983299475-->
<!--Designer: @xueyulong-->
<!--Tester: @chenmingze-->
## 创建ArkTS卡片
创建卡片当前有两种入口：

- 创建工程时，选择Application，可以在创建工程后右键新建卡片。
- 创建工程时，选择Atomic Service（元服务），也可以在创建工程后右键新建卡片。

![WidgetCreateProject](figures/WidgetCreateProject.png)
>**说明：** 
>
>基于不同版本的DevEco Studio，请以实际界面为准。

在已有的应用工程中，可以通过右键新建ArkTS卡片，具体的操作方式如下。

1. 右键新建卡片。  
   ![WidgetProjectCreate1](figures/WidgetProjectCreate1.png)
>**说明：** 
>
> 在API 10及以上 Stage模型的工程中，开发者可通过Service Widget菜单可直接选择创建动态卡片（Dynamic Widget）或静态卡片（Static Widget）。创建卡片后，也可在卡片的[form_config.json配置文件](arkts-ui-widget-configuration.md)中，通过isDynamic参数修改卡片类型：isDynamic置空或赋值为“true”，则该卡片为[为动态卡片](./arkts-form-overview.md#动态卡片)；isDynamic赋值为"false"，则该卡片为[静态卡片](./arkts-form-overview.md#静态卡片)。
   
2. 根据实际业务场景，选择一个卡片模板。  
   ![WidgetProjectCreate2](figures/WidgetProjectCreate2.png)

3. 在选择卡片的开发语言类型（Language）时，选择ArkTS选项。选择卡片支持的外观规格（Support dimension）时，选择期望的卡片尺寸，然后选择默认的外观规格（Default dimension），最后点击“Finish”，即可完成ArkTS卡片创建。详细的卡片外观规格可参考[form_config.json](arkts-ui-widget-configuration.md#配置文件字段说明)配置文件，后续也可以在form_config.json配置文件中修改卡片规格。
   ![WidgetProjectCreate3](figures/WidgetProjectCreate3.png)
   
   建议根据实际使用场景命名卡片名称，ArkTS卡片创建完成后，工程中会新增如下卡片相关文件：卡片生命周期管理文件（EntryFormAbility.ets）、卡片页面文件（WidgetCard.ets）和卡片配置文件（form_config.json）。  
   ![WidgetProjectView](figures/WidgetProjectView.png)
## 工程结构介绍
**图1** ArkTS卡片工程目录、相关模块  
![WidgetModules](figures/WidgetModules.png)


- [FormExtensionAbility](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md)：卡片扩展模块，提供卡片创建、销毁、刷新等生命周期回调。

- [FormExtensionContext](../reference/apis-form-kit/js-apis-inner-application-formExtensionContext.md)：FormExtensionAbility的上下文环境，提供FormExtensionAbility具有的接口和能力。

- [formProvider](../reference/apis-form-kit/js-apis-app-form-formProvider.md)：提供了获取卡片信息、更新卡片、设置卡片更新时间等能力。

- [formInfo](../reference/apis-form-kit/js-apis-app-form-formInfo.md)：提供了卡片信息和状态等相关类型和枚举。

- [formBindingData](../reference/apis-form-kit/js-apis-app-form-formBindingData.md)：提供卡片数据绑定的能力，包括FormBindingData对象的创建、相关信息的描述。

- [页面布局（WidgetCard.ets）](arkts-ui-widget-page-overview.md)：基于ArkUI提供卡片UI开发能力。
   - [ArkTS卡片通用能力](arkts-ui-widget-page-overview.md#arkts卡片支持的页面能力)：提供了能在ArkTS卡片中使用的组件、属性和API。
   - [ArkTS卡片特有能力](arkts-ui-widget-event-overview.md)：postCardAction用于卡片内部和提供方应用间的交互，仅在卡片中可以调用。

- [卡片配置](arkts-ui-widget-configuration.md)：包含FormExtensionAbility的配置和卡片的配置。
   - 在[module.json5配置文件](../quick-start/module-configuration-file.md)中的extensionAbilities标签下，配置FormExtensionAbility相关信息。
   - 在resources/base/profile/目录下的[form_config.json](arkts-ui-widget-configuration.md#配置文件字段说明)配置文件中，配置卡片（WidgetCard.ets）相关信息。


