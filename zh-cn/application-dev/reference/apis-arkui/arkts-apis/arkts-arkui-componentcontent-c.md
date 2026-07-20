# ComponentContent

继承自[Content](docroot://reference/apis-arkui/js-apis-arkui-Content.md#content-1)。

**继承/实现关系：** ComponentContent extends [Content](arkts-arkui-content-c.md)

**起始版本：** 12

<!--Device-unnamed-export class ComponentContent<T extends Object> extends Content--><!--Device-unnamed-export class ComponentContent<T extends Object> extends Content-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="constructor"></a>
## constructor

```TypeScript
constructor(uiContext: UIContext, builder: WrappedBuilder<[]>)
```

ComponentContent的构造函数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentContent-constructor(uiContext: UIContext, builder: WrappedBuilder<[]>)--><!--Device-ComponentContent-constructor(uiContext: UIContext, builder: WrappedBuilder<[]>)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | [UIContext](../arkts-components/arkts-arkui-uicontext-t.md) | 是 | 创建对应节点时所需要的UI上下文。 |
| builder | [WrappedBuilder](../arkts-components/arkts-arkui-wrappedbuilder-c.md)&lt;[]&gt; | 是 | 封装不带参builder函数的WrappedBuilder对象。 |

<a id="constructor-1"></a>
## constructor

```TypeScript
constructor(uiContext: UIContext, builder: WrappedBuilder<[T]>, args: T)
```

ComponentContent的构造函数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentContent-constructor(uiContext: UIContext, builder: WrappedBuilder<[T]>, args: T)--><!--Device-ComponentContent-constructor(uiContext: UIContext, builder: WrappedBuilder<[T]>, args: T)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | [UIContext](../arkts-components/arkts-arkui-uicontext-t.md) | 是 | 创建对应节点时所需要的UI上下文。 |
| builder | [WrappedBuilder](../arkts-components/arkts-arkui-wrappedbuilder-c.md)&lt;[T]&gt; | 是 | 封装带参builder函数的WrappedBuilder对象。 |
| args | T | 是 | WrappedBuilder对象封装的builder函数的参数。 |

<a id="constructor-2"></a>
## constructor

```TypeScript
constructor(uiContext: UIContext, builder: WrappedBuilder<[T]>, args: T, options: BuildOptions)
```

ComponentContent的构造函数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentContent-constructor(uiContext: UIContext, builder: WrappedBuilder<[T]>, args: T, options: BuildOptions)--><!--Device-ComponentContent-constructor(uiContext: UIContext, builder: WrappedBuilder<[T]>, args: T, options: BuildOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | [UIContext](../arkts-components/arkts-arkui-uicontext-t.md) | 是 | 创建对应节点时所需要的UI上下文。 |
| builder | [WrappedBuilder](../arkts-components/arkts-arkui-wrappedbuilder-c.md)&lt;[T]&gt; | 是 | 封装带参builder函数的WrappedBuilder对象。 |
| args | T | 是 | WrappedBuilder对象封装的builder函数的参数。 |
| options | [BuildOptions](arkts-arkui-buildernode-buildoptions-i.md) | 是 | build的配置参数，判断是否支持@Builder中嵌套@Builder的行为。*@Builder** within **@Builder**. |

<a id="dispose"></a>
## dispose

```TypeScript
dispose(): void
```

立即释放当前ComponentContent对象对[基本概念：实体节点](docroot://ui/arkts-user-defined-node.md#基本概念)的引用关系。关于ComponentContent的解绑场景请参见[解除实体节点引用关系](docroot://ui/arkts-user-defined-arktsNode-builderNode.md#解除实体节点引用关系)。

> **说明：**

> 当ComponentContent对象调用dispose之后，会与后端实体节点解除引用关系。若前端对象ComponentContent无法释放，容易导致内存泄漏。建议在不再需要操作该ComponentContent对象时，开发  
> 者主动调用dispose释放后端节点，以减少引用关系的复杂性，降低内存泄漏的风险。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentContent-dispose(): void--><!--Device-ComponentContent-dispose(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="inheritfreezeoptions"></a>
## inheritFreezeOptions

```TypeScript
inheritFreezeOptions(enabled: boolean): void
```

设置当前ComponentContent对象是否继承父组件中自定义组件的冻结策略。如果设置继承状态为false，则ComponentContent对象的冻结策略为false。在这种情况下，节点在不活跃状态下不会被冻结。

> **说明：**

> ComponentContent设置inheritFreezeOptions为true，且父组件为自定义组件、BuilderNode、ComponentContent、ReactiveBuilderNode或  
> ReactiveComponentContent时，会继承父组件的冻结策略。当子组件为自定义组件时，其冻结策略不会传递给子组件。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentContent-inheritFreezeOptions(enabled: boolean): void--><!--Device-ComponentContent-inheritFreezeOptions(enabled: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | ComponentContent对象是否设置为继承父组件中自定义组件的冻结策略。true为继承父组件中自定义组件的冻结策略，false为不继承父组件中自定义组件的冻结策略。 |

<a id="isdisposed"></a>
## isDisposed

```TypeScript
isDisposed(): boolean
```

查询当前ComponentContent对象是否已解除与后端实体节点的引用关系。前端节点均绑定有相应的后端实体节点，当节点调用dispose接口解除绑定后，再次调用接口可能会出现crash、返回默认值的情况。由于业务需求，可能存在节点在dispose后仍被调用接口的情况。为此，提供此接口以供开发者在操作节点前检查其有效性，避免潜在风险。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentContent-isDisposed(): boolean--><!--Device-ComponentContent-isDisposed(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 后端实体节点是否解除引用。true为节点已与后端实体节点解除引用，false为节点未与后端实体节点解除引用。 |

<a id="istransferred"></a>
## isTransferred

```TypeScript
isTransferred(): boolean
```

返回一个标志位，表示当前 ComponentContent 是否通过动态-静态转换获取。该转换包含两个方向：从动态转换为静态，以及从静态转换为动态。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentContent-isTransferred(): boolean--><!--Device-ComponentContent-isTransferred(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | - 如果 ComponentContent 是经过动态与静态之间转换获得，则返回 true；否则返回 false。 |

<a id="recycle"></a>
## recycle

```TypeScript
recycle(): void
```

- 触发ComponentContent中自定义组件的回收。自定义组件的回收是组件复用机制中的环节，具体信息请参见[@Reusable装饰器：V1组件复用](docroot://ui/state-management/arkts-reusable.md)。  
- ComponentContent通过reuse和recycle完成其内外自定义组件之间的复用事件传递，具体使用场景请参见[BuilderNode调用reuse和recycle接口实现节点复用能力](docroot://ui/arkts-user-defined-arktsNode-builderNode.md#buildernode调用reuse和recycle接口实现节点复用能力)。从API版本26.0.0开始，ComponentContent中的自定义组件支持V2组件复用，请参见[@ReusableV2装饰器：V2组件复用](docroot://ui/state-management/arkts-new-reusableV2.md)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentContent-recycle(): void--><!--Device-ComponentContent-recycle(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="reuse"></a>
## reuse

```TypeScript
reuse(param?: Object): void
```

触发ComponentContent中的自定义组件的复用。组件复用请参见[@Reusable装饰器：V1组件复用](docroot://ui/state-management/arkts-reusable.md)。关于ComponentContent的解绑场景请参见[解除实体节点引用关系](docroot://ui/arkts-user-defined-arktsNode-builderNode.md#解除实体节点引用关系)。从API版本26.0.0开始，ComponentContent中的自定义组件支持V2组件复用，请参见[@ReusableV2装饰器：V2组件复用](docroot://ui/state-management/arkts-new-reusableV2.md)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentContent-reuse(param?: Object): void--><!--Device-ComponentContent-reuse(param?: Object): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | Object | 否 | 用于复用ComponentContent的参数。该参数将直接用于ComponentContent中所有顶层自定义组件的复用，应该包含每个自定义组件的构造函数参数所需内容，否则会导致未定义行为。调用此方法将同步触发内部自定义组件的[aboutToReuse](docroot://reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttoreuse10)生命周期回调，并将该参数作为回调的入参。默认值为undefined，此时ComponentContent中的自定义组件将直接使用构造时的数据源。 |

<a id="update"></a>
## update

```TypeScript
update(args: T): void
```

用于更新[WrappedBuilder](docroot://ui/state-management/arkts-wrapBuilder.md)对象封装的builder函数参数，与constructor传入的参数类型保持一致。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentContent-update(args: T): void--><!--Device-ComponentContent-update(args: T): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| args | T | 是 | 用于更新[WrappedBuilder](docroot://ui/state-management/arkts-wrapBuilder.md)对象封装的builder函数参数，与constructor传入的参数类型保持一致。 |

<a id="updateconfiguration"></a>
## updateConfiguration

```TypeScript
updateConfiguration(): void
```

传递系统环境变化事件，触发节点的全量更新。系统环境变化的相关信息请参见[@ohos.app.ability.Configuration (环境变量)](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-configuration-configuration-i.md)。

> **说明：**

> updateConfiguration接口用于通知对象更新当前的系统环境变化。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentContent-updateConfiguration(): void--><!--Device-ComponentContent-updateConfiguration(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

