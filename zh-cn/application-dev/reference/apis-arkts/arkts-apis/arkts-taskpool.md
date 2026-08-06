# @ohos.taskpool

任务池（taskpool）为应用程序提供多线程运行环境，降低资源消耗并提升系统性能，开发者无需关心线程的生命周期。 使用任务池API可创建后台任务（Task），执行或取消任务等操作。理论上，任务池API允许创建的任务数量不受限制，但由于内存限制， 不建议无限制地创建大量任务。此外，不建议在任务中执行阻塞操作，尤其是无限期阻塞操作，因为阻塞操作会占用工作线程，影响其他任务的调度和应用性能。 创建同一优先级的任务时，可以自行决定其执行顺序。任务的实际执行顺序与任务提交到任务池的顺序一致。任务的默认优先级为MEDIUM。 当同一时间待执行的任务数量大于任务池工作线程数量，任务池会根据负载均衡机制进行扩容，增加工作线程数量，减少整体等待时长。 同样，当执行的任务数量减少，工作线程数量大于执行任务数量，部分工作线程处于空闲状态，任务池会根据负载均衡机制进行缩容，减少工作线程数量。 任务池API返回错误码。如需了解各错误码的详细信息，请参阅文档\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。 请查阅\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_，了解使用TaskPool时的相关注意点。 文档中涉及以下任务概念： - 任务组任务：对应为[TaskGroup]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_任务。 - 串行队列任务：对应为[SequenceRunner]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_任务。 - 异步队列任务：对应为[AsyncRunner]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_任务。 - 周期任务：由[executePeriodically]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_执行的任务。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

<!--Device-unnamed-declare namespace taskpool--><!--Device-unnamed-declare namespace taskpool-End-->

