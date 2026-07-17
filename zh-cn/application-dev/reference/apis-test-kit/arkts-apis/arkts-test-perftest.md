# @ohos.test.PerfTest

## 导入模块

```TypeScript
import { PerfTestStrategy, PerfMetric, PerfTest, PerfMeasureResult } from '@kit.TestKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [PerfTest](arkts-test-test-perftest-perftest-c.md) | PerfTest类为白盒性能测试框架的总入口，提供测试任务创建、测试代码段执行和数据采集、测量结果获取等能力。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [PerfMeasureResult](arkts-test-test-perftest-perfmeasureresult-i.md) | 性能指标对应测量结果数据。 |
| [PerfTestStrategy](arkts-test-test-perftest-perfteststrategy-i.md) | 性能测试执行策略。&gt; **说明** &gt; &gt; 属性actionCode和resetCode的入参类型为回调函数"Callback\&lt;boolean&gt;"。在代码段中需要主动调用此回调函数，通知框架代码段执行完成，否则会导致代码段执行超时。 &gt; &gt; 其中，回调函数的参数为boolean类型，true代表代码段执行符合预期，false代表代码段执行不符合预期。[代码示例](arkts-test-test-perftest-perftest-c.md#create-1)。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [PerfMetric](arkts-test-test-perftest-perfmetric-e.md) | 框架支持采集的性能指标。&gt; **说明** &gt; &gt; &gt; - 测试过程中，代码段执行开始前和代码段执行结束后，会分别采集指定应用进程的CPU和内存数据，因此测试过程中需要保证被测应用进程一直存在。 &gt; &gt; &gt; - 应用启动时延数据受系统打点上报限制，开始时间为点击事件上报时间点，响应时延结束时间为点击后系统响应首帧的上屏时间点（首帧显示在屏幕上的时间点），完成时延结束时间为应用启动后的首帧上屏时间点，与端到端用户感知时延存在差异。 &gt; &gt; - 应用启动时延数据采集支持的场景：桌面点击应用图标启动、Dock栏点击应用图标启动、应用中心点击应用图标启动。 &gt; &gt; - 单次测试期间，仅第一次指定应用启动的时延数据会被采集。 &gt; &gt; &gt; - 页面切换时延计算受系统打点上报限制，开始时间为点击事件上报时间点，完成时延结束时间为页面切换后的首帧上屏时间点，与端到端用户感知时延存在差异。 &gt; &gt; - 页面切换时延数据采集支持的场景：Router、Navigation控件内的页面切换。 &gt; &gt; - 单次测试期间，仅指定应用内第一次页面切换的时延数据会被采集。 &gt; &gt; &gt; - 列表滑动帧率：指的是在列表滑动时，屏幕每秒钟渲染更新帧的次数。 &gt; &gt; - 列表滑动帧率数据采集支持的场景：ArkUI子系统List、Grid、scroll、waterflow滚动控件列表的滑动。 &gt; &gt; - 单次测试期间，仅指定应用内第一次列表滑动的帧率数据会被采集。 |

