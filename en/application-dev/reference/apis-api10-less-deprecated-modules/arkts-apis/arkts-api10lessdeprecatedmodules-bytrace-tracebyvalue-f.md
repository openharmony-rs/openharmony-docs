# traceByValue

## Modules to Import

```TypeScript
```

## traceByValue

```TypeScript
function traceByValue(name: string, count: number): void
```

Defines a numeric variable that indicates the number of timeslice trace tasks.

**Since:** 7

**Deprecated since:** 8

**Substitutes:** traceByValue

**System capability:** SystemCapability.HiviewDFX.HiTrace

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the numeric variable. |
| count | number | Yes | Value of the numeric variable. |

**Examples**

```TypeScript
let traceCount = 3;
bytrace.traceByValue("myTestCount", traceCount);
traceCount = 4;
bytrace.traceByValue("myTestCount", traceCount);
// Service flow...
```
