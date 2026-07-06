# EAWorker和宿主线程的即时消息通信 (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

[EAWorker（独占线程任务执行器）(ArkTS)](../reference/apis-arkts/eaworker_managed.md)适合需要独占线程、长期驻留或固定线程上下文的任务。宿主线程可以通过EAWorker.run向EAWorker提交任务，也可以通过MessageHandler和Message按消息类型进行即时通信。

ArkTS-Sta中不使用ArkTS-Dyn的Worker线程文件和postMessage接口。EAWorker消息通信基于concurrency.MessageHandler和concurrency.Message实现，消息携带的数据默认按共享对象引用传递。

下面以EAWorker响应hello world请求为例说明。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。

## 创建EAWorker并注册消息处理函数

```ts
// ArkTS-Sta示例
const REQUEST_HELLO: int = 1;
const RESPONSE_SUCCESS: int = 2;

async function communicateWithWorker(): Promise<void> {
  let worker: EAWorker = new EAWorker("messageWorker");
  worker.start();

  let done = new Promise<void>((resolve, reject) => {
    let mainHandler = new concurrency.MessageHandler((msg: concurrency.Message) => {
      if (msg.getWhat() == RESPONSE_SUCCESS) {
        let result = msg.getObject() as string;
        console.info("main receive: " + result); // main receive: success
        resolve(undefined);
      }
    }, EAWorker.main());

    let workerHandler = new concurrency.MessageHandler((msg: concurrency.Message) => {
      if (msg.getWhat() == REQUEST_HELLO) {
        let data = msg.getObject() as string;
        if (data == "hello world") {
          let response = new concurrency.Message(RESPONSE_SUCCESS, "success", mainHandler);
          response.sendToTarget();
        }
      }
    }, worker);

    let request = new concurrency.Message(REQUEST_HELLO, "hello world", workerHandler);
    if (!workerHandler.sendMessage(request)) {
      reject(new Error("send message failed"));
    }
  });

  try {
    await done;
  } finally {
    await worker.join();
  }
}
```

## 使用说明

- MessageHandler需要关联一个已启动的EAWorker。给未启动或已退出的EAWorker发送消息会失败。
- Message可以携带消息标识符、对象或回调函数。接收方可通过getWhat、getObject和getCallback获取消息内容。
- 可以调用handler.sendMessage(message)发送消息，也可以调用message.sendToTarget()发送到Message构造时指定的目标Handler。
- 同一个Message只能通过sendToTarget发送一次，重复发送会抛出异常。
- Message携带的对象在ArkTS-Sta中是共享对象引用。消息机制不自动提供并发读写保护。

如果只需要向EAWorker提交一次任务并获取结果，优先使用worker.run；如果需要按消息类型分发、取消待处理消息或在多个EAWorker之间持续通信，使用MessageHandler和Message更合适。

更多接口说明请参见[MessageHandler](../reference/apis-arkts/message_handler.md)和[Message](../reference/apis-arkts/message.md)。
