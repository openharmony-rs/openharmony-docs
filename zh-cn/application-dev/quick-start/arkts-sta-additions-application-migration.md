# ArkTS静态类型及应用迁移改造概述

## 应用迁移到ArkTS静态类型

### 迁移改造流程概述

应用迁移到ArkTS静态类型的流程如下：首先进行场景识别，定位需要从TypeScript迁移到ArkTS的模块并分析模块间的依赖关系，评估性能提升预期。接着进入模块改造阶段，包括架构设计、代码改造，以及将TS代码转换为ArkTS动态代码。然后使用工具完成语法适配和ArkTS静态代码并行化改造。改造完成后，先验证功能是否正常，再开启AOT进行性能验收。所有验收通过后，即完成整个迁移流程。

![迁移改造流程概述](./figures/迁移改造流程概述.png "迁移改造流程概述")

## 场景识别

### 寻找需要改造的模块

**HiTrace进行耗时分析**

在业务代码中使用HiTrace对关键耗时点进行分析，详细使用方法可参考官方文档：[HiTrace](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/hitrace)。

**基础使用方式**

```typescript
import hiTraceMeter from '@ohos.hiTraceMeter';

hiTraceMeter.startTrace("TaskTrace", 0x001);
...
const bundleInfo:bundleManager.BundleInfo = bundleManager.getBundleInfoForSelfSync(
      bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_APPLICATION |
      bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_METADATA
    );
...  
hiTraceMeter.finishTrace("TaskTrace", 0x001);
```

**常见耗时场景**

| 场景类型 | 问题表现。 |
|:---------|:---------|
| 动态库加载耗时 | 应用启动/模块初始化时，动态库文件加载时间过长。 |
| 业务逻辑执行耗时 | 核心流程中单段代码执行耗时长（如数据处理、计算等）。 |

### 实例分析

**第一步：分析业务代码执行流程**

业务执行流程示例如下：

![原动态代码执行图](./figures/原动态代码执行图.png "原动态代码执行图")

**示例代码（TaskB+Data初始化）**

```typescript
import lazy bundleManager from '@ohos.bundle.bundleManager';
import hiTraceMeter from '@ohos.hiTraceMeter';
import { Data } from './Data';

export function TaskB():void {
  // Trace起始点
  hiTraceMeter.startTrace("Task-inner", 0x001);

  try {
    // 读取bundleInfo信息
    const bundleInfo:bundleManager.BundleInfo = bundleManager.getBundleInfoForSelfSync(
      bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_APPLICATION |
      bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_METADATA
    );

    const appInfo:bundleManager.ApplicationInfo = bundleInfo.appInfo;
    if (!appInfo?.metadataArray) {
      throw new Error("Invalid appInfo or no metadata found");
    }

    // 遍历数据并存储到Map中
    for (const item of appInfo.metadataArray) {
      if (!item?.metadata) {
        continue;
      }
      for (const innerItem of item.metadata) {
        if (innerItem?.name && innerItem?.value) {
          Data.getInstance().addMetadata(innerItem.name, innerItem.value);
        }
      }
    }
  } catch (error) {
    hilog.error(DOMAIN, TASK, `Task error: ${error}`);
  } finally {
    // Trace结束点
    hiTraceMeter.finishTrace("Task-inner", 0x001);
  }
}
```

**第二步：分析Trace**

- **Task任务总耗时：** 7.9ms。
  ![TaskTrace](./figures/TaskTrace.png "TaskTrace")

- **加载libbundlemanager.so耗时：** 1.7ms。
  ![加载libbundlemanager.so](./figures/加载libbundlemanager.so.png "加载libbundlemanager.so")。

**第三步：得出结论**

在该例子中，TaskA耗时10ms，TaskC耗时1ms，通过表格中的耗时数据可以得出：

| 项目 | 耗时 |
|------|------|
| TaskA | 10ms |
| TaskB+Data解析 | 7.9ms |
| TaskC | 1ms |
| **总计** | **18.9ms** |

**结论：TaskB+Data解析执行耗时7.9ms，占主线程总耗时18.9ms的42%，并行化改造收益大。**


### 模块改造前依赖分析

在确定改造方案前，需要分析模块的调用链路和依赖关系，评估改造范围和可行性。

