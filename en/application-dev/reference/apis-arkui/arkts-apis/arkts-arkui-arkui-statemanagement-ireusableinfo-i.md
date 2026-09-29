# IReusableInfo

```TypeScript
export declare interface IReusableInfo
```

The **IReusableInfo** API provides information about the current number and maximum number of reusable components managed by the reuse pool.

**Since:** 26.0.0

<!--Device-unnamed-export declare interface IReusableInfo--><!--Device-unnamed-export declare interface IReusableInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IReusableInfo, StorageDefaultCreator, TypeConstructorWithArgs, PersistenceErrorCallback, TypeConstructor, TypeDecorator, MonitorCallback, MonitorOptions, GetterCallback, SetterCallback, ObservedResult, DecoratorInfo, ElementInfo } from '@kit.ArkUI';
```

## count

```TypeScript
readonly count: number
```

Number of components currently recycled in the pool. If **reuseId** is specified, **count** indicates the number of components with the reuse ID.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-IReusableInfo-readonly count: number--><!--Device-IReusableInfo-readonly count: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxCount

```TypeScript
maxCount: number
```

Maximum number of components that can be recycled in the pool. If **reuseId** is specified, **maxCount** indicates the number of components with the reuse ID. Setting **maxCount** to a value smaller than that of **count** will cause the framework to asynchronously clear redundant components. During a delay, the value of **count** may temporarily exceed that of **maxCount**. Default value: **100**; maximum value: **200**; minimum value: **0**. If the assigned value is out of range, the value close to the maximum or minimum value is used. If the assigned value is a decimal, it is rounded down.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-IReusableInfo-maxCount: number--><!--Device-IReusableInfo-maxCount: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## reuseId

```TypeScript
readonly reuseId?: string
```

Reuse ID specified when a component is recycled. If the component is not recycled using **reuseId**, **undefined** is used.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-IReusableInfo-readonly reuseId?: string--><!--Device-IReusableInfo-readonly reuseId?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
