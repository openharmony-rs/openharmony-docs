---
kits: ["ArkTS / 方舟编程语言"]
description: "介绍JSVM内存泄漏定位方法，先通过hidumper采样定性区分Native内存与JS堆内存泄漏，再分别借助DevEco Studio Profiler与DevTools堆快照对比找到泄漏源头。"
keywords: [内存泄漏, 定性分析, hidumper, Native内存, JS堆内存, 堆快照对比, OH_JSVM_CreateReference, DevEco Studio, 内存分析]
doctype: guide
status: active
---

# JSVM 定位内存泄漏问题指导
<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->

JSVM的内存占用包括Native内存占用(C/C++侧的内存占用)和底层的JS引擎的堆内存占用，JS引擎会维护一个堆来管理其生成的JS对象，其生命周期由JS引擎维护，除此之外的内存我们归为Native内存。用户在使用JSVM时，可能碰到这两种内存异常增长的情况。

本文先介绍如何定性分析，然后分两个部分介绍如何定位Native内存泄漏和JS引擎堆内存泄漏。

## 定性分析

可以通过hdc连接设备，执行如下命令行的方式对目标应用的内存进行采样，比较一段时间内的内存变化情况，从而定性分析是Native内存泄漏，还是JS堆内存异常增长。下图中Pss Total列，native heap对应Native内存占用，AnonPage other对应js堆内存占用。
```hdc
hidumper --mem $(pidof dest_app)
```
<div align=left><img src="figures/jsvm_locate_memory_leak_hidump.png"/></div>


## Native内存泄漏定位
### 典型场景
1. OH_JSVM_CreateReference 和 OH_JSVM_DeleteReference 接口没有成对调用，导致Reference没有被释放。
```c++
JSVM_Value obj = nullptr;
OH_JSVM_CreateObject(env, &obj);
// 创建引用
JSVM_Ref reference;
OH_JSVM_CreateReference(env, obj, 1, &reference);

// 使用引用
JSVM_Value result;
OH_JSVM_GetReferenceValue(env, reference, &result);

// 未释放引用
// OH_JSVM_DeleteReference(env, reference);
```

### 定位步骤
为了分析Native内存泄漏，可以借助DevEco Studio的内存分析模块，具体参考文档：[内存分析及优化](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-insight-session-allocations-memory)。
1. 使用Profiler的Allocation模块记录一段时间内的Native内存信息。

   <div align=left><img src="figures/jsvm_locate_memory_leak_allocation1.png"/></div>  

2. 比较这段时间内"Created & Existing"的内存变化情况，如果存在占比较大且Count较大的未释放内存，则怀疑存在内存泄漏，展开进一步查看调用栈。

   <div align=left><img src="figures/jsvm_locate_memory_leak_allocation2.png"/></div> 


## JS引擎堆内存泄漏定位
### 典型场景
1. 全局变量滥用，导致DOM元素未释放。
```js
const elements = [];
function createElements() {
  for (let i = 0; i < 1000; i++) {
    const el = document.createElement('div');
    document.body.appendChild(el);
    elements.push(el); // 即使从 DOM 移除，数组仍保留引用
  }
}
```

### 定位步骤

JSVM目前提供了OH_JSVM_OpenInspector开启inspector，参考[使用OH_JSVM_OpenInspector](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/jsvm-debugger-cpuprofiler-heapsnapshot#%E4%BD%BF%E7%94%A8-oh_jsvm_openinspector)，在此基础上可以[使用 Chrome inspect 页面进行调试](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/jsvm-debugger-cpuprofiler-heapsnapshot#%E4%BD%BF%E7%94%A8-chrome-inspect-%E9%A1%B5%E9%9D%A2%E8%BF%9B%E8%A1%8C%E8%B0%83%E8%AF%95)。

通过使用DevTools工具，对目标场景内的堆内存进行快照（快照前先点击上方的垃圾回收按钮进行垃圾回收），利用快照对比功能，找到未释放的JS对象和其所在源码中的位置，进一步指导定位堆内存未释放的原因。

<div align=left><img src="figures/jsvm_locate_memory_leak_devtool.png"/></div> 

### 通过 --heap-dump-on-oom 在OOM时自动导出堆转储

除了通过DevTools手动抓取堆快照进行对比分析外，JSVM还支持在JS堆内存耗尽（OOM，Out Of Memory）时，由引擎自动将当前堆内存导出为堆转储文件，用于事后定位堆内存泄漏。

在初始化JSVM时，通过`JSVM_InitOptions`的`argc`/`argv`传入`--heap-dump-on-oom`选项即可开启该能力。`OH_JSVM_Init`会将argv中的引擎参数透传给底层JS引擎。

```c++
// 初始化JSVM时开启OOM堆转储
static int32_t TestJSVM()
{
  JSVM_InitOptions initOptions = {0};
  int argc = 2;
  const char* argv[2] = {
    "",
    "--heap-dump-on-oom",
  };
  initOptions.argc = &argc;
  initOptions.argv = const_cast<char**>(argv);
  // 初始化JavaScript引擎实例
  JSVM_CALL(OH_JSVM_Init(&initOptions));
  // ... 创建VM/Env并执行业务逻辑
  return 0;
}
```

> **说明：**
>
> - `--heap-dump-on-oom`为开发调试参数，开启会带来一定的性能开销，仅建议在定位JS堆内存泄漏问题时临时开启，正式发布版本不建议携带该参数。
> - 开启后，当JS堆内存达到上限触发OOM时，引擎会在进程退出前将当前堆快照写入堆转储文件。
> - 堆转储文件的默认输出路径为`/data/app/el2/100/base/<包名>/`（以包名 `com.example.Test` 为例，文件输出至 `/data/app/el2/100/base/com.example.Test/` 下），文件名形如 `xxx.rawheap`，可通过hdc工具将其从设备取回后分析。
> - `xxx.rawheap` 堆转储文件需通过 `js_rawheap_translator` 工具转换为 `.heapsnapshot` 格式文件后才能用于可视化分析，具体转换方法参考[js-rawheap-translator工具](../tools/js-rawheap-translator.md)。
> - 转换生成的 `.heapsnapshot` 文件可导入DevTools工具或DevEco Studio中解析，定位未释放的JS对象及其引用链。
