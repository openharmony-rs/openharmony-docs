# 并发常见问题

## TaskPool任务不执行快速定位指导

开发者发现TaskPool任务不执行时，可按照以下步骤快速定位。

1. **taskpool.execute接口是否调用**。

   taskpool.execute被调用时，Hilog会打印TaskPool维测日志（Task Allocation: taskId:）。
   如果发现没有该维测日志表明taskpool.execute实际未调用，应用需排查taskpool.execute之前的其他业务逻辑是否执行完成。

   ```ts
   console.info("test start");
   ... // 其他业务逻辑
   taskpool.execute(xxx);
   
   // 如果test start在控制台打印，但是并未出现Task Allocation: taskId:的日志，则taskpool.execute没有执行，应用需要排查其他业务逻辑。
   ```

2. **TaskPool任务是否被执行**。

   调用taskpool.execute接口会打印TaskPool**调用态维测日志**Task Allocation: taskId:。 
   定位到目标任务对应的Task Allocation: taskId:日志后，在日志中搜索taskId后跟随的Id号，正常情况会打印**执行态日志**（Task Perform: name:）和**结束态日志**（Task PerformTask End: taskId:）。

   1.  如果只有调用态日志，没有执行态日志。可能是由于先执行的TaskPool任务阻塞了TaskPool工作线程，导致TaskPool工作线程不可用，后执行的TaskPool任务无法执行。应用可以排查自身业务逻辑，或者通过trace进一步定位。

   2. 如果只有调用态日志和执行态日志，没有结束态日志。应用优先分析自定义的TaskPool任务内的业务逻辑是否存在阻塞操作。

   3. 如果调用态日志和执行态日志时间间隔较久，且应用关注任务的执行时机，可以按照以下步骤继续分析。

      1. 查看是否发生大量TaskPool任务堆积未执行的情况。如果在较短时间内执行大量任务（出现大量调用态日志），后执行的任务需要等待前置任务执行完。此时可以检查TaskPool的扩容情况，如果在调用态日志打印之前，TaskPool工作线程数量已扩容到接近上限（上限数量为日志片段log2中的maxThreads字段），则可能是短时间内任务数量太多导致，应用可以通过合理设置优先级将重要任务和有时效要求的任务优先执行。

      2. 查看前置执行的TaskPool任务是否本身耗时较长或者发生阻塞。如果前置任务本身耗时较长，应用可以通过合理设置优先级解决。如果前置任务发生了意料之外的阻塞（一段时间后阻塞解除），应用需要排查自身业务逻辑。

   ```ts
   // hilog 日志片段（模拟）
   // log1： 大量任务提交
   taskpool:: Task Allocation: taskId: , priority: , executeState:
   taskpool:: Task Allocation: taskId: , priority: , executeState:
   taskpool:: Task Allocation: taskId: , priority: , executeState:
   taskpool:: Task Allocation: taskId: , priority: , executeState:
   taskpool:: Task Allocation: taskId: , priority: , executeState:
   ...
   // log2: 扩容日志
   taskpool:: maxThreads: , create num: , total num:
   // log3: 执行态日志
   taskpool:: Task Perform: name: , taskId: , priority:
   ```

3. **TaskPool任务执行时是否发生异常**。

   1. 如果在执行TaskPool任务过程中发生JS异常，TaskPool会捕获该JS异常并通过taskpool.execute().catch((e:Error)=>{})将异常信息返回，应用需要查看异常信息并修复。

      ```ts
      taskpool.execute().then((res: object)=>{
        // 任务执行完处理结果
        ...
      }).catch((e: Error)=>{
        // 任务发生异常后处理异常
        ...
      })
      ```

   2. 如果.catch分支无异常信息返回，但是应用通过TaskPool任务实现的功能发生问题，应用需要查看TaskPool任务逻辑是否发生阻塞，导致功能异常。

## TaskPool任务执行慢排查思路

开发者发现TaskPool任务的调用态日志（如taskpool::add taskId:或者taskpool::Task Allocation: taskId:）与执行态日志（taskpool::Task Perform: name:）间隔时间较长时，可参考该排查指导进行问题定位。

