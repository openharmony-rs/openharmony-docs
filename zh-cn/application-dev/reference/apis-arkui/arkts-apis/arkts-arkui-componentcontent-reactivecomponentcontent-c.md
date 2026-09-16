# ReactiveComponentContent

ReactiveComponentContent继承自[Content](../../../reference/apis-arkui/js-apis-arkui-Content.md#content-1)，是一个用于动态承载和复用UI内容的容器组件。它通过@Builder函数构建UI，并利用[ReactiveBuilderNode](arkts-arkui-buildernode-reactivebuildernode-c.md)生成和管理组件树。该组件的核心价值在于为动态内容提供完整的生命周期管理，使其能够融入ArkUI的组件复用体系，特别适用于长列表等需要高性能渲染的场景。

**继承/实现关系：** ReactiveComponentContent extends [Content](arkts-arkui-content-c.md)

**起始版本：** 22

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(uiContext: UIContext, builder: WrappedBuilder<T>, config: BuildOptions, ...args: T)
```

ReactiveComponentContent的构造函数。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) | 是 | 创建对应节点时所需的UI上下文。 |
| builder | WrappedBuilder&lt;T&gt; | 是 | 封装带参builder函数的WrappedBuilder对象。 |
| config | [BuildOptions](arkts-arkui-buildernode-buildoptions-i.md) | 是 | 配置Builder的构建行为，BuildOptions中所有属性均为可选。 |
| args | T | 是 | WrappedBuilder对象封装的builder函数的参数。负责将外部数据传递给构造函数中指定的WrappedBuilder&lt;T&gt;的builder函数。类型T需与WrappedBuilder&lt;T&gt;中指定的参数类型保持一致。支持多个入参。不传入参数时默认为空数组[]。 |

**示例**

```TypeScript
该示例展示了如何使用ReactiveComponentContent构造函数动态创建包含响应式内容的UI组件，实现了builder函数的嵌套调用和函数参数的灵活传递。
```

## dispose

```TypeScript
dispose(): void
```

立即释放当前ReactiveComponentContent对象对[实体节点](../../../ui/arkts-user-defined-node.md#基本概念)的引用关系。关于ReactiveComponentContent的解绑场景请参见[解除实体节点引用关系](../../../ui/arkts-user-defined-arktsNode-builderNode.md#解除实体节点引用关系)。

> **说明：** 
> 
> ReactiveComponentContent对象调用dispose接口后，会与后端实体节点解除引用关系。调用dispose后再次调用该对象的其他接口可能会出现crash或返回默认值，建议在操作节点前通过
> [isDisposed](#isdisposed)接口检查其有效性。若前端ReactiveComponentContent对象无法释放，容易导致内存泄漏。建议开发者在
> 不需要操作该ReactiveComponentContent对象时，主动调用dispose释放后端节点，以减少引用关系的复杂性，降低内存泄漏风险。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

```TypeScript
该示例展示了如何使用dispose接口正确释放ReactiveComponentContent对象，管理节点生命周期。
```

## flushState

```TypeScript
flushState(): void
```

更新ReactiveComponentContent。当ReactiveComponentContent中[WrappedBuilder](../../../ui/state-management/arkts-wrapBuilder.md)对象封装的builder函数中使用的绑定参数是由V1装饰器（如@Observed）装饰的类实例时，需要在此类数据变更后手动调用本接口更新数据。当使用V2装饰器（如@ObservedV2）装饰的类实例时，支持自动更新，无需手动调用。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

```TypeScript
该示例展示了flushState接口在ReactiveComponentContent中的使用场景，通过对比使用V2装饰器（如@ObservedV2）装饰的类与使用V1装饰器（如@Observed）装饰的类的数据更新机制，演示了不同响应式方案下的状态更新策略。
```

## inheritFreezeOptions

```TypeScript
inheritFreezeOptions(enabled: boolean): void
```

设置当前ReactiveComponentContent对象是否继承父组件中自定义组件的冻结策略[ComponentOptions](../arkts-components/arkts-arkui-componentoptions-i.md)。冻结策略用于控制组件在不活跃状态下是否暂停状态刷新。如果设置继承状态为false，则ReactiveComponentContent对象的冻结策略为false。适用于多页面导航（Navigation）等需要对不活跃组件进行冻结管理的场景。

> **说明：** 
> 
> ReactiveComponentContent设置inheritFreezeOptions为true，且父组件为自定义组件、BuilderNode、ComponentContent、ReactiveBuilderNode或
> ReactiveComponentContent时，会继承父组件的冻结策略。当子组件为自定义组件时，ReactiveComponentContent的冻结策略不会传递给该子组件。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | ReactiveComponentContent对象是否设置为继承父组件中自定义组件的冻结策略。<br>true：继承父组件中自定义组件的冻结策略；false：不继承父组件中自定义组件的冻结策略。<br>**说明：** 仅当父组件为自定义组件、BuilderNode、ComponentContent、ReactiveBuilderNode或ReactiveComponentContent时，设置true才会继承父组件的冻结策略。 |

**示例**

```TypeScript
该示例演示了ReactiveComponentContent设置继承状态为true，继承父自定义组件的冻结策略。组件在不活跃时冻结，切换为活跃状态时解冻并更新缓存的数据。
```

## isDisposed

```TypeScript
isDisposed(): boolean
```

查询当前ReactiveComponentContent对象是否已解除与后端实体节点的引用关系。前端节点均绑定有相应的后端实体节点，当节点调用dispose接口解除绑定后，再次调用接口可能会出现crash、返回默认值的情况。由于业务需求，可能存在节点在dispose后仍被调用接口的情况。为此，提供此接口以供开发者在操作节点前检查其有效性，避免潜在风险。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 后端实体节点是否解除引用。<br>true：节点已与后端实体节点解除引用；false：节点未与后端实体节点解除引用。 |

**示例**

```TypeScript
该示例展示了如何使用isDisposed接口检查ReactiveComponentContent对象是否已解除与后端实体节点的引用关系，提供了节点状态安全检测的完整实现方案。
```

## isTransferred

```TypeScript
isTransferred(): boolean
```

判断ReactiveComponentContent是否通过transfer.transferStatic或者transfer.transferDynamic方法创建。如果通过上述两个接口创建，则不支持以下方法：[update](arkts-arkui-componentcontent-c.md#update)，[dispose](arkts-arkui-componentcontent-c.md#dispose)，[updateConfiguration](arkts-arkui-componentcontent-c.md#updateconfiguration)，[inheritFreezeOptions](arkts-arkui-componentcontent-c.md#inheritfreezeoptions)。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回ReactiveComponentContent是否通过transfer.transferStatic或transfer.transferDynamic方法创建。<br>true：ReactiveComponentContent通过transfer.transferStatic或transfer.transferDynamic方法创建。<br>false：ReactiveComponentContent不通过transfer.transferStatic或transfer.transferDynamic方法创建。 |

## recycle

```TypeScript
recycle(): void
```

触发ReactiveComponentContent中自定义组件的回收。自定义组件的回收是组件复用机制中的环节，具体信息请参见[@Reusable装饰器：V1组件复用](../../../ui/state-management/arkts-reusable.md)。从API版本26.0.0开始，ReactiveComponentContent中的自定义组件支持V2组件复用，请参见[@ReusableV2装饰器：V2组件复用](../../../ui/state-management/arkts-new-reusableV2.md)。

ReactiveComponentContent通过[reuse](#reuse)和recycle完成其内外自定义组件之间的复用事件传递，具体使用场景请参见[BuilderNode调用reuse和recycle接口实现节点复用能力](../../../ui/arkts-user-defined-arktsNode-builderNode.md#buildernode调用reuse和recycle接口实现节点复用能力)。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

```TypeScript
实现了一个包含多层组件复用的高性能长列表，通过ReactiveComponentContent动态管理Builder内容，在列表滚动时实现组件的自动回收与复用。
```

```TypeScript


从API版本26.0.0开始，ReactiveComponentContent中的自定义组件支持V2组件复用。
```

## reuse

```TypeScript
reuse(param?: Object): void
```

触发ReactiveComponentContent中的自定义组件的复用。组件复用请参见[@Reusable装饰器：V1组件复用](../../../ui/state-management/arkts-reusable.md)。关于ReactiveComponentContent的解绑场景请参见[解除实体节点引用关系](../../../ui/arkts-user-defined-arktsNode-builderNode.md#解除实体节点引用关系)。从API版本26.0.0开始，ReactiveComponentContent中的自定义组件支持V2组件复用，请参见[@ReusableV2装饰器：V2组件复用](../../../ui/state-management/arkts-new-reusableV2.md)。

ReactiveComponentContent通过reuse和[recycle](#recycle)接口完成其内外自定义组件之间的复用事件传递，具体使用场景请参见[BuilderNode调用reuse和recycle接口实现节点复用能力](../../../ui/arkts-user-defined-arktsNode-builderNode.md#buildernode调用reuse和recycle接口实现节点复用能力)。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | Object | 否 | 用于复用[ReactiveComponentContent](arkts-arkui-componentcontent-reactivecomponentcontent-c.md)的参数。该参数将直接用于ReactiveComponentContent中所有顶层自定义组件的复用，应该包含每个自定义组件的构造函数参数所需内容，否则会导致未定义行为。调用此方法将同步触发内部自定义组件的aboutToReuse生命周期回调，并将该参数作为回调的入参。默认值为undefined，此时ReactiveComponentContent中的自定义组件将直接使用构造时的数据源。 |

**示例**

```TypeScript
请参考[recycle](#recycle)中的示例。
```

## updateConfiguration

```TypeScript
updateConfiguration(): void
```

传递系统环境变化事件，触发节点的全量更新，用于通知对象更新所使用的系统环境配置。适用于系统深浅色模式切换、语言变更、字体大小调整等需要节点响应系统配置变化的场景。系统环境变化的相关信息请参见[@ohos.app.ability.Configuration (环境变量)](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-configuration-configuration-i.md)。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

```TypeScript
该示例展示了如何使用updateConfiguration接口响应系统环境配置变化，实现ReactiveComponentContent构建的UI节点的动态适配更新。
```
