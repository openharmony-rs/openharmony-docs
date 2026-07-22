# ResourceUsageObserver

```TypeScript
export type ResourceUsageObserver = (resourceType: ResourceType, resourceSize: number, detailInfo?: Record<string, number>) => void
```

定义应用资源使用情况的观察者回调函数，作为[errorManager.setDefaultResourceUsageObserver](arkts-ability-errormanager-setdefaultresourceusageobserver-f.md#setdefaultresourceusageobserver)的入参，用于监听各类资源占用变化，并支持应用执行自定义资源处理逻辑。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-errorManager-export type ResourceUsageObserver = (resourceType: ResourceType, resourceSize: long, detailInfo?: Record<string, long>) => void--><!--Device-errorManager-export type ResourceUsageObserver = (resourceType: ResourceType, resourceSize: long, detailInfo?: Record<string, long>) => void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resourceType | [ResourceType](arkts-ability-errormanager-resourcetype-e.md) | 是 | 表示应用资源超基线的类型。  |
| resourceSize | number | 是 | 表示应用资源超基线的资源使用量。  |
| detailInfo | Record&lt;string, number&gt; | 否 | 表示应用资源超基线资源使用量的细分项字典。<br>**说明**：仅在resourceType为PSS_MEMORY时存在，为其他类型或缺 省时为空；<br>key为小写内存类型，value为对应细分项资源大小；<br>细分项的key包含arkts、native、ion、gpu、ashmem和other。 第二个值必须大于**0**。单位：KB。  |