**现有模块执行流程分析**

存在的问题：

- 主线程阻塞： 数据初始化TaskB函数需在主线程顺序执行。
- 资源占用： 长时间占用主线程资源，影响系统响应效率。

**并行化改造方案**

| 改造维度 | 改造策略 | 预期效果 |
|:---------|:---------|:---------|
| 并发优化 | 将数据初始化逻辑迁移至子线程异步执行 | 释放主线程处理其他业务。 |
| 内存共享 | 将TaskB和Data函数改造为静态代码 | 实现线程间高效共享，避免重复加载，确保线程安全访问。 |


### 改造后性能收益预估

**并行化执行流程**

并行化改造后，TaskA和TaskB可同时并行执行，TaskC等待两者完成后执行：

![改造后混编代码执行流程图](./figures/改造后混编代码执行流程图.png "改造后混编代码执行流程图")

**性能收益对比**

| 方案 | 执行方式 | 总耗时 |
|:-----|:---------|:-------|
| 原有方案 | 单线程串行执行 | TaskA:10ms + TaskB:7.9ms + TaskC:1ms = 18.9ms |
| 并行化改造 | TaskA与TaskB并行执行 | TaskA:10ms + TaskC:1ms = 11ms|

结论：TaskB+Data解析执行并行化改造后，预期能够减少总耗时7.9ms。


## 模块改造

### 改造模块架构设计

针对需要改造的具体模块，需要考虑以下几个方面：
* **该模块能够兼容新老设备**，即改造后的应用包能够分发到支持的目标设备上；
* **该模块实现能够运行时回滚**，即改造后静态类型实现如果存在bug可以通过开关回退到改造前的实现；
* **该模块保持对外接口不变**，即对外的接口保持动态类型不变。

根据以上设计目标的改造模块架构如下图所示：

![改造模块架构设计](./figures/arkts-static-architecture.PNG "改造模块架构设计")

待改造的模块主要包含1个接口文件`Index.ets`和2个动态特性实现文件`dFeature1.ets`和`dFeature2.ets`，目标是新增特性1的静态类型实现文件`sFeature1.ets`，并且能够在不支持静态类型的设备上也能够运行，整体架构分为四层：

- 接口层：`Index.ets`需要保持对外不变。
- 分发层：`dispatch.js`根据API版本号在运行时分发到静态实现或者动态实现。
- 代理层：`proxy.ets`是特性1的静态实现。
- 实现层：`sFeature1.ets`的业务逻辑实现。

