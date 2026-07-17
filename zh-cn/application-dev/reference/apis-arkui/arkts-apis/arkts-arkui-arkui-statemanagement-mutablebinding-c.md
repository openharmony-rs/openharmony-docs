# MutableBinding

可变数据绑定的泛型类，允许对绑定值进行读写操作，提供完整的get和set访问器。

**起始版本：** 20

<!--Device-unnamed-export declare class MutableBinding<T>--><!--Device-unnamed-export declare class MutableBinding<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { Binding, ComponentReuse, CustomComponentLifecycleState, ComponentInactive, PersistenceV2, ComponentDisappear, MutableBinding, CustomComponentLifecycleObserver, AppStorageV2, Type, ConnectOptionsCollections, CollectionType, CustomComponentContext, IReusePool, ConnectOptions, UIUtils, ComponentActive, CustomComponentLifecycle, ComponentInit, ComponentAppear, ComponentBuilt, ComponentRecycle, IReusableInfo } from '@kit.ArkUI';
```

## value

```TypeScript
set value(newValue: T)
```

提供set访问器，用于设置当前绑定值的值。构造MutableBinding类实例时必须提供set访问器，否则触发set访问器会造成运行时错误。

**类型：** T

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-MutableBinding-set value(newValue: T)--><!--Device-MutableBinding-set value(newValue: T)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

