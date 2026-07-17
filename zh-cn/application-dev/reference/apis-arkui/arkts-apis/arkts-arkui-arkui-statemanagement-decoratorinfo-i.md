# DecoratorInfo

可被观察对象关联的装饰器和组件信息。

**起始版本：** 23

<!--Device-unnamed-export interface DecoratorInfo--><!--Device-unnamed-export interface DecoratorInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { Binding, ComponentReuse, CustomComponentLifecycleState, ComponentInactive, PersistenceV2, ComponentDisappear, MutableBinding, CustomComponentLifecycleObserver, AppStorageV2, Type, ConnectOptionsCollections, CollectionType, CustomComponentContext, IReusePool, ConnectOptions, UIUtils, ComponentActive, CustomComponentLifecycle, ComponentInit, ComponentAppear, ComponentBuilt, ComponentRecycle, IReusableInfo } from '@kit.ArkUI';
```

## decoratorName

```TypeScript
decoratorName: string
```

当对象是V1对象时，值是对象关联的装饰器名称。

当V1对象使用[@Track](../../../../ui/state-management/arkts-track.md)时，值为：'@Track'。

当V2对象使用[@Trace](../../../../ui/state-management/arkts-new-observedV2-and-trace.md)时，值为：'@Trace'。

当V2对象使用[makeObserved](arkts-arkui-arkui-statemanagement-uiutils-c.md#makeobserved-1)时，值为：'MakeObserved'。

当V2对象使用[enableV2Compatibility](arkts-arkui-arkui-statemanagement-uiutils-c.md#enablev2compatibility-1)时，值为：'EnableV2Compatible'。

当V2对象使用built-in类型数据时，值为：'ProxyObservedV2'。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-DecoratorInfo-decoratorName: string--><!--Device-DecoratorInfo-decoratorName: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dependentInfo

```TypeScript
dependentInfo: Array<ElementInfo>
```

使用该可观察对象的组件信息。若对象没有用在任何UI上，则返回空数组。

**类型：** Array<ElementInfo>

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-DecoratorInfo-dependentInfo: Array<ElementInfo>--><!--Device-DecoratorInfo-dependentInfo: Array<ElementInfo>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## owningComponentId

```TypeScript
owningComponentId: number
```

V1对象返回被使用的组件id。

**V1对象有属性使用[@Track](../../../../ui/state-management/arkts-track.md)装饰器时和V2对象返回的是对象名称，无组件id，返回-1。**

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-DecoratorInfo-owningComponentId: number--><!--Device-DecoratorInfo-owningComponentId: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## owningComponentOrClassName

```TypeScript
owningComponentOrClassName: string
```

V1对象返回被使用的组件名称。

V1对象有属性使用[@Track](../../../../ui/state-management/arkts-track.md)装饰器时返回对象名称。

V2对象返回对象名称。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-DecoratorInfo-owningComponentOrClassName: string--><!--Device-DecoratorInfo-owningComponentOrClassName: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## stateVariableName

```TypeScript
stateVariableName: string
```

被装饰器装饰的属性名称。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-DecoratorInfo-stateVariableName: string--><!--Device-DecoratorInfo-stateVariableName: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