在ArkTS静态类型改造案例中[一套源码支持ArkTS动静态类型](###一套源码支持ArkTS动静态类型) 小节中会以代码详细展示各个层次的写法。

### 代码改造案例

基于改造模块架构，总结如下代码案例：

- **静态调用动态实现：** 在业务逻辑模块中定义了继承自动态开放API基类的子类实现，在静态上下文中需要从子线程回主线程后才能访问该对象。
- **分发层实现：** 对外提供的API存在被子线程调用的情况需要静态化，同时定义好定义分发类。
- **代理层实现：** 要接受动态类型参数，并访问它的属性或方法，如果要动态和静态2个类实现一致，需要定义代理类，实现动态到静态类型的转换。

### TS代码改造为ArkTS动态代码（按需）

详细的TypeScript到ArkTS动态代码改造，请参考：

**[TypeScript到ArkTS代码改造指南](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/typescript-to-arkts-migration-guide)**

### ArkTS动态到静态迁移工具

EasyTrans是ArkTS动态类型到静态类型的官方迁移工具，集成在DevEco Studio中，提供代码扫描和自动语法规则修复功能，可大幅降低迁移成本。


**文件扫描**

1. 打开迁移工具

在DevEco Studio中打开EasyTrans迁移工具界面：

![迁移工具使用](./figures/迁移工具使用.png "迁移工具使用")

2. 选择扫描范围

| 扫描范围 | 适用场景。 |
|:---------|:---------|
| **项目级** | 整体迁移，首次扫描推荐。 |
| **文件夹级** | 针对特定模块迁移。 |
| **单文件级** | 验证单个文件的改造效果。 |

3. 选择扫描模式

| 扫描类型 | 扫描速度 | 支持互操作问题扫描 | 适用场景 |
|:---------|:---------|:---------------------|:---------|
| **Fast Scan** |  快速 |  不支持 | 快速评估、初步排查。 |
| **Full Scan** |  完整 |  支持 | 正式迁移前全面检查。 |

> **建议：** 首次迁移建议使用**Full Scan**模式。

**问题修复**

扫描完成后，工具会展示所有可修复的语法规则代码：

![扫描结果](./figures/迁移工具扫描结果.png "迁移工具扫描结果")

**问题分类**

| 问题类型 | 标识 | 处理说明 |
|:---------|:-----|:---------|
| **可自动修复** | Auto-fixable | 点击右上方"一键修复"按钮。 |
| **需手动修复** | Manually-fixable | 查看右侧详情，根据建议手动修改。 |

**操作步骤**

1. 自动修复问题
   - 勾选需要修复的问题。
   - 点击工具栏右上方的 **"Fix All"** 或 **"Fix Selected"** 按钮。
   - 工具自动完成修复，并显示修复结果。

2. 手动修复问题
   - 点击问题项，右侧面板显示：
     - 问题描述。
     - 修改建议。
     - 代码示例。
   - 根据提示手动调整代码。

**使用建议**

| 场景 | 建议操作 |
|:-----|:---------|
| **首次迁移** | 使用Full Scan全面扫描 → 批量自动修复 → 逐项处理手动问题。 |
| **增量更新** | 使用Fast Scan快速验证新代码。 |
| **复杂项目** | 分模块扫描修复，避免一次性改动过大。 |

### C++代码从NAPI迁移到ANI

C++ 代码迁移主要包含以下三种方案：

| 迁移场景 | 说明。 |
|---------|------|
| **NAPI → ANI** | 从Node-API直接迁移到ANI。 |
| **NAPI → Taihe** | 使用Taihe工具自动生成桥接代码。 |
| **AKI → Taihe** | 从AKI框架迁移到Taihe框架代码。 |


**方案1. NAPI → ANI**

适用场景：项目代码量少于1000行、接口数量不超过10个。

| 内容 | 链接。 |
|------|------|
| 迁移指南 | [NAPI到ANI迁移指南](https://gitcode.com/openharmony/docs/blob/OpenHarmony_feature_20250702/zh-cn/application-dev/napi/napi2ani/napi2ani_guide.md) |
| ANI完整手册 | [Ark Native Interface应用实践手册](https://gitcode.com/openharmony/docs/blob/OpenHarmony_feature_20250702/zh-cn/application-dev/ani/ani-usage-scenarios.md) |

核心差异：
- 模块加载：NAPI自动注册 → ANI显式 `loadLibrary()`。
- 类型系统：动态类型 `napi_value` → 静态类型 `ani_int`/`ani_object` 等。
- Mangling规则：需编写方法签名如 `"ii:"`（两个int参数）。

**方案2. NAPI → Taihe**

适用场景：代码量超过10万行或接口数量超过50个的项目。

| 内容 | 链接 |
|------|------|
| 迁移指南 | [NAPI到Taihe迁移指南](https://gitcode.com/openharmony/docs/blob/OpenHarmony_feature_20250702/zh-cn/application-dev/napi/napi2ani/napi2taihe.md) |
| Taihe介绍 | [Taihe是什么？](https://gitcode.com/openharmony/docs/blob/OpenHarmony_feature_20250702/zh-cn/application-dev/taihe/taihe-introduction.md)。 |
| 快速开始 | [Taihe快速开始](https://gitcode.com/openharmony/docs/blob/OpenHarmony_feature_20250702/zh-cn/application-dev/taihe/taihe-quick-start.md)。 |
| IDL语法 | [Taihe IDL参考](https://gitcode.com/openharmony/docs/blob/OpenHarmony_feature_20250702/zh-cn/application-dev/taihe/taihe-idl-reference.md)。 |

**迁移步骤：**
1. 编写 `.ohidl` 接口定义文件。

- 基于NAPI业务的声明文件内容如下：
```typescript
export const add: (a: number, b: number) : number;
```

- 对应的ohidl接口定义文件内容如下：
```idl
function add(a: f64, b: f64) => f64;
```
这里a、b、add返回值的类型应根据实际数值范围和精度要求进行调整，如需使用整数类型，可以使用i32、i64。

- ohidl文件放置位置如下：

![ohidl文件放置位置](./figures/ohidl文件放置位置.png)

2. 执行编译，生成胶水代码。

- 对ohidl文件所在模块执行编译操作。

![napi2taihe模块编译](./figures/napi2taihe模块编译.png)

- 编译结果中查看是否有ohidl文件的报错。

![Taihe胶水代码拷贝](./figures/taihe胶水代码拷贝.png)

- 在cmake打包配置文件中添加如下：
```cmake
include(${OHIDL_GENERATED_CMAKE_FILE})
include_directories(
  ${TAIHE_GEN_INCLUDE}
  ${TAIHE_RUNTIME_INCLUDE}
)
add_library(yourLibName SHARED
  ${TAIHE_GEN_SRC}
  ${TAIHE_RUNTIME_SRC}
)
```

3. 实现C++ 业务逻辑。

- 编辑接口实现文件。
```cpp
#include "calc.impl.hpp"
#include "stdexcept"

namespace {
// 接口实现
double add(double a, double b) {
    return a + b;
}
}  // namespace

// Since these macros are auto-generate, lint will cause false positive.
// NOLINTBEGIN
// 接口绑定
TH_EXPORT_CPP_API_add(add);
// NOLINTEND
```

4. ArkTS逻辑中接口调用。

- 加载so。
ANI采用显式加载方案，允许在运行时当应用程序需要调用so接口时，使用loadLibrary进行加载。
```typescript
loadLibrary('yourLibName');
```

- 接口调用。
```typescript
// 方法导入需要导入build文件夹下生成的ets文件
// 示例采用相对路径方式引入，请根据实际场景修改相对路径
import { add } from '../../../build/default/generated/ohidl/default/calc';
const ret = add(1, 2);
```

**注意事项：**
1. temp文件夹只是一个模版文件夹，当熟悉Taihe注册规则和语法后，可手写业务模块注册和业务接口实现文件，不用手动拷贝。
2. 迁移过程中，如果需要在部分C++已经实现的情况下修改ohidl，则重新生成的业务接口实现文件，需要手动修改，例如在ohidl中新增了接口，需要手动拷贝temp文件夹中的接口声明，到已经实现了部分功能的接口实现文件中。

**方案3. AKI → Taihe**

适用场景：已使用AKI框架的项目。

| 项目 | 文档链接 |
|------|------|
| 迁移指南 | [AKI到Taihe迁移指南](https://gitcode.com/openharmony/docs/blob/OpenHarmony_feature_20250702/zh-cn/application-dev/napi/napi2ani/aki2taihe.md) |

### ArkTS静态代码并行化改造

在完成ArkTS动态到静态的语法迁移后，下一步是将代码进行并行化改造，充分利用多核CPU能力，提升应用性能。ArkTS静态类型提供了两种主要的并行化方案：**taskpool**（任务池）和**EAWorker**（独占线程任务执行器）。

**taskpool并行化改造**

taskpool是ArkTS静态类型提供的任务池机制，用于管理多个工作线程，自动分配任务到可用线程执行，适合执行大量短时任务。

核心特性：
- 自动线程管理：无需关心线程生命周期。
- 任务优先级：支持HIGH、MEDIUM、LOW、IDLE四种优先级。
任务组管理：支持将关联任务分组后批量执行，组内任务自动调度执行。
- 串行队列：支持需要顺序执行的任务队列。
- 内存共享：天然支持内存共享，无需使用@Sendable装饰器。

适用场景：
- 大量独立的计算任务。
- 数据处理、加密解密等CPU密集型操作。
- 需要并发执行的多任务场景。

**[taskpool参考文档](https://gitcode.com/openharmony/docs/blob/OpenHarmony_feature_20250702/zh-cn/application-dev/reference/native-lib/arkts-sta-taskpool.md)**

**EAWorker并行化改造**

EAWorker（Exclusive ArkTS Worker）是独占线程任务执行器，为开发者提供专属的工作线程，适合执行长时任务或需要独占资源的任务。

核心特性：
- 独占线程：每个EAWorker实例绑定一个专属线程。
- 线程复用：可复用同一EAWorker实例执行多个任务。
- 互操作支持：可选择开启与ArkTS-Dyn的互操作能力。
- 生命周期管理：需要手动调用join释放资源。

适用场景：
- 需要持续运行数小时或更长时间的任务（如数据同步、后台处理）。
- 需要独占线程资源的任务。
- 需要与ArkTS-Dyn代码互操作的场景。

**[EAWorker参考文档](https://gitcode.com/openharmony/docs/blob/OpenHarmony_feature_20250702/zh-cn/application-dev/reference/native-lib/eaworker_managed.md)**

### 功能验证

完成ArkTS静态化改造和并行化改造后，需要对改造后的代码进行全面的功能验证，确保：
- 静态化改造后的代码功能与原动态代码一致。
- 并行化改造后的执行结果正确。
- 动静态互操作正常工作。
- 异常处理机制有效。


## 性能验收

完成代码改造后，需要开启AOT编译并进行性能验证，确保静态化改造达到预期效果。

### 开启AOT

**手动开启AOT**

设备端手动触发AOT编译，在真机或模拟器上通过hdc命令手动触发应用AOT编译：

```bash
# 1. 连接设备
hdc shell

# 2. 关闭 SELinux（临时）
setenforce 0

# 3. 执行完整模式 AOT 编译
bm compile -m full "com.example.yourapp"

# 或使用 hdc 直接执行（无需进入 shell）
hdc shell setenforce 0 && bm compile -m full "com.example.yourapp"
```

**命令说明**

| 参数 | 说明 |
|:-----|:-----|
| `hdc shell` | 进入设备shell环境。 |
| `setenforce 0` | 临时关闭SELinux（编译需要）。 |
| `bm compile` | Bundle Manager编译命令。 |
| `-m full` | 完整编译模式，执行AOT。 |
| `"包名"` | 应用的包名。 |

**获取应用包名**

```bash
# 方法1：查看已安装应用列表
hdc shell bm list -a

# 方法2：从 app.json5 查看
{
  "bundleName": "com.example.yourapp"
}
```


### 性能验证

**关键性能指标**

运行时性能验证需要关注以下核心指标：

| 指标 | 测量方法 |
|:-----|:---------|
| 冷启动时间 | 从启动到首页完全渲染完成且能响应用户点击。 |
| 关键路径耗时 | 使用HiTrace测量。 |
| 内存占用 | DevEco Studio Profiler|
| CPU利用率 | Profiler性能分析。 |

**启动时间测量**

```typescript
'use static'

import hiTraceMeter from '@ohos.hiTraceMeter';

export class PerformanceMonitor {
  static measureLaunchTime(): void {
    // 应用启动时开始计时
    hiTraceMeter.startTrace("AppLaunch", 0x001);

    // 首页渲染完成
    hiTraceMeter.finishTrace("AppLaunch", 0x001);

    // 在 Trace 中查看 "AppLaunch" 耗时
  }
}
```

关键路径耗时测量，使用HiTrace标记改造前后的关键路径：

```typescript
'use static'

import hiTraceMeter from '@ohos.hiTraceMeter';

export function TaskB(): void {
  hiTraceMeter.startTrace("TaskB-Static", 0x002);

  try {
    // 业务逻辑
  } finally {
    hiTraceMeter.finishTrace("TaskB-Static", 0x002);
  }
}

// 对比指标
// 动态类型 TaskB 耗时: 7.9ms
// 静态类型 TaskB 耗时: 5.2ms (-34%)
```

**使用Profiling工具**

参考：[DevEco Profiler调优工具简介](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-profiler)

## ArkTS静态类型迁移改造案例

参考：[ArkTS静态类型迁移改造案例](./arkts-sta-migration-case.md "ArkTS静态类型迁移改造案例")

## ArkTS静态类型改造案例

参考：[ArkTS静态类型改造案例](./arkts-sta-transformation-case.md "ArkTS静态类型改造案例")

## ArkTS静态类型应用迁移改造常见问题

参考：[ArkTS静态类型应用迁移改造常见问题](./arkts-sta-migration-questions "ArkTS静态类型应用迁移改造常见问题")
