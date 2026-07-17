# BuilderNode

class BuilderNode\<Args extends Object[]>

BuilderNode支持通过无状态的UI方法[@Builder](../../../../ui/state-management/arkts-builder.md)生成组件树，并持有组件树的根节点。不支持定义为状态变量。BuilderNode中持有的FrameNode仅用于将该BuilderNode作为子节点挂载到其他FrameNode上。对BuilderNode持有的FrameNode进行属性设置与子节点操作可能会产生未定义行为，因此不建议通过BuilderNode的[getFrameNode](arkts-arkui-buildernode-c.md#getframenode-1)方法和[FrameNode](arkts-arkui-framenode-c.md)的[getRenderNode](arkts-arkui-framenode-c.md#getrendernode-1)方法获取RenderNode，并通过[RenderNode](arkts-arkui-rendernode-c.md)的接口对其进行属性设置与子节点操作。

**起始版本：** 11

<!--Device-unnamed-export class BuilderNode<Args extends Object[]>--><!--Device-unnamed-export class BuilderNode<Args extends Object[]>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## build

```TypeScript
build(builder: WrappedBuilder<Args>, arg?: Object): void
```

依照传入的对象创建组件树，并持有组件树的根节点。无状态的UI方法[@Builder](../../../../ui/state-management/arkts-builder.md)最多拥有一个根节点。

支持自定义组件。

> **说明**  
>  
> - @Builder嵌套使用的时候需要保证内外的@Builder方法的入参对象一致。  
>  
> - 最外层的@Builder只支持一个入参。  
>  
> - build的参数是值传递，需要使用[update](arkts-arkui-buildernode-c.md#update-1)接口进行更新。  
>  
> - 需要操作BuilderNode中的对象时，需要保证其引用不被回收。当BuilderNode对象被虚拟机回收之后，它的[FrameNode](arkts-arkui-framenode-c.md)、  
> [RenderNode](arkts-arkui-rendernode-c.md)对象也会与后端节点解引用。即从BuilderNode中获取的FrameNode对象不对应任何一个节点。  
>  
> - BuilderNode对象会持有实体节点的引用。如果不需要使用BuilderNode前端对象管理后端节点，可以调用[dispose](arkts-arkui-buildernode-c.md#dispose-1)接口，实现前后端对象的解绑。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BuilderNode-build(builder: WrappedBuilder<Args>, arg?: Object): void--><!--Device-BuilderNode-build(builder: WrappedBuilder<Args>, arg?: Object): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | [WrappedBuilder](../arkts-components/arkts-arkui-common-wrappedbuilder-c.md)<Args> | 是 | 创建对应节点树的时候所需的无状态UI方法[@Builder](../../../../ui/state-management/arkts-builder.md)。 |
| arg | Object | 否 | builder的入参。当前仅支持一个入参，且入参对象类型与@Builder定义的入参类型保持一致。<br/>默认值：undefined |

## build

```TypeScript
build(builder: WrappedBuilder<Args>, arg: Object, options: BuildOptions): void
```

依照传入的对象创建组件树，并持有组件树的根节点。无状态的UI方法[@Builder](../../../../ui/state-management/arkts-builder.md)最多拥有一个根节点。

支持自定义组件。相比[build(builder: WrappedBuilder\<Args>, arg?: Object)](arkts-arkui-buildernode-c.md#build-1)接口，本接口支持builder的配置参数，用于判断是否支持@Builder中嵌套@Builder。

> **说明**  
>  
> - @Builder进行创建和更新的规格参考[@Builder](../../../../ui/state-management/arkts-builder.md)。  
>  
> - 最外层的@Builder只支持一个入参。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BuilderNode-build(builder: WrappedBuilder<Args>, arg: Object, options: BuildOptions): void--><!--Device-BuilderNode-build(builder: WrappedBuilder<Args>, arg: Object, options: BuildOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | [WrappedBuilder](../arkts-components/arkts-arkui-common-wrappedbuilder-c.md)<Args> | 是 | 创建对应节点树的时候所需的无状态UI方法[@Builder](../../../../ui/state-management/arkts-builder.md)。 |
| arg | Object | 是 | builder的入参。当前仅支持一个入参，且入参对象类型与@Builder定义的入参类型保持一致。 |
| options | [BuildOptions](arkts-arkui-buildernode-buildoptions-i.md) | 是 | builder的配置参数，判断是否支持@Builder中嵌套@Builder的行为。 |

## constructor

```TypeScript
constructor(uiContext: UIContext, options?: RenderOptions)
```

当将BuilderNode生成的内容嵌入到其它RenderNode中显示时，需要显式指定RenderOptions中的selfIdealSize，否则Builder内的节点默认父组件布局约束为[0, 0]。该场景下，若不设置selfIdealSize则认为BuilderNode中子树的根节点大小为[0, 0]。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BuilderNode-constructor(uiContext: UIContext, options?: RenderOptions)--><!--Device-BuilderNode-constructor(uiContext: UIContext, options?: RenderOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | [UIContext](../arkts-components/arkts-arkui-uicontext-t.md) | 是 | UI上下文，获取方式可参考[UIContext获取方法](../../../../ui/arkts-global-interface.md#uicontext获取方法)。 |
| options | [RenderOptions](arkts-arkui-buildernode-renderoptions-i.md) | 否 | BuilderNode的构造可选参数。<br/>默认值：undefined |

## dispose

```TypeScript
dispose(): void
```

立即释放当前BuilderNode对象对[实体节点](../../../../ui/arkts-user-defined-node.md#基本概念)的引用关系。关于BuilderNode的解绑场景请参见[节点解绑](../../../../ui/arkts-user-defined-arktsNode-builderNode.md#解除实体节点引用关系)。

> **说明：**  
>  
> 当BuilderNode对象调用dispose之后，会与后端实体节点解除引用关系。若前端对象BuilderNode无法释放，容易导致内存泄漏。建议在不再需要对该BuilderNode对象进行操作时，开发者主动调用dispose  
> 释放后端节点，以减少引用关系的复杂性，降低内存泄漏的风险。具体场景可见  
> [BuilderNode前后端循环引用导致的内存泄漏问题](../../../../ui/arkts-user-defined-node-faq.md#buildernode前后端循环引用导致的内存泄漏问题)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BuilderNode-dispose(): void--><!--Device-BuilderNode-dispose(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getFrameNode

```TypeScript
getFrameNode(): FrameNode | null
```

获取BuilderNode中的[FrameNode](arkts-arkui-framenode-c.md)。在BuilderNode执行build操作之后，才会生成FrameNode。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BuilderNode-getFrameNode(): FrameNode | null--><!--Device-BuilderNode-getFrameNode(): FrameNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](../arkts-components/arkts-arkui-framenode-t.md) | **FrameNode** object. If no such object is held by the **BuilderNode** instance, null is returned. |

## inheritFreezeOptions

```TypeScript
inheritFreezeOptions(enabled: boolean): void
```

设置当前BuilderNode对象是否继承父组件中自定义组件的冻结策略。如果设置继承状态为false，则BuilderNode对象的冻结策略为false。在这种情况下，节点在不活跃状态下不会被冻结。  
> **说明：**  
>  
> BuilderNode设置inheritFreezeOptions为true，且父组件为自定义组件、BuilderNode、ComponentContent、ReactiveBuilderNode或  
> ReactiveComponentContent时，会继承父组件的冻结策略。当子组件为自定义组件时，其冻结策略不会传递给子组件

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-BuilderNode-inheritFreezeOptions(enabled: boolean): void--><!--Device-BuilderNode-inheritFreezeOptions(enabled: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | BuilderNode对象是否设置为继承父组件中自定义组件的冻结策略。true为继承父组件中自定义组件的冻结策略，false为不继承父组件中自定义组件的冻结策略。 |

## isDisposed

```TypeScript
isDisposed(): boolean
```

查询当前BuilderNode对象是否已解除与后端实体节点的引用关系。前端节点均绑定有相应的后端实体节点，当节点调用dispose接口解除绑定后，再次调用接口可能会出现crash、返回默认值的情况。由于业务需求，可能存在节点在dispose后仍被调用接口的情况。为此，提供此接口以供开发者在操作节点前检查其有效性，避免潜在风险。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-BuilderNode-isDisposed(): boolean--><!--Device-BuilderNode-isDisposed(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 后端实体节点是否解除引用。true为节点已与后端实体节点解除引用，false为节点未与后端实体节点解除引用。 |

## postInputEvent

```TypeScript
postInputEvent(event: InputEventType): boolean
```

将事件分发到目标节点。

offsetA为builderNode相对于父组件的偏移，offsetB为命中位置相对于builderNode的偏移，offsetC为offsetA+offsetB，最终输入给postInputEvent中的window信息。

![接口坐标换算示例图](../../../../reference/apis-arkui/figures/postInputEvent-point.png)

> **说明：**  
>  
> - 传入的坐标值需要转换为px，坐标转换示例可以参考下面示例代码。  
>  
> - 鼠标左键点击事件将转换为触摸事件，转发时应注意不在外层同时绑定触摸事件与鼠标事件，否则可能导致坐标偏移。这是由于在事件转换过程中，SourceType不会发生变化，规格可查看  
> [onTouch](../../../../reference/apis-arkui/arkui-ts/ts-universal-events-touch.md#ontouch)。  
>  
> - 注入事件为轴事件[（AxisEvent）](./../@internal/component/ets/common)时，由于轴事件中缺少旋转轴信息，因此注入的事件无法触发  
> [RotationGesture](./../@internal/component/ets/gesture)。  
>  
> - 转发的事件会在被分发到的目标组件所在的子树里做touchtest，并触发对应手势，原始事件也会触发当前组件所在组件树中的手势。不保证两类手势的竞争结果。  
>  
> - 如果是开发者构造的事件，必填字段必须赋值，比如触摸事件的touches字段，轴事件的scrollStep字段。要保证事件的完整，比如触摸事件的  
> [TouchType](./../@internal/component/ets/enums)中DOWN和UP字段都要有，防止出现未定义行为。  
>  
> - [webview](../../apis-arkweb/arkts-apis/arkts-web-webview.md)已经处理过坐标系变换，可以将事件直接下发。  
>  
> - postTouchEvent接口需要提供手势坐标相对于post事件对端内的局部坐标，postInputEvent接口需要提供手势坐标相对于post事件对端内的窗口坐标。  
>  
> - 不建议同一个事件转发多次。不支持[UIExtensionComponent](./../@internal/component/ets/ui_extension_component)。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-BuilderNode-postInputEvent(event: InputEventType): boolean--><!--Device-BuilderNode-postInputEvent(event: InputEventType): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [InputEventType](arkts-arkui-inputeventtype-t.md) | 是 | 用于透传的输入事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 事件是否被成功派发。如果事件派发成功，则返回true；否则，返回false。 |

## postInputEventWithStrategy

```TypeScript
postInputEventWithStrategy(event: InputEventType, competitionStrategy?: CompetitionStrategy): boolean
```

将含有竞争策略的事件分发到目标UI组件节点。

接口调用前需要将event转化为对应的事件，并对event中的window参数的坐标进行转化：offsetA表示builderNode相对于父组件的偏移量，offsetB为命中位置相对于builderNode的偏移量，offsetC是offsetA与offsetB之和，最终作为event中的window参数，传递给postInputEventWithStrategy方法，具体请参考示例。

![接口坐标换算示例图](../../../../reference/apis-arkui/figures/postInputEvent-point.png)

> **说明：**  
>  
> - 传入的坐标值单位需要转换为px，坐标转换示例可以参考下面示例代码。  
>  
> - 系统在处理鼠标左键点击事件时将转换为触摸事件，转发时应注意不在外层同时绑定触摸事件与鼠标事件，否则可能导致坐标偏移。这是由于在事件转换过程中，  
> [TouchType](./../@internal/component/ets/enums)不会发生变化，规格可查看  
> [onTouch](../../../../reference/apis-arkui/arkui-ts/ts-universal-events-touch.md#ontouch)。  
>  
> - 注入事件为轴事件[AxisEvent](./../@internal/component/ets/common)时，由于轴事件中缺少旋转轴信息，因此注入的事件无法触发旋转手势  
> [RotationGesture](./../@internal/component/ets/gesture)。  
>  
> - 转发的事件会在被分发到的目标组件及其子组件里做事件处理，并触发对应手势。可以通过入参控制当前组件和目标组件手势是否为竞争关系。  
>  
> - 如果event转化为对应的事件后，该事件为开发者构造的事件，必填字段必须赋值，比如触摸事件的touches字段，轴事件的scrollStep字段。要保证事件的完整，比如触摸事件的  
> [TouchType](./../@internal/component/ets/enums)中必须同时包含DOWN和UP两个字段，防止出现程序异常或意外崩溃。  
>  
> - 支持同一个事件转发多次，不支持[UIExtensionComponent](./../@internal/component/ets/ui_extension_component)调用本接口  
> 。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-BuilderNode-postInputEventWithStrategy(event: InputEventType, competitionStrategy?: CompetitionStrategy): boolean--><!--Device-BuilderNode-postInputEventWithStrategy(event: InputEventType, competitionStrategy?: CompetitionStrategy): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [InputEventType](arkts-arkui-inputeventtype-t.md) | 是 | 用于事件分发的输入事件。 |
| competitionStrategy | [CompetitionStrategy](arkts-arkui-enums-competitionstrategy-e.md) | 否 | Whether the gesture for posting the event is in a competition scenario. By default, the gesture is not in a competition scenario. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 事件是否被成功派发。如果成功，则返回true；否则，返回false。 |

## postTouchEvent

```TypeScript
postTouchEvent(event: TouchEvent): boolean
```

将原始事件派发到某个BuilderNode创建出的FrameNode上。

postTouchEvent是从组件树的中间节点往下分发，需要变换到父组件坐标系才能分发成功，参考下图。

OffsetA为buildNode相对于父组件的偏移量，可以通过FrameNode中的[getPositionToParent](arkts-arkui-framenode-c.md#getpositiontoparent-1)获取。OffsetB为point点相对于buildNode的偏移量，可以通过[TouchEvent](../../../../reference/apis-arkui/arkui-ts/ts-universal-events-touch.md#touchevent对象说明) 获取。OffsetC为OffsetA与OffsetB的和，是传给postTouchEvent的最终结果。

![postTouchEvent](../../../../reference/apis-arkui/figures/postTouchEvent.PNG)

> **说明：**  
>  
> - 传入的坐标值需要转换为px，如果builderNode有仿射变换，则需要再叠加仿射变换。  
>  
> - 在[webview](../../../../reference/apis-arkweb/webview)中，内部已经处理过坐标系变换，可以将TouchEvent事件直接下发。  
>  
> - 同一时间戳，postTouchEvent只能调用一次。  
>  
> - 不支持[UIExtensionComponent](./../@internal/component/ets/ui_extension_component)。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BuilderNode-postTouchEvent(event: TouchEvent): boolean--><!--Device-BuilderNode-postTouchEvent(event: TouchEvent): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [TouchEvent](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-touchevent-touchevent-i.md) | 是 | 触摸事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 派发事件是否成功。true为已命中响应事件的组件，false为未命中任何可响应事件的组件。<br/>**说明：** <br/>如果未按照预期命中组件，需要确认以下几点：<br/>1.坐标系是否转换正确。<br/>2.组件是否可交互状态。<br/>3.是否绑定事件。 |

## recycle

```TypeScript
recycle(): void
```

触发BuilderNode中自定义组件的回收。自定义组件的回收是组件复用机制中的环节，具体信息请参见[@Reusable装饰器：V1组件复用](../../../../ui/state-management/arkts-reusable.md)。从API版本26.0.0开始，BuilderNode中的自定义组件支持V2组件复用，请参见[@ReusableV2装饰器：V2组件复用](../../../../ui/state-management/arkts-new-reusableV2.md)。

> **说明：**  
>  
> BuilderNode通过reuse和recycle完成其内外自定义组件之间的复用事件传递，具体使用场景请参见  
> [BuilderNode调用reuse和recycle接口实现节点复用能力](../../../../ui/arkts-user-defined-arktsNode-builderNode.md#buildernode调用reuse和recycle接口实现节点复用能力)  
> 。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BuilderNode-recycle(): void--><!--Device-BuilderNode-recycle(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## reuse

```TypeScript
reuse(param?: Object): void
```

触发BuilderNode中的自定义组件的复用。组件复用请参见[@Reusable装饰器：V1组件复用](../../../../ui/state-management/arkts-reusable.md)。关于BuilderNode的解绑场景请参见[节点解绑](../../../../ui/arkts-user-defined-arktsNode-builderNode.md#解除实体节点引用关系)。从API版本26.0.0开始，BuilderNode中的自定义组件支持V2组件复用，请参见[@ReusableV2装饰器：V2组件复用](../../../../ui/state-management/arkts-new-reusableV2.md)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BuilderNode-reuse(param?: Object): void--><!--Device-BuilderNode-reuse(param?: Object): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | Object | 否 | 用于复用BuilderNode的参数。该参数将直接用于BuilderNode中所有顶层自定义组件的复用，应该包含每个自定义组件的构造函数参数所需内容，否则，会导致未定义行为。调用此方法将同步触发内部自定义组件的[aboutToReuse](../../../../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttoreuse10)生命周期回调，并将该参数作为回调的入参。默认值为undefined，此时BuilderNode中的自定义组件将直接使用构造时的数据源。 |

## update

```TypeScript
update(arg: Object): void
```

根据提供的参数更新BuilderNode，该参数与[build](arkts-arkui-buildernode-c.md#build-1)方法调用时传入的参数类型相同。对自定义组件进行update的时候需要在自定义组件中将使用的变量定义为[@Prop](../../../../ui/state-management/arkts-prop.md)类型。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BuilderNode-update(arg: Object): void--><!--Device-BuilderNode-update(arg: Object): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arg | Object | 是 | 用于更新BuilderNode的参数，和[build](arkts-arkui-buildernode-c.md#build-1)调用时传入的参数类型一致。 |

## updateConfiguration

```TypeScript
updateConfiguration(): void
```

传递系统环境变化事件，触发节点的全量更新。系统环境变化的相关信息请参见[@ohos.app.ability.Configuration (环境变量)](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-configuration-configuration-i.md)。

> **说明：**  
>  
> updateConfiguration接口用于通知对象更新，更新所使用的系统环境由应用当前的系统环境变化决定。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BuilderNode-updateConfiguration(): void--><!--Device-BuilderNode-updateConfiguration(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

