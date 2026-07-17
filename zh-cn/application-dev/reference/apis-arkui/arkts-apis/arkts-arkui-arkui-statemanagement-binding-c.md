# Binding

只读数据绑定的泛型类，可以绑定任意类型的数据。

**起始版本：** 20

<!--Device-unnamed-export declare class Binding<T>--><!--Device-unnamed-export declare class Binding<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { Binding, ComponentReuse, CustomComponentLifecycleState, ComponentInactive, PersistenceV2, ComponentDisappear, MutableBinding, CustomComponentLifecycleObserver, AppStorageV2, Type, ConnectOptionsCollections, CollectionType, CustomComponentContext, IReusePool, ConnectOptions, UIUtils, ComponentActive, CustomComponentLifecycle, ComponentInit, ComponentAppear, ComponentBuilt, ComponentRecycle, IReusableInfo } from '@kit.ArkUI';
```

## value

```TypeScript
get value(): T
```

提供get访问器，用于获取绑定的值。

**类型：** T

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-Binding-get value(): T--><!--Device-Binding-get value(): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

