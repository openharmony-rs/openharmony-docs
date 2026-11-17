# RecoverableConnectOptions

```TypeScript
export declare class RecoverableConnectOptions<T extends object, S extends object>
```

定义[RecoverableStorage.connect](arkts-arkui-arkui-statemanagement-recoverablestorage-c.md#connect)的连接选项。

**起始版本：** 26.1.0

<!--Device-unnamed-export declare class RecoverableConnectOptions<T extends object, S extends object>--><!--Device-unnamed-export declare class RecoverableConnectOptions<T extends object, S extends object>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IDefaultReusePool, IReusableInfo, StorageDefaultCreator, TypeConstructorWithArgs, PersistenceErrorCallback, TypeConstructor, TypeDecorator, MonitorCallback, MonitorOptions, GetterCallback, SetterCallback, ObservedResult, DecoratorInfo, ElementInfo, RecoverableStorage, RecoverableConnectOptions, RecoverableStorageError, NotifyOnErrorCallback } from '@kit.ArkUI';
```

## defaultCreator

```TypeScript
defaultCreator: StorageDefaultCreator<T>
```

默认值构造器。首次连接（内存与快照中均不存在该key）时使用，恢复失败时作为回退。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-RecoverableConnectOptions-defaultCreator: StorageDefaultCreator<T>--><!--Device-RecoverableConnectOptions-defaultCreator: StorageDefaultCreator<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## defaultSubCreator

```TypeScript
defaultSubCreator?: StorageDefaultCreator<S>
```

集合嵌套**\

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-RecoverableConnectOptions-defaultSubCreator?: StorageDefaultCreator<S>--><!--Device-RecoverableConnectOptions-defaultSubCreator?: StorageDefaultCreator<S>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## notifyOnError

```TypeScript
notifyOnError?: NotifyOnErrorCallback
```

序列化/反序列化错误回调。不指定时错误在内部处理，不会导致应用崩溃。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-RecoverableConnectOptions-notifyOnError?: NotifyOnErrorCallback--><!--Device-RecoverableConnectOptions-notifyOnError?: NotifyOnErrorCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## component

```TypeScript
component: BaseCustomComponent
```

自定义组件实例，传入**this**，用于获取窗口级实例ID实现实例间隔离。

**类型：** [BaseCustomComponent](../arkts-components/arkts-arkui-common-comp-basecustomcomponent-c.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-RecoverableConnectOptions-component: BaseCustomComponent--><!--Device-RecoverableConnectOptions-component: BaseCustomComponent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## key

```TypeScript
key?: string
```

可恢复状态变量的key。不指定时使用类型名作为key。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-RecoverableConnectOptions-key?: string--><!--Device-RecoverableConnectOptions-key?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: TypeConstructorWithArgs<T>
```

可恢复状态变量的类型。仅支持对象类型；**number**、**string**、**boolean**等简单类型会被拒绝。

**类型：** [TypeConstructorWithArgs](arkts-arkui-arkui-statemanagement-typeconstructorwithargs-i.md)&lt;T&gt;

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-RecoverableConnectOptions-type: TypeConstructorWithArgs<T>--><!--Device-RecoverableConnectOptions-type: TypeConstructorWithArgs<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
