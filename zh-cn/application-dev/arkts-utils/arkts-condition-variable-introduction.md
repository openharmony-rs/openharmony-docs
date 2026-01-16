# 异步等待
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @lijiamin2025-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

ArkTS引入了异步任务的等待和被唤醒能力，以解决多线程任务时序控制问题。异步任务的等待和被唤醒[ConditionVariable](../reference/apis-arkts/arkts-apis-arkts-utils-locks.md#conditionvariable18)对象支持跨线程引用传递。

ArkTS语言支持异步操作，现已增加异步任务的等待和唤醒功能。当异步任务收到唤醒通知或等待超时后，将继续执行。

> **说明：**
>
> 使用异步方法需标记为async，调用时需用await修饰，确保时序正确。

## 使用示例

[Sendable](arkts-sendable.md)共享对象在不同线程控制异步任务等待和唤醒的示例如下：

<!-- @[sendable_object](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationObjects/SendableObject/AsynchronousWaiting/entry/src/main/ets/pages/Index.ets) -->

