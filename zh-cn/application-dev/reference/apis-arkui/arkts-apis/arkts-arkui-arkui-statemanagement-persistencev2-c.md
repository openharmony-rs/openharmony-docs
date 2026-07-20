# PersistenceV2

继承自[AppStorageV2](arkts-arkui-arkui-statemanagement-appstoragev2-c.md)，PersistenceV2具体UI使用说明，详见[PersistenceV2(持久化存储UI状态)](docroot://ui/state-management/arkts-new-persistencev2.md)。

**继承/实现关系：** PersistenceV2 extends [AppStorageV2](arkts-arkui-arkui-statemanagement-appstoragev2-c.md)

**起始版本：** 12

<!--Device-unnamed-export declare class PersistenceV2 extends AppStorageV2--><!--Device-unnamed-export declare class PersistenceV2 extends AppStorageV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { Binding, ComponentReuse, CustomComponentLifecycleState, ComponentInactive, PersistenceV2, ComponentDisappear, MutableBinding, CustomComponentLifecycleObserver, AppStorageV2, Type, ConnectOptionsCollections, CollectionType, CustomComponentContext, IReusePool, ConnectOptions, UIUtils, ComponentActive, CustomComponentLifecycle, ComponentInit, ComponentAppear, ComponentBuilt, ComponentRecycle, IReusableInfo } from '@kit.ArkUI';
```

<a id="globalconnect"></a>
## globalConnect

```TypeScript
static globalConnect<T extends object>(
    type: ConnectOptions<T>
  ): T | undefined
```

将键值对数据储存在应用磁盘中。如果给定的key已经存在于[PersistenceV2](docroot://ui/state-management/arkts-new-persistencev2.md)中，返回对应的值；否则，会通过获取默认值的构造器构造默认值，并返回。如果globalConnect的是[\@ObservedV2](docroot://ui/state-management/arkts-new-observedV2-and-trace.md)对象，该对象[\@Trace](docroot://ui/state-management/arkts-new-observedV2-and-trace.md)属性的变化，会触发整个关联对象的自动刷新；非\@Trace属性变化则不会，如有必要，可调用[PersistenceV2.save](arkts-arkui-arkui-statemanagement-persistencev2-c.md#save-1)接口手动存储。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PersistenceV2-static globalConnect<T extends object>(
    type: ConnectOptions<T>
  ): T | undefined--><!--Device-PersistenceV2-static globalConnect<T extends object>(
    type: ConnectOptions<T>
  ): T | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [ConnectOptions](../../apis-ability-kit/arkts-apis/arkts-ability-ability-connectoptions-t.md)&lt;T&gt; | 是 | 传入的connect参数，详细说明见ConnectOptions参数说明。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Returns the data if creation or acquisition is successful; otherwise, returns **undefined**. |

<a id="globalconnect-1"></a>
## globalConnect

```TypeScript
static globalConnect<T extends CollectionType<S>, S extends object>(
    type: ConnectOptionsCollections<T, S> | ConnectOptions<T>
  ): T | undefined
```

将键值对数据储存在应用磁盘中。支持集合类型[`Array`，`Map`，`Set`，`Date`，`collections.Array`, `collections.Map`, `collections.Set`类型的持久化](docroot://ui/state-management/arkts-new-persistencev2.md#globalconnect支持集合的类型)。注意在持久化`Array<ClassA>`类型的数据时，需要调用[`makeObserved`](arkts-arkui-arkui-statemanagement-uiutils-c.md#makeobserved-1)使返回的对象被观察到。不支持多个嵌套集合，例如不支持`Array<Array<ClassA>>`的持久化。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PersistenceV2-static globalConnect<T extends CollectionType<S>, S extends object>(
    type: ConnectOptionsCollections<T, S> | ConnectOptions<T>
  ): T | undefined--><!--Device-PersistenceV2-static globalConnect<T extends CollectionType<S>, S extends object>(
    type: ConnectOptionsCollections<T, S> | ConnectOptions<T>
  ): T | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [ConnectOptionsCollections](arkts-arkui-arkui-statemanagement-connectoptionscollections-c.md)&lt;T, S&gt; \| ConnectOptions&lt;T&gt; | 是 | 传入的globalConnect参数，详细说明见ConnectOptions和ConnectOptionsCollections参数说明。<br/>当开发者在ConnectOptionsCollections中提供默认defaultSubCreator时，则需要同时提供默认创建器defaultCreator，如果不提供，会导致持久化失败。且集合项类型S必须与defaultSubCreator的返回类型相同。如果返回类型不一致，编译会报错。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Returns the data if creation or acquisition is successful; otherwise, returns **undefined**. |

<a id="notifyonerror"></a>
## notifyOnError

```TypeScript
static notifyOnError(callback: PersistenceErrorCallback | undefined): void
```

在持久化失败时调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PersistenceV2-static notifyOnError(callback: PersistenceErrorCallback | undefined): void--><!--Device-PersistenceV2-static notifyOnError(callback: PersistenceErrorCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [PersistenceErrorCallback](arkts-arkui-persistenceerrorcallback-t.md) \| undefined | 是 | 持久化失败时调用。 |

<a id="save"></a>
## save

```TypeScript
static save<T>(keyOrType: string | TypeConstructorWithArgs<T>): void
```

将指定的键值对数据持久化一次。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PersistenceV2-static save<T>(keyOrType: string | TypeConstructorWithArgs<T>): void--><!--Device-PersistenceV2-static save<T>(keyOrType: string | TypeConstructorWithArgs<T>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyOrType | string \| TypeConstructorWithArgs&lt;T&gt; | 是 | 需要持久化的key；如果指定的是type类型，持久化的key为type的name。 |

