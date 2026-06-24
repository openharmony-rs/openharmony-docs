# @ohos.app.ability.errorManager

ErrorManager模块提供对错误观测器的注册和注销的能力，主要是观测应用发生js crash和appfreeze等错误。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [off](arkts-ability-errormanager-off-f.md#off-1) | 注销错误观测器。使用callback异步返回。<br/><br/>仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。<br/> |
| [off](arkts-ability-errormanager-off-f.md#off-2) | 注销错误观测器。使用Promise异步返回。<br/><br/>仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。<br/> |
| [off](arkts-ability-errormanager-off-f.md#off-3) | 注销主线程消息处理监听器。<br/><br/>仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。<br/> |
| [off](arkts-ability-errormanager-off-f.md#off-4) | 注销被拒绝promise监听器。<br/><br/>仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。<br/> |
| [off](arkts-ability-errormanager-off-f.md#off-5) | 注销被拒绝promise监听器，注销后无法监听进程中的promise异常。<br/><br/>如果传入的回调不在通过on方法注册的回调队列中，将抛出16300004错误码，因此建议使用try-catch逻辑进行处理。<br/> |
| [off](arkts-ability-errormanager-off-f.md#off-6) | 取消之前注册的应用主线程freeze监听。<br/><br/>仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。<br/><br/>如果传入的回调与通过on方法注册回调不一致，将抛出16300004错误码，因此建议使用try-catch逻辑进行处理。<br/> |
| [off](arkts-ability-errormanager-off-f.md#off-7) | 注销错误观测器，注销之前注册在同一线程的callback全局监听。<br/><br/>如果传入的回调不在通过on方法注册的回调队列中，将抛出16300004错误码，因此建议使用try-catch逻辑进行处理。<br/> |
| [on](arkts-ability-errormanager-on-f.md#on-1) | 注册错误观测器。注册后可以捕获到应用产生的js crash，属于应用崩溃的一种。观测器捕获到该异常时应用不退出，建议在回调函数执行完后，增加同步退出操作。<br/><br/>仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。<br/> |
| [on](arkts-ability-errormanager-on-f.md#on-2) | 注册主线程消息处理耗时监听器。注册后可以捕获到应用主线程处理消息的具体执行时间。<br/><br/>仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。<br/> |
| [on](arkts-ability-errormanager-on-f.md#on-3) | 注册被拒绝promise监听器。注册后可以捕获到当前线程中未被捕获到的promise rejection。<br/><br/>仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。<br/> |
| [on](arkts-ability-errormanager-on-f.md#on-4) | 在进程中任意线程注册被拒绝promise监听器，注册后可以捕获到当前进程中未被捕获到的promise rejection。<br/> |
| [on](arkts-ability-errormanager-on-f.md#on-5) | 注册应用主线程freeze监听。多次注册情况下，取最后一次注册的结果。<br/><br/>仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。<br/><br/>&gt; **注意**：<br/>&gt;<br/>&gt; 如果该回调函数执行时间超过1s，可能导致[AppRecovery](arkts-app-ability-apprecovery.md#appRecovery)功能不可用。通过解析hilog日志中的begin与Freeze<br/>&gt; callback execution completed两者的时间差可以计算回调函数执行时长，如果超过1秒，可以尝试采用异步处理、减少阻塞操作、优化数据结构等方法优化回调逻辑，降低执行时长。<br/> |
| [on](arkts-ability-errormanager-on-f.md#on-6) | 在进程中的任意线程中注册 `errormanager.on` 接口，监听整个进程中任意线程的异常。观测器捕获到该异常时应用不退出，建议在回调函数执行完后，增加同步退出操作。<br/> |
| [setDefaultErrorHandler](arkts-ability-errormanager-setdefaulterrorhandler-f.md#setDefaultErrorHandler-1) | 发生JS_CRASH异常时，支持链式回调，返回上一次注册的处理器，仅限主线程调用。<br/><br/>如果传入非法参数或在子线程调用，将抛出错误码并返回undefined，因此建议使用try-catch逻辑进行处理。<br/><br/>若接口参数为空，后续注册的处理器将无法与前序已注册的处理器建立关联，从而中断链式调用。<br/> |
| [setDefaultFreezeObserver](arkts-ability-errormanager-setdefaultfreezeobserver-f.md#setDefaultFreezeObserver-1) | 设置默认冻屏观测器。此函数将在通过errorManager.on注册的回调函数执行后立即执行。<br/>可用于替代errorManager.on实现链式调用。<br/>如果为某个模块设置空观测器，将导致调用链中断。<br/><br/>此API必须在主线程中调用。<br/> |
| [setDefaultResourceUsageObserver](arkts-ability-errormanager-setdefaultresourceusageobserver-f.md#setDefaultResourceUsageObserver-1) | 设置资源占用观察者，应用资源超基线时，支持链式回调，返回上一次注册的资源占用观察者，仅限主线程调用。<br/><br/>如果传入非法参数或在子线程调用，将抛出错误码并返回undefined，因此建议使用try-catch逻辑进行处理。<br/><br/>若接口参数为空，后续注册的观察者将无法与前序已注册的观察者建立关联，从而中断链式调用。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [GlobalError](arkts-ability-errormanager-globalerror-i.md) | 有关异常事件名字、消息、错误堆栈信息、异常线程名称和类型的对象。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [InstanceType](arkts-ability-errormanager-instancetype-e.md) | 虚拟机的实例类型。<br/> |
| [ResourceType](arkts-ability-errormanager-resourcetype-e.md) | 应用资源超基线的类型。<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ErrorHandler](arkts-ability-errormanager-errorhandler-t.md) | 当ArkTS运行时抛出用户未捕获异常时，将调用ErrorHandler。<br/> |
| [ErrorObserver](arkts-ability-errormanager-errorobserver-t.md) | ErrorObserver模块。<br/> |
| [FreezeObserver](arkts-ability-errormanager-freezeobserver-t.md) | 定义应用主线程freeze回调，用于应用自定义添加freeze信息。<br/> |
| [GlobalObserver](arkts-ability-errormanager-globalobserver-t.md) | 定义异常监听，可以作为<br/>[errorManager.on('globalErrorOccurred')](arkts-ability-errormanager-on-f.md#on-6)<br/>和<br/>[errorManager.on('globalUnhandledRejectionDetected')](arkts-ability-errormanager-on-f.md#on-4)<br/>的入参监听当前应用主线程事件处理事件。<br/> |
| [LoopObserver](arkts-ability-errormanager-loopobserver-t.md) | LoopObserver模块。定义异常监听，可作为 `errormanager.on` 函数的参数，监听并处理当前应用主线程超时的事件。<br/> |
| [ResourceUsageObserver](arkts-ability-errormanager-resourceusageobserver-t.md) | 定义应用资源使用情况的观察者回调函数，作为<br/>[errorManager.setDefaultResourceUsageObserver](arkts-ability-errormanager-setdefaultresourceusageobserver-f.md#setDefaultResourceUsageObserver-1)的入参，用于监听各类资源占用变化，<br/>并支持应用执行自定义资源处理逻辑。<br/> |
| [UnhandledRejectionObserver](arkts-ability-errormanager-unhandledrejectionobserver-t.md) | 定义异常监听，用于捕获Promise异步操作失败的原因。<br/> |

