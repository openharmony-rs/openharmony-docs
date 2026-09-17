# startTrace

## Modules to Import

```TypeScript
```

## startTrace

```TypeScript
function startTrace(name: string, taskId: number, expectedTime?: number): void
```

Marks the start of a timeslice trace task.

> **NOTE:** 
> 
> If multiple trace tasks with the same name need to be performed at the same time or a trace task needs to be
> performed multiple times concurrently, different task IDs must be specified in **startTrace**. If the trace tasks
> with the same name are not performed at the same time, the same task ID can be used. For details, see the
> bytrace.finishTrace example.

**Since:** 7

**Deprecated since:** 8

**Substitutes:** startTrace

**System capability:** SystemCapability.HiviewDFX.HiTrace

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of a timeslice trace task. |
| taskId | number | Yes | ID of a timeslice trace task. |
| expectedTime | number | No | Expected duration of the trace, in ms. This parameter is optional and is left blank by default. |

**Examples**

```TypeScript
bytrace.startTrace("myTestFunc", 1);
bytrace.startTrace("myTestFunc", 1, 5); // The expected duration of the trace is 5 ms.
```