### 排查方向：出问题的TaskPool任务优先级较低，应用后续新增较多优先级更高的TaskPool任务，导致原有低优先级的TaskPool任务执行延后

**场景示例一**

某应用创建了低优先级的TaskPool任务，且其他业务场景依赖这个任务执行。后续，应用又创建了很多中优先级任务，导致原有的低优先级任务执行时机延后，其他业务场景未按计划时间点完成任务。

**解决方案**

对完成执行时间点有要求的任务以低优先级执行不是好的选择，应用需要根据业务场景设置合理的任务优先级，且合理搭配任务优先级。

**场景示例二**

应用对某个TaskPool任务（简称taskA）执行时间有要求，执行超过5s时有检测机制。应用将taskA设置为MEDIUM优先级，在taskA前以MEDIUM优先级执行了较多其他任务，且这些任务耗时3s/5s不等，将已有线程和新扩容的线程均占满，导致taskA从taskpool.execute到执行结束超过5s。

**解决方案**

1.分析其他任务执行耗时3s/5s是否合理；2.调整taskA优先级。

### 排查方向：晚执行的TaskPool任务是串行任务或者依赖其他任务

**场景示例**

如果问题场景对应的TaskPool任务是串行队列任务，查看该串行队列内前面任务的执行情况。如日志片段1所示该串行队列有四个任务，问题场景对应的是第四个任务，查看日志片段2发现第二个任务执行了2s，对于应用业务逻辑是不正常的。
```ts
// hilog 日志片段1（模拟）
// seqRunner共有四个任务
taskpool:: taskId 389508780288 in seqRunner 393913878464 immediately.
taskpool:: add taskId: 394062838784 to seqRunner 393913878464
taskpool:: add taskId: 393918679936 to seqRunner 393913878464
taskpool:: add taskId: 393918673408 to seqRunner 393913878464

// hilog 日志片段2（模拟）
// 查看第二个任务, 发现任务执行到执行结束间隔2s
18:28:28.223 taskpool:: taskId 394062838784 in seqRunner 393913878464 immediately.
18:28:28.224 taskpool:: Task Perform: name : , taskId : 394062838784, priority : 0
18:28:30.243 taskpool:: Task Perform End: taskId : 394062838784, performResult : Successful
```

**解决方案**

应用继续分析第二个任务中的业务逻辑是否存在耗时操作。

### 排查方向：@Concurrent标记的方法所在的ets文件里import过多模块

**场景示例**

TaskPool第一次执行任务慢，间隔几百毫秒，原因是子线程反序列化之前，会将@Concurrent标记的方法所在的ets文件import的所有模块都初始化，导致出现任务调度慢的情况。应用可通过trace进一步定位，如果反序列化成功前有许多init module的trace，应用自行排查ets文件是否import过多模块。

**解决方案**

1.可拆分@Concurrent方法到单独的ets文件，减少模块初始化时间；2.使用延迟加载（lazy import）。

## TaskPool序列化失败问题定位指导

**问题现象**

1. JS异常
   
   入参序列化失败

   ```ts
   // API version 20之前版本
   Error message:An exception occurred during serialization, taskpool: failed to serialize arguments.

   // API version 20及之后版本
   Error message:An exception occurred during serialization, taskpool: failed to serialize arguments.
   Serialize error: Serialize don't support object type: 
   ```

   返回结果序列化失败

   ```ts
   // API version 20之前版本
   Error message:An exception occurred during serialization, taskpool: failed to serialize result.

   // API version 20及之后版本
   Error message:An exception occurred during serialization, taskpool: failed to serialize result.
   Serialize error: Serialize don't support object type: 
   ```

2. Hilog错误日志

   ```ts
   // API version 20之前版本
   [ecmascript] Unsupport serialize object type: 
   [ecmascript] ValueSerialize: serialize data is incomplete

   // API version 20及之后版本
   [ecmascript] Serialize don't support object type: 
   [ecmascript] ValueSerialize: serialize data is incomplete
   ```

**问题原因**

