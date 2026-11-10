# ArkTSVM

```TypeScript
class ArkTSVM
```

为开发者提供虚拟机维测能力的类。

**起始版本：** 23

<!--Device-util-class ArkTSVM--><!--Device-util-class ArkTSVM-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { util } from '@kit.ArkTS';
```

## enableHandleMemoryOptimization

```TypeScript
static enableHandleMemoryOptimization(): void
```

开启按比例的 handle/原始类型存储收缩优化。默认关闭；一旦开启将无法关闭。开启前使用传统的保守收缩策略。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArkTSVM-static enableHandleMemoryOptimization(): void--><!--Device-ArkTSVM-static enableHandleMemoryOptimization(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

## enableLocalHandleDetection

```TypeScript
static enableLocalHandleDetection(): void
```

EventHandler和libuv的异步事件循环机制在执行异步任务时，任务将不在当前handle scope的管理范围内执行，创建的napi_value不会被自动回收。若开发者在任务回调中未添加scope，将导致内存泄漏。调用该接口后，可确保这两个机制的任务在scope范围内执行，从而避免内存泄漏。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArkTSVM-static enableLocalHandleDetection(): void--><!--Device-ArkTSVM-static enableLocalHandleDetection(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**示例**

```TypeScript
// napi_init.cpp C++侧示例代码
#include "napi/native_api.h"
#include "uv.h"

static napi_value CreateObject(napi_env env, napi_callback_info info)
{
    uv_loop_s* loop = nullptr;
    napi_status status = napi_get_uv_event_loop(env, &loop);
    if (status != napi_ok) {
        napi_throw_error(env, nullptr, "napi_get_uv_event_loop fail");
        return nullptr;
    }
    uv_work_t* work = new uv_work_t;
    work->data = env;
    int ret = uv_queue_work(loop, work,
        [](uv_work_t* work){},
        [](uv_work_t* work, int status){
            napi_env env = static_cast<napi_env>(work->data);
            for (int i = 0; i < 1000; i++) {
                napi_value obj = nullptr;
                // 在libuv提供的异步机制中没有加scope会导致内存泄漏
                napi_create_object(env, &obj);
            }
            delete work;
        }
    );
    if (ret != 0) {
        delete work;
    }
    return nullptr;
}
```

在CMakeLists.txt中添加以下动态链接库：

```TypeScript
libuv.so
```

```TypeScript
// index.d.ts 接口声明
export const createObject: () => void;
```

```TypeScript
// Index.ets ArkTS侧示例代码
import { hilog } from '@kit.PerformanceAnalysisKit';
import testNapi from 'libentry.so';
import { util } from '@kit.ArkTS';

try {
  // 若不开启LocalHandle内存泄漏兜底机制，可能导致内存溢出。启用该机制后，系统将自动回收EventHandler和libuv异步任务中创建的napi_value
  util.ArkTSVM.enableLocalHandleDetection();
  testNapi.createObject();
  hilog.info(0x0000, 'testTag', 'Test Node-API createObject success');
} catch (error) {
  hilog.error(0x0000, 'testTag', 'Test Node-API createObject failed error: %{public}s', error.message);
}
```

可能出现的问题：

如果之前内存泄漏的对象被继续使用，使用enableLocalHandleDetection接口后，系统会回收内存泄漏对象。继续使用该对象会导致内存泄漏问题转变为稳定性问题。

```TypeScript
napi_value global_js_object;
napi_value dangerous_function(napi_env env, napi_callback_info info) {
    napi_value js_obj;
    napi_create_object(env, &js_obj);
    global_js_object = js_obj; // 直接存储到全局变量，开启LocalHandle内存泄漏兜底机制后被释放
    return nullptr;
}
```

## getAllVMHeapMemoryInfo

```TypeScript
static getAllVMHeapMemoryInfo(): Promise<HeapMemoryInfo[]>
```

获取所有VM线程的堆内存信息，包括线程ID、线程名称、堆类型和堆对象大小，适用于内存泄漏排查、内存使用分析等场景。使用Promise异步回调。

接口获取到的堆包含两种类型：local堆，即应用进程中每个ArkTS线程独有的虚拟机堆；shared堆，即应用进程中所有ArkTS线程共享的虚拟机堆。

> **说明：** 
> 
> 此接口在执行时会暂停所有VM线程运行以获取内存信息。由于需要等待所有VM线程暂停，高负载场景下调用此接口的耗时可能较高。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArkTSVM-static getAllVMHeapMemoryInfo(): Promise<HeapMemoryInfo[]>--><!--Device-ArkTSVM-static getAllVMHeapMemoryInfo(): Promise<HeapMemoryInfo[]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[HeapMemoryInfo](arkts-arkts-util-heapmemoryinfo-i.md)[]&gt; | Promise对象，解析为HeapMemoryInfo对象数组，每个对象包含线程ID、线程名称、堆类型和堆对象大小。此方法可以获取local堆和shared堆的内存信息。 |

**示例**

```TypeScript
import { util } from '@kit.ArkTS';

