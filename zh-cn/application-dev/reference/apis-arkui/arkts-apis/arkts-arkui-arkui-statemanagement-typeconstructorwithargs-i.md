# TypeConstructorWithArgs

含有任意入参的类构造器。

**起始版本：** 12

<!--Device-unnamed-export interface TypeConstructorWithArgs<T>--><!--Device-unnamed-export interface TypeConstructorWithArgs<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { Binding, ComponentReuse, CustomComponentLifecycleState, ComponentInactive, PersistenceV2, ComponentDisappear, MutableBinding, CustomComponentLifecycleObserver, AppStorageV2, Type, ConnectOptionsCollections, CollectionType, CustomComponentContext, IReusePool, ConnectOptions, UIUtils, ComponentActive, CustomComponentLifecycle, ComponentInit, ComponentAppear, ComponentBuilt, ComponentRecycle, IReusableInfo } from '@kit.ArkUI';
```

## constructor

```TypeScript
new(...args: any): T
```

创建并返回一个指定类型T的实例。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TypeConstructorWithArgs-new(...args: any): T--><!--Device-TypeConstructorWithArgs-new(...args: any): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| args | any | 是 | 函数入参。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | T类型的实例。 |

