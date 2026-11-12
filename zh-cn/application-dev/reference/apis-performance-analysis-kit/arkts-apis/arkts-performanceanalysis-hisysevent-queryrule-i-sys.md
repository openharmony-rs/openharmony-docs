# QueryRule（系统接口）

```TypeScript
interface QueryRule
```

系统事件查询规则对象接口。

**起始版本：** 9

<!--Device-hiSysEvent-interface QueryRule--><!--Device-hiSysEvent-interface QueryRule-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
```

## condition

```TypeScript
condition?: string
```

事件的额外参数条件，格式：{"version":"V1","condition":{"and":[{"param":"参数","op":"操作符","value":"比较值"}]}}。

参数：指定事件参数的键值，类型为string。

操作符支持：=、!=、&lt;、<=、>和&gt;=。

value：比较值，类型可为string、number等。

支持在“and”数组中配置多个条件，查询结果取交集。建议避免配置过多复杂条件以优化查询性能。默认不传该参数时不进行额外参数过滤。

**类型：** string

**起始版本：** 10

<!--Device-QueryRule-condition?: string--><!--Device-QueryRule-condition?: string-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## domain

```TypeScript
domain: string
```

查询包含的事件领域。

**类型：** string

**起始版本：** 9

<!--Device-QueryRule-domain: string--><!--Device-QueryRule-domain: string-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## names

```TypeScript
names: string[]
```

查询所包含的多个事件名称，每个查询规则对象包含多个系统事件名称。

**类型：** string[]

**起始版本：** 9

<!--Device-QueryRule-names: string[]--><!--Device-QueryRule-names: string[]-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。
