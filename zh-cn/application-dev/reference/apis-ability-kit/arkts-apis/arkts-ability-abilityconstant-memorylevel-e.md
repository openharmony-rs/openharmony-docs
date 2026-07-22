# MemoryLevel

整机可用内存级别，该类型为枚举，可配合UIAbility的[onMemoryLevel()](arkts-ability-app-ability-ability-ability-c.md#onmemorylevel)方法根据level执行不同内存级别的相应操作。
> **说明：**  
>  
> - 不同产品的触发条件可能存在差异。以12G内存的标准设备为例：  
> - 当整机可用内存下降至1700MB~1800MB时，会触发取值为0的onMemoryLevel回调，表示当前整机可用内存适中。  
> - 当整机可用内存下降至1600MB~1700MB时，会触发取值为1的onMemoryLevel回调，表示当前整机可用内存偏低。  
> - 当整机可用内存下降至1600MB以下时，会触发取值为2的onMemoryLevel回调，表示当前整机可用内存很低。  
>  
> - LRU：表示按应用最近使用顺序排序的链表。通常将最近使用的应用放在链表头部（位置靠前），将最不常用的应用放在链表尾部（位置靠后）。当内存不足时，位置靠后的应用将优先被清理。  
>  
> - 当LRU发生变化时，后台应用会根据处于应用使用排序链表（LRU）的位置，触发对应MemoryLevel级别(MEMORY_LEVEL_BACKGROUND_MODERATE、  
> MEMORY_LEVEL_BACKGROUND_LOW、MEMORY_LEVEL_BACKGROUND_CRITICAL)的onMemoryLevel回调。如果应用被冻结，则会在应用唤醒时收到对应的onMemoryLevel回  
> 调，因此不建议在此回调接口中做耗时操作。

**起始版本：** 9

<!--Device-AbilityConstant-export enum MemoryLevel--><!--Device-AbilityConstant-export enum MemoryLevel-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## MEMORY_LEVEL_MODERATE

```TypeScript
MEMORY_LEVEL_MODERATE = 0
```

表示整机可用内存适中。由于整机内存水线的不同，在不同产品上的表现可能存在差异，参见下方说明。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-MemoryLevel-MEMORY_LEVEL_MODERATE = 0--><!--Device-MemoryLevel-MEMORY_LEVEL_MODERATE = 0-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## MEMORY_LEVEL_LOW

```TypeScript
MEMORY_LEVEL_LOW = 1
```

表示整机可用内存低。由于整机内存水线的不同，在不同产品上的表现可能存在差异，参见下方说明。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-MemoryLevel-MEMORY_LEVEL_LOW = 1--><!--Device-MemoryLevel-MEMORY_LEVEL_LOW = 1-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## MEMORY_LEVEL_CRITICAL

```TypeScript
MEMORY_LEVEL_CRITICAL = 2
```

表示整机可用内存极低。由于整机内存水线的不同，在不同产品上的表现可能存在差异，参见下方说明。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-MemoryLevel-MEMORY_LEVEL_CRITICAL = 2--><!--Device-MemoryLevel-MEMORY_LEVEL_CRITICAL = 2-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## MEMORY_LEVEL_UI_HIDDEN

```TypeScript
MEMORY_LEVEL_UI_HIDDEN = 3
```

表示应用程序的所有UI界面已不可见，此时应该释放一些资源。该枚举仅对从前台切换到后台的应用生效。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-MemoryLevel-MEMORY_LEVEL_UI_HIDDEN = 3--><!--Device-MemoryLevel-MEMORY_LEVEL_UI_HIDDEN = 3-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## MEMORY_LEVEL_BACKGROUND_MODERATE

```TypeScript
MEMORY_LEVEL_BACKGROUND_MODERATE = 4
```

表示应用刚被使用过，即处于应用使用排序链表（LRU）的头部，暂时不会被系统清理。该枚举仅对后台应用生效。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-MemoryLevel-MEMORY_LEVEL_BACKGROUND_MODERATE = 4--><!--Device-MemoryLevel-MEMORY_LEVEL_BACKGROUND_MODERATE = 4-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## MEMORY_LEVEL_BACKGROUND_LOW

```TypeScript
MEMORY_LEVEL_BACKGROUND_LOW = 5
```

表示应用已被用户使用完一段时间，即处于应用使用排序链表（LRU）的中部，存在被系统清理的风险。该枚举仅对后台应用生效。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-MemoryLevel-MEMORY_LEVEL_BACKGROUND_LOW = 5--><!--Device-MemoryLevel-MEMORY_LEVEL_BACKGROUND_LOW = 5-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## MEMORY_LEVEL_BACKGROUND_CRITICAL

```TypeScript
MEMORY_LEVEL_BACKGROUND_CRITICAL = 6
```

表示应用长期未被使用，即处于应用使用排序链表（LRU）的尾部，会被系统优先清理。该枚举仅对后台应用生效。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-MemoryLevel-MEMORY_LEVEL_BACKGROUND_CRITICAL = 6--><!--Device-MemoryLevel-MEMORY_LEVEL_BACKGROUND_CRITICAL = 6-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

