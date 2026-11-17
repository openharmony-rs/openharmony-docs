# RecoverableStorageError

```TypeScript
export declare interface RecoverableStorageError
```

定义[RecoverableStorage](../../../ui/state-management/arkts-new-recoverablestorage.md)回调上报的错误信息。

**起始版本：** 26.1.0

<!--Device-unnamed-export declare interface RecoverableStorageError--><!--Device-unnamed-export declare interface RecoverableStorageError-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IDefaultReusePool, IReusableInfo, StorageDefaultCreator, TypeConstructorWithArgs, PersistenceErrorCallback, TypeConstructor, TypeDecorator, MonitorCallback, MonitorOptions, GetterCallback, SetterCallback, ObservedResult, DecoratorInfo, ElementInfo, RecoverableStorage, RecoverableConnectOptions, RecoverableStorageError, NotifyOnErrorCallback } from '@kit.ArkUI';
```

## keys

```TypeScript
keys: Array<string>
```

受错误影响的key列表。

**类型：** Array&lt;string&gt;

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-RecoverableStorageError-keys: Array<string>--><!--Device-RecoverableStorageError-keys: Array<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## message

```TypeScript
message: string
```

错误的附加信息。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-RecoverableStorageError-message: string--><!--Device-RecoverableStorageError-message: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## reason

```TypeScript
reason: 'serialization' | 'deserialization'
```

错误原因。取值为**'serialization'**（序列化失败，如超出序列化上限或字段不可序列化）或**'deserialization'**（反序列化失败，如数据损坏、类型不匹配）。**connect**入口错误（类型不支持、参数非法）以**BusinessError(140124)**直接**抛出**，不经本回调上报。推荐用户数据总量：每实例≤100KB（150KB序列化预算，与系统数据共享）。

**类型：** 'serialization' &#124; 'deserialization'

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-RecoverableStorageError-reason: 'serialization' | 'deserialization'--><!--Device-RecoverableStorageError-reason: 'serialization' | 'deserialization'-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