**系统能力：** SystemCapability.Utils.Lang

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [cancel](arkts-arkts-taskpool-cancel-f.md#cancel) | 取消任务池中的任务。 - 当任务在taskpool等待队列中，取消该任务后该任务将不再执行，并返回任务被取消的异常。 - 当任务已经在taskpool工作线程执行，取消该任务并不影响任务继续执行。执行结果在catch分支返回，开发者可搭配isCanceled方法对任务取消行为作出响应。 - taskpool.cancel对其之前的taskpool.execute、taskpool.executeDelayed或taskpool.executePeriodically生效。 从API version 20开始，支持在执行cancel操作后，在catch分支里使用BusinessError&lt; [taskpool.TaskResult]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_&gt;的泛型标记，来获取任务中抛出的异常信息或最终的执行结果。 |
| [cancel](arkts-arkts-taskpool-cancel-f.md#cancel-1) | 取消任务池中的任务组。如果任务组中的任务未全部执行结束，则整个任务组的执行结果返回undefined。 从API version 20开始，支持在执行cancel操作后，在catch分支里使用BusinessError&lt; [taskpool.TaskResult]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_&gt;的泛型标记，来获取任务中抛出的异常信息或最终的执行结果。 |
| [cancel](arkts-arkts-taskpool-cancel-f.md#cancel-2) | 通过任务ID取消任务池中的任务。 - 如果任务在taskpool等待队列中，取消后任务将不再执行，并返回任务取消的异常。 - 当任务已经在taskpool工作线程执行，取消该任务并不影响任务继续执行。执行结果在catch分支返回，开发者可搭配isCanceled方法对任务取消行为作出响应。 - taskpool.cancel对其之前的taskpool.execute、taskpool.executeDelayed或taskpool.executePeriodically生效。 - 在其他线程调用taskpool.cancel时，需注意其行为是异步的，可能导致在cancel调用之后的taskpool.execute或taskpool.executeDelayed的任务被取消。 从API version 20开始，支持在执行cancel操作后，在catch分支里使用BusinessError&lt; [taskpool.TaskResult]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_&gt;的泛型标记。这可以用来获取任务中抛出的异常信息或最终的执行结果。 |
| [execute](arkts-arkts-taskpool-execute-f.md#execute) | 将待执行的函数放入taskpool的内部任务队列，函数不会立即执行，而是等待分发到工作线程执行。在当前执行模式下， 不支持取消任务。使用Promise异步回调。 |
| [execute](arkts-arkts-taskpool-execute-f.md#execute-1) | 校验并发函数的参数类型和返回类型后，将函数添加到taskpool的任务队列。在当前执行模式下，不支持取消任务。使用Promise异步回调。 |
| [execute](arkts-arkts-taskpool-execute-f.md#execute-2) | 将创建好的任务添加到taskpool的内部任务队列中，任务不会立即执行，而是等待分发到工作线程执行。当前模式支持设置任务优先级和通过cancel取消任务。使用Promise异步回调。 |
| [execute](arkts-arkts-taskpool-execute-f.md#execute-3) | 将创建好的泛型任务放入taskpool的内部任务队列，校验任务的参数类型和返回值类型。使用Promise异步回调。 execute任务的校验是结合**new GenericsTask**一起用的，参数、返回值类型需与**new GenericsTask**中的类型保持一致。 |
| [execute](arkts-arkts-taskpool-execute-f.md#execute-4) | 将创建好的任务组放入taskpool内部任务队列，任务组中的任务不会立即执行，而是等待分发到工作线程执行。任务组中任务全部执行完成后， 结果数组统一返回。此模式适用于执行关联任务。使用Promise异步回调。 |
| [execute](arkts-arkts-taskpool-execute-f.md#execute-5) | 将创建好的任务添加到taskpool的内部任务队列中，任务不会立即执行，而是等待分发到工作线程执行。当前模式支持设置任务优先级、设置超时时间和通过cancel取消任务。使用Promise异步回调。 |
| [execute](arkts-arkts-taskpool-execute-f.md#execute-6) | 将创建好的泛型任务放入taskpool的内部任务队列，不校验任务的参数类型和返回值类型。使用Promise异步回调。 execute任务的校验是结合new GenericsTask一起用的，参数、返回值类型需与new GenericsTask中的类型保持一致。 |
| [execute](arkts-arkts-taskpool-execute-f.md#execute-7) | 将创建好的任务组放入taskpool内部任务队列，任务组中的任务不会立即执行，而是等待分发到工作线程执行。任务组中任务全部执行完成后，结果数组统一返回。此模式适用于执行关联任务。使用Promise异步回调。 configs配置里可以指定任务组执行的超时时间和优先级。指定的超时时间到了，但是任务组还未完成，则会抛出任务组超时的异常信息。 |
| [executeDelayed](arkts-arkts-taskpool-executedelayed-f.md#executedelayed) | 延时执行任务。当前执行模式可以设置任务优先级，可通过cancel取消任务。使用Promise异步回调。 |
| [executeDelayed](arkts-arkts-taskpool-executedelayed-f.md#executedelayed-1) | 延时执行泛型任务，使用Promise异步回调。 executeDelayed任务的类型校验与GenericsTask的构造类型相关联，参数类型和返回值类型需与new GenericsTask时指定的类型保持一致。 |
| [executePeriodically](arkts-arkts-taskpool-executeperiodically-f.md#executeperiodically) | 周期任务每隔period时长执行一次。当前执行模式支持设置任务优先级，可通过cancel取消任务。 |
| [executePeriodically](arkts-arkts-taskpool-executeperiodically-f.md#executeperiodically-1) | 周期执行泛型任务，使用Promise异步回调。 executePeriodically任务的类型校验与GenericsTask的构造类型相关联，参数类型和返回值类型需与new GenericsTask时指定的类型保持一致。 |
| [getTask](arkts-arkts-taskpool-gettask-f.md#gettask) | 通过taskId或taskId与taskName获取对应的Task实例。 |
| [getTaskPoolInfo](arkts-arkts-taskpool-gettaskpoolinfo-f.md#gettaskpoolinfo) | 获取任务池的线程信息和任务信息。 |
| [isConcurrent](arkts-arkts-taskpool-isconcurrent-f.md#isconcurrent) | 检查函数是否为并发函数。 |
| [terminateTask](arkts-arkts-taskpool-terminatetask-f.md#terminatetask) | 中止任务池中的长时任务，在长时任务执行完成后调用。中止后，执行长时任务的线程可能会被回收。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [AsyncRunner](arkts-arkts-taskpool-asyncrunner-c.md) | 表示异步队列。可以指定任务执行的并发度和排队策略。 |
| [GenericsTask](arkts-arkts-taskpool-genericstask-c.md) | 表示泛型任务。**GenericsTask**继承自 [Task]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 相比创建Task，创建GenericsTask可以在编译阶段校验并发函数的传参和返回值类型。其余行为与Task相同。 |
| [LongTask](arkts-arkts-taskpool-longtask-c.md) | 表示长时任务。**LongTask**继承自 [Task]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 长时任务不设置执行时间上限，长时间运行不会触发超时异常，但不支持将同一任务多次执行或者将该任务加入任务组（TaskGroup）。 执行长时任务的线程会持续存在，直到任务完成并调用[terminateTask]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_后，该线程在空闲时被回收。 |
| [SequenceRunner](arkts-arkts-taskpool-sequencerunner-c.md) | 表示串行队列的任务，用于执行一组需要串行执行的任务。 |
| [Task](arkts-arkts-taskpool-task-c.md) | 调用Task中的任何接口前必须先使用构造函数创建Task对象。任务可以多次执行，也可以放入任务组、串行队列或异步队列执行，还支持添加依赖关系。 |
| [TaskGroup](arkts-arkts-taskpool-taskgroup-c.md) | 表示任务组，一次执行一组任务，适用于执行一组有关联的任务。如果所有任务正常执行，异步执行完毕后返回所有任务结果的数组， 数组中元素的顺序与调用[addTask]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_添加任务的顺序相同。如果任意任务失败， 则会抛出对应异常。如果任务组中存在多个任务失败的情况，则会抛出第一个失败任务的异常。任务组可以多次执行，但执行后不能新增任务。 |
| [TaskInfo](arkts-arkts-taskpool-taskinfo-c.md) | 任务的内部信息。 |
| [TaskPoolInfo](arkts-arkts-taskpool-taskpoolinfo-c.md) | 任务池的内部信息。 |
| [ThreadInfo](arkts-arkts-taskpool-threadinfo-c.md) | 工作线程的内部信息。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Configs](arkts-arkts-taskpool-configs-i.md) | 任务或任务组的配置项。 |
| [TaskResult](arkts-arkts-taskpool-taskresult-i.md) | 处于等待或执行过程中的任务进行取消操作后，在catch分支里捕获到BusinessError里的补充信息。其他场景下该信息为undefined。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Priority](arkts-arkts-taskpool-priority-e.md) | 表示所创建任务（Task）执行时的优先级。工作线程优先级跟随任务优先级更新，对应关系参考\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| [State](arkts-arkts-taskpool-state-e.md) | 表示任务（Task）状态的枚举。 状态转换规则如下： - 当任务创建成功后，调用execute，任务进入taskpool等待队列，状态设置为WAITING。 - 任务从等待队列出来进入taskpool工作线程中，任务状态更新为RUNNING。 - 当任务执行完成，返回结果后，如果任务再次被执行，则状态重置为WAITING。 - 当主动cancel任务时，将任务状态更新为CANCELED。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [CallbackFunction](arkts-arkts-taskpool-callbackfunction-t.md) | 注册的回调函数类型。 |
| [CallbackFunctionWithError](arkts-arkts-taskpool-callbackfunctionwitherror-t.md) | 注册带有错误码的回调函数类型。 |

