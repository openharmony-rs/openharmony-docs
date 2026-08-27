# MonitorOptions

[addMonitor](arkts-arkui-arkui-statemanagement-uiutils-c.md#addmonitor)的可选参数，用于配置回调类型以及是否使能通配符能力。

**起始版本：** 20

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IReusableInfo } from '@kit.ArkUI';
```

## enableWildcard

```TypeScript
enableWildcard?: boolean
```

配置当前addMonitor是否使能通配符能力。true表示使能，false表示关闭。默认值为false，即关闭。当关闭通配符能力，但路径中含有通配符时，该路径将视为不合法路径。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isSynchronous

```TypeScript
isSynchronous?: boolean
```

配置当前回调函数是否为同步回调。true为同步回调。默认值为false，即异步回调。

**类型：** boolean

**默认值：** false

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
