# PersistenceV2

继承自[AppStorageV2](arkts-arkui-arkui-statemanagement-appstoragev2-c.md#AppStorageV2)，PersistenceV2提供UI状态的持久化存储能力，支持将应用状态数据持久化到磁盘，在应用重启后恢复数据，适用于需要保留UI状态数据的场景。具体UI使用说 明，详见[PersistenceV2(持久化存储UI状态)](../../../ui/state-management/arkts-new-persistencev2.md)。

**继承/实现关系：** PersistenceV2 extends [AppStorageV2](arkts-arkui-arkui-statemanagement-appstoragev2-c.md#AppStorageV2)

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-unnamed-export declare class PersistenceV2--><!--Device-unnamed-export declare class PersistenceV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## globalConnect

```TypeScript
static globalConnect<T extends object>(
    type: ConnectOptions<T>
  ): T | undefined
```

将键值对数据存储在应用磁盘中。如果给定的key已经存在于[PersistenceV2](../../../ui/state-management/arkts-new-persistencev2.md)中，返回对应的值；否则，会通 过获取默认值的构造器构造默认值，并返回。如果通过globalConnect连接的对象是 [\@ObservedV2](../../../ui/state-management/arkts-new-observedV2-and-trace.md)对象，该对象 [\@Trace](../../../ui/state-management/arkts-new-observedV2-and-trace.md)属性的变化，会触发整个关联对象的自动刷新；非\@Trace属性变化则不会自动持久 化，如需持久化非\@Trace属性的变化，可调用[PersistenceV2.save](#save)接口手动存储。 > **说明：** > > 1、若未指定key，使用默认构造器defaultCreator返回数据的类名作为key存入PersistenceV2中。 > > 2、确保数据已经存储在PersistenceV2中，可省略默认构造器，获取存储的数据；否则必须指定默认构造器，不指定将导致应用异常。 > > 3、同一个key，globalConnect不同类型的数据会导致应用异常，应用需要确保类型匹配。 > > 4、key建议使用有意义的值，可由字母、数字、下划线组成，长度不超过255个字符，使用非法字符或空字符的行为是未定义的。 > > 5、关联[\@Observed](../../../ui/state-management/arkts-observed-and-objectlink.md)对象时，因为该类型的name属性未定义， > 需要指定key或者自定义name属性。 > > 6、数据的存储路径为应用级别，不同module使用相同的key和相同的加密分区进行globalConnect，存储的数据副本应用仅有一份。 > > 7、globalConnect使用同一个key但设置了不同的加密级别，数据为第一个使用globalConnect的加密级别，并且PersistenceV2中的数据也会存入最先使用key的加密级别。 > > 8、connect和globalConnect不建议混用，因为数据副本路径不同，如果混用，则key不可以一样，否则会crash。 > > 9、EL5加密要想生效，需要开发者在module.json中配置字段ohos.permission.PROTECT_SCREEN_LOCK_DATA， > 使用说明见[声明权限](../../../security/AccessToken/declare-permissions.md)。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PersistenceV2-static globalConnect<T extends object>(    type: ConnectOptions<T>  ): T | undefined--><!--Device-PersistenceV2-static globalConnect<T extends object>(    type: ConnectOptions<T>  ): T | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [ConnectOptions](arkts-arkui-arkui-statemanagement-connectoptions-c.md)&lt;T&gt; | 是 | globalConnect的配置参数，包含指定的类型、key、默认构造器和加密级别等配置项，详细说明见ConnectOptions参数说明。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 创建或获取数据成功时，返回数据；否则返回undefined。 |

## globalConnect

```TypeScript
static globalConnect<T extends CollectionType<S>, S extends object>(
    type: ConnectOptionsCollections<T, S> | ConnectOptions<T>
  ): T | undefined
```

将键值对数据存储在应用磁盘中。支持集合类型 [`Array`，`Map`，`Set`，`collections.Array`，`collections.Map`，`collections.Set`类型的持久化](../../../ui/state-management/arkts-new-persistencev2.md#globalconnect支持集合的类型)。 注意在持久化`Array&lt;ClassA&gt;`类型的数据时，需要调用[`makeObserved`](arkts-arkui-arkui-statemanagement-uiutils-c.md#makeObserved)使返回的对象被观察到。不支持多个嵌套集合，例如不支持 `Array&lt;Array<ClassA>&gt;&lt;ClassA&gt;>`的持久化。 > **说明：** > > 1、若未指定key，使用默认构造器defaultCreator返回数据的类名作为key存入PersistenceV2中。 > > 2、key建议使用有意义的值，可由字母、数字、下划线组成，长度不超过255，使用非法字符或空字符的行为是未定义的。 > > 3、connect和globalConnect不建议混用，因为数据副本路径不同，如果混用，则key不可以一样，否则会crash。 > > 其他通用条件详见globalConnect&lt;sup&gt;18+&lt;/sup&gt;的说明。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PersistenceV2-static globalConnect<T extends CollectionType<S>, S extends object>(    type: ConnectOptionsCollections<T, S> | ConnectOptions<T>  ): T | undefined--><!--Device-PersistenceV2-static globalConnect<T extends CollectionType<S>, S extends object>(    type: ConnectOptionsCollections<T, S> | ConnectOptions<T>  ): T | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [ConnectOptionsCollections](arkts-arkui-arkui-statemanagement-connectoptionscollections-c.md)&lt;T, S&gt; \| [ConnectOptions](arkts-arkui-arkui-statemanagement-connectoptions-c.md)&lt;T&gt; | 是 | globalConnect的配置参数，支持ConnectOptions和 ConnectOptionsCollections两种类型，包含类型、key、默认构造器、集合项构造器等配置项，详细说明见ConnectOptions和ConnectOptionsCollections参数说明。 &lt;br&gt;当开发者在ConnectOptionsCollections中提供默认defaultSubCreator时，则需要同时提供默认创建器defaultCreator，如果不提供，会导致持久化失败。且集合项类型S必须与 defaultSubCreator的返回类型相同。如果返回类型不一致，编译会报错。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 创建或获取数据成功时，返回数据；否则返回undefined。 |

## notifyOnError

```TypeScript
static notifyOnError(callback: PersistenceErrorCallback | undefined): void
```

注册持久化失败时的回调函数。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PersistenceV2-static notifyOnError(callback: PersistenceErrorCallback | undefined): void--><!--Device-PersistenceV2-static notifyOnError(callback: PersistenceErrorCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [PersistenceErrorCallback](arkts-arkui-persistenceerrorcallback-t.md) \| undefined | 是 | 持久化失败时的回调函数。回调参数包括：key（出错的键值）、reason（出错原因类型，取值为'quota'、' serialization'或'unknown'）、message（出错的详细信息）和oldValue（反序列化失败时返回的旧数据，可选）。 |

## save

```TypeScript
static save<T>(keyOrType: string | TypeConstructorWithArgs<T>): void
```

将指定的键值对数据持久化一次。 > **说明：** > > 由于非[\@Trace](../../../ui/state-management/arkts-new-observedV2-and-trace.md)的数据改变 > 不会触发[PersistenceV2](../../../ui/state-management/arkts-new-persistencev2.md)的自动持久化，当非\@Trace的数据发生变化且需要持久化时， > 可调用该接口持久化对应key的数据。 > > 手动持久化当前内存中不处于connect状态的key是无意义的。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PersistenceV2-static save<T>(keyOrType: string | TypeConstructorWithArgs<T>): void--><!--Device-PersistenceV2-static save<T>(keyOrType: string | TypeConstructorWithArgs<T>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyOrType | string \| [TypeConstructorWithArgs](arkts-arkui-arkui-statemanagement-typeconstructorwithargs-i.md)&lt;T&gt; | 是 | 需要持久化的key；如果指定的是type类型，持久化的key为type的name。 |

