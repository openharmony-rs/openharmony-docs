# worker

JS跨线程通信工具。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

<!--Device-unnamed-declare namespace worker--><!--Device-unnamed-declare namespace worker-End-->

**系统能力：** SystemCapability.Utils.Lang

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ThreadWorker](arkts-arkts-worker-threadworker-c.md) | 使用以下方法前，需先构造ThreadWorker实例。ThreadWorker类继承WorkerEventTarget。 使用Worker模块时，API version 18及之后的版本建议在宿主线程中注册onAllErrors回调，以捕获Worker线程生命周期内的各种异常。API version 18之前的版本应注册onerror回调。 如果未注册onAllErrors或onerror回调，当Worker线程出现异常时会发生崩溃问题。 注意，onerror接口仅能捕获onmessage回调中的同步异常，捕获异常后，Worker线程将进入销毁流程，无法继续使用。 onAllErrors接口与onerror接口之间的行为差异如下： 1. 异常捕获范围 onAllErrors接口可以捕获Worker线程的onmessage回调、timer回调以及文件执行等流程中产生的全局异常。 onerror接口仅能捕获Worker线程的onmessage回调中同步方法产生的异常，无法捕获多线程回调和模块化相关异常。 2. 异常捕获后的线程状态 onAllErrors接口捕获异常后，Worker线程仍然存活并可以继续使用。这使开发者可以在捕获异常后执行其他操作，无需担心线程终止。 onerror接口捕获异常后，Worker线程会进入销毁流程，无法继续使用。这意味着在onerror触发后，Worker线程将被终止，后续操作将无法进行。 3. 适用场景 onAllErrors接口适用于捕获Worker线程中所有类型异常的场景，特别是确保异常发生后Worker线程仍能继续运行的复杂场景。 onerror接口适用于只需要捕获onmessage回调中同步异常的简单场景。由于捕获异常后线程会被销毁，适用于不需要继续使用Worker线程的情况。 推荐使用onAllErrors接口，因为它提供了更全面的异常捕获能力，并且不会导致线程终止。 |
| [Worker](arkts-arkts-worker-worker-c.md) | Worker类包含所有Worker功能。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [RestrictedWorker](arkts-arkts-worker-restrictedworker-c-sys.md) | RestrictedWorker类继承[ThreadWorker]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_，具有ThreadWorker中所有的方法。 RestrictedWorker主要用于提供受限的Worker线程运行环境，该线程运行环境中只允许导入Worker模块，不允许导入其他API。 |
<!--DelEnd-->

### 常量

| 名称 | 说明 |
| --- | --- |
| [parentPort](arkts-arkts-worker-con.md#parentport) | Worker线程用于与宿主线程通信的对象。 |
| [workerPort](arkts-arkts-worker-con.md#workerport) | Worker线程用于与宿主线程通信的对象。 |

