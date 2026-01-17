# 多线程取消TaskPool任务场景
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @lijiamin2025-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

由于任务池[TaskPool](../reference/apis-arkts/js-apis-taskpool.md)的任务对象[Task](../reference/apis-arkts/js-apis-taskpool.md#task)不支持跨线程传递，无法在子线程中直接取消任务。从 API version 18 开始，Task新增了[任务ID](../reference/apis-arkts/js-apis-taskpool.md#属性)属性，支持通过任务ID在子线程中取消任务。开发者可将已创建任务的任务ID存储在[Sendable对象](./arkts-sendable.md)中，需要取消任务时，通过Sendable对象在子线程中取消任务。详情可参考以下示例。

1. 定义一个Sendable类，在类属性中存储任务ID。

   <!-- @[define_sendable](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCasesSecond/entry/src/main/ets/utils/Sendable.ets) --> 

2. 在UI主线程向TaskPool提交一个延时任务，并在子线程取消该任务。

   <!-- @[taskpool_cancel](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCasesSecond/entry/src/main/ets/pages/TaskpoolCancel.ets) -->  