util.ArkTSVM.getAllVMHeapMemoryInfo().then(
  result => {
    result.forEach(info => {
      console.info(info.threadId?.toString());
      console.info(info.threadName);
      console.info(info.heapType);
      console.info(info.heapObjectSize.toString());
    })
  }
);
```

## getGlobalHandleCount

```TypeScript
static getGlobalHandleCount(): number
```

获取当前调用线程所属虚拟机中正在使用的全局句柄（global handle）数量，适用于内存观测等场景。

> **说明：** 
> 
> 在worker线程中调用本接口时，返回的是该worker线程所属虚拟机的计数，而非主线程虚拟机的计数。
> 
> 该接口仅统计强引用（global handle）的数量，不包含弱引用（WeakRef）和Sendable引用（SendableRef）的数量。
> 弱引用存储在独立的弱引用链表中，Sendable引用存储在独立的Sendable全局存储中，均不在本接口的遍历范围内。
> 返回值受强引用创建/删除操作的影响，例如napi_create_strong_reference、napi_delete_strong_reference等接口
> 会相应增减计数，napi_create_strong_sendable_reference、napi_delete_strong_sendable_reference等接口
> 不会影响计数结果。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArkTSVM-static getGlobalHandleCount(): number--><!--Device-ArkTSVM-static getGlobalHandleCount(): number-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前调用线程所属虚拟机中正在使用的全局句柄数量。 |

**示例**

```TypeScript
import { util } from '@kit.ArkTS';

let count: number = util.ArkTSVM.getGlobalHandleCount();
console.info(`current global handle count: ${count}`);
```

## hintGC

```TypeScript
static hintGC(level?: UrgencyLevel): void
```

提示当前ArkTS虚拟机主动触发GC的接口。虚拟机根据当前内存状态和紧急程度决定是否触发GC。默认参数值是Urgency.LOW。不推荐高频调用，因为GC可能带来较高的性能开销

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArkTSVM-static hintGC(level?: UrgencyLevel): void--><!--Device-ArkTSVM-static hintGC(level?: UrgencyLevel): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| level | [UrgencyLevel](arkts-arkts-util-urgencylevel-e.md) | 否 | 紧急程度.<br>可选的参数值如下: <br>- **Urgency.LOW** (默认值): 紧急程度低, GC触发阈值相对较高,适用于开发者期望主动触发GC去回收已死亡的对象但是应用的ArkTS内存压力仍然可控的场景。<br>- **Urgency.MEDIUM**: 紧急程度中等, GC触发阈值介于LOW和HIGH之间。<br>- **Urgency.HIGH**: 紧急程度高, GC触发阈值低,适用于应用的ArkTS内存压力已经非常高，开发者期望系统尽可能快地触发GC去回收内存的场景 |

## offVMHeapMemoryPressure

```TypeScript
static offVMHeapMemoryPressure(): void
```

取消已注册的内存预警回调函数。此接口需要在主线程调用。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArkTSVM-static offVMHeapMemoryPressure(): void--><!--Device-ArkTSVM-static offVMHeapMemoryPressure(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**示例**

```TypeScript
import { util } from '@kit.ArkTS';

util.ArkTSVM.offVMHeapMemoryPressure();
```

## onVMHeapMemoryPressure

```TypeScript
static onVMHeapMemoryPressure(callback: Callback<string>, heapMemoryThreshold: HeapMemoryThreshold): boolean
```

注册一个回调函数，在虚拟机主线程完成垃圾回收后，如果堆内存超过预警阈值则触发回调执行，适用于主动内存管理（在内存压力较大时触发资源清理）、OOM预防等场景。

虚拟机是通过统计存活对象大小来判断是否达到内存预警阈值，由于虚拟机堆存在一定内存碎片以及浮动垃圾，无法保证在OOM前肯定会触发到回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArkTSVM-static onVMHeapMemoryPressure(callback: Callback<string>, heapMemoryThreshold: HeapMemoryThreshold): boolean--><!--Device-ArkTSVM-static onVMHeapMemoryPressure(callback: Callback<string>, heapMemoryThreshold: HeapMemoryThreshold): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | 是 | 垃圾回收后内存达到预警阈值时触发的回调函数，字符串参数表示内存压力事件的类型。目前事件的类型有三种取值，"LocalHeapMemPressure"，"SharedHeapMemPressure"，"ProcessHeapMemPressure"。 |
| heapMemoryThreshold | [HeapMemoryThreshold](arkts-arkts-util-heapmemorythreshold-i.md) | 是 | 堆内存预警阈值配置，以百分比设置，取值范围为[70, 95]。超出范围时自动限制到有效区间。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 注册成功返回true，当不在主线程调用或回调已注册时返回false。 |

**示例**

```TypeScript
import { util } from '@kit.ArkTS';

