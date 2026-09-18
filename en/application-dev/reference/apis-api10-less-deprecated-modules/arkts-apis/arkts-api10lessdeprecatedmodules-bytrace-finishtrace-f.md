# finishTrace

## Modules to Import

```TypeScript
```

## finishTrace

```TypeScript
function finishTrace(name: string, taskId: number): void
```

Marks the end of a timeslice trace task.

> **NOTE:** 
> 
> To stop a trace task, the values of name and task ID in **finishTrace** must be the same as those in
> **startTrace**.

**Since:** 7

**Deprecated since:** 8

**Substitutes:** finishTrace

**System capability:** SystemCapability.HiviewDFX.HiTrace

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of a timeslice trace task. |
| taskId | number | Yes | ID of a timeslice trace task. |

**Examples**

```TypeScript
bytrace.finishTrace("myTestFunc", 1);
```

```TypeScript
// Start trace tasks with the same name concurrently.
bytrace.startTrace("myTestFunc", 1);
// Service flow...
bytrace.startTrace("myTestFunc", 2);  // The second trace task starts while the first task is still running. The first and second tasks have the same name but different task IDs.
// Service flow...
bytrace.finishTrace("myTestFunc", 1);
// Service flow...
bytrace.finishTrace("myTestFunc", 2);
```

```TypeScript
// Start trace tasks with the same name in serial mode.
bytrace.startTrace("myTestFunc", 1);
// Service flow...
bytrace.finishTrace("myTestFunc", 1);  // The first trace task ends.
// Service flow...
bytrace.startTrace("myTestFunc", 1);   // The second trace task starts after the first task ends. The two tasks have the same name and task ID.
// Service flow...
bytrace.finishTrace("myTestFunc", 1);
```
