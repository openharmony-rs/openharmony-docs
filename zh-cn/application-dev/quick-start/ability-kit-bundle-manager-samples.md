# 应用程序包指南配套示例代码
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->

| 场景分类 | Sample名称 | 语言 | 场景介绍 |
| -------- | -------- | -------- | -------- |
| 静态共享包 | [HarPackage](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/bmsSample/HarPackage) | ArkTS | 使用HAR静态共享包导出ArkUI组件、接口与资源，演示HAR的创建、使用与集成。 |
| 动态共享包 | [InAppHsp1](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/bmsSample/InAppHsp1) | ArkTS | 使用HSP动态共享包导出ArkUI组件、接口与资源，演示应用内HSP的创建与引用。 |
| 共享包页面跳转 | [InAppHsp2](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/bmsSample/InAppHsp2) | ArkTS | 使用HSP结合Navigation实现页面跳转，演示从entry模块跳转到library并返回的流程。 |
| 应用配置 | [AppConfigurationFile](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/bmsSample/AppConfigurationFile) | ArkTS | 使用app.json5配置文件声明应用全局信息，演示bundleName、版本号、图标与多开模式等配置。 |
| 模块配置 | [ModuleConfigurationFile01](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/bmsSample/ModuleConfigurationFile01) | ArkTS | 使用module.json5配置文件声明模块信息，演示abilities、pages、metadata等基础字段的配置。 |
| 模块配置 | [ModuleConfigurationFile02](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/bmsSample/ModuleConfigurationFile02) | ArkTS | 使用module.json5的distributionFilter配置，演示按设备类型精准分发HAP的配置方法。 |
| 模块配置 | [ModuleConfigurationFile03](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/bmsSample/ModuleConfigurationFile03) | ArkTS | 使用module.json5的distributionFilter与metadata，演示多entry模块的细分设备分发策略。 |
| 模块配置 | [ModuleConfigurationFile04](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/bmsSample/ModuleConfigurationFile04) | ArkTS | 使用module.json5的atomicService标签，演示元服务相关配置方法。 |
| 模块配置 | [ModuleConfigurationFile05](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/bmsSample/ModuleConfigurationFile05) | ArkTS | 使用module.json5的hnpPackages与definePermissions字段，演示HNP包与自定义权限配置。 |
| 静态快捷方式 | [TypicalScenarioConfiguration](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/bmsSample/TypicalScenarioConfiguration) | ArkTS | 使用shortcuts配置静态快捷方式，演示长按应用图标快速直达指定功能页面。 |
| 应用分身 | [AppClone](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/bmsSample/AppClone) | ArkTS | 使用app.json5的multiAppMode配置应用分身，演示同一应用多账号同时登录并独立运行。 |
| 应用多实例 | [Multiinstance](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/bmsSample/Multiinstance) | ArkTS | 使用app.json5的multiAppMode配置应用多实例，演示2in1设备上多进程多账号运行。 |
| 应用图标 | [LayeredImage1](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/bmsSample/LayeredImage1) | ArkTS | 使用app.json5与module.json5配置单层图标和应用名称，演示应用图标与名称的配置方法。 |
| 应用图标 | [LayeredImage2](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/bmsSample/LayeredImage2) | ArkTS | 使用app.json5与module.json5配置分层图标和应用名称，演示分层图标的配置方法。 |
| 备用图标 | [LayeredImage3](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/bmsSample/LayeredImage3) | ArkTS | 使用alternateIcons与bundleManager接口配置备用图标，演示备用图标的启用、查询与恢复。 |
| HAR转HSP | [HarToHsp](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/bmsSample/HarToHsp) | ArkTS | 使用配置变更将HAR工程转换为HSP工程，演示type、pages与编译任务的调整步骤。 |
| HSP转HAR | [HspToHar](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/bmsSample/HspToHar) | ArkTS | 使用配置变更将HSP工程转换为HAR工程，演示type字段与编译任务的调整步骤。 |
| HAP转HAR | [HapToHar](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/bmsSample/HapToHar) | ArkTS | 使用配置变更将HAP工程转换为HAR工程，演示module.json5、hvigorfile.ts与Index.ets配置。 |
| 集成态HSP | [IntegratedHsp](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/bmsSample/IntegratedHsp) | ArkTS | 使用集成态HSP在多个应用中共享基础能力，演示bundleName解耦与自动重签名的配置。 |
| 签名信息获取 | [CommonProblemOfApplication](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/bmsSample/CommonProblemOfApplication) | ArkTS | 使用bundleManager.getBundleInfoForSelf获取签名信息，演示应用指纹、appId与appIdentifier的获取。 |
