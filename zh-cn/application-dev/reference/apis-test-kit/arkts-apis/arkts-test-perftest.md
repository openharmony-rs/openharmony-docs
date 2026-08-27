# @ohos.test.PerfTest

PerfTest提供白盒性能测试能力，供开发者在测试场景使用。支持对指定代码段或指定场景自动化执行测试，
 并采集耗时、CPU、内存、时延、帧率等性能数据。
 > **说明：**
 >
 > - 本模块首批接口从API version 20开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
 >
 > - 本模块接口在<!--RP1-->[单元测试框架](../../../application-test/unittest-guidelines.md)<!--RP1End-->中使用。
 >
 > - 本模块接口不支持并发调用。
 >
 > - 本模块接口适用于手机、平板、PC/2in1、智慧屏、车机。


## 导入模块

```TypeScript
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [PerfTest](arkts-test-test-perftest-perftest-c.md) | PerfTest类为白盒性能测试框架的总入口。 提供测试任务创建、测试代码段执行和数据采集、测量结果获取等能力。 通过[create](arkts-test-test-perftest-perftest-c.md#create)创建实例。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [PerfMeasureResult](arkts-test-test-perftest-perfmeasureresult-i.md) | 性能指标对应测量结果数据。 |
| [PerfTestStrategy](arkts-test-test-perftest-perfteststrategy-i.md) | 性能测试执行策略。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [PerfMetric](arkts-test-test-perftest-perfmetric-e.md) | 框架支持采集的性能指标。 |
