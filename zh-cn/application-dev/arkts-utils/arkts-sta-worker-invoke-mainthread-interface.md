# EAWorker同步调用宿主线程的接口 (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

[EAWorker（独占线程任务执行器）(ArkTS)](../reference/apis-arkts/eaworker_managed.md)中的任务如果需要调用宿主线程接口，可以使用EAWorker.postToMain将函数投递到主线程执行，并通过返回的任务句柄等待主线程执行结果。

ArkTS-Sta不使用ArkTS-Dyn Worker中的registerGlobalCallObject和callGlobalCallObjectMethod接口。静态场景下，建议通过显式共享对象、函数参数和EAWorker.postToMain完成宿主线程接口调用。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。

## 在宿主线程实现接口

```ts
// ArkTS-Sta示例
class HostService {
  getMessage(): string {
    return "this is a message from HostService";
  }
}
```

## 在EAWorker中同步调用宿主线程接口

以下示例中，invokeHostService运行在EAWorker线程中。该函数通过EAWorker.postToMain把宿主线程接口调用投递到主线程，并同步等待返回值。

```ts
// ArkTS-Sta示例
function invokeHostService(service: HostService): string {
  let resultPromise = EAWorker.postToMain<string>(() => {
    return service.getMessage();
  });

  return resultPromise.Await();
}

export async function callHostInterface(): Promise<void> {
  let service: HostService = new HostService();
  let worker: EAWorker = new EAWorker("invokeHostWorker");
  worker.start();

  try {
    let result = await worker.run<string>(invokeHostService, service);
    console.info("worker result: " + result.Await()); // worker result: this is a message from HostService
  } finally {
    await worker.join();
  }
}
```

## 使用约束

- EAWorker.postToMain会将函数调度到主线程执行，返回的任务句柄可用于获取主线程执行结果。
- EAWorker.postToMain的目标是主线程。如果宿主线程不是主线程，需要使用MessageHandler关联目标EAWorker进行通信。
- 同步等待会阻塞当前工作线程。仅建议在耗时短、调用关系清晰的接口封装中使用。
- 如果被等待的任务依赖同一个工作线程上的任务继续执行，可能发生死锁。不要在主线程上同步等待投递到主线程的任务。
- 传入postToMain的函数及其捕获对象在ArkTS-Sta中按共享语义处理。共享可变对象需要使用同步机制保证线程安全。
