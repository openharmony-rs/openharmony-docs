# ResourceUsageObserver

```TypeScript
export type ResourceUsageObserver = (resourceType: ResourceType, resourceSize: long, detailInfo?: Record<string, long>) => void
```

定义应用资源使用情况的观察者回调函数，作为 [errorManager.setDefaultResourceUsageObserver]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的入参，用于监听各类资源占用变化， 并支持应用执行自定义资源处理逻辑。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-errorManager-export type ResourceUsageObserver = (resourceType: ResourceType, resourceSize: long, detailInfo?: Record<string, long>) => void--><!--Device-errorManager-export type ResourceUsageObserver = (resourceType: ResourceType, resourceSize: long, detailInfo?: Record<string, long>) => void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resourceType | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 表示应用资源超基线的类型。  |
| resourceSize | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：long | 是 | 表示应用资源超基线的资源使用量。  |
| detailInfo | ArkTS-Dyn: Record&lt;string, number&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Record&lt;string, long&gt; | 否 | 表示应用资源超基线资源使用量的细分项字典。\_\_\_HTML\_TAG\_USD\_0\_\_\_**说明**：仅在resourceType为PSS\_MEMORY时存在，为其他类型或缺 省时为空；\_\_\_HTML\_TAG\_USD\_1\_\_\_key为小写内存类型，value为对应细分项资源大小；\_\_\_HTML\_TAG\_USD\_2\_\_\_细分项的key包含arkts、native、ion、gpu、ashmem和other。 第二个值必须大于**0**。单位：KB。  |

