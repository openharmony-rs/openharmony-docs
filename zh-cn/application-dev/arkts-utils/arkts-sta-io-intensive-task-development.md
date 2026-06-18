# I/O密集型任务开发指导（TaskPool） (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

I/O密集型任务的性能瓶颈通常在磁盘读写、数据库访问或网络通信上。单次I/O操作可以通过异步接口减少阻塞，但大量I/O任务集中执行时，仍可能占用当前线程调度资源。ArkTS-Sta中可使用[taskpool (启动任务池)](../reference/apis-arkts/arkts-sta-taskpool.md)将密集I/O任务调度到后台线程执行。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。
> - 本文示例使用文件写入表示I/O密集型任务。实际应用中，请根据使用的文件、网络或数据库API处理权限、路径和异常。

## 定义I/O任务

以下示例将文件路径作为参数传入TaskPool任务。上下文、路径等宿主侧对象建议在任务外准备好，再通过参数传递给任务函数。

```ts
// ArkTS-Sta示例
async function writeFile(data: string, filePath: string): Promise<void> {
  // 此处省略具体文件API调用。
  // 实际开发中可在这里执行文件打开、写入和关闭操作。
  console.info("write data to " + filePath + ": " + data); // write data to /data/storage/el2/base/files/path1.txt: Hello World!（示例输出）
}

async function writeFiles(fileList: Array<string>): Promise<boolean> {
  for (let i = 0; i < fileList.length; i++) {
    await writeFile("Hello World!", fileList[i]);
  }
  return true;
}
```

## 使用TaskPool执行密集I/O

```ts
// ArkTS-Sta示例
async function runIoTask(): Promise<void> {
  let fileList: Array<string> = [
    "/data/storage/el2/base/files/path1.txt",
    "/data/storage/el2/base/files/path2.txt"
  ];

  let result: boolean = (await taskpool.execute(writeFiles, fileList)) as boolean;
  if (result) {
    console.info("taskpool execute I/O task success"); // taskpool execute I/O task success
  }
}
```

如果I/O任务之间相互独立，也可以拆成多个Task并使用Promise.all等待结果。

```ts
// ArkTS-Sta示例
async function runIoTasksInParallel(): Promise<void> {
  let fileList: Array<string> = [
    "/data/storage/el2/base/files/path1.txt",
    "/data/storage/el2/base/files/path2.txt"
  ];

  let promises: Array<Promise<Any>> = [];
  for (let filePath of fileList) {
    promises.push(taskpool.execute(writeFile, "Hello World!", filePath));
  }

  await Promise.all<Any>(promises);
  console.info("all I/O tasks finished"); // all I/O tasks finished
}
```

## 使用建议

- 密集I/O任务可使用TaskPool放到后台线程执行，避免阻塞当前线程。
- 文件路径、数据库连接参数等应在宿主线程准备好，再传入TaskPool任务。
- ArkTS-Sta对象默认共享。若多个任务共享同一个可变列表、缓存或连接状态，需要使用锁或并发容器。
- I/O任务数量过多时，可使用[AsyncRunner](../reference/apis-arkts/arkts-sta-taskpool.md#asyncrunner)限制并发度，避免同时发起过多I/O操作。
- 需要长期维持连接或固定线程上下文时，可考虑EAWorker，但普通批量I/O优先使用TaskPool。
