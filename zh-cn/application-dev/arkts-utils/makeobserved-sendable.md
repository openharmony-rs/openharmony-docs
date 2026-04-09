# ArkUI数据更新场景
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @lijiamin2025-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

当需要网络下载或者本地生成的数据需要发送到UI线程进行展示时，由于ArkUI的标注和[\@Sendable装饰器](../arkts-utils/arkts-sendable.md#sendable装饰器)不能同时修饰变量和对象，因此需要使用[makeObserved](../ui/state-management/arkts-new-makeObserved.md)在ArkUI中导入可观测的Sendable共享数据。

本示例说明以下场景：
- makeObserved在传入@Sendable类型的数据后有观测能力，且其变化可以触发UI更新。
- 从子线程获取数据，整体替换UI线程的可观测数据。
- 从子线程获取的数据重新执行makeObserved，变为可观测数据。
- 将数据从UI主线程传递回子线程时，只传递不可观测的数据。makeObserved的返回值不能直接传给子线程。

<!-- @[define_sendable_class](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCases/entry/src/main/ets/managers/SendableData.ets) -->

<!-- @[define_sendable_class](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCases/entry/src/main/ets/managers/SendableData.ets) -->

<!-- @[update_arkui_data](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCases/entry/src/main/ets/managers/MakeobservedSendable.ets) -->

<!-- @[update_arkui_data](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCases/entry/src/main/ets/managers/MakeobservedSendable.ets) -->