# Worker常驻线程通过TaskPool进行多任务并发处理
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @lijiamin2025-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

ArkTS应用开发过程中，可以选择TaskPool或Worker线程进行多任务并发处理，也可以两种并发能力都选择。

本示例将说明在Worker线程中通过TaskPool执行并发任务。

1. 在主线程中创建Worker线程并发送消息。

   <!-- @[worker_taskpool](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCasesSecond/entry/src/main/ets/pages/workerAndTaskpool.ets) -->    

2. 在Worker线程中调用TaskPool执行并发任务。

   <!-- @[define_worker](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCasesSecond/entry/src/main/ets/workers/Worker.ets) -->    
