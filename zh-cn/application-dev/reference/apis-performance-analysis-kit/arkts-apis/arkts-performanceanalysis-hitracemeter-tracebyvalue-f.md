# traceByValue

## 导入模块

```TypeScript
import { hiTraceMeter } from '@kit.PerformanceAnalysisKit';
```

## traceByValue

```TypeScript
function traceByValue(name: string, count: long): void
```

用来标记一个跟踪的整数变量，该变量的数值会不断变化。适用于需要实时监控数值变化（如网络请求次数、缓存命中率、内存占用等）的场景，能够帮助开发者 快速发现异常波动，分析数据趋势。 从API version 19开始，建议使用 [traceByValue](#tracebyvalue)接口，以便分级控 制跟踪输出。

**起始版本：** 23

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-hiTraceMeter-function traceByValue(name: string, count: long): void--><!--Device-hiTraceMeter-function traceByValue(name: string, count: long): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 要跟踪的整数变量名称。 由于单条trace记录的总长度限制为512Byte，超过的部分将会被截断，建议该参数的长度不要超过420Byte。 |
| count | long | 是 | 整数变量的值。 |

**示例**

ArkTS-Dyn示例：

```TypeScript
let traceCount: number = 3;
hiTraceMeter.traceByValue("myTestCount", traceCount);  // 使用trace打点记录myTestCount的值。
traceCount = 4;
hiTraceMeter.traceByValue("myTestCount", traceCount);  // 当myTestCount发生变化时，记录新值。
// 业务流程......
```

ArkTS-Sta示例：

```TypeScript
let traceCount: long = 3;  // 定义要跟踪的整数变量初始值
hiTraceMeter.traceByValue("myTestCount", traceCount);  // 使用trace打点记录myTestCount的值。
traceCount = 4;
hiTraceMeter.traceByValue("myTestCount", traceCount);  // 当myTestCount发生变化时，记录新值。
// 业务流程......
```


## traceByValue

```TypeScript
function traceByValue(level: HiTraceOutputLevel, name: string, count: long): void
```

整数跟踪事件，分级控制跟踪输出。用来标记一个预先定义需要跟踪的整数变量名及整数值。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-hiTraceMeter-function traceByValue(level: HiTraceOutputLevel, name: string, count: long): void--><!--Device-hiTraceMeter-function traceByValue(level: HiTraceOutputLevel, name: string, count: long): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| level | [HiTraceOutputLevel](arkts-performanceanalysis-hitracemeter-hitraceoutputlevel-e.md) | 是 | 跟踪输出级别。 |
| name | string | 是 | 要跟踪的整数变量名称。 由于单条trace记录的总长度限制为512Byte，超出部分将被截断，建议该参数的长度不要超过420Byte。 |
| count | long | 是 | 整数变量的值。 |

**示例**

ArkTS-Dyn示例：

```TypeScript
const COMMERCIAL = hiTraceMeter.HiTraceOutputLevel.COMMERCIAL;
let traceCount: number = 3;
hiTraceMeter.traceByValue(COMMERCIAL, "myTestCount", traceCount);
traceCount = 4;
hiTraceMeter.traceByValue(COMMERCIAL, "myTestCount", traceCount);
// 业务流程......
```

ArkTS-Sta示例：

```TypeScript
const COMMERCIAL = hiTraceMeter.HiTraceOutputLevel.COMMERCIAL;
let traceCount: long = 3;
hiTraceMeter.traceByValue(COMMERCIAL, "myTestCount", traceCount);
traceCount = 4;
hiTraceMeter.traceByValue(COMMERCIAL, "myTestCount", traceCount);
// 业务流程......
```

