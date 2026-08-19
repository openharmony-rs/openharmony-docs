# @ohos.app.ability.errorManager

ErrorManager模块提供对应用运行时各类异常的全局观测能力，包括注册和注销错误观测器，主要用于监测应用崩溃（JS_CRASH）、应用冻屏（APP_FREEZE）、未捕获的Promise异常、资源超基线等错误场景。 通过设置监听器，开发者可以实时捕获异常信息、追踪问题根源、记录关键指标，从而提高应用的稳定性监控能力，加快故障排查和定位效率，提升应用质量和用户体验。

**起始版本：** 24

<!--Device-unnamed-declare namespace errorManager--><!--Device-unnamed-declare namespace errorManager-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { errorManager } from '@kit.AbilityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [offFreeze](arkts-ability-errormanager-offfreeze-f.md) | 注销冻屏事件观测器。 此函数只能在主线程中调用。 |
| [offUnhandledRejection](arkts-ability-errormanager-offunhandledrejection-f.md) | Unregister unhandled rejection observer. |
| [off_error](arkts-ability-errormanager-offerror-f.md#offerror) | 注销错误观测器。使用callback异步返回。 仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。 |
| [off_error](arkts-ability-errormanager-offerror-f.md#offerror) | 注销错误观测器。使用Promise异步返回。 仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。 |
| [off_freeze](arkts-ability-errormanager-offfreeze-f.md) | 取消之前注册的应用主线程freeze监听。 仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。 如果传入的回调与通过on方法注册回调不一致，将抛出16300004错误码，因此建议使用try-catch逻辑进行处理。 |
| [off_globalErrorOccurred](arkts-ability-errormanager-offglobalerroroccurred-f.md#offglobalerroroccurred) | 注销错误观测器，注销之前注册在同一线程的callback全局监听。 如果传入的回调不在通过on方法注册的回调队列中，将抛出16300004错误码，因此建议使用try-catch逻辑进行处理。 |
| [off_globalUnhandledRejectionDetected](arkts-ability-errormanager-offglobalunhandledrejectiondetected-f.md#offglobalunhandledrejectiondetected) | 注销被拒绝promise监听器，注销后无法监听进程中的promise异常。 如果传入的回调不在通过on方法注册的回调队列中，将抛出16300004错误码，因此建议使用try-catch逻辑进行处理。 |
| [off_loopObserver](arkts-ability-errormanager-offloopobserver-f.md#offloopobserver) | 注销主线程消息处理监听器。 仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。 |
| [off_unhandledRejection](arkts-ability-errormanager-offunhandledrejection-f.md) | 注销被拒绝promise监听器。 仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。 |
| [onFreeze](arkts-ability-errormanager-onfreeze-f.md) | 注册冻屏事件观测器。 此函数只能在主线程中调用。 请注意，每个进程只支持注册一个观测器。 如果多次注册，后注册的将覆盖之前的。 |
| [onUnhandledRejection](arkts-ability-errormanager-onunhandledrejection-f.md) | Register unhandled rejection observer. |
| [on_error](arkts-ability-errormanager-onerror-f.md#onerror) | 注册错误观测器。注册后可以捕获到应用产生的js crash，属于应用崩溃的一种。观测器捕获到该异常时应用不退出，建议在回调函数执行完后，增加同步退出操作。 仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。 |
| [on_freeze](arkts-ability-errormanager-onfreeze-f.md) | 注册应用主线程freeze监听。多次注册情况下，取最后一次注册的结果。 仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。 > **注意**： > > 如果该回调函数执行时间超过1s，可能导致[AppRecovery](arkts-app-ability-apprecovery.md)功能不可用。通过解析hilog日志中的begin与Freeze > callback execution completed两者的时间差可以计算回调函数执行时长，如果超过1秒，可以尝试采用异步处理、减少阻塞操作、优化数据结构等方法优化回调逻辑，降低执行时长。 > 该接口请勿与[errorManager.setDefaultFreezeObserver](arkts-ability-errormanager-setdefaultfreezeobserver-f.md)接口混用，混用可能会导致注册的回调函数执行失败。 |
| [on_globalErrorOccurred](arkts-ability-errormanager-onglobalerroroccurred-f.md#onglobalerroroccurred) | 在进程中的任意线程中注册 `errormanager.on` 接口，监听整个进程中任意线程的异常。观测器捕获到该异常时应用不退出，建议在回调函数执行完后，增加同步退出操作。 |
| [on_globalUnhandledRejectionDetected](arkts-ability-errormanager-onglobalunhandledrejectiondetected-f.md#onglobalunhandledrejectiondetected) | 在进程中任意线程注册被拒绝promise监听器，注册后可以捕获到当前进程中未被捕获到的promise rejection。 |
| [on_loopObserver](arkts-ability-errormanager-onloopobserver-f.md#onloopobserver) | 注册主线程消息处理耗时监听器。注册后可以捕获到应用主线程处理消息的具体执行时间。 仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。 |
| [on_unhandledRejection](arkts-ability-errormanager-onunhandledrejection-f.md) | 注册被拒绝promise监听器。注册后可以捕获到当前线程中未被捕获到的promise rejection。 仅在主线程中使用。使用线程出错时，将抛出错误码，因此建议使用try-catch逻辑进行处理。 |
| [setDefaultErrorHandler](arkts-ability-errormanager-setdefaulterrorhandler-f.md) | 发生JS_CRASH异常时，支持链式回调，返回上一次注册的处理器，仅限主线程调用。 如果传入非法参数或在子线程调用，将抛出错误码并返回undefined，因此建议使用try-catch逻辑进行处理。 若接口参数为空，后续注册的处理器将无法与前序已注册的处理器建立关联，从而中断链式调用。 |
| [setDefaultFreezeObserver](arkts-ability-errormanager-setdefaultfreezeobserver-f.md) | 发生APP_FREEZE时，支持链式回调，返回上一次注册的处理器，仅限主线程调用。 如果传入非法参数或在子线程调用，将抛出错误码并返回undefined，因此建议使用try-catch逻辑进行处理。 |
| [setDefaultResourceUsageObserver](arkts-ability-errormanager-setdefaultresourceusageobserver-f.md) | 设置资源占用观察者，应用资源超基线时，支持链式回调，返回上一次注册的资源占用观察者，仅限主线程调用。 如果传入非法参数或在子线程调用，将抛出错误码并返回undefined，因此建议使用try-catch逻辑进行处理。 若接口参数为空，后续注册的观察者将无法与前序已注册的观察者建立关联，从而中断链式调用。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [GlobalError](arkts-ability-errormanager-globalerror-i.md) | 有关异常事件名字、消息、错误堆栈信息、异常线程名称和类型的对象。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [InstanceType](arkts-ability-errormanager-instancetype-e.md) | 虚拟机的实例类型。 |
| [ResourceType](arkts-ability-errormanager-resourcetype-e.md) | 应用资源超基线的类型。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ErrorHandler](arkts-ability-errormanager-errorhandler-t.md) | 当ArkTS运行时抛出用户未捕获异常时，将调用ErrorHandler。 |
| [ErrorObserver](arkts-ability-errormanager-errorobserver-t.md) | ErrorObserver模块。 |
| [FreezeObserver](arkts-ability-errormanager-freezeobserver-t.md) | 定义应用主线程freeze回调，用于应用自定义添加freeze信息。 |
| [GlobalObserver](arkts-ability-errormanager-globalobserver-t.md) | 定义异常监听，可以作为 [errorManager.on('globalErrorOccurred')](arkts-ability-errormanager-onerror-f.md#onerror) 和 [errorManager.on('globalUnhandledRejectionDetected')](arkts-ability-errormanager-onerror-f.md#onerror) 的入参监听当前应用主线程事件处理事件。 |
| [LoopObserver](arkts-ability-errormanager-loopobserver-t.md) | LoopObserver模块。定义异常监听，可作为 `errormanager.on` 函数的参数，监听并处理当前应用主线程超时的事件。 |
| [ResourceUsageObserver](arkts-ability-errormanager-resourceusageobserver-t.md) | 定义应用资源使用情况的观察者回调函数，作为 [errorManager.setDefaultResourceUsageObserver](arkts-ability-errormanager-setdefaultresourceusageobserver-f.md)的入参，用于监听各类资源占用变化， 并支持应用执行自定义资源处理逻辑。 |
| [UnhandledRejectionObserver](arkts-ability-errormanager-unhandledrejectionobserver-t.md) | 当发生未处理的拒绝时，系统将调用此观测器。 |

