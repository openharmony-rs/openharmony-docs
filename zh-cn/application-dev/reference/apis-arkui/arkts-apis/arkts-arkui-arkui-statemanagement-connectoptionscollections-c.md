# ConnectOptionsCollections

globalConnect 接口参数类型，ConnectOptionsCollections继承自[ConnectOptions\&lt;T\&gt;](arkts-arkui-arkui-statemanagement-connectoptions-c.md)。当开发者需要持久化容器类型数据（如`Array&lt;S&gt;`）时，需要使用 `ConnectOptionsCollections`入参。如下展示`StorageDefaultCreator&lt;T&gt;`和`StorageDefaultCreator&lt;S&gt;`示例：

**继承/实现关系：** ConnectOptionsCollections extends ConnectOptions<T>

**起始版本：** 23

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IReusableInfo } from '@kit.ArkUI';
```

## defaultCreator

```TypeScript
defaultCreator?: StorageDefaultCreator<T>
```

用于持久化容器类型数据，当提供默认`defaultSubCreator`时，则需要同时提供默认构造器`defaultCreator`，不提供默认构造器会导致持久化失败。集合项类型`S`必须与`defaultSubCreator`的 返回类型相同。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## defaultSubCreator

```TypeScript
defaultSubCreator?: StorageDefaultCreator<S>
```

使用该集合项默认构造函数，用于持久化容器类数据。使用此参数时，必须同时提供`defaultCreator`，否则会导致持久化失败。如果defaultSubCreator返回的是`undefined`或`null`时，会导致持久化失 败。 当持久化用户自定义class类集合（如`Array&lt;ClassA&gt;`）时，`defaultCreator`中的泛型类型`T`为`Array&lt;ClassA&gt;`，则`defaultSubCreator`中的泛型类型`S`为 `ClassA`。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
