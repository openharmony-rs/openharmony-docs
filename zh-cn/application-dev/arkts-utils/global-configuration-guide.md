# 全局配置项功能场景
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @lijiamin2025-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

对于需要使用进程单例的场景，例如不同并发实例间需要数据保持一致的全局配置项功能，可以采用[共享模块](arkts-sendable-module.md)来实现。

以下示例展示了只有在Wi-Fi打开且用户登录的情况下才能进行下载的功能，具体步骤如下。

1. 编写全局配置文件。

   <!-- @[global_config](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCases/entry/src/main/ets/managers/Config.ets) -->

   <!-- @[global_config](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCases/entry/src/main/ets/managers/Config.ets) -->

2. UI主线程及子线程访问全局配置项。

   <!-- @[access_global_config](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCases/entry/src/main/ets/managers/GlobalConfigurationGuide.ets) -->

   <!-- @[access_global_config](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCases/entry/src/main/ets/managers/GlobalConfigurationGuide.ets) -->
