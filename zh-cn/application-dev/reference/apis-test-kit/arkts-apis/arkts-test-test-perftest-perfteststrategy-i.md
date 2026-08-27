# PerfTestStrategy

性能测试执行策略。

> **说明：**
> 
> 属性actionCode和resetCode的入参类型为回调函数"Callback\&lt;boolean&gt;"。
> 在代码段中需要主动调用此回调函数，通知框架代码段执行完成，否则会导致代码段执行超时。
> 其中，回调函数的参数为boolean类型，true代表代码段执行符合预期，false代表代码段执行不符合预期。
> [代码示例](arkts-test-test-perftest-perftest-c.md#create)。

**起始版本：** 20

**系统能力：** SystemCapability.Test.PerfTest

## 导入模块

```TypeScript
```

## actionCode

```TypeScript
actionCode: Callback<Callback<boolean>>
```

测试代码段。入参为回调函数，需在代码段中主动调用以通知框架执行完成，否则会导致执行超时。

**类型：** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt;&gt;

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.PerfTest

## bundleName

```TypeScript
bundleName?: string
```

被测应用包名，格式要求与应用的bundleName一致。当需要测试非当前应用的性能数据时，传入目标应用的包名。 默认为""，框架在执行测试时测试当前应用的性能数据。

**类型：** string

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.PerfTest

## iterations

```TypeScript
iterations?: number
```

测试迭代执行次数，取值范围为大于0的整数，默认值为5。超出范围时抛出异常。

**类型：** number

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.PerfTest

## metrics

```TypeScript
metrics: Array<PerfMetric>
```

被测性能指标列表，列表为空则不采集任何性能指标数据。

**类型：** Array&lt;[PerfMetric](arkts-test-test-perftest-perfmetric-e.md)&gt;

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.PerfTest

## resetCode

```TypeScript
resetCode?: Callback<Callback<boolean>>
```

测试结束环境重置代码段。 当测试代码段修改了全局状态（如全局变量、配置等）需要在每轮测试后重置时传入此参数。 默认为空，框架在执行测试时不执行此代码段。 入参为回调函数，需在代码段中主动调用以通知框架执行完成，否则会导致执行超时。

**类型：** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt;&gt;

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.PerfTest

## timeout

```TypeScript
timeout?: number
```

单次代码段（actionCode/resetCode）执行的超时时间，取值范围为大于0的整数，单位：ms，默认值为10000ms。 当测试代码段执行耗时较长时，可适当增大此值以避免超时，超时后将触发异常，并终止测试执行。

**类型：** number

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.PerfTest
