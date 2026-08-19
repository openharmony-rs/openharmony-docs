# begin

## 导入模块

```TypeScript
import { hiTraceChain } from '@kit.PerformanceAnalysisKit';
```

## begin

```TypeScript
function begin(name: string, flags?: int): HiTraceId
```

开始跟踪，同步接口。用于在业务流程的起始节点启动分布式跟踪，例如在用户点击按钮发起请求、服务端收到请求开始处理、启动后台任务等场景。 当前线程TLS（Thread Local Storage，线程本地存储）中不存在有效的HiTraceId时，生成有效的HiTraceId并设置到当前线程TLS中，返回该 HiTraceId。当前线程TLS中已存在有效的HiTraceId时，不会开始新的跟踪，返回各属性值均为0的无效HiTraceId。

**起始版本：** 23

<!--Device-hiTraceChain-function begin(name: string, flags?: int): HiTraceId--><!--Device-hiTraceChain-function begin(name: string, flags?: int): HiTraceId-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 跟踪业务名。该参数的长度不超过63Byte，超出部分将被截断。 |
| flags | int | 否 | 跟踪标志组合，具体可参考[HiTraceFlag](arkts-performanceanalysis-hitracechain-hitraceflag-e.md)。当需要跟踪异步调用时设置 INCLUDE_ASYNC，不创建分支信息时设置DONOT_CREATE_SPAN，调试场景下设置TP_INFO可打印埋点信息。默认值为0，表示只跟踪同步调用、创建分支信 息、不打印日志。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [HiTraceId](arkts-performanceanalysis-hitracechain-hitraceid-i.md) | 当前线程TLS中的HiTraceId实例。 |

**示例**

```TypeScript
// 开始跟踪，跟踪标志是INCLUDE_ASYNC与DONOT_CREATE_SPAN的并集。
let traceId = hiTraceChain.begin("business", hiTraceChain.HiTraceFlag.INCLUDE_ASYNC | hiTraceChain.HiTraceFlag.DONOT_CREATE_SPAN);
// 若干业务逻辑完成后，结束跟踪。
hiTraceChain.end(traceId);
```

