# TaskPool和Worker的对比 (TaskPool和Worker)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->


TaskPool和Worker的作用是为应用程序提供多线程运行环境，用于处理耗时计算任务或其他密集型任务，避免任务阻塞宿主线程，提高系统性能和资源利用率。


本文将从[实现特点](#实现特点对比)和[适用场景](#适用场景对比)两个方面比较TaskPool与Worker。


## 实现特点对比

**表1** TaskPool和Worker的实现特点对比

| 实现 | TaskPool | Worker |
| -------- | -------- | -------- |
| 内存模型 | 线程间隔离，内存不共享。 | 线程间隔离，内存不共享。 |
| 参数传递机制 | 采用标准的结构化克隆算法（Structured Clone）进行序列化、反序列化，完成参数传递。<br/>支持ArrayBuffer转移、SharedArrayBuffer共享和Sendable引用传递。 | 采用标准的结构化克隆算法（Structured Clone）进行序列化、反序列化，完成参数传递。<br/>支持ArrayBuffer转移、SharedArrayBuffer共享和Sendable引用传递。 |
| 参数传递 | 直接传递，无需封装。 | 消息对象唯一参数，需要自己封装。 |
| 方法调用 | 直接传入并调用\@Concurrent修饰的方法。 | 在Worker线程中解析消息并调用对应方法。 |
| 返回值 | 异步调用后默认返回。 | 主动发送消息，需在onmessage中解析并赋值。 |
| 生命周期 | TaskPool自动管理其生命周期，无需关注任务负载。 | 开发者需自行管理Worker的数量和生命周期。 |
| 任务池个数上限 | 自动管理，无需配置。 | 同个进程下，最多支持同时开启64个Worker线程，实际数量由进程内存决定。 |
| 任务执行时长上限 | 3分钟（不包含Promise和async/await异步调用的耗时，例如网络下载、文件读写等I/O任务的耗时），长时任务无执行时长上限。 | 无限制。 |
| 设置任务的优先级 | 支持配置任务优先级。 | 从API version 18开始，支持配置Worker线程优先级。 |
| 执行任务的取消 | 支持取消已经发起的任务。 | 不支持。 |
| 线程复用 | 支持。 | 不支持。 |
| 任务延时执行 | 支持。 | 不支持。 |
| 设置任务依赖关系 | 支持。 | 不支持。 |
| 串行队列 | 支持。 | 不支持。 |
| 任务组 | 支持。 | 不支持。 |
| 周期任务 | 支持。 | 不支持。 |
| 异步队列 | 支持。 | 不支持。 |


## 适用场景对比

TaskPool和Worker均支持多线程并发能力。由于TaskPool的工作线程会绑定系统的调度优先级，并支持负载均衡（自动扩缩容），相比之下，Worker需要开发者自行创建，存在创建耗时。因此，性能方面TaskPool优于Worker，推荐在大多数场景中使用TaskPool。

TaskPool偏向于独立任务，任务在线程中执行时，无需关注线程的生命周期。超长任务（大于3分钟且非长时任务）会被系统自动回收。而Worker适用于长时间占据线程的任务，需要开发者主动管理线程的生命周期。

常见开发场景及适用说明如下：

- 运行时间超过3分钟的任务（不包括Promise和async/await异步调用的耗时，如网络下载、文件读写等I/O任务的耗时）：例如后台进行1小时的预测算法训练等CPU密集型任务，需要使用Worker。场景示例可参考[常驻任务开发指导](resident-task-guide.md)。

- 有关联的一系列同步任务：例如在一些需要创建、使用句柄的场景中，每次创建的句柄都不同，必须永久保存该句柄，以确保后续操作正确执行，需要使用Worker。场景示例可参考[使用Worker处理关联的同步任务](sync-task-development.md#使用worker处理关联的同步任务)。

- 需要设置优先级的任务：在API version 18 之前，Worker不支持设置调度优先级，需要使用TaskPool。从API version 18开始，Worker支持设置调度优先级，开发者可以根据使用场景和任务特性选择使用TaskPool或Worker。例如[图像直方图绘制场景](cpu-intensive-task-development.md#使用taskpool进行图像直方图处理)，后台计算的直方图数据会用于前台界面的显示，影响用户体验，需要高优先级处理，且任务相对独立，推荐使用TaskPool。

- 需要频繁取消的任务：如图库大图浏览场景。为提升体验，系统会同时缓存当前图片左右各两张图片。当往一侧滑动跳到下一张图片时，需取消另一侧的缓存任务，此时需使用TaskPool。

- 大量或调度点分散的任务：例如大型应用中的多个模块包含多个耗时任务，不建议使用Worker进行负载管理，推荐使用TaskPool。场景示例可参考[批量数据写数据库场景](batch-database-operations-guide.md)。