TaskPool实现任务的函数（Concurrent函数）入参和返回结果需满足线程间通信支持的对象类型，详情请查看[线程间通信对象](../reference/apis-arkts/js-apis-taskpool.md#序列化支持类型)。当Concurrent函数的入参或返回结果是线程间通信不支持的对象类型时，会出现上述现象。应用可以结合Hilog日志中打印的对象类型进一步排查通信对象是否符合要求。

**场景示例**

1. 应用在启动TaskPool任务时，在Concurrent函数中传入线程间通信不支持的对象类型，导致抛出入参序列化失败异常。  
**解决方案**：应用需要查看[线程间通信对象](../reference/apis-arkts/js-apis-taskpool.md#序列化支持类型)排查Concurrent函数入参。

2. 应用在启动TaskPool任务时，抛出入参序列化失败异常，同时Hilog打印错误日志Unsupport serialize object type: Proxy（API version 20及之后版本打印错误日志：Serialize error: Serialize don't support object type: Proxy）。基于错误日志可知应用在Concurrent函数中传入代理对象，排查代码发现入参使用了@State装饰器，导致原对象实际上变为Proxy代理对象，代理对象不属于线程间通信支持的对象类型。  
**解决方案**：TaskPool不支持@State、@Prop等装饰器修饰的复杂类型，具体内容可见[TaskPool注意事项](taskpool-introduction.md#taskpool注意事项)。应用需要去掉@State装饰器。

3. 应用执行TaskPool任务时，抛出返回结果序列化失败异常，排查代码发现Concurrent Function返回结果是不支持的序列化类型。
   
   ```ts
   // utils.ets
   @Concurrent
   export function printArgs(args: number) {
     return args;
   }

   // index.ets
   import { taskpool } from '@kit.ArkTS'
   import { BusinessError } from '@kit.BasicServicesKit'
   import { printArgs} from './utils'
   @Concurrent
   function createTask(a: number, b:number) {
     let sum = a + b;
     // task1: 不支持的序列化类型
     let task: taskpool.Task = new taskpool.Task(printArgs, sum);
     return task;
   }

   function executeTask() {
     // task2
     let task: taskpool.Task = new taskpool.Task(createTask, 1, 2);
     taskpool.execute(task).then((res) => {
     }).catch((e: BusinessError) => {
       // 打印“返回结果序列化失败”异常信息
       console.error("execute task failed " + e.message);
     })
   }
   ```

   **解决方案**：task1在.then中创建执行，Concurrent Function的返回结果设置为可序列化的类型。

   ```ts
   // utils.ets
   @Concurrent
   export function printArgs(args: number) {
     return args;
   }

   // index.ets
   import { taskpool } from '@kit.ArkTS'
   import { BusinessError } from '@kit.BasicServicesKit'
   import { printArgs} from './utils'
   @Concurrent
   function createTask(a: number, b:number) {
     // 支持的序列化类型
     let sum = a + b;
     return sum;
   }

   function executeTask() {
     // task2
     let task: taskpool.Task = new taskpool.Task(createTask, 1, 2);
     taskpool.execute(task).then((res) => {
       // task1
       let task: taskpool.Task = new taskpool.Task(printArgs, res);
     }).catch((e: BusinessError) => {
       console.error("execute task failed " + e.message);
     })
   }
   ```

## Sendable类A的实例对象a传递到子线程后，使用a instanceof A判断返回false

应用在子线程使用instanceof接口时，需要在导出Sendable类A的ets文件使用"use shared"指令标记该模块为[共享模块](../arkts-utils/arkts-sendable-module.md)。

**代码示例**

```ts
// pages/index.ets
import { worker, ErrorEvent } from '@kit.ArkTS'
import { A } from './sendable'
const workerInstance = new worker.ThreadWorker('../workers/Worker.ets');
function testInstanceof() {
  let a = new A();
  if (a instanceof A) {
    // 打印test instanceof in main thread success
    console.info("test instanceof in main thread success");
  } else {
    console.info("test instanceof in main thread fail");
  }
  workerInstance.postMessageWithSharedSendable(a);
  workerInstance.onerror = (err: ErrorEvent) => {
    console.error("worker err :" + err.message)
  }
}

testInstanceof()
```
```ts
// pages/sendable.ets
"use shared"
@Sendable
export class A {
    name: string = "name";
    printName(): string {
        return this.name;
    }
}
```
```ts
// workers/Worker.ets
import { A } from '../pages/sendable'
import { worker, ThreadWorkerGlobalScope, MessageEvents } from '@kit.ArkTS'

const workerPort: ThreadWorkerGlobalScope = worker.workerPort;
workerPort.onmessage = (e: MessageEvents) => {
    let a : A = e.data as A;
    if (a instanceof A) {
        // 打印test instanceof in worker thread success
        console.info("test instanceof in worker thread success");
    } else {
        console.info("test instanceof in worker thread fail");
    }
}
```

## 使用Sendable特性抛JS异常排查指导

由于Sendable特性存在固定布局、Sendable无法持有非Sendable等规格限制，开发者在进行Sendable改造时可能触发相关约束，导致抛出相应的JS异常。应用可参考以下内容进行代码排查。

### 属性类型不一致异常

**问题现象**

```ts
JS异常：TypeError: Cannot set sendable property with mismatched type
```

**问题原因与解决方案**

由于ArkTS运行时在属性赋值时会严格进行类型一致性校验，如果定义的属性类型与传入的对象类型不一致，会抛出上述JS异常。应用需要基于JS异常栈定位到对应的ts文件代码行，排查相应的业务逻辑。

**场景示例**

1. 应用在向子线程传递Sendable类A的实例对象时，抛出类型不一致异常。基于JS栈定位到问题发生在创建类A的实例对象时，排查后发现应用当前模块与其他模块联调时，其他模块未使用Sendable类B封装数据集。   
**解决方案** ： 应用当前模块将其他模块传递的数据使用Sendable类重新封装。

   ```ts
   @Sendable
   export class B {
     constructor() {}
   }

   @Sendable
   export class A {
     constructor(b: B) {
       this.b = b;
     }
     public b: B | undefined = undefined;
   }
   ```

2. 应用查看JS异常栈发现运行this.g = g赋值语句时，抛出类型不一致异常。排查代码后发现属性g使用了@State装饰器，导致原对象变为Proxy代理对象，造成定义类型与传入类型不一致。  
**解决方案**：去掉@State装饰器

### 新增属性异常

**问题现象**

```ts
JS异常：TypeError: Cannot add property in prevent extensions
```

**问题原因与解决方案**

由于Sendable类的布局固定，不允许增删属性，对Sendable对象新增属性时会抛出上述JS异常。应用需要基于JS异常栈定位到对应的ts文件代码行，排查相应的业务逻辑。

**异常场景示例**

1. 应用基于业务需要在同一个ets文件定义了同名的Sendable类和namespace，抛出新增属性异常。由于ts会合并同名的class和namespace，将namespace中的导出的内容附加到同名类上，实际上是对Sendable类新增属性，导致抛出上述异常。  
**解决方案**：规格限制，暂不支持合并同名Sendable class和namespace。

2. 应用在HAR中使用Sendable特性时，抛出新增属性异常。查看JS异常栈，发现异常代码行定位在js文件，而Sendable特性不支持在js文件中使用，导致抛出非预期的异常。  
**解决方案**：在HAR中使用Sendable特性时，[配置tsHAR](../quick-start/har-package.md#编译生成ts文件)。

3. 应用在Local Test单元测试或预览器中使用Sendable特性时，抛出新增属性异常。由于Sendable特性暂不支持在Local Test和预览器中使用，导致抛出非预期的异常。  
**解决方案**：规格限制，暂不支持。

## ArkTS提供的Promise能力的原理是什么

Promise是ArkTS提供的异步并发能力，是标准的JS语法。详情请查看[Promise](async-concurrency-overview.md#promise)概述。

## TaskPool线程是否可以执行不需要@Concurrent和@Sendable修饰的JS闭包函数

TaskPool执行的任务函数必须使用@Concurrent装饰器修饰，由于Concurrent函数不能访问闭包，因此函数内不可调用当前文件的其他普通函数，详情请参考[TaskPool注意事项](taskpool-introduction.md#taskpool注意事项)。但是，开发者可以通过给Concurrent函数传参的方式，传入@Sendable装饰器修饰的普通function和Async function，在Concurrent函数内调用Sendable function。

因此，TaskPool线程目前不支持执行普通的JS闭包函数。如果有相关诉求，开发者可以根据业务需要使用[Worker](worker-introduction.md)并发能力进行业务改造。

## TaskPool任务执行后的结果如何保存到自定义的数据结构

**问题描述**

TaskPool的任务执行函数Concurrent Function只能使用局部变量和函数入参，TaskPool任务执行后的结果应该如何保存到自定义的数据结构。

**解决方案**

1. 自定义Sendable类。[Sendable对象](arkts-sendable.md)可以在不同的子线程中共享，开发者可以将任务执行后的结果保存到Sendable对象上。

2. TaskPool任务执行后的结果可以在.then中返回，需要保存的数据如果仅在当前线程使用，可以在.then中将执行结果保存到自定义的数据结构中。

   ```ts
   import { taskpool } from '@kit.ArkTS'
   import { BusinessError } from '@kit.BasicServicesKit'
   @Concurrent
   function createTask(a: number) {
     return a;
   }
   function executeTask() {
     let task: taskpool.Task = new taskpool.Task(createTask, 1)
     taskpool.execute(task).then((res) => {
       console.info('execute task success');
       // 保存到自定义的数据结构
     }).catch((e: BusinessError) => {
       console.error('execute task error: ' + e.message);
     })
    }
   ```

## Sendable类在子线程无法加载

**问题描述**

Sendable装饰器修饰的类与Observed装饰器修饰的类定义在同一个ets文件中，在TaskPool子线程加载Sendable类时捕获到错误信息：SendableItem is not initialized。

```ts
// Index.ets: 在Index页面新增以下代码
import { taskpool } from '@kit.ArkTS'
import { BusinessError } from '@kit.BasicServicesKit'
import { SendableItem } from './sendable'

@Concurrent
function createTask() {
  let data = new SendableItem();
}

function executeTask() {
  let task = new taskpool.Task(createTask);
  taskpool.execute(task).then((res) => {
    console.info('execute task success');
  }).catch((e: BusinessError) => {
    console.error('execute task error: ' + e.message);
  })
}

executeTask();
```

```ts
// sendable.ets
@Observed
export class NormalItem {
  age: number = 0;
}

@Sendable
export class SendableItem {
  name: string = '';
}
```

**根因分析**

Observed装饰器仅支持在UI线程使用，不能在子线程、Worker、TaskPool中直接或者间接使用，否则会导致应用功能失效甚至crash。由于sendable.ets文件中定义了Observed装饰器修饰的类，即使该类没有被显式调用也可能被解析执行，当解析到Observed这类UI装饰器时则抛出异常：Observed is not defined，导致当前文件中的其他模块的解析被中断。在TaskPool子线程加载Sendable类时抛出异常：SendableItem is not initialized。

**解决方案**

将Observed装饰器修饰的类NormalItem剥离到单独的ets文件后，TaskPool子线程再去加载Sendable类SendableItem，应用运行符合预期。

```ts
// Index.ets: 在Index页面新增以下代码
import { taskpool } from '@kit.ArkTS'
import { BusinessError } from '@kit.BasicServicesKit'
import { SendableItem } from './sendable'

@Concurrent
function createTask() {
  let data = new SendableItem();
}

function executeTask() {
  let task = new taskpool.Task(createTask);
  taskpool.execute(task).then((res) => {
    console.info('execute task success');
  }).catch((e: BusinessError) => {
    console.error('execute task error: ' + e.message);
  })
}

executeTask();
```

```ts
// sendable.ets
@Sendable
export class SendableItem {
  name: string = '';
}
```

```ts
// ui.ets
@Observed
export class NormalItem {
  age: number = 0;
}
```
