# CustomComponentLifecycleObserver

开发者注册自定义组件生命周期回调后，当该自定义组件的生命周期发生变化时，将触发监听器中相应的生命周期回调。与生命周期装饰器的区别在于：生命周期装饰器由组件自身响应生命周期事件， CustomComponentLifecycleObserver从外部观察组件生命周期事件；若仅需组件自身响应生命周期变化，使用生命周期装饰器即可，若需集中监控多个组件的生命周期， 则使用CustomComponentLifecycleObserver。

**起始版本：** 23

<!--Device-unnamed-export declare interface CustomComponentLifecycleObserver--><!--Device-unnamed-export declare interface CustomComponentLifecycleObserver-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IReusableInfo } from '@kit.ArkUI';
```

## aboutToAppear

```TypeScript
aboutToAppear?(): void
```

aboutToAppear函数在创建自定义组件的新实例后、其build()函数执行之前被调用。开发者可以在此阶段修改状态变量，更改将在后续执行build()函数中生效。 其功能与aboutToAppear类似，受自定义组件状态机约束， 在被监听的自定义组件向CustomComponentLifecycleState.APPEARED转变时触发回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CustomComponentLifecycleObserver-aboutToAppear?(): void--><!--Device-CustomComponentLifecycleObserver-aboutToAppear?(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToDisappear

```TypeScript
aboutToDisappear?(): void
```

aboutToDisappear函数在自定义组件被销毁之前执行。不建议在aboutToDisappear函数中修改状态变量，特别是\@Link变量的修改可能会导致应用程序行为不稳定。 其功能与aboutToDisappear类似，不同的是， CustomComponentLifecycleObserver中的aboutToDisappear函数受状态机约束， 只有被监听的自定义组件状态向CustomComponentLifecycleState.DISAPPEARED转变前触发回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CustomComponentLifecycleObserver-aboutToDisappear?(): void--><!--Device-CustomComponentLifecycleObserver-aboutToDisappear?(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToRecycle

```TypeScript
aboutToRecycle?(): void
```

当组件被回收后，先执行应用程序中定义的资源释放等回收操作，完成回收后调用aboutToRecycle函数，受自定义组件状态机约束，即从CustomComponentLifecycleState.BUILT 到CustomComponentLifecycleState.RECYCLED阶段触发回调。随后该组件被冻结，以避免该组件处于复用池时进行UI更新。最后，回收会递归遍历所有子组件， 对每个完成回收的子组件调用子组件中注册的aboutToRecycle函数。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CustomComponentLifecycleObserver-aboutToRecycle?(): void--><!--Device-CustomComponentLifecycleObserver-aboutToRecycle?(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToReuse

```TypeScript
aboutToReuse?(params?: Record<string, Object | undefined | null>): void
```

当可复用的自定义组件从缓存中重新添加到节点树时调用aboutToReuse函数，受自定义组件状态机约束，即从CustomComponentLifecycleState.RECYCLED 到CustomComponentLifecycleState.BUILT阶段触发回调。最后，复用会递归遍历所有子组件，对每个完成复用的子组件调用子组件中注册的aboutToReuse函数。在状态管理V1的组件里， 该函数允许有一个入参或者无参，当params存在时表示V1组件的复用回调；在状态管理V2的组件里，该函数没有入参。 > **说明：** > > - 在状态管理V1的组件里，aboutToReuse函数允许有一个入参或者无参。入参params建议为Record\&lt;string, Object \| undefined \| null\&gt;类型。 > > - 在状态管理V2的组件里，aboutToReuse函数没有入参。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CustomComponentLifecycleObserver-aboutToReuse?(params?: Record<string, Object | undefined | null>): void--><!--Device-CustomComponentLifecycleObserver-aboutToReuse?(params?: Record<string, Object | undefined | null>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | Record&lt;string, Object \| undefined \| null&gt; | 否 | 组件复用时接收的构造参数，仅V1组件的复用回调支持该参数。不传此参数时，复用回调函数无入参。 |

## onDidBuild

```TypeScript
onDidBuild?(): void
```

onDidBuild函数在自定义组件的build()函数执行后被调用，受自定义组件状态机约束，在被监听的自定义组件状态向CustomComponentLifecycleState.BUILT转变时触发回调。 开发者可以在此阶段实现不影响实际UI的功能，例如事件数据上报。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CustomComponentLifecycleObserver-onDidBuild?(): void--><!--Device-CustomComponentLifecycleObserver-onDidBuild?(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

