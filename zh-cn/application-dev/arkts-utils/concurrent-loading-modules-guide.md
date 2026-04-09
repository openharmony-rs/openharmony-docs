# 业务模块并发加载场景
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @lijiamin2025-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

在应用启动时，多个业务模块需要加载，例如地图应用中的定位、打车、导航等模块。如果全部在UI主线程初始化，会严重影响应用冷启动时间。此时，应在不同子线程中并行加载这些模块，以降低启动耗时。

通过使用ArkTS提供的TaskPool能力，可以将不同的业务初始化任务移到子线程中。业务模块可通过下沉C++实现为[NativeBinding对象](transferabled-object.md)或在ArkTS层定义为[Sendable对象](arkts-sendable.md)，从而将初始化的模块返回给UI主线程调用，实现如下。

1. 各业务功能（SDK）模块定义（这里以使用Sendable对象为例）。

   计算器业务模块定义如下：

   <!-- @[define_calculator_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCases/entry/src/main/ets/sdk/Calculator.ets) -->

   <!-- @[define_calculator_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCases/entry/src/main/ets/sdk/Calculator.ets) -->

   定时器业务模块的定义如下：

   <!-- @[define_timer_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCases/entry/src/main/ets/sdk/TimerSdk.ets) -->

   <!-- @[define_timer_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCases/entry/src/main/ets/sdk/TimerSdk.ets) -->

2. 在UI主线程触发各业务模块分发到子线程，加载完成后在UI主线程使用，示例如下：

   <!-- @[distribute_child_thread](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCases/entry/src/main/ets/managers/ConcurrentLoadingModulesGuide.ets) -->

   <!-- @[distribute_child_thread](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCases/entry/src/main/ets/managers/ConcurrentLoadingModulesGuide.ets) -->