let callback = (event: string) => {
  console.info('Memory pressure event: ' + event);
};

let threshold: util.HeapMemoryThreshold = {
  localHeapThreshold: 75,
  sharedHeapThreshold: 80,
  processHeapThreshold: 85
};

let result : boolean = util.ArkTSVM.onVMHeapMemoryPressure(callback, threshold);
console.info('Registration result: ' + result);
```

## setMultithreadingDetectionEnabled

```TypeScript
static setMultithreadingDetectionEnabled(enabled: boolean, options?: MultithreadingDetectionOptions):void
```

若enabled为true则开启，为false则关闭。开启多线程安全检测，多线程问题的C/C++崩溃转储文件（cppcrash文件）里会包含多线程信息（如线程ID、锁状态等）。关闭多线程安全检测，则C/C++崩溃转储文件（cppcrash文件）里不会包含多线程信息。

options是用于配置多线程安全检测的行为参数。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArkTSVM-static setMultithreadingDetectionEnabled(enabled: boolean, options?: MultithreadingDetectionOptions):void--><!--Device-ArkTSVM-static setMultithreadingDetectionEnabled(enabled: boolean, options?: MultithreadingDetectionOptions):void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 控制多线程安全检测开关的开启或关闭。true表示开启，false表示关闭。 |
| options | [MultithreadingDetectionOptions](arkts-arkts-util-multithreadingdetectionoptions-i.md) | 否 | 多线程安全检测的参数配置，此参数不填时，对应各属性取MultithreadingDetectionOptions的默认值。<br>**适用版本：** 26.0.0 |

**示例**

```TypeScript
import { util } from '@kit.ArkTS';

// 打开多线程安全检测开关
util.ArkTSVM.setMultithreadingDetectionEnabled(true);
// 关闭多线程安全检测开关
util.ArkTSVM.setMultithreadingDetectionEnabled(false);
// 设置崩溃行为
util.ArkTSVM.setMultithreadingDetectionEnabled(true, { abort: false });
// 调整检测粒度
util.ArkTSVM.setMultithreadingDetectionEnabled(true, { frequency: 200 });
// 调整上报间隔
util.ArkTSVM.setMultithreadingDetectionEnabled(true, { interval: 10 });
// 同时设置三个参数
util.ArkTSVM.setMultithreadingDetectionEnabled(true, {
  abort: false,
  frequency: 500,
  interval: 60
});
```

## setTrackGlobalRef

```TypeScript
static setTrackGlobalRef(enable: boolean): void
```

开启或关闭napi_ref与全局对象之间的关联追踪。开启后，堆快照中全局对象节点将包含napi_ref的地址信息；关闭后（enable为false），将停止追踪，堆快照中不再显示napi_ref与全局对象之间的关联关系。

开启追踪后，虚拟机会额外记录napi_ref与全局对象的关联关系，可能带来一定的内存和性能开销。在不需要调试时，建议调用`util.ArkTSVM.setTrackGlobalRef(false)`关闭追踪。

该接口的开关为进程级别，进程内的所有线程共享同一开关状态。在任意线程调用本接口设置开关后，将对该进程内所有线程生效。

关于napi_ref的详细说明，请参考napi_ref使用指导。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArkTSVM-static setTrackGlobalRef(enable: boolean): void--><!--Device-ArkTSVM-static setTrackGlobalRef(enable: boolean): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否开启追踪。true表示开启追踪（可能带来一定的内存和性能开销），false表示关闭追踪。建议在不需要调试时设置为false以避免性能开销。 |

**示例**

```TypeScript
// napi_init.cpp C++侧示例代码
#include "napi/native_api.h"

static napi_value CreateGlobalRef(napi_env env, napi_callback_info info)
{
    napi_value js_obj = nullptr;
    napi_create_object(env, &js_obj);
    // 创建napi_ref，与全局handle建立关联
    napi_ref ref = nullptr;
    napi_create_reference(env, js_obj, 1, &ref);
    // 开启setTrackGlobalRef后，堆快照中将包含该ref对应的native引用地址信息
    return nullptr;
}
```

```TypeScript
// Index.d.ts 接口声明
export const createGlobalRef: () => void;
```

```TypeScript
// Index.ets ArkTS侧示例代码
import { hilog } from '@kit.PerformanceAnalysisKit';
import testNapi from 'libentry.so';
import { util } from '@kit.ArkTS';

try {
  // 开启napi_ref与全局handle的关联追踪，开启后堆快照中将包含native引用地址信息
  util.ArkTSVM.setTrackGlobalRef(true);
  testNapi.createGlobalRef();
  hilog.info(0x0000, 'testTag', 'Test Node-API createGlobalRef success');
} catch (error) {
  hilog.error(0x0000, 'testTag', 'Test Node-API createGlobalRef failed error: %{public}s', error.message);
}
```
