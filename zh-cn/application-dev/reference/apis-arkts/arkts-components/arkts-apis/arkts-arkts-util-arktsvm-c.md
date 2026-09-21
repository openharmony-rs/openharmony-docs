# ArkTSVM

```TypeScript
class ArkTSVM
```

为开发者提供虚拟机维测能力的类。

**起始版本：** 23

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { util } from '@kit.ArkTS';
```

## enableLocalHandleDetection

```TypeScript
static enableLocalHandleDetection(): void
```

开启 local handle 检测，以避免在 Libuv 或 EventHandler 的事件循环（event looper）中出现内存泄漏。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

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

从 ArkTS-VM 和共享堆中获取所有堆内存信息。

> **说明：** 
> 
> 此接口在执行时会暂停所有VM线程运行以获取内存信息。由于需要等待所有VM线程暂停，高负载场景下调用此接口的耗时可能较高。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[HeapMemoryInfo](arkts-arkts-util-heapmemoryinfo-i.md)[]&gt; | 返回一个 promise，包含 ArkTS-VM 的 local 堆和共享堆中的所有堆内存信息。 |

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

获取当前调用线程所属 ArkTS 虚拟机正在使用的全局 handle 数量。可用于维测场景，例如根据全局 handle 数量决定是否生成内存快照。

> **说明：** 
> 
> 该计数是在调用线程所属的虚拟机上查询的。在 worker 中调用此接口返回的是该 worker 自身虚拟机的计数，而非主
> 虚拟机的计数。
> 
> 仅统计强引用（global handle）的数量，不包含弱引用（WeakRef）和 Sendable 引用（SendableRef）。弱引用存储在
> 独立的弱引用链表中，Sendable 引用存储在独立的 Sendable 全局存储中，均不在本接口的遍历范围内。
> 
> 返回值受强引用创建/删除操作的影响。例如，napi_create_strong_reference、napi_delete_strong_reference 会相应
> 增减计数，而 napi_create_strong_sendable_reference、napi_delete_strong_sendable_reference 不会影响计数结果。

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回当前虚拟机正在使用的全局 handle 数量，该值大于等于 0。 |

## offVMHeapMemoryPressure

```TypeScript
static offVMHeapMemoryPressure(): void
```

取消注册在 GC 后堆内存超过临界预警阈值时触发的回调。

@static

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

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

注册一个回调函数，在 GC（垃圾回收）后堆内存超过临界预警阈值时触发。必须在主线程上调用，且仅能注册一个回调。

NOTE:无法保证在 OOM（内存溢出）前一定会触发该回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | 是 | 在 GC 后内存达到阈值时触发的回调。字符串参数表示内存压力事件的类型："LocalHeapMemPressure"、"SharedHeapMemPressure" 或 "ProcessHeapMemPressure"。 |
| heapMemoryThreshold | [HeapMemoryThreshold](arkts-arkts-util-heapmemorythreshold-i.md) | 是 | 表示 GC 后触发回调的堆内存百分比阈值。取值范围为 [70, 95]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 注册成功返回 `true`；若不在主线程调用或回调已注册，则返回 `false`。@static |

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

设置是否开启多线程安全检测。当 **enabled** 设置为 **true** 时开启检测，多线程问题的 cppcrash 文件中将包含多线程相关的详细信息。当 **enabled** 设置为 **false** 时关闭检测，相应的 cppcrash 文件中将不包含此类详细信息。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 控制是否开启多线程安全检测。**true** 表示开启检测，**false** 表示关闭检测。 |
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

开启或关闭 napi_ref 与全局 handle 之间关联关系的追踪。开启后，堆快照将包含 native 引用地址信息。关闭后（enable 为false），将停止追踪，堆快照中不再显示 native 引用与全局 handle 之间的关联关系。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 布尔标志位，指示是开启还是关闭追踪。**true** 表示开启追踪，**false** 表示关闭追踪。 |

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
