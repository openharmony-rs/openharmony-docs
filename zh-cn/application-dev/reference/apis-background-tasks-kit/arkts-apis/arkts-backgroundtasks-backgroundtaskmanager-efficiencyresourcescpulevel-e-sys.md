# EfficiencyResourcesCpuLevel（系统接口）

能效资源CPU级别。

**起始版本：** 23

<!--Device-backgroundTaskManager-export enum EfficiencyResourcesCpuLevel--><!--Device-backgroundTaskManager-export enum EfficiencyResourcesCpuLevel-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**系统接口：** 此接口为系统接口。

## SMALL_CPU

```TypeScript
SMALL_CPU = 0
```

表示运行在小核，用于处理轻量级后台任务，CPU频点较低。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EfficiencyResourcesCpuLevel-SMALL_CPU = 0--><!--Device-EfficiencyResourcesCpuLevel-SMALL_CPU = 0-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**系统接口：** 此接口为系统接口。

## MEDIUM_CPU

```TypeScript
MEDIUM_CPU = 1
```

表示最高可以运行在中核，系统基于负载决策运行在小核或中核。平衡性能与能效，用于需要处理复杂任务的场景，CPU频点高。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EfficiencyResourcesCpuLevel-MEDIUM_CPU = 1--><!--Device-EfficiencyResourcesCpuLevel-MEDIUM_CPU = 1-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**系统接口：** 此接口为系统接口。

## LARGE_CPU

```TypeScript
LARGE_CPU = 2
```

表示最高可以运行在大核，系统基于负载决策运行在小核、中核或大核。 极致性能，用于应对重载任务的场景，CPU频点最高。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EfficiencyResourcesCpuLevel-LARGE_CPU = 2--><!--Device-EfficiencyResourcesCpuLevel-LARGE_CPU = 2-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**系统接口：** 此接口为系统接口。

