# ElementInfo

可被观察对象关联的组件信息，包含系统组件和自定义组件。

**起始版本：** 23

<!--Device-unnamed-export interface ElementInfo--><!--Device-unnamed-export interface ElementInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IReusableInfo } from '@kit.ArkUI';
```

## elementId

```TypeScript
elementId: number
```

组件的ID。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ElementInfo-elementId: number--><!--Device-ElementInfo-elementId: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## elementName

```TypeScript
elementName: string
```

组件的名称。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ElementInfo-elementName: string--><!--Device-ElementInfo-elementName: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

