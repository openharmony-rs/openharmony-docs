# EfficiencyResourcesCpuLevel (System API)

Defines the CPU level of the efficiency resource.

**Since:** 23

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**System API:** This is a system API.

## SMALL_CPU

```TypeScript
SMALL_CPU = 0
```

The background task runs on small CPU cores. This level caters to lightweight background tasks with a relatively low CPU frequency.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**System API:** This is a system API.

## MEDIUM_CPU

```TypeScript
MEDIUM_CPU = 1
```

The background task can run on medium CPU cores at maximum. The system determines whether to run the task on small or medium CPU cores based on load. This level balances performance and energy efficiency, and is applicable to scenarios requiring complex task processing with a high CPU frequency.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**System API:** This is a system API.

## LARGE_CPU

```TypeScript
LARGE_CPU = 2
```

The background task can run on large CPU cores at maximum. The system determines whether to run the task on small, medium, or large CPU cores based on load. This level delivers ultimate performance, and is applicable to scenarios requiring heavy-load task processing with the highest CPU frequency.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**System API:** This is a system API.
