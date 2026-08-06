# ConnectOptionsCollections

[globalConnect]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_ 接口参数类型，ConnectOptionsCollections继承自[ConnectOptions\&lt;T\&gt;]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_。当开发者需要持久化容器类型数据（如\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_）时，需要使用 \_\_\_INLINE\_CODE\_DESC\_USD\_1\_\_\_入参。 如下展示\_\_\_INLINE\_CODE\_DESC\_USD\_2\_\_\_和\_\_\_INLINE\_CODE\_DESC\_USD\_3\_\_\_示例：

**继承/实现关系：** ConnectOptionsCollections extends [ConnectOptions<T>](ConnectOptions<T>)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

<!--Device-unnamed-export class ConnectOptionsCollections<T extends CollectionType<S>, S extends object> extends ConnectOptions<T>--><!--Device-unnamed-export class ConnectOptionsCollections<T extends CollectionType<S>, S extends object> extends ConnectOptions<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## defaultCreator

```TypeScript
defaultCreator?: StorageDefaultCreator<T>
```

用于持久化容器类型数据，当提供默认\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_时，则需要同时提供默认构造器\_\_\_INLINE\_CODE\_DESC\_USD\_1\_\_\_，不提供默认构造器会导致持久化失败。集合项类型\_\_\_INLINE\_CODE\_DESC\_USD\_2\_\_\_必须与\_\_\_INLINE\_CODE\_DESC\_USD\_3\_\_\_的 返回类型相同。

**类型：** StorageDefaultCreator&lt;T&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ConnectOptionsCollections-defaultCreator?: StorageDefaultCreator<T>--><!--Device-ConnectOptionsCollections-defaultCreator?: StorageDefaultCreator<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## defaultSubCreator

```TypeScript
defaultSubCreator?: StorageDefaultCreator<S>
```

使用该集合项默认构造函数，用于持久化容器类数据。使用此参数时，必须同时提供\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_，否则会导致持久化失败。如果defaultSubCreator返回的是\_\_\_INLINE\_CODE\_DESC\_USD\_1\_\_\_或\_\_\_INLINE\_CODE\_DESC\_USD\_2\_\_\_时，会导致持久化失 败。 当持久化用户自定义class类集合（如\_\_\_INLINE\_CODE\_DESC\_USD\_3\_\_\_）时，\_\_\_INLINE\_CODE\_DESC\_USD\_4\_\_\_中的泛型类型\_\_\_INLINE\_CODE\_DESC\_USD\_5\_\_\_为\_\_\_INLINE\_CODE\_DESC\_USD\_6\_\_\_，则\_\_\_INLINE\_CODE\_DESC\_USD\_7\_\_\_中的泛型类型\_\_\_INLINE\_CODE\_DESC\_USD\_8\_\_\_为 \_\_\_INLINE\_CODE\_DESC\_USD\_9\_\_\_。

**类型：** StorageDefaultCreator&lt;S&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ConnectOptionsCollections-defaultSubCreator?: StorageDefaultCreator<S>--><!--Device-ConnectOptionsCollections-defaultSubCreator?: StorageDefaultCreator<S>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

