# traceByValue

## traceByValue

```TypeScript
function traceByValue(name: string, count: number): void
```

标记预追踪耗时任务的数值变量，该变量的数值会不断变化。traceByValue可独立使用，用于记录某个数值变量的变化轨迹。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 8

**替代接口：** ohos.hiTraceMeter.traceByValue

<!--Device-bytrace-function traceByValue(name: string, count: number): void--><!--Device-bytrace-function traceByValue(name: string, count: number): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 数值变量的名称。 |
| count | number | 是 | 数值变量的值。 |

**示例：**

```TypeScript
let traceCount = 3;
bytrace.traceByValue("myTestCount", traceCount);
traceCount = 4;
bytrace.traceByValue("myTestCount", traceCount);
// 业务流程......
```

