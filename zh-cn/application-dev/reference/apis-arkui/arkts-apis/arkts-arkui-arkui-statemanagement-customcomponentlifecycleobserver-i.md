# CustomComponentLifecycleObserver

用户注册自定义组件生命周期回调后，当该自定义组件的生命周期发生变化时，将触发监听器中相应的生命周期回调。

**起始版本：** 23

<!--Device-unnamed-export declare interface CustomComponentLifecycleObserver--><!--Device-unnamed-export declare interface CustomComponentLifecycleObserver-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { Binding, ComponentReuse, CustomComponentLifecycleState, ComponentInactive, PersistenceV2, ComponentDisappear, MutableBinding, CustomComponentLifecycleObserver, AppStorageV2, Type, ConnectOptionsCollections, CollectionType, CustomComponentContext, IReusePool, ConnectOptions, UIUtils, ComponentActive, CustomComponentLifecycle, ComponentInit, ComponentAppear, ComponentBuilt, ComponentRecycle, IReusableInfo } from '@kit.ArkUI';
```

<a id="abouttoappear"></a>
## aboutToAppear

```TypeScript
aboutToAppear?(): void
```

aboutToAppear函数在创建自定义组件的新实例后，执行其build()函数之前执行。开发者可以在此阶段修改状态变量。其功能与[aboutToAppear](../arkts-components/arkts-arkui-basecustomcomponent-c.md#abouttoappear-1)类似，但是在自定义组件状态机的约束下触发的。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CustomComponentLifecycleObserver-aboutToAppear?(): void--><!--Device-CustomComponentLifecycleObserver-aboutToAppear?(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="abouttodisappear"></a>
## aboutToDisappear

```TypeScript
aboutToDisappear?(): void
```

aboutToDisappear函数在自定义组件被销毁之前执行。不建议在aboutToDisappear函数中修改状态变量，特别是@Link变量的修改可能会导致应用程序行为不稳定。其功能与[aboutToDisappear](../arkts-components/arkts-arkui-basecustomcomponent-c.md#abouttodisappear-1)类似，不同的是，CustomComponentLifecycleObserver中的aboutToDisappear函数受状态机约束，只有被监听的自定义组件状态向CustomComponentLifecycleState.DISAPPEARED转变前触发回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CustomComponentLifecycleObserver-aboutToDisappear?(): void--><!--Device-CustomComponentLifecycleObserver-aboutToDisappear?(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="abouttorecycle"></a>
## aboutToRecycle

```TypeScript
aboutToRecycle?(): void
```

当组件被回收后触发，先执行应用程序中定义的必要回收操作，完成回收后调用aboutToRecycle函数。随后该组件被冻结，以避免该组件处于回收池时进行UI更新。最后，aboutToRecycle函数会递归遍历所有子组件，对每个完成回收的组件调用aboutToRecycle函数。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CustomComponentLifecycleObserver-aboutToRecycle?(): void--><!--Device-CustomComponentLifecycleObserver-aboutToRecycle?(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="abouttoreuse"></a>
## aboutToReuse

```TypeScript
aboutToReuse?(params?: Record<string, Object | undefined | null>): void
```

当可复用的自定义组件从缓存中重新添加到节点树时调用aboutToReuse函数，以接收组件的构造参数。当params存在时，表示V1组件的复用回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CustomComponentLifecycleObserver-aboutToReuse?(params?: Record<string, Object | undefined | null>): void--><!--Device-CustomComponentLifecycleObserver-aboutToReuse?(params?: Record<string, Object | undefined | null>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | Record&lt;string, Object \| undefined \| null&gt; | 否 | 当params存在时，表示V1组件的复用回调。 |

<a id="ondidbuild"></a>
## onDidBuild

```TypeScript
onDidBuild?(): void
```

onDidBuild函数在自定义组件的新实例构建完成后，执行其build()函数之后执行。开发者可以在此阶段实现一些不影响实际UI的功能，例如事件数据上报。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CustomComponentLifecycleObserver-onDidBuild?(): void--><!--Device-CustomComponentLifecycleObserver-onDidBuild?(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

