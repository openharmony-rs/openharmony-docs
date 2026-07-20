# PerfTestStrategy

性能测试执行策略。

> **说明**  
>  
> 属性actionCode和resetCode的入参类型为回调函数"Callback\<boolean>"。在代码段中需要主动调用此回调函数，通知框架代码段执行完成，否则会导致代码段执行超时。  
> > 其中，回调函数的参数为boolean类型，true代表代码段执行符合预期，false代表代码段执行不符合预期。[代码示例](arkts-test-test-perftest-perftest-c.md#create-1)。

**起始版本：** 20

<!--Device-unnamed-declare interface PerfTestStrategy--><!--Device-unnamed-declare interface PerfTestStrategy-End-->

**系统能力：** SystemCapability.Test.PerfTest

## 导入模块

```TypeScript
import { PerfTestStrategy, PerfMetric, PerfTest, PerfMeasureResult } from '@kit.TestKit';
```

## actionCode

```TypeScript
actionCode: Callback<Callback<boolean>>
```

测试代码段。

**类型：** Callback&lt;Callback&lt;boolean&gt;&gt;

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PerfTestStrategy-actionCode: Callback<Callback<boolean>>--><!--Device-PerfTestStrategy-actionCode: Callback<Callback<boolean>>-End-->

**系统能力：** SystemCapability.Test.PerfTest

## bundleName

```TypeScript
bundleName?: string
```

被测应用包名。默认为""，框架运行时测试当前测试应用的性能数据。

**类型：** string

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PerfTestStrategy-bundleName?: string--><!--Device-PerfTestStrategy-bundleName?: string-End-->

**系统能力：** SystemCapability.Test.PerfTest

## iterations

```TypeScript
iterations?: number
```

测试迭代执行次数，默认值为5。

**类型：** number

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PerfTestStrategy-iterations?: int--><!--Device-PerfTestStrategy-iterations?: int-End-->

**系统能力：** SystemCapability.Test.PerfTest

## metrics

```TypeScript
metrics: Array<PerfMetric>
```

被测性能指标列表。

**类型：** Array&lt;PerfMetric&gt;

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PerfTestStrategy-metrics: Array<PerfMetric>--><!--Device-PerfTestStrategy-metrics: Array<PerfMetric>-End-->

**系统能力：** SystemCapability.Test.PerfTest

## resetCode

```TypeScript
resetCode?: Callback<Callback<boolean>>
```

测试结束环境重置代码段。默认为空，框架运行时不执行此代码段。

**类型：** Callback&lt;Callback&lt;boolean&gt;&gt;

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PerfTestStrategy-resetCode?: Callback<Callback<boolean>>--><!--Device-PerfTestStrategy-resetCode?: Callback<Callback<boolean>>-End-->

**系统能力：** SystemCapability.Test.PerfTest

## timeout

```TypeScript
timeout?: number
```

单次代码段（actionCode/resetCode）执行的超时时间，默认值为10000ms。

**类型：** number

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PerfTestStrategy-timeout?: int--><!--Device-PerfTestStrategy-timeout?: int-End-->

**系统能力：** SystemCapability.Test.PerfTest

