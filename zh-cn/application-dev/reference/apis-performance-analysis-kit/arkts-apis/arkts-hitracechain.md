# @ohos.hiTraceChain

本模块提供了端侧业务流程调用链跟踪的打点能力，包括业务流程跟踪的启动、结束、信息埋点等能力。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-unnamed-declare namespace hiTraceChain--><!--Device-unnamed-declare namespace hiTraceChain-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [begin](arkts-performanceanalysis-hitracechain-begin-f.md#begin) | 开始跟踪，同步接口。用于在业务流程的起始节点启动分布式跟踪，例如在用户点击按钮发起请求、服务端收到请求开始处理、启动后台任务等场景。 当前线程TLS（Thread Local Storage，线程本地存储）中不存在有效的HiTraceId时，生成有效的HiTraceId并设置到当前线程TLS中，返回该 HiTraceId。当前线程TLS中已存在有效的HiTraceId时，不会开始新的跟踪，返回各属性值均为0的无效HiTraceId。 |
| [clearId](arkts-performanceanalysis-hitracechain-clearid-f.md#clearid) | 清除跟踪标识，同步接口。用于在需要切断当前跟踪链的场景，例如业务逻辑分支不再需要跟踪、任务完成后清理跟踪标识、或者在开始新的跟踪前清理旧的 跟踪标识。 将当前线程TLS中的HiTraceId设置为无效。 |
| [createSpan](arkts-performanceanalysis-hitracechain-createspan-f.md#createspan) | 创建跟踪分支，同步接口。用于在业务流程中标记重要的子流程，例如在请求处理过程中的关键步骤、服务端处理链中的各个阶段、或者需要重点关注的业务 分支。 创建一个HiTraceId，使用当前线程TLS中的chainId、spanId初始化HiTraceId的chainId、parentSpanId，并为HiTraceId生成一个新的spanId， 返回该HiTraceId。 |
| [enableFlag](arkts-performanceanalysis-hitracechain-enableflag-f.md#enableflag) | 启用HiTraceId中指定的跟踪标志，同步接口。用于在业务流程中动态调整跟踪行为，例如在调试时启用TP\_\_\_ESCAPED\_UNDERSCORE\_\_\_INFO标志以打印埋点信息、在需要跟踪异步调用时 启用INCLUDE\_\_\_ESCAPED\_UNDERSCORE\_\_\_ASYNC标志、在需要禁用日志关联时启用DISABLE\_\_\_ESCAPED\_UNDERSCORE\_\_\_LOG标志。 |
| [end](arkts-performanceanalysis-hitracechain-end-f.md#end) | 结束跟踪，同步接口。用于在业务流程的结束节点终止分布式跟踪，例如在请求处理完成返回结果、用户操作流程结束、后台任务执行完毕等场景。 若给定的HiTraceId有效，且等于当前线程TLS中的HiTraceId，结束跟踪并将当前线程TLS中的HiTraceId设置为无效。 若给定的HiTraceId无效，或不等于当前线程TLS中的HiTraceId，结束跟踪失败，打印结束跟踪失败hilog日志。 |
| [getId](arkts-performanceanalysis-hitracechain-getid-f.md#getid) | 获取跟踪标识，同步接口。用于在需要传递当前跟踪标识的场景，例如将跟踪标识传递给子线程、传递给其他进程、或者在日志中记录当前跟踪标识。 获取当前线程TLS中的HiTraceId。若当前线程TLS中不存在有效的HiTraceId，返回各属性值均为0的无效HiTraceId。 |
| [isFlagEnabled](arkts-performanceanalysis-hitracechain-isflagenabled-f.md#isflagenabled) | 判断HiTraceId是否启用了跟踪标志flag，同步接口。用于在业务逻辑中根据跟踪标志进行不同处理，例如检查是否启用了INCLUDE\_\_\_ESCAPED\_UNDERSCORE\_\_\_ASYNC标志以决定是否 等待异步操作完成、检查是否启用了TP\_\_\_ESCAPED\_UNDERSCORE\_\_\_INFO标志以决定是否打印调试信息。 |
| [isValid](arkts-performanceanalysis-hitracechain-isvalid-f.md#isvalid) | 判断HiTraceId是否有效，同步接口。 |
| [setId](arkts-performanceanalysis-hitracechain-setid-f.md#setid) | 设置跟踪标识，同步接口。用于在需要将外部跟踪标识设置到当前线程的场景，例如从父线程继承跟踪标识、从其他进程接收跟踪标识、从设备间通信获取跟踪 标识。 将给定的HiTraceId设置到当前线程TLS中。若给定的HiTraceId无效，则不执行任何操作。 |
| [tracepoint](arkts-performanceanalysis-hitracechain-tracepoint-f.md#tracepoint) | [@ohos.hiTraceMeter (性能打点)]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_跟踪信息埋点，同步接口。 本接口与HiTraceMeter模块协同工作，HiTraceChain负责跟踪链的管理，HiTraceMeter负责性能数据的采集和统计。当type为客户端发送CS且服务端 接收到SR时，进行同步HiTraceMeter开始打点；当type为服务端发送SS且客户端接收到CR时，进行同步HiTraceMeter结束打点；CS和CR以及SR和SS的 信息埋点需配套使用。否则，HiTraceMeter开始与结束打点无法正常匹配；当type为通用类型GENERAL时，不会进行HiTraceMeter打点。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [HiTraceId](arkts-performanceanalysis-hitracechain-hitraceid-i.md) | 此接口为HiTraceId对象接口。用于标识分布式跟踪链中的唯一节点，在需要跨线程、跨进程、跨设备跟踪业务流程的场景中使用，例如电商下单流程、支付流 程、分布式服务调用链等。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [HiTraceCommunicationMode](arkts-performanceanalysis-hitracechain-hitracecommunicationmode-e.md) | 跟踪通信类型枚举。用于标识通信发生的层级，例如THREAD用于标记同一应用内线程间通信，PROCESS用于标记同一设备内进程间通信，DEVICE用于标记跨设 备的分布式通信。 |
| [HiTraceFlag](arkts-performanceanalysis-hitracechain-hitraceflag-e.md) | 跟踪标志组合类型枚举。用于控制分布式跟踪的行为模式，例如在需要跟踪异步调用的业务流程中使用INCLUDE\_\_\_ESCAPED\_UNDERSCORE\_\_\_ASYNC标志，在不需要详细分支信息的简单业务 流程中使用DONOT\_\_\_ESCAPED\_UNDERSCORE\_\_\_CREATE\_\_\_ESCAPED\_UNDERSCORE\_\_\_SPAN标志，在需要调试埋点信息的场景中使用TP\_\_\_ESCAPED\_UNDERSCORE\_\_\_INFO标志。 |
| [HiTraceTracepointType](arkts-performanceanalysis-hitracechain-hitracetracepointtype-e.md) | 跟踪埋点类型枚举。用于标识业务流程中的关键节点，例如CS和CR用于标记客户端请求的发送和接收，SS和SR用于标记服务端请求的接收和发送，GENERAL用 于标记无法归入上述四种场景的其他关键节点。 |

