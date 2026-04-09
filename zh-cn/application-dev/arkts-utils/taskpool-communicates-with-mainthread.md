# TaskPool任务与宿主线程通信
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @lijiamin2025-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

如果Task不仅需要返回最终执行结果，还需定时通知宿主线程状态和数据变化，或分段返回大量数据（如从数据库读取大量数据），可按以下方式实现。

下面以多个图片加载任务结果实时返回为例说明。

1. 实现接收Task消息的方法。

   <!-- @[receive_task_message](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationScenario/entry/src/main/ets/managers/TaskSendDataUsage.ets) -->

   <!-- @[receive_task_message](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationScenario/entry/src/main/ets/managers/TaskSendDataUsage.ets) -->

2. 在需要执行的Task中，添加sendData()接口将消息发送给宿主线程。

   <!-- @[implement_child_thread_task](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationScenario/entry/src/main/ets/managers/IconItemSource.ets) -->

   <!-- @[implement_child_thread_task](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationScenario/entry/src/main/ets/managers/IconItemSource.ets) -->

   <!-- @[implement_child_thread_task](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationScenario/entry/src/main/ets/managers/TaskSendDataUsage.ets) -->

   <!-- @[implement_child_thread_task](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationScenario/entry/src/main/ets/managers/TaskSendDataUsage.ets) -->

3. 最后，在宿主线程通过onReceiveData()接口接收消息。

   这样宿主线程就可以通过notice()接口接收到Task发送的数据。

   <!-- @[receive_task_data](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationScenario/entry/src/main/ets/managers/TaskSendDataUsage.ets) -->

   <!-- @[receive_task_data](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationScenario/entry/src/main/ets/managers/TaskSendDataUsage.ets) -->
