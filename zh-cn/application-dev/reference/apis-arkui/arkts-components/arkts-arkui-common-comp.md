# Common

Common通用接口

## Common

```TypeScript
Common()
```

构造器。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 装饰器

| 名称 | 说明 |
| --- | --- |
| [@AnimatableExtend](arkts-arkui-common-comp-animatableextend-d.md) | @AnimatableExtend装饰器用于自定义可动画的属性方法，该装饰器内定义的函数在动画过程中会被逐帧调用，直到动画结束。 |
| [@Builder](arkts-arkui-common-comp-builder-d.md) | \@Builder装饰的函数也称为“自定义构建函数”，用于封装可复用的UI构建逻辑，可在自定义组件中多次调用，从而减少代码重复、提升UI构建的可维护性，适用于需要复用相同UI结构的场景。 |
| [@BuilderParam](arkts-arkui-common-comp-builderparam-d.md) | \@BuilderParam用于装饰指向[@Builder](arkts-arkui-common-comp-builder-d.md#builder)函数的变量，使自定义组件能够接收外部传入的\@Builder函数，实现UI内容的自定义渲染。适用于需要将父组件的UI构建逻辑传递给子组件、实现组件内容动态定制的场景。 |
| [@Component](arkts-arkui-common-comp-component-d.md) | \@Component装饰器能装饰struct关键字声明的结构体。struct被\@Component装饰后具备组件化的能力，可实现UI的封装与复用，适用于构建可复用的自定义组件、拆分复杂界面等场景。使用时需要实现build方法描述UI，一个struct只能被一个\@Component装饰。 |
| [@ComponentV2](arkts-arkui-common-comp-componentv2-d.md) | @ComponentV2主要配合状态管理V2使用，相比[\@Component](../../../ui/state-management/arkts-create-custom-components.md#component)，@ComponentV2支持对象的深度观测和深度监听，装饰器易用性高、拓展性强，适用于需要深度观测嵌套对象状态的场景。除非特别说明，@ComponentV2装饰的自定义组件将与@Component装饰的自定义组件保持相同的行为。 |
| [@Computed](arkts-arkui-common-comp-computed-d.md) | @Computed为方法装饰器，用于状态管理V2中，装饰getter方法，使其变为计算属性，其返回值会被缓存，仅当依赖的源数据发生变化时才重新计算，减少重复计算带来的开销。 |
| [@Concurrent](arkts-arkui-common-comp-concurrent-d.md) | Defining Concurrent MethodDecorator |
| [@Consume](arkts-arkui-common-comp-consume-d.md) | [@Provide](arkts-arkui-common-comp-provide-d.md#provide)和\@Consume配套使用，用于[状态管理V1](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)，实现跨组件层级的双向同步，适用于需要在多层嵌套组件间共享状态的场景，能够避免逐层传递的繁琐，简化组件间的通信逻辑。\@Consume装饰的变量作为数据消费方，通过别名或变量名与\@Provide装饰的变量建立双向绑定关系。当\@Provide或\@Consume装饰的变量发生变化时，变化会自动同步到对方。匹配规则：优先使用别名匹配，若未设置别名则使用变量名匹配。 |
| [@Consumer](arkts-arkui-common-comp-consumer-d.md) | [@Provider](arkts-arkui-common-comp-provider-d.md#provider)和@Consumer搭配使用，用于[状态管理V2](../../../ui/state-management/arkts-state-management-overview.md#状态管理v2)中，实现跨组件层级的数据双向同步。@Consumer装饰数据消费方，从数据源获取数据，适用于多层嵌套组件间需要共享和同步状态的场景，可避免通过多层组件逐级传递数据的繁琐操作，简化跨组件层级状态管理。如果@Consumer在组件树中未找到别名匹配的@Provider，将使用自身初始值，不进行数据同步。 |
| [@CustomDialog](arkts-arkui-common-comp-customdialog-d.md) | Defining CustomDialog ClassDecorator |
| [@CustomEnv](arkts-arkui-common-comp-customenv-d.md) | 用于获取自定义环境变量。 |
| [@Entry](arkts-arkui-common-comp-entry-d.md) | \@Entry装饰的自定义组件将作为UI页面的入口，被框架识别为页面的根组件，适用于构建独立UI页面的场景。 |
| [@Env](arkts-arkui-common-comp-env-d.md) | 定义Env PropertyDecorator。 |
| [@Event](arkts-arkui-common-comp-event-d.md) | @Event装饰回调方法，用于状态管理V2中，作为自定义组件的输出。@Event通常与@Param配合使用，@Param负责由父组件向子组件传递数据，@Event负责定义子组件向父组件传递消息的回调接口，适用于需要在子组件中触发父组件状态变更或事件处理的场景。 |
| [@Extend](arkts-arkui-common-comp-extend-d.md) | \@Extend装饰器用于扩展指定组件的样式，支持在装饰的函数中统一定义多个样式属性，并可通过参数传递实现样式的灵活复用，适用于需要将相同样式应用到多个组件、减少样式代码重复的场景。 |
| [@Link](arkts-arkui-common-comp-link-d.md) | @Link用于[状态管理V1](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)，接收父组件传入的状态变量的引用，建立父子组件间的双向数据绑定。适用于需要在子组件中直接修改父组件状态、简化父子组件通信的场景。 |
| [@Local](arkts-arkui-common-comp-local-d.md) | @Local用于状态管理V2中，表示组件内部的状态，使得自定义组件内部的变量具有观测能力。适用于需要在自定义组件内部维护和观测局部状态的场景（如计数器、开关状态等）。使用@Local可以简化组件内部状态管理逻辑，当状态变化时自动触发UI刷新，无需手动管理。 |
| [@LocalBuilder](arkts-arkui-common-comp-localbuilder-d.md) | `@LocalBuilder`拥有和局部[`@Builder`](arkts-arkui-common-comp-builder-d.md#builder)相同的功能，且比局部`@Builder`能够更好地确定组件的父子关系和状态管理的父子关系。适用于需要在自定义构建函数中维持组件父子关系，并保持状态管理同步的场景。开发指南参考：[`@LocalBuilder`装饰器：维持组件关系](../../../ui/state-management/arkts-localBuilder.md)。 |
| [@LocalStorageLink](arkts-arkui-common-comp-localstoragelink-d.md) | @LocalStorageLink在状态管理V1中使用，用于与LocalStorage中指定键名对应的属性建立双向数据同步：@LocalStorageLink装饰的变量与LocalStorage中对应属性任一方发生变化时，变更均会同步到另一方。适用于需要在多个组件间共享UI状态并与LocalStorage保持数据实时同步的场景，可避免逐层传递数据，保证跨组件数据一致性。 |
| [@LocalStorageProp](arkts-arkui-common-comp-localstorageprop-d.md) | @LocalStorageProp在状态管理V1中使用，用于与LocalStorage中指定键名对应的属性建立单向数据同步：LocalStorage中对应属性值的变更会同步到@LocalStorageProp装饰的变量，但仅修改@LocalStorageProp装饰的变量不会同步回LocalStorage。适用于需要在多个组件间共享LocalStorage且仅保持单向数据流的场景，可避免不必要的数据回写。 |
| [@Monitor](arkts-arkui-common-comp-monitor-d.md) | @Monitor装饰器在状态管理V2中用于监听状态变量修改，使得状态变量支持深度监听。适用于需要在状态变量或其嵌套属性发生变化时执行自定义逻辑（如数据同步、UI刷新、日志记录等）的场景。相比状态管理V1的@Watch，@Monitor支持深度监听嵌套对象属性的变化，并从API版本26.0.0开始支持通配符能力，可更灵活地匹配状态变量路径。 |
| [@ObjectLink](arkts-arkui-common-comp-objectlink-d.md) | @ObjectLink用于状态管理V1中，接收\@Observed装饰的类的实例，并与父组件中的数据源建立双向数据绑定，适用于在子组件中独立观察并监听嵌套类属性并触发UI刷新的场景。 |
| [@Observed](arkts-arkui-common-comp-observed-d.md) | \@Observed是类装饰器，用于状态管理V1中，观察嵌套类对象的属性变化。 |
| [@ObservedV2](arkts-arkui-common-comp-observedv2-d.md) | @ObservedV2是类装饰器，用于状态管理V2中。@ObservedV2与@Trace配套使用，装饰类以及类中的属性，使得被装饰的类和属性具有深度观测的能力。相较于状态管理V1的@Observed，@ObservedV2提供了更细粒度的属性级深度观测能力，适用于需要精确追踪嵌套对象属性变化并驱动UI更新的场景，能够有效提升状态管理的性能和灵活性。 |
| [@Once](arkts-arkui-common-comp-once-d.md) | @Once作为辅助装饰器，用于状态管理V2中，需要搭配[ |
| [@Param](arkts-arkui-common-comp-param-d.md) | @Param在状态管理V2中用于接收外部输入，实现父子组件之间的单向数据同步。适用于父组件需要向子组件单向传递状态数据的场景，能够简化组件间通信，保证数据流向清晰。@Param装饰的变量不允许在组件内部直接修改，如需子组件向父组件同步数据，请配合@Event使用。 |
| [@Preview](arkts-arkui-common-comp-preview-d.md) | 定义预览类装饰器。 |
| [@Prop](arkts-arkui-common-comp-prop-d.md) | @Prop用于[状态管理V1](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)，接收外部传入值，并与父组件建立单向同步关系。当父组件中[@State](arkts-arkui-common-comp-state-d.md#state)等装饰的状态变量发生变化时，会同步更新到子组件中对应的@Prop变量，触发子组件重新渲染。@Prop采用单向数据流机制，子组件对@Prop变量的修改仅在子组件内部生效，不会反向同步到父组件。适用于子组件需要响应父组件状态变化但不需要反向修改的场景。 |
| [@Provide](arkts-arkui-common-comp-provide-d.md) | \@Provide和[@Consume](arkts-arkui-common-comp-consume-d.md#consume)配套使用，用于[状态管理V1](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)，实现跨组件层级的双向同步，适用于需要跨越多层组件传递状态、避免逐层传递的场景，能够解决组件层级较深时状态传递繁琐的问题。\@Provide装饰的变量作为数据源，通过别名或变量名与\@Consume装饰的变量建立双向绑定关系。当\@Provide或\@Consume装饰的变量发生变化时，变化会自动同步到对方。 |
| [@Provider](arkts-arkui-common-comp-provider-d.md) | @Provider和@Consumer搭配使用，用于状态管理V2中，实现跨组件层级的数据双向同步。@Provider装饰数据提供方，为子组件提供数据，适用于组件层级较深、需要跨多层组件共享状态且避免逐层传递数据的场景，可简化状态管理流程，降低组件间的耦合度。 |
| [@Require](arkts-arkui-common-comp-require-d.md) | \@Require装饰器用于校验[\@Prop](../../../ui/state-management/arkts-prop.md)、[\@State](../../../ui/state-management/arkts-state.md)、[\@Provide](../../../ui/state-management/arkts-provide-and-consume.md)、[\@BuilderParam](../../../ui/state-management/arkts-builderparam.md)、[\ |
| [@Reusable](arkts-arkui-common-comp-reusable-d.md) | 为了降低反复创建销毁自定义组件带来的性能开销，开发者可以使用\@Reusable装饰\@Component装饰的自定义组件，实现组件复用。\@Reusable支持通过reuseId标识不同类型的可复用组件，提供aboutToReuse回调接收复用参数，并支持配置内存优化策略。该装饰器适用于列表滚动、频繁切换组件显示与隐藏等需要反复创建销毁组件的场景。 |
| [@ReusableV2](arkts-arkui-common-comp-reusablev2-d.md) | 为了降低反复创建销毁自定义组件带来的性能开销，开发者可以使用\@ReusableV2装饰[\@ComponentV2](arkts-arkui-common-comp-componentv2-d.md#componentv2)装饰的自定义组件，达成组件复用的效果，适用于列表滚动、频繁切换组件显示/隐藏等需要反复创建和销毁组件的场景，支持通过参数配置内存优化策略。 |
| [@Sendable](arkts-arkui-common-comp-sendable-d.md) | Defining Sendable ClassDecorator The Sendable decorator can be used only for classes. A class with this decorator is marked as sendable, and the class object can be shared globally. Since 12, the Sendable decorator can be used for function and typeAlias also. A function with this decorator is marked as sendable, and the function can be an shareable property of sendable-class object. A typeAlias with this decorator is marked as sendable, and the typeAlias can be used to declare properties, variables, and arguments that need to be assigned with sendable-function. |
| [@State](arkts-arkui-common-comp-state-d.md) | @State用于[状态管理V1](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)，将自定义组件内的普通变量转变为状态变量，当状态变量变化时，触发组件内UI重新渲染。适用于需要在组件内管理可变状态的场景。 |
| [@StorageLink](arkts-arkui-common-comp-storagelink-d.md) | @StorageLink是状态管理V1的装饰器，用于与AppStorage中指定键名的属性建立双向数据同步：当@StorageLink装饰的变量发生变化时，变更会同步到AppStorage中该键名对应的属性；当AppStorage中该键名对应的属性发生变化时，变更也会同步回@StorageLink装饰的变量。适用于需要跨页面、跨Ability共享AppStorage全局状态并与AppStorage保持双向数据同步的场景，可避免逐层传递状态数据，保证数据一致性。 |
| [@StorageProp](arkts-arkui-common-comp-storageprop-d.md) | @StorageProp用于状态管理V1中，与AppStorage中对应的属性建立单向数据同步。AppStorage中对应属性的变化会同步到@StorageProp装饰的变量，但仅修改@StorageProp装饰的变量不会同步回AppStorage。适用于需要跨页面、跨Ability感知AppStorage全局状态变化且仅保持单向数据流的场景，可避免不必要的数据回写。 |
| [@Styles](arkts-arkui-common-comp-styles-d.md) | \@Styles装饰器用于将多条样式设置提炼为一个方法，在组件声明处直接调用，实现自定义样式的定义与复用。适用于多个组件需要共享相同样式、减少重复代码、提升样式一致性维护效率的场景。 |
| [@SyncMonitor](arkts-arkui-common-comp-syncmonitor-d.md) | @SyncMonitor用于[状态管理V2](../../../ui/state-management/arkts-state-management-overview.md#状态管理v2)，同步监听状态变量修改，使得状态变量支持深度监听。适用于需要精确监听对象嵌套属性变化、数组元素修改等深层状态变化的场景，解决了传统监听方式无法感知深层属性变化的问题，提升状态管理的精确性和开发效率。 |
| [@Trace](arkts-arkui-common-comp-trace-d.md) | @Trace是属性装饰器，用于[状态管理V2](../../../ui/state-management/arkts-state-management-overview.md#状态管理v2)中。[@ObservedV2](arkts-arkui-common-comp-observedv2-d.md#observedv2)与@Trace配套使用，装饰类以及类中的属性，使被装饰的类和属性具有深度观测能力，即能够深度观测嵌套对象中属性值的变化，并触发UI自动刷新，适用于需要精确观测和管理类属性变化状态的场景。 |
| [@Track](arkts-arkui-common-comp-track-d.md) | @Track用于状态管理V1中，通过装饰class对象的指定属性实现属性级精准观测。当被@Track装饰的属性发生变化时，系统仅更新依赖该属性的UI组件，从而减少不必要的UI重渲染。适用于class对象包含较多属性，需要减少冗余UI刷新、优化渲染性能的场景。 |
| [@Watch](arkts-arkui-common-comp-watch-d.md) | @Watch装饰器用于状态管理V1中，监听状态变量的变化，并在变量变化时触发指定回调函数。适用于状态变量变化时需要自动执行联动逻辑、数据同步或计算衍生值的场景。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AccessibilityHoverEvent](arkts-arkui-accessibilityhoverevent-i.md) | The accessibility hover action triggers this method invocation. |
| [AlignRuleOption](arkts-arkui-alignruleoption-i.md) | Defines the align rule options of relative container. |
| [AnimatableArithmetic](arkts-arkui-animatablearithmetic-i.md) | 该接口定义非number数据类型的动画运算规则。对非number类型的数据（如数组、结构体、颜色等）做动画，需要实现AnimatableArithmetic\&lt;T\&gt;接口中加法、减法、乘法和判断相等函数，使得该数据能参与动画的插值运算和识别该数据是否发生改变。即定义它们为实现了AnimatableArithmetic\&lt;T\&gt;接口的类型。 |
| [AnimateParam](arkts-arkui-animateparam-i.md) | 动画效果相关参数。 |
| [AreaChangeOptions](arkts-arkui-areachangeoptions-i.md) | 区域变化相关的参数。 |
| [AttributeModifier](arkts-arkui-attributemodifier-i.md) | Defines the attribute modifier. |
| [AxisEvent](arkts-arkui-axisevent-i.md) | 轴事件的对象说明，继承于[BaseEvent](arkts-arkui-baseevent-i.md)。 |
| [BackgroundBlurStyleOptions](arkts-arkui-backgroundblurstyleoptions-i.md) | 继承自[BlurStyleOptions](arkts-arkui-blurstyleoptions-i.md)。 |
| [BackgroundBrightnessOptions](arkts-arkui-backgroundbrightnessoptions-i.md) | 背景亮度选项。 |
| [BackgroundEffectOptions](arkts-arkui-backgroundeffectoptions-i.md) | 背景效果参数。 |
| [BackgroundImageOptions](arkts-arkui-backgroundimageoptions-i.md) | 定义背景图选项。 |
| [BackgroundOptions](arkts-arkui-backgroundoptions-i.md) | background配置选项。 |
| [BaseEvent](arkts-arkui-baseevent-i.md) | 基础事件类型。 |
| [BindOptions](arkts-arkui-bindoptions-i.md) | 半模态、全模态的公共配置接口。 |
| [BlurOptions](arkts-arkui-bluroptions-i.md) | 灰阶模糊参数。 |
| [BlurSnapshotOptions](arkts-arkui-blursnapshotoptions-i-sys.md) | 模糊快照优化选项。设置该对象后，将开启模糊优化。 |
| [BlurStyleOptions](arkts-arkui-blurstyleoptions-i.md) | 模糊样式选项，用于配置模糊效果的深浅色模式、取色模式、灰阶模糊参数和模糊程度。 |
| [BorderImageOption](arkts-arkui-borderimageoption-i.md) | Border image option |
| [Callback](arkts-arkui-callback-i.md) | 定义基础的回调函数。 |
| [CaretOffset](arkts-arkui-caretoffset-i.md) | 光标相对输入框的位置信息。 |
| [ClickEffect](arkts-arkui-clickeffect-i.md) | 定义点击回弹效果。 |
| [ClickEvent](arkts-arkui-clickevent-i.md) | 继承于[BaseEvent](arkts-arkui-baseevent-i.md)。 |
| [CommonConfiguration](arkts-arkui-commonconfiguration-i.md) | 开发者需要自定义class实现ContentModifier接口。 |
| [ComponentOptions](arkts-arkui-componentoptions-i.md) | 自定义组件参数，用于配置是否支持组件冻结和全局复用池，适用于需要优化自定义组件性能表现和提升组件复用效率的场景。 |
| [Configuration](arkts-arkui-configuration-i.md) | Defines the data type of the interface restriction. |
| [ContentCoverOptions](arkts-arkui-contentcoveroptions-i.md) | 继承自[BindOptions](arkts-arkui-bindoptions-i.md)。 |
| [ContentModifier](arkts-arkui-contentmodifier-i.md) | 开发者需要自定义class实现ContentModifier接口。 |
| [ContextMenuAnimationOptions](arkts-arkui-contextmenuanimationoptions-i.md) | 长按预览时显示的样式信息。 |
| [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md) | 菜单项的信息。 |
| [CrownEvent](arkts-arkui-crownevent-i.md) | 组件接收表冠事件的数据结构。内容包括时间戳、旋转角速度、旋转角度、表冠动作和阻止事件冒泡。 |
| [CustomPopupOptions](arkts-arkui-custompopupoptions-i.md) | 弹出自定义气泡的信息。 |
| [DateRange](arkts-arkui-daterange-i.md) | Defines a range of dates. |
| [DepthColorRGB](arkts-arkui-depthcolorrgb-i-sys.md) | 深度空间中的RGB颜色。用于为组件设置空间效果参数。 |
| [DepthVector3](arkts-arkui-depthvector3-i-sys.md) | 深度空间中的三维向量。用于为组件设置空间效果参数。 |
| [DepthVector4](arkts-arkui-depthvector4-i-sys.md) | 深度空间中的4D向量。用于为组件设置空间效果参数。 |
| [DismissContentCoverAction](arkts-arkui-dismisscontentcoveraction-i.md) |  |
| [DismissPopupAction](arkts-arkui-dismisspopupaction-i.md) | 气泡关闭的信息。 |
| [DismissSheetAction](arkts-arkui-dismisssheetaction-i.md) | 半模态关闭前的回调。 |
| [DragEvent](arkts-arkui-dragevent-i.md) | 拖拽事件信息。 |
| [DragInteractionOptions](arkts-arkui-draginteractionoptions-i.md) | 设置拖拽过程中预览图浮起的交互模式。 |
| [DragItemInfo](arkts-arkui-dragiteminfo-i.md) | 定义拖拽过程中拖拽项的相关信息。 |
| [DragPreviewOptions](arkts-arkui-dragpreviewoptions-i.md) | 设置拖拽过程中预览图处理模式及数量角标的显示。 |
| [DropOptions](arkts-arkui-dropoptions-i.md) | 设置落入过程的参数。 |
| [EdgeEffectOptions](arkts-arkui-edgeeffectoptions-i.md) | edgeEffect属性参数对象。 |
| [EdgeLightParams](arkts-arkui-edgelightparams-i-sys.md) | 定义边缘流光效果参数。 |
| [EditModeOptions](arkts-arkui-editmodeoptions-i.md) | List/Grid组件编辑模式选项属性参数对象。 |
| [EntryOptions](arkts-arkui-entryoptions-i.md) | 页面入口配置选项，用于在\@Entry装饰页面时配置路由名称、状态存储和共享存储等参数。 |
| [EventTarget](arkts-arkui-eventtarget-i.md) | [BaseEvent](arkts-arkui-baseevent-i.md)中参数target的类型。 |
| [ExpectedFrameRateRange](arkts-arkui-expectedframeraterange-i.md) | 设置动画期望的帧率。 |
| [FadingEdgeOptions](arkts-arkui-fadingedgeoptions-i.md) | fadingEdge属性边缘渐隐参数对象。 |
| [FocusAxisEvent](arkts-arkui-focusaxisevent-i.md) | 焦点轴事件的对象说明，继承于[BaseEvent](arkts-arkui-baseevent-i.md)。 |
| [FocusMovement](arkts-arkui-focusmovement-i.md) | 设置对应的按键对应的走焦目的组件，缺省则遵循默认走焦规则。 |
| [ForegroundBlurStyleOptions](arkts-arkui-foregroundblurstyleoptions-i.md) | 继承自[BlurStyleOptions](arkts-arkui-blurstyleoptions-i.md)，内容模糊样式选项。 |
| [ForegroundEffectOptions](arkts-arkui-foregroundeffectoptions-i.md) | 前景效果参数，用于配置组件前景的模糊半径，控制前景内容的模糊程度。 |
| [GeometryInfo](arkts-arkui-geometryinfo-i.md) | 父组件（自定义组件）布局信息，继承自[SizeResult](arkts-arkui-sizeresult-i.md)。 |
| [GeometryTransitionOptions](arkts-arkui-geometrytransitionoptions-i.md) |  |
| [GestureModifier](arkts-arkui-gesturemodifier-i.md) | 开发者需要自定义class实现GestureModifier接口。 |
| [GravityCenterOptions](arkts-arkui-gravitycenteroptions-i-sys.md) | 定义引力中心参数。 |
| [HistoricalPoint](arkts-arkui-historicalpoint-i.md) | 历史点信息。 |
| [HorizontalAlignParam](arkts-arkui-horizontalalignparam-i.md) | 定义相对容器的水平对齐规则。 |
| [HoverEvent](arkts-arkui-hoverevent-i.md) | 继承于[BaseEvent](arkts-arkui-baseevent-i.md)。 |
| [ICurve](arkts-arkui-icurve-i.md) | 曲线对象。 |
| [IMonitor](arkts-arkui-imonitor-i.md) | 当监听的状态变量变化时，状态管理框架侧将回调开发者注册的函数，并传入变化信息。变化信息的类型为IMonitor。 |
| [IMonitorValue](arkts-arkui-imonitorvalue-i.md) | @Monitor监听状态变量变化的具体信息，通过IMonitor的value接口获取。T为状态变量类型。 |
| [InputCounterOptions](arkts-arkui-inputcounteroptions-i.md) | 计数器的配置项。 |
| [InputEventInterceptResult](arkts-arkui-inputeventinterceptresult-i.md) | 输入事件拦截结果接口，用于监听器回调[InputEventListener](arkts-arkui-inputeventlistener-t.md)返回是否拦截的决策。 |
| [InputEventMonitor](arkts-arkui-inputeventmonitor-i.md) | 输入事件监听器标识对象。 |
| [InvertOptions](arkts-arkui-invertoptions-i.md) | 前景智能取反色。基于灰度阈值区间决定反色取值，参见[invert](arkts-arkui-commonmethod-c.md#invert)中的详细机制说明。 |
| [ItemDragEventHandler](arkts-arkui-itemdrageventhandler-i.md) | 定义拖拽事件 |
| [ItemDragInfo](arkts-arkui-itemdraginfo-i.md) | 拖拽点信息对象。 |
| [KeyEvent](arkts-arkui-keyevent-i.md) | 按键事件信息。 |
| [KeyframeAnimateParam](arkts-arkui-keyframeanimateparam-i.md) | 动画选项设置。 |
| [KeyframeState](arkts-arkui-keyframestate-i.md) | 关键帧状态设置。 |
| [Layoutable](arkts-arkui-layoutable-i.md) | 子组件布局信息。 |
| [LayoutBorderInfo](arkts-arkui-layoutborderinfo-i.md) | 子组件边框信息 |
| [LayoutChild](arkts-arkui-layoutchild-i.md) | 布局和测量发生时，框架传递给子组件的信息。 |
| [LayoutInfo](arkts-arkui-layoutinfo-i.md) | 子组件布局位置信息 |
| [LightSource](arkts-arkui-lightsource-i-sys.md) | 一个组件支持添加1个光源。 |
| [LinearGradient](arkts-arkui-lineargradient-i.md) | Linear Gradient Interface |
| [LinearGradientBlurOptions](arkts-arkui-lineargradientbluroptions-i.md) |  |
| [LinearGradientOptions](arkts-arkui-lineargradientoptions-i.md) | 线性渐变的参数。 |
| [LocalizedAlignRuleOptions](arkts-arkui-localizedalignruleoptions-i.md) | Defines the Localized align rule options of relative container. |
| [LocalizedHorizontalAlignParam](arkts-arkui-localizedhorizontalalignparam-i.md) | Defines the localized horizontal align param of relative container. |
| [LocalizedVerticalAlignParam](arkts-arkui-localizedverticalalignparam-i.md) | Defines the localized vertical align param of relative container. |
| [Measurable](arkts-arkui-measurable-i.md) | 子组件位置信息。 |
| [MeasureResult](arkts-arkui-measureresult-i.md) | Sub component MeasureResult info. |
| [MenuElement](arkts-arkui-menuelement-i.md) | 菜单项的图标、文本和交互信息。 |
| [MenuGridStyleOptions](arkts-arkui-menugridstyleoptions-i.md) | 菜单栅格样式选项。 |
| [MenuMaskType](arkts-arkui-menumasktype-i.md) | 设置蒙层样式。 |
| [MenuOptions](arkts-arkui-menuoptions-i.md) | 配置弹出菜单的参数，继承自[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)。 |
| [MonitorDecoratorOptions](arkts-arkui-monitordecoratoroptions-i.md) | @Monitor装饰器的配置选项。 |
| [MotionBlurAnchor](arkts-arkui-motionbluranchor-i.md) | 运动模糊锚点坐标。 |
| [MotionBlurOptions](arkts-arkui-motionbluroptions-i.md) | 运动模糊选项。 |
| [MotionPathOptions](arkts-arkui-motionpathoptions-i.md) | 路径动画的运动路径参数选项。 |
| [MouseEvent](arkts-arkui-mouseevent-i.md) | 继承于[BaseEvent](arkts-arkui-baseevent-i.md)。 |
| [MouseHistoricalPoint](arkts-arkui-mousehistoricalpoint-i.md) | 鼠标事件历史点信息。 |
| [MultiShadowOptions](arkts-arkui-multishadowoptions-i.md) | 投影样式参数。 |
| [NestedScrollOptions](arkts-arkui-nestedscrolloptions-i.md) | nestedScroll属性参数对象。 |
| [OverlayOffset](arkts-arkui-overlayoffset-i.md) | 设置浮层基于自身左上角的偏移量。浮层默认处于组件左上角。 |
| [OverlayOptions](arkts-arkui-overlayoptions-i.md) | 浮层的定位。 |
| [PickerDialogButtonStyle](arkts-arkui-pickerdialogbuttonstyle-i.md) | Provide an interface for the button style of picker |
| [PickerTextStyle](arkts-arkui-pickertextstyle-i.md) | Provide an interface for the text style of picker |
| [PixelMapMock](arkts-arkui-pixelmapmock-i-sys.md) | 带有release函数的像素图对象。 |
| [PixelRoundPolicy](arkts-arkui-pixelroundpolicy-i.md) | 指定组件级像素取整的方向。 |
| [PixelStretchEffectOptions](arkts-arkui-pixelstretcheffectoptions-i.md) | 像素扩展属性集合，用于描述像素扩展的信息。 |
| [PointLightStyle](arkts-arkui-pointlightstyle-i-sys.md) | 通过设置光源和被照亮的类型实现点光源照亮周围组件的UI效果。 |
| [PopupBorderLinearGradient](arkts-arkui-popupborderlineargradient-i.md) | 弹出边框线性渐变色。 |
| [PopupCommonOptions](arkts-arkui-popupcommonoptions-i.md) | 配置弹出气泡的参数。使用[UIContext](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md)中的[getPromptAction()](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction)方法获取到[PromptAction](../arkts-apis/arkts-arkui-arkui-uicontext-promptaction-c.md)对象，再通过该对象调用[openPopup](../arkts-apis/arkts-arkui-arkui-uicontext-promptaction-c.md#openpopup)和[updatePopup](../arkts-apis/arkts-arkui-arkui-uicontext-promptaction-c.md#updatepopup)时传入的options参数。 |
| [PopupMaskType](arkts-arkui-popupmasktype-i.md) | 设置遮罩层颜色。 |
| [PopupMessageOptions](arkts-arkui-popupmessageoptions-i.md) | 气泡文本的样式。 |
| [PopupOptions](arkts-arkui-popupoptions-i.md) | 基础气泡的信息。 |
| [PopupStateChangeParam](arkts-arkui-popupstatechangeparam-i.md) | 气泡的显示状态。 |
| [PreviewConfiguration](arkts-arkui-previewconfiguration-i.md) | 配置自定义拖拽过程中的预览图样式。 |
| [PreviewParams](arkts-arkui-previewparams-i.md) | @Preview参数对象。 |
| [ProvideOptions](arkts-arkui-provideoptions-i.md) | ProvideOptions是\@Provide的选项。允许在同一组件树上通过allowOverride重写同名的\@Provide，适用于子组件需要覆盖父组件同名\@Provide值的场景，提高了跨层级状态管理的灵活性。具体例子可见[\@Provide支持allowOverride参数](../../../ui/state-management/arkts-provide-and-consume.md#provide支持allowoverride参数)。 |
| [RadialGradientOptions](arkts-arkui-radialgradientoptions-i.md) | 径向渐变参数。 |
| [Rectangle](arkts-arkui-rectangle-i.md) | 矩形区域类型。 |
| [RectResult](arkts-arkui-rectresult-i.md) | 位置和尺寸类型，用于描述组件的位置和宽高。 |
| [ResponseRegion](arkts-arkui-responseregion-i.md) | 由输入工具类型、触摸位置和大小组成的触摸热区。 |
| [ReusableOptions](arkts-arkui-reusableoptions-i.md) | 可复用自定义组件的参数，用于配置内存优化策略，适用于需要降低可复用自定义组件内存使用量的场景。 |
| [ReuseOptions](arkts-arkui-reuseoptions-i.md) | 复用选项，用于配置复用标识ID，相同复用标识ID的组件会被互相复用，提高复用匹配的精确度。 |
| [RotateAngleOptions](arkts-arkui-rotateangleoptions-i.md) | 指定各轴旋转角的旋转参数选项。 |
| [RotateOptions](arkts-arkui-rotateoptions-i.md) | 组件旋转参数。 |
| [ScaleOptions](arkts-arkui-scaleoptions-i.md) | 定义缩放选项。 |
| [SelectionOptions](arkts-arkui-selectionoptions-i.md) | setTextSelection选中文字时的配置。 |
| [ShadowOptions](arkts-arkui-shadowoptions-i.md) | 阴影属性集合，用于设置阴影的模糊半径、阴影的颜色、X轴和Y轴的偏移量。 |
| [sharedTransitionOptions](arkts-arkui-sharedtransitionoptions-i.md) | 共享元素转场动效参数。 |
| [SheetDismiss](arkts-arkui-sheetdismiss-i.md) | 控制半模态的关闭。 |
| [SheetOptions](arkts-arkui-sheetoptions-i.md) | 继承自[BindOptions](arkts-arkui-bindoptions-i.md)。 |
| [SheetTitleOptions](arkts-arkui-sheettitleoptions-i.md) | 半模态面板的标题。 |
| [SizeResult](arkts-arkui-sizeresult-i.md) | 组件尺寸信息。 |
| [SmartGestureShortcutOptions](arkts-arkui-smartgestureshortcutoptions-i.md) | 智慧手势响应行为配置对象。 |
| [SpatialEffectParams](arkts-arkui-spatialeffectparams-i-sys.md) | 空间效果选项。用于为组件设置空间效果参数。 |
| [SpatialPosition](arkts-arkui-spatialposition-i-sys.md) | 三维空间中的空间角位置。用于为组件设置空间效果参数。 |
| [SpringBackAction](arkts-arkui-springbackaction-i.md) | 控制半模态关闭前的回弹。 |
| [StateStyles](arkts-arkui-statestyles-i.md) | 组件不同状态下的样式。 |
| [SweepGradientOptions](arkts-arkui-sweepgradientoptions-i.md) | 角度渐变参数。 |
| [SystemAdaptiveOptions](arkts-arkui-systemadaptiveoptions-i.md) | 系统自适应调节参数，系统会默认开启根据芯片算力进行自适应效果调节的能力。 |
| [TextContentControllerOptions](arkts-arkui-textcontentcontrolleroptions-i.md) | 用于设置输入框插入字符时的配置选项。 |
| [TextDecorationOptions](arkts-arkui-textdecorationoptions-i.md) | 文本装饰线的配置项。 |
| [TipsOptions](arkts-arkui-tipsoptions-i.md) | 悬浮气泡自定义参数。 |
| [TouchEvent](arkts-arkui-touchevent-i.md) | 继承于[BaseEvent](arkts-arkui-baseevent-i.md)。在非事件注入场景下，changedTouches是按屏幕刷新率重采样的点，而touches是按器件刷新率上报的点，因此changedTouches与touches的数据可能不同。 |
| [TouchObject](arkts-arkui-touchobject-i.md) | 触摸事件类型。 |
| [TransitionOptions](arkts-arkui-transitionoptions-i.md) | TransitionOptions通过指定结构体内的参数来指定转场效果。 |
| [TranslateOptions](arkts-arkui-translateoptions-i.md) | 定义平移选项。 |
| [UICommonEvent](arkts-arkui-uicommonevent-i.md) | 用于设置基础事件回调。方法入参为undefined的时候，重置对应的事件回调。 |
| [UIGestureEvent](arkts-arkui-uigestureevent-i.md) | 用于设置组件绑定的手势。 |
| [UIScrollableCommonEvent](arkts-arkui-uiscrollablecommonevent-i.md) | 用于设置滚动事件回调。 |
| [VerticalAlignParam](arkts-arkui-verticalalignparam-i.md) | 定义相对容器的垂直对齐规则。 |
| [VisibleAreaEventOptions](arkts-arkui-visibleareaeventoptions-i.md) | 关于区域变化相关的参数。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [AccessibilityActionInterceptCallback](arkts-arkui-accessibilityactioninterceptcallback-t.md) | 定义onAccessibilityActionIntercept中使用的回调类型。 |
| [AccessibilityCallback](arkts-arkui-accessibilitycallback-t.md) | 提供开启无障碍模式后的无障碍悬浮回调事件类型。 |
| [AccessibilityFocusCallback](arkts-arkui-accessibilityfocuscallback-t.md) | 定义onAccessibilityFocus中使用的回调类型。 |
| [AccessibilityTransparentCallback](arkts-arkui-accessibilitytransparentcallback-t.md) | 提供开启朗读类辅助应用后未能被无障碍悬浮响应的触摸事件回调类型。 |
| [AnimationRange](arkts-arkui-animationrange-t.md) | 动画开始和结束时相对预览原图缩放比例。 |
| [AreaChangeCallback](arkts-arkui-areachangecallback-t.md) | 组件区域变化事件的回调类型。 |
| [Blender](arkts-arkui-blender-t-sys.md) | [Blender](arkts-arkui-blender-t-sys.md) |
| [BorderRadiusType](arkts-arkui-borderradiustype-t.md) | 圆角类型。 |
| [BuilderCallback](arkts-arkui-buildercallback-t.md) | `BuilderCallback`是全局`@Builder`函数的类型别名，作为`mutableBuilder`函数的入参类型，用于指定待封装的全局`@Builder`函数。 |
| [CircleShape](arkts-arkui-circleshape-t.md) | 导入CircleShape类型对象。 |
| [ComponentContent](arkts-arkui-componentcontent-t.md) | 组件内容的实体封装。 |
| [Context](arkts-arkui-context-t.md) | Get context. |
| [CustomBuilder](arkts-arkui-custombuilder-t.md) | 定义CustomBuilder类型。 |
| [CustomBuilderT](arkts-arkui-custombuildert-t.md) | 定义带参数的CustomBuilder类型 |
| [DataLoadParams](arkts-arkui-dataloadparams-t.md) | 落入操作时使用的数据加载参数。 |
| [DataSyncOptions](arkts-arkui-datasyncoptions-t.md) | 作为startDataLoading的入参对象。 |
| [DragSpringLoadingConfiguration](arkts-arkui-dragspringloadingconfiguration-t.md) | 定义拖拽的悬停检测配置参数的接口。 |
| [DrawContext](arkts-arkui-drawcontext-t.md) | [DrawContext](arkts-arkui-drawcontext-t.md) |
| [EllipseShape](arkts-arkui-ellipseshape-t.md) | 导入EllipseShape类型对象。 |
| [EnvDecorator](arkts-arkui-envdecorator-t.md) | 定义EnvDecorator属性装饰器类型。 |
| [Filter](arkts-arkui-filter-t.md) | 导入Filter类型对象。 |
| [FractionStop](arkts-arkui-fractionstop-t.md) | 定义模糊段。 |
| [GestureCollectInterceptCallback](arkts-arkui-gesturecollectinterceptcallback-t.md) | 定义在[onGestureCollectIntercept](arkts-arkui-commonmethod-c.md#ongesturecollectintercept)中使用的回调类型。 |
| [GestureRecognizerJudgeBeginCallback](arkts-arkui-gesturerecognizerjudgebegincallback-t.md) | 自定义手势识别器判定回调类型。 |
| [HoverCallback](arkts-arkui-hovercallback-t.md) | hover事件的回调类型。 |
| [ImageModifier](arkts-arkui-imagemodifier-t.md) | [ImageModifier](arkts-arkui-imagemodifier-t.md) |
| [InputEventListener](arkts-arkui-inputeventlistener-t.md) | 输入事件监听器回调函数类型。 |
| [IntentionCode](arkts-arkui-intentioncode-t.md) | 按键对应的意图。 |
| [Matrix4Transit](arkts-arkui-matrix4transit-t.md) | 为普通方法导入Matrix4Transit类型对象。@typedef { import('../api/@ohos.matrix4').default.Matrix4Transit } Matrix4Transit |
| [MonitorDecorator](arkts-arkui-monitordecorator-t.md) | @Monitor装饰器的实际类型。 |
| [NavDestinationInfo](arkts-arkui-navdestinationinfo-t.md) | NavDestinationInfo实例对象。 |
| [NavigationInfo](arkts-arkui-navigationinfo-t.md) | NavigationInfo实例对象。 |
| [OnDidStopDraggingCallback](arkts-arkui-ondidstopdraggingcallback-t.md) | 滚动组件在结束拖拽时触发的回调。 |
| [OnDragEventCallback](arkts-arkui-ondrageventcallback-t.md) | 拖拽事件的回调函数。 |
| [OnGetPreviewBadgeCallback](arkts-arkui-ongetpreviewbadgecallback-t.md) | 即将启动多选长按聚拢动画时，触发用于获取选中数量的回调。 |
| [OnItemDragStartCallback](arkts-arkui-onitemdragstartcallback-t.md) | 开始拖拽列表或网格元素时触发的回调。 |
| [OnMoveHandler](arkts-arkui-onmovehandler-t.md) | 定义数据源拖拽回调。 |
| [OnNeedSoftkeyboardCallback](arkts-arkui-onneedsoftkeyboardcallback-t.md) | 当绑定该方法的组件判断是否需要键盘时，将触发此回调。前提条件：组件需可获焦，否则本接口不生效。 |
| [OnScrollCallback](arkts-arkui-onscrollcallback-t.md) | 滚动组件滑动时触发的回调。 |
| [OnVisibleIndexesChangeCallback](arkts-arkui-onvisibleindexeschangecallback-t.md) | 懒加载布局容器[LazyColumnLayout](../arkts-apis/arkts-arkui-arkui-components-arklazycolumnlayout-con.md#lazycolumnlayout)、LazyVGridLayout、[LazyVWaterFlowLayout](../arkts-apis/arkts-arkui-arkui-components-arklazywaterflowlayout-con.md#lazyvwaterflowlayout)所显示的子组件索引发生变化时的回调类型。 |
| [OnWillScrollCallback](arkts-arkui-onwillscrollcallback-t.md) | Called before scroll to allow developer to control real offset the Scrollable can scroll. |
| [OnWillStopDraggingCallback](arkts-arkui-onwillstopdraggingcallback-t.md) | 滚动组件划动离手时触发的回调。 |
| [Optional](arkts-arkui-optional-t.md) | 定义可选类型，其值可以是undefined。 |
| [PathShape](arkts-arkui-pathshape-t.md) | 导入PathShape类型对象。 |
| [PixelMap](arkts-arkui-pixelmap-t.md) | Defines the PixelMap type object for ui component. |
| [PointerStyle](arkts-arkui-pointerstyle-t.md) | 光标样式。 |
| [PopupStateChangeCallback](arkts-arkui-popupstatechangecallback-t.md) | 气泡状态变化事件回调。 |
| [PromptActionDialogController](arkts-arkui-promptactiondialogcontroller-t.md) | 从promptAction导入弹出框控制器类型 |
| [RectShape](arkts-arkui-rectshape-t.md) | 导入RectShape类型对象。 |
| [ReuseIdCallback](arkts-arkui-reuseidcallback-t.md) | 获取复用标识ID的回调方法。 |
| [ReusePoolOwnership](arkts-arkui-reusepoolownership-t.md) | 全局复用池的持有类型。 |
| [RouterPageInfo](arkts-arkui-routerpageinfo-t.md) | RouterPageInfo实例对象。 |
| [ShouldBuiltInRecognizerParallelWithCallback](arkts-arkui-shouldbuiltinrecognizerparallelwithcallback-t.md) | 系统内置手势与响应链上其他组件的手势设置并行关系的回调事件类型。 |
| [ShouldRecognizerParallelWithCallback](arkts-arkui-shouldrecognizerparallelwithcallback-t.md) | 手势与响应链上其他组件的手势设置并行关系的回调事件类型。 |
| [SizeChangeCallback](arkts-arkui-sizechangecallback-t.md) | 组件区域变化时的回调类型。 |
| [SpringLoadingContext](arkts-arkui-springloadingcontext-t.md) | 定义回调上下文信息的类，用于在悬停检测回调中传递给应用程序，使其能访问拖拽状态。 |
| [Summary](arkts-arkui-summary-t.md) | 拖拽相关数据的简介。 |
| [SymbolGlyphModifier](arkts-arkui-symbolglyphmodifier-t.md) | SymbolGlyphModifier类型，用于设置自定义图标小符号。 |
| [SystemUiMaterial](arkts-arkui-systemuimaterial-t.md) | 系统材质对象基类。 |
| [Theme](arkts-arkui-theme-t.md) | 主题对象。 |
| [TipsMessageType](arkts-arkui-tipsmessagetype-t.md) | 悬浮气泡弹窗信息。 |
| [TouchTestDoneCallback](arkts-arkui-touchtestdonecallback-t.md) | 动态指定手势识别器是否参与手势处理的回调事件类型，回调内参数的生命周期跟随回调本身，参数内的方法仅支持在回调内同步使用。 |
| [TransitionEffects](arkts-arkui-transitioneffects-t.md) | 定义所有转场效果。 |
| [TransitionFinishCallback](arkts-arkui-transitionfinishcallback-t.md) | 定义组件转场动画结束回调的类型。 |
| [UIContext](arkts-arkui-uicontext-t.md) | [UIContext](arkts-arkui-uicontext-t.md) |
| [UnifiedData](arkts-arkui-unifieddata-t.md) | 拖拽相关的数据。 |
| [UniformDataType](arkts-arkui-uniformdatatype-t.md) | 标准化数据类型。 |
| [VisibleAreaChangeCallback](arkts-arkui-visibleareachangecallback-t.md) | 组件可见区域变化事件的回调类型。 |
| [VisualEffect](arkts-arkui-visualeffect-t.md) | 导入VisualEffect类型对象。 |
| [window](arkts-arkui-window-t.md) |  |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AccessibilityAction](arkts-arkui-accessibilityaction-e.md) | 辅助功能操作类型的枚举@enum { number } |
| [AccessibilityActionInterceptResult](arkts-arkui-accessibilityactioninterceptresult-e.md) | intercept action的枚举@enum { number } |
| [AccessibilityRoleType](arkts-arkui-accessibilityroletype-e.md) | 定义组件的屏幕朗读功能角色类型。@enum { number } |
| [AccessibilitySamePageMode](arkts-arkui-accessibilitysamepagemode-e.md) | 当前跨进程嵌入式显示的组件和宿主应用的同page模式。@enum { number } |
| [AdaptiveColor](arkts-arkui-adaptivecolor-e.md) | 取色模式。 |
| [AnchoredColorMode](arkts-arkui-anchoredcolormode-e.md) | 配置组件主题跟随的颜色模式。 |
| [AvailableLayoutArea](arkts-arkui-availablelayoutarea-e.md) | 预览图宽高设置为百分比时的参考可布局区域大小。 |
| [BlendApplyType](arkts-arkui-blendapplytype-e.md) | 标识如何将指定的混合模式应用于视图的内容。 |
| [BlendMode](arkts-arkui-blendmode-e.md) | 混合模式。 |
| [BlurStyle](arkts-arkui-blurstyle-e.md) | 模糊样式类型。 |
| [BlurStyleActivePolicy](arkts-arkui-blurstyleactivepolicy-e.md) | 定义背景模糊激活策略。 |
| [ChainStyle](arkts-arkui-chainstyle-e.md) | 定义链的风格，支持attributeModifier动态设置属性方法。 |
| [ContentClipMode](arkts-arkui-contentclipmode-e.md) | 表示滚动容器的内容裁剪模式。 |
| [DismissReason](arkts-arkui-dismissreason-e.md) | 关闭原因类型。 |
| [DistortionMode](arkts-arkui-distortionmode-e-sys.md) | 非线性形变动画模式的枚举。 |
| [DragAnimationType](arkts-arkui-draganimationtype-e-sys.md) | 拖拽动画类型。 |
| [DragBehavior](arkts-arkui-dragbehavior-e.md) | 当设置[DragResult](arkts-arkui-dragresult-e.md)为DROP_ENABLED后，可设置DragBehavior为复制（COPY）或剪切（MOVE）。当DragBehavior为复制（COPY）时，拖拽对象的角标会显示加号；为剪切（MOVE）时，拖拽对象的角标不会显示加号。DragBehavior用来向开发者描述数据的处理方式是复制（COPY）还是剪切（MOVE），但无法最终决定对数据的实际处理方式。DragBehavior会通过onDragEnd带回给数据拖出方，发起拖拽的一方可通过DragBehavior来区分做出的是复制（COPY）还是剪切（MOVE）数据的不同行为。 |
| [DraggingSizeChangeEffect](arkts-arkui-draggingsizechangeeffect-e.md) | 当一个节点上同时设置长按浮起预览（参考bindContextMenu）与拖拽时，使用该字段设置长按浮起预览图与拖拽预览图过渡动效方式。 |
| [DragPreviewMode](arkts-arkui-dragpreviewmode-e.md) | 设置拖拽预览图的显示模式。 |
| [DragResult](arkts-arkui-dragresult-e.md) | 定义拖拽操作的结果及组件的落入选定状态。 |
| [EdgeLightMode](arkts-arkui-edgelightmode-e-sys.md) | 边缘光效动画模式枚举。 |
| [EffectEdge](arkts-arkui-effectedge-e.md) | 表示当前边缘效果要生效的边缘。 |
| [EffectType](arkts-arkui-effecttype-e.md) | 效果模板类型的枚举值。效果模板为预设的视觉效果参数配置，包含模糊半径、饱和度、亮度和颜色等参数。 |
| [FinishCallbackType](arkts-arkui-finishcallbacktype-e.md) | 动画中定义onFinish回调的类型。 |
| [HapticFeedbackMode](arkts-arkui-hapticfeedbackmode-e.md) | 菜单弹出时振动效果。 |
| [HoverModeAreaType](arkts-arkui-hovermodeareatype-e.md) | 悬停态显示区域类型。 |
| [KeyboardAvoidMode](arkts-arkui-keyboardavoidmode-e.md) | 气泡避让键盘时，避让模式的枚举类型。 |
| [LayoutSafeAreaEdge](arkts-arkui-layoutsafeareaedge-e.md) | 扩展安全区域的边缘。 |
| [LayoutSafeAreaType](arkts-arkui-layoutsafeareatype-e.md) | 扩展布局安全区域的枚举类型。 |
| [MenuGridPosition](arkts-arkui-menugridposition-e.md) | 栅格菜单在菜单中的位置枚举值。 |
| [MenuKeyboardAvoidMode](arkts-arkui-menukeyboardavoidmode-e.md) | 菜单避让软键盘的模式。 |
| [MenuPolicy](arkts-arkui-menupolicy-e.md) | 菜单弹出的策略。 |
| [MenuPreviewMode](arkts-arkui-menupreviewmode-e.md) | 菜单的预览样式。 |
| [ModalMode](arkts-arkui-modalmode-e.md) | 子窗菜单的模态模式。 |
| [ModalTransition](arkts-arkui-modaltransition-e.md) | 全屏模态转场方式枚举类型，用于设置全屏模态转场类型。 |
| [OutlineStyle](arkts-arkui-outlinestyle-e.md) | 外描边样式。 |
| [PreDragStatus](arkts-arkui-predragstatus-e.md) | 定义拖拽手势触发前的各阶段状态。 |
| [PreviewScaleMode](arkts-arkui-previewscalemode-e.md) | 预览图的缩放方式。 |
| [RepeatMode](arkts-arkui-repeatmode-e.md) | 用于设置被切割的图片在边框上的重复方式。 |
| [ReusableMemOptStrategy](arkts-arkui-reusablememoptstrategy-e.md) | 可复用自定义组件内存优化策略枚举。 |
| [SafeAreaEdge](arkts-arkui-safeareaedge-e.md) | 扩展安全区域的边缘。 |
| [SafeAreaType](arkts-arkui-safeareatype-e.md) | 扩展安全区域的枚举类型。 |
| [ScrollSizeMode](arkts-arkui-scrollsizemode-e.md) | 半模态面板上下滑动时的内容更新方式。 |
| [ShadowStyle](arkts-arkui-shadowstyle-e.md) | 组件阴影效果。 |
| [ShadowType](arkts-arkui-shadowtype-e.md) | 阴影类型。 |
| [SheetKeyboardAvoidMode](arkts-arkui-sheetkeyboardavoidmode-e.md) | 半模态激活输入法时对软键盘的避让方式。 |
| [SheetMode](arkts-arkui-sheetmode-e.md) | 半模态的显示层级模式。 |
| [SheetSize](arkts-arkui-sheetsize-e.md) | 指定半模态的高度。 |
| [SheetType](arkts-arkui-sheettype-e.md) | 半模态弹窗的样式。 |
| [SourceTool](arkts-arkui-sourcetool-e.md) | 定义输入源对应的工具类型。 |
| [SourceType](arkts-arkui-sourcetype-e.md) | 定义输入源对应的设备类型。 |
| [SystemProperties](arkts-arkui-systemproperties-e.md) | 定义系统环境变量枚举值 |
| [ThemeColorMode](arkts-arkui-themecolormode-e.md) | 设置颜色模式。 |
| [TouchTestStrategy](arkts-arkui-touchteststrategy-e.md) | 事件派发策略。 |
| [TransitionEdge](arkts-arkui-transitionedge-e.md) | 转场边缘类型。 |
| [TransitionHierarchyStrategy](arkts-arkui-transitionhierarchystrategy-e-sys.md) | 共享元素动画过程中in/out组件层级位置移动策略枚举。 |

## 示例

```TypeScript
该示例主要演示通过foregroundBlurStyle为图片设置内容模糊效果。
```

```TypeScript
### 示例1（半模态设置边缘光效动画）

以下示例通过设置edgeLightMode属性开启边缘光效动画，同时使用[SheetOptions](ts-universal-attributes-sheet-transition.md#sheetoptions)中的systemMaterial接口实现了半透明材质效果。

从API版本26.0.0开始，[SheetOptions](arkts-arkui-sheetoptions-i.md)新增edgeLightMode属性。


```

```TypeScript
### 示例2（半模态设置模糊优化）

以下示例通过设置blurSnapshot属性开启模糊优化。当使用[SheetOptions](ts-universal-attributes-sheet-transition.md#sheetoptions)中的systemMaterial接口设置材质效果或使用[SheetOptions](ts-universal-attributes-sheet-transition.md#sheetoptions)中的blurStyle接口设置模糊时发现功耗明显增加时，可以尝试开启模糊优化。

从API版本26.0.0开始，[SheetOptions](arkts-arkui-sheetoptions-i.md)新增blurSnapshot属性。
```

```TypeScript
属性动画状态下添加运动模糊效果。
```

```TypeScript
### 示例1（设置键盘接续）

该示例通过[onNeedSoftkeyboard](arkts-arkui-commonmethod-c.md#onneedsoftkeyboard)接口，设置按钮需要键盘。在从输入框拉起键盘后，点击按钮使焦点切换到按钮，此时键盘将不会收起，再次点击输入框可继续输入。

从API version 24开始，新增[onNeedSoftkeyboard](arkts-arkui-commonmethod-c.md#onneedsoftkeyboard)接口。
```

```TypeScript
该示例通过setCursor实现了鼠标光标样式的设置。
```

```TypeScript
该示例实现了组件注册表冠事件，并上报接收到的表冠事件数据内容。
```

```TypeScript
### 示例1（List使用OnMove进行拖拽）

以下示例展示了ForEach在List组件内使用时的拖拽效果。
```

```TypeScript
### 示例2（List使用OnMove进行拖拽，并设置拖拽事件回调）

从API version 20开始，以下示例展示了ForEach在List组件设置拖拽效果后触发的回调事件。
```

```TypeScript
### 示例3（Grid规则布局使用ForEach的onMove进行拖拽，并设置拖拽事件回调）

从API版本26.0.0开始，以下示例展示了ForEach在Grid组件设置拖拽效果后触发的回调事件，Grid里全是规则的GridItem。


```

```TypeScript
### 示例4（Grid不规则布局使用ForEach的onMove进行拖拽，并设置拖拽事件回调）

从API版本26.0.0开始，以下示例展示了ForEach在Grid组件设置拖拽效果后触发的回调事件，Grid里存在不规则的GridItem。应用可通过[irregularIndexes](ts-container-grid.md#gridlayoutoptions10对象说明)设置哪些索引是不规则节点，通过修改对应索引的rectSize调整该GridItem所占的行列数。


```

```TypeScript
### 示例5（Grid不规则布局使用LazyForEach的onMove进行拖拽，并设置拖拽事件回调）

从API版本26.0.0开始，以下示例展示了LazyForEach在Grid组件设置拖拽效果后触发的回调事件，Grid里存在不规则的GridItem。应用可通过irregularIndexes设置哪些索引是不规则节点，通过修改对应索引的rectSize调整该GridItem所占的行列数。
```

```TypeScript

```

```TypeScript
### 示例6（Grid不规则布局使用Repeat的onMove进行拖拽，并设置拖拽事件回调）

从API版本26.0.0开始，以下示例展示了Repeat在Grid组件设置拖拽效果后触发的回调事件，Grid里存在不规则的GridItem。应用可通过irregularIndexes设置哪些索引是不规则节点，通过修改对应索引的rectSize调整该GridItem所占的行列数。
```

```TypeScript
该示例分别使用了不传参@Preview和传参的@Preview。
```

```TypeScript
### 示例1（触摸测试模式为Block和Transparent的触摸测试效果）

该示例通过设置不同的[HitTestMode](./ts-appendix-enums.md#hittestmode9)值演示了Block和Transparent的触摸测试效果。
```

```TypeScript
### 示例2（触摸测试类型为BLOCK_HIERARCHY时的触摸测试效果）

从API version 20开始，该示例演示了设置触摸测试模式为BLOCK_HIERARCHY时的触摸测试效果。
```

```TypeScript
### 示例3（触摸测试类型为BLOCK_DESCENDANTS时的触摸测试效果）

从API version 20开始，该示例演示了设置触摸测试模式为BLOCK_DESCENDANTS时的触摸测试效果。
```

```TypeScript
### 示例4（Stack组件中多节点重合时的触摸测试效果）

该示例演示了在Stack组件中存在多节点触摸区域重叠时的触摸测试效果。此时设置[HitTestMode](./ts-appendix-enums.md#hittestmode9)为None时，重叠的背景区域无法响应触摸测试；只有设置为Transparent时，背景区域才能响应触摸测试。
```

```TypeScript
### 示例1（使用全屏模态转场）

该示例主要演示通过bindContentCover来实现全屏模态转场。


```

```TypeScript
### 示例2（自定义转场动画）

全屏模态无动画转场模式下，自定义转场动画。


```

```TypeScript
### 示例3（上下切换转场）

全屏模态上下切换转场。


```

```TypeScript
### 示例4（透明度渐变转场）

全屏模态透明度渐变转场。


```

```TypeScript
### 示例5（设置不同效果的自定义转场）

该示例主要演示全屏模态旋转、平移等自定义转场。


```

```TypeScript
### 示例6（设置全屏模态适配安全区）

从API version 20开始，该示例主要演示设置enableSafeArea为true后全屏模态适配安全区的内容效果。全屏模态容器的背景色为浅蓝色，内容颜色为灰色，内容在安全区内布局。
```

```TypeScript
### 示例1（设置组件获焦和走焦的效果）

该示例通过配置[defaultFocus](#defaultfocus9)可以使绑定的组件成为[层级页面](../../../ui/arkts-common-events-focus-event.md#基础概念)创建后首次获焦的焦点，配置[groupDefaultFocus](arkts-arkui-commonmethod-c.md#groupdefaultfocus)可以使绑定的组件成为tabIndex容器创建后首次获焦的焦点，配置[focusOnTouch](arkts-arkui-commonmethod-c.md#focusontouch)可以使绑定的组件点击后立即获焦。

示意图：

首次进入时，焦点默认在defaultFocus绑定的TextInput组件上：



首次按Tab键，焦点切换到tabIndex(1)的容器上，且自动走焦到内部第一个可获焦组件上：



第二次按Tab键，焦点切换到tabIndex(2)的容器上，且自动走焦到其内部的groupDefaultFocus绑定的组件上：



第三次按Tab键，焦点切换到tabIndex(3)的容器上，且自动走焦到内部配置了defaultFocus的组件上：



点击绑定了focusOnTouch的组件，组件自身获焦，焦点框被清除，再按下Tab键后，显示焦点框：


```

```TypeScript
### 示例2（设置指定组件获焦）

该示例通过配置[focusControl.requestFocus](#requestfocus9)使指定组件获取焦点。

示意图：

按下Tab键，激活焦点态显示。

申请不存在的组件获焦：



申请不可获焦的组件获焦：



申请存在且可获焦的组件获焦：


```

```TypeScript
### 示例3（设置焦点框样式）

该示例通过配置[focusBox](#focusbox12)修改组件的焦点框样式。


```

```TypeScript
### 示例4（设置焦点组走焦）

该示例通过配置[focusScopePriority](arkts-arkui-commonmethod-c.md#focusscopepriority)，可以使绑定的组件在所属容器首次获焦时成为焦点，配置[focusScopeId](arkts-arkui-commonmethod-c.md#focusscopeid)，可以使绑定的容器组件成为焦点组。

示意图：

首次按下Tab键时，焦点转移到容器1中绑定focusScopePriority的组件上。



继续按下Tab键，焦点转移到容器1下一个组件上。



再次按下Tab键，焦点转移到容器1下一个组件上。



继续按下Tab键，焦点转移到容器2中配置了focusScopePriority的组件上。



继续按下Tab键，焦点转移到容器1中名为Group1的组件上。


```

```TypeScript
### 示例5（设置Tab走焦停留）

该示例通过配置[tabStop](arkts-arkui-commonmethod-c.md#tabstop)实现使用Tab走焦停留在组件上。

示意图：

连续按下两次Tab键，焦点转移到button2上。



接着按下Tab键，焦点转移到配置了tabStop的组件。



再按下Enter键，焦点转移至内部button3上。



再按下ESC键，焦点转移到配置了tabStop的组件上。



再按下Tab键，焦点循环走焦到button1上。


```

```TypeScript
### 示例6（设置自定义走焦）

从API version 18开始，该示例通过配置[nextFocus](arkts-arkui-commonmethod-c.md#nextfocus)实现自定义走焦规则。

如果不配置[nextFocus](arkts-arkui-commonmethod-c.md#nextfocus)，默认的按下Tab键的走焦顺序为：M->A->B->C->D->E->F；配置了[nextFocus](arkts-arkui-commonmethod-c.md#nextfocus)以后，走焦顺序变更为：M->D->F->B->C。
```

```TypeScript
该示例通过Text组件设置组件尺寸变化事件，当Text尺寸变化时可以触发onSizeChange事件，获取oldValue和newValue参数。
```

```TypeScript
### 示例1（使用onAreaChange监听区域变化）

该示例通过Text组件设置组件区域变化事件，当Text布局变化时可以触发onAreaChange事件，获取相关参数。


```

```TypeScript
### 示例2（使用onAreaChange自定义间隔监听区域变化）

该示例通过设置[expectedUpdateInterval](arkts-arkui-areachangeoptions-i.md)，当Text布局变化时可以触发[onAreaChange](#onareachange-1)事件，达到间隔回调的效果。

从API版本26.0.0开始，新增[onAreaChange](#onareachange-1)、[AreaChangeCallback](arkts-arkui-areachangecallback-t.md)和[AreaChangeOptions](arkts-arkui-areachangeoptions-i.md)。
```

```TypeScript
### 示例1（使用外描边属性）

该示例主要演示如何通过[outline](arkts-arkui-commonmethod-c.md#outline)来实现组件外描边。


```

```TypeScript
### 示例2（使用LocalizedEdgeColors类型）

该示例将[outline](arkts-arkui-commonmethod-c.md#outline)属性中的color属性值设置为[LocalizedEdgeColors](ts-types.md#localizededgecolors12)类型。
```

```TypeScript
### 示例1（系统组件设置自定义属性）

在[Column](ts-container-column.md)组件上设置自定义属性，并在其对应的FrameNode上获取所设置的自定义属性。
```

```TypeScript
### 示例2（自定义组件设置自定义属性）

从API版本26.0.0开始，自定义组件支持通过[customProperty](#customproperty)接口设置自定义属性。本示例以[自定义组件的自定义布局](../../../ui/state-management/arkts-page-custom-components-layout.md)场景为例，在自定义组件上设置自定义属性，并在其[onMeasureSize](ts-custom-component-layout.md#onmeasuresize10)回调中获取所设置的自定义属性。
```

```TypeScript
### 示例1（组件绑定Modifier切换背景颜色）

该示例通过Button绑定Modifier实现了点击切换背景颜色的效果。


```

```TypeScript
### 示例2（组件绑定Modifier实现按压态效果）

该示例通过Button绑定Modifier实现了按压态的效果。如果配合状态管理V2使用，详情见：[Modifier与makeObserved](../../../ui/state-management/arkts-v1-v2-migration-inner-object.md#modifier)。


```

```TypeScript
### 示例3（自定义Modifier不支持感知@State装饰的状态数据变化）

该示例通过状态数据设置自定义Modifier的宽度，自定义Modifier不支持感知@State装饰的状态数据变化，点击按钮后宽度不发生改变。


```

```TypeScript
### 示例4（Modifier和自定义Modifier的属性同时生效）

该示例通过自定义Modifier设置了width、height和margin，点击按钮时设置[borderStyle](ts-appendix-enums.md#borderstyle)和[borderWidth](ts-universal-attributes-border.md#borderwidth)，点击后5个属性同时生效。


```

```TypeScript
### 示例5（组件绑定Modifier获焦样式）

该示例通过Button绑定Modifier实现了组件在获得焦点时的样式效果。点击Button2后，Button会显示获得焦点后的样式。


```

```TypeScript
### 示例6（组件绑定Modifier禁用状态的样式）

该示例通过Button绑定Modifier实现了组件禁用时的样式效果。点击Button2后，Button会显示禁用状态的样式。


```

```TypeScript
### 示例7（组件绑定Modifier选中状态样式）

该示例通过Radio绑定Modifier实现了组件选中时的样式效果。


```

```TypeScript
### 示例8（自定义组件绑定Modifier实现按压态效果）

该示例通过Common（自定义）绑定Modifier实现了按压态的效果。


```

```TypeScript
### 示例9（组件绑定Modifier实现鼠标悬浮态效果）

该示例通过Button绑定Modifier实现了鼠标悬浮态的效果。当鼠标移动到Button上时，Button的背景颜色变为红色，此时为悬浮态效果；当鼠标离开Button时，Button的背景颜色变为黑色，此时为普通态效果；同时通过[applyHoveredAttribute](arkts-arkui-attributemodifier-i.md#applyhoveredattribute)接口设置悬浮态样式。

从API版本26.0.0开始，新增[applyHoveredAttribute](arkts-arkui-attributemodifier-i.md#applyhoveredattribute)接口。
```

```TypeScript
// xxx.ets
@Entry
@Component
struct Example {
  build() {
    Column() {
      Flex({ wrap: FlexWrap.Wrap }) {
        Column() {
          Text('width(220)')
            .width(220)
            .height(40)
            .backgroundColor(0xF9CF93)
            .textAlign(TextAlign.Center)
            .fontColor(Color.White)
            .fontSize('12vp')
        }.margin(5)

        Column() {
          Text("width('220px')")
            .width('220px')
            .height(40)
            .backgroundColor(0xF9CF93)
            .textAlign(TextAlign.Center)
            .fontColor(Color.White)
        }.margin(5)

        Column() {
          Text("width('220vp')")
            .width('220vp')
            .height(40)
            .backgroundColor(0xF9CF93)
            .textAlign(TextAlign.Center)
            .fontColor(Color.White)
            .fontSize('12vp')
        }.margin(5)

        Column() {
          Text("width('220lpx') designWidth:720")
            .width('220lpx')
            .height(40)
            .backgroundColor(0xF9CF93)
            .textAlign(TextAlign.Center)
            .fontColor(Color.White)
            .fontSize('12vp')
        }.margin(5)

        Column() {
          Text("width(getUIContext().vp2px(220) + 'px')")
            .width(this.getUIContext().vp2px(220) + 'px')
            .height(40)
            .backgroundColor(0xF9CF93)
            .textAlign(TextAlign.Center)
            .fontColor(Color.White)
            .fontSize('12vp')
        }.margin(5)

        Column() {
          Text("fontSize('12fp')")
            .width(220)
            .height(40)
            .backgroundColor(0xF9CF93)
            .textAlign(TextAlign.Center)
            .fontColor(Color.White)
            .fontSize('12fp')
        }.margin(5)

        Column() {
          Text('width(px2vp(220))')
            .width(this.getUIContext().px2vp(220))
            .height(40)
            .backgroundColor(0xF9CF93)
            .textAlign(TextAlign.Center)
            .fontColor(Color.White)
            .fontSize('12fp')
        }.margin(5)
      }.width('100%')
    }
  }
}
```

```TypeScript
### 示例1（使用onHover）

该示例通过按钮设置了悬浮事件[onHover](#onhover)，鼠标悬浮可触发该事件修改按钮颜色。

示意图：

未悬浮时的文本内容与背景颜色：



手写笔悬浮时改变文本内容与背景颜色：


```

```TypeScript
### 示例2（使用onHoverMove）

从API version 15开始，该示例设置了按钮的[onHoverMove](arkts-arkui-commonmethod-c.md#onhovermove)事件。当手写笔悬浮在按钮上时，UI会显示手写笔当前悬浮的位置。
```

```TypeScript
### 示例1（设置组件提亮）

该示例主要通过advancedBlendMode给组件添加提亮效果。

效果图如下：


```

```TypeScript
### 示例2（设置节点组剔除属性）

该示例演示在组件的属性动画场景下，如何通过使用节点组剔除属性[excludeFromRenderGroup](arkts-arkui-commonmethod-c-sys.md#excludefromrendergroup)，避免节点组缓存反复失效。

从API version 22开始，新增[excludeFromRenderGroup](arkts-arkui-commonmethod-c-sys.md#excludefromrendergroup)属性。


```

```TypeScript
### 示例3（设置组件提亮并渐隐）

从API version 23开始，该示例主要演示如何通过advancedBlendMode给组件同时添加提亮和渐隐效果。


```

```TypeScript
### 示例4（设置组件边缘流光效果）

该示例主要演示如何通过[edgeLight](#edgelight)给组件添加边缘流光效果。

从API版本26.0.0开始，新增edgeLight方法。
```

```TypeScript
该示例展示了组件获焦和失焦的情况，按钮获焦和失焦时会改变按钮的颜色。
```

```TypeScript
### 示例1（悬浮气泡的显示和消失）

此示例为bindTips通过绑定Button产生悬浮气泡。


```

```TypeScript
### 示例2（多个悬浮气泡的显示和消失）

此示例展示了如何使用bindTips配置多个悬浮气泡依次显示和消失。


```

```TypeScript
### 示例3（设置悬浮气泡的沉浸光感视效）

该示例通过[TipsOptions](#tipsoptions类型说明)中的systemMaterial属性设置组件的系统材质，实现了bindTips的沉浸光感视效。

该示例配图为高算力设备强档效果，组件沉浸光感效果会根据设备算力与用户在系统中设置的沉浸光感效果自适应调整，开发者无需额外适配。

从API版本26.0.0开始，在TipsOptions中新增了systemMaterial属性。
```

```TypeScript
### 示例1（动态绑定手势）

该示例通过gestureModifier动态设置组件绑定的手势。


```

```TypeScript
### 示例2（动态绑定手势组）

该示例通过gestureModifier动态设置组件绑定的手势组。
```

```TypeScript
### 示例1（自定义手势判定）

该示例通过配置[onGestureJudgeBegin](arkts-arkui-commonmethod-c.md#ongesturejudgebegin)实现了对长按、快滑、滑动、捏合和拖动手势的自定义判定。从API version 21开始，支持通过[BaseEvent](ts-universal-events-click.md#baseevent8)的axisPinch属性获取双指缩放比例。


```

```TypeScript
### 示例2（自定义区域手势判定）

该示例通过配置onGestureJudgeBegin，根据触发位置所在区域决定长按手势和拖动手势是否响应。


```

```TypeScript
### 示例3（实时监测参与手势的有效触点的数量及其简要信息）

该示例通过配置onGestureJudgeBegin回调，读取fingerInfos实时检测参与手势的有效触点数量、各个触点ID及其坐标。
```

```TypeScript
### 示例1 (使用onVisibleAreaChange来监听区域变化)

该示例对组件设置[onVisibleAreaChange](arkts-arkui-commonmethod-c.md#onvisibleareachange)事件，当组件完全显示或者完全消失时触发回调。
```

```TypeScript
### 示例2 (使用onVisibleAreaApproximateChange来监听区域变化)

从API version 17开始，该示例对组件设置[onVisibleAreaApproximateChange](arkts-arkui-commonmethod-c.md#onvisibleareaapproximatechange)事件，当组件完全显示或者完全消失时触发回调。


```

```TypeScript
### 示例3 (设置measureFromViewport计算子组件超出父组件显示时的可见区域)

从API version 22开始，该示例展示onVisibleAreaChange事件设置measureFromViewport参数后的效果对比，主要差异体现在回调返回的组件可见比例（currentRatio）上。设置measureFromViewport为true时，返回的组件可见比例（currentRatio）更符合实际效果。由于不同设备的屏幕像素密度不同，可见区域变化事件的计算过程涉及小数取整，currentRatio可能存在微小差异。
```

```TypeScript
该示例通过hoverEffect设置组件的鼠标悬浮态显示效果。
```

```TypeScript
该示例演示通过foregroundEffect接口设置前景属性。
```

```TypeScript
### 示例1（使用自动内存优化策略）

以下示例中，可复用自定义组件ReusableComponent通过[ReusableOptions](arkts-arkui-reusableoptions-i.md)的memoryOptimizationStrategy属性使用了自动内存优化策略。点击Recycle按钮，可触发ReusableComponent组件回收。之后应用退后台，可触发复用池缓存释放。

从API版本26.0.0开始，新增ReusableOptions接口。
```

```TypeScript
该示例主要演示如何通过keyframeAnimateTo来设置关键帧动画，包括delay延迟、onFinish播放完成回调以及各关键帧的curve曲线配置。
```

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  @State lightIntensity: number = 0;
  @State bloomValue: number = 0;

  build() {
    Row({ space: 20 }) {
      Flex()
        .pointLight({ illuminated: IlluminatedType.BORDER })
        .backgroundColor(0x307af7)
        .size({ width: 50, height: 50 })
        .borderRadius(25)

      Flex()
        .pointLight({
          lightSource: {
            intensity: this.lightIntensity,
            positionX: '50%',
            positionY: '50%',
            positionZ: 80
          },
          bloom: this.bloomValue
        })
        .animation({ duration: 333 })
        .backgroundColor(0x307af7)
        .size({ width: 50, height: 50 })
        .borderRadius(25)
        .onTouch((event: TouchEvent) => {
          // 按下时增强光源强度和发光强度，松开或取消时恢复默认效果。
          if (event.type === TouchType.Down) {
            this.lightIntensity = 1;
            this.bloomValue = 1;
          } else if (event.type === TouchType.Up || event.type === TouchType.Cancel) {
            this.lightIntensity = 0;
            this.bloomValue = 0;
          }
        })

      Flex()
        .pointLight({ illuminated: IlluminatedType.BORDER_CONTENT })
        .backgroundColor(0x307af7)
        .size({ width: 50, height: 50 })
        .borderRadius(25)
    }
    .justifyContent(FlexAlign.Center)
    .backgroundColor(Color.Black)
    .size({ width: '100%', height: '100%' })
  }
}
```

```TypeScript
### 示例1（使用不同裁剪属性）

该示例通过[clipShape](arkts-arkui-commonmethod-c.md#clipshape)、[clip](#clip12)、[maskShape](arkts-arkui-commonmethod-c.md#maskshape)实现图片的裁剪和遮罩。


```

```TypeScript
### 示例2（实现组件遮罩）

该示例通过[mask](#mask12)实现图片的遮罩。
```

```TypeScript
### 示例1（禁用默认点击音效）

该示例通过配置enableClickSoundEffect属性，实现组件禁用默认点击音效，开发者可以在onClick回调中调用音频相关接口自定义发音。自定义发音可参考[SoundPool播放短音频指南](../../../media/media/using-soundpool-for-playback.md)。

从API version 24开始，新增[enableClickSoundEffect](arkts-arkui-commonmethod-c.md#enableclicksoundeffect)属性。
```

```TypeScript
### 示例1（通过DrawModifier进行自定义绘制）

通过DrawModifier对[Text](ts-basic-components-text.md)组件进行自定义绘制。


```

```TypeScript
### 示例2（通过DrawModifier对容器的前景进行自定义绘制）

通过DrawModifier对[Column](ts-container-column.md)容器的前景进行自定义绘制。
```

```TypeScript
该示例主要演示前景滤镜、背景滤镜和合成滤镜的模糊效果。
```

```TypeScript
### 示例1（设置组件快捷键）

该示例通过设置组件的快捷键，同时按控制键+对应的字符可以触发组件响应快捷键，并触发onClick事件或自定义事件。


```

```TypeScript
### 示例2（快捷键的绑定和解除绑定）

该示例演示了如何实现快捷键的绑定和解除绑定。
```

```TypeScript
### 示例1（设置无障碍文本和无障碍说明）

该示例主要演示accessibilityText无障碍文本和accessibilityDescription无障碍说明的播报内容。
```

```TypeScript
### 示例2（设置无障碍组）

该示例主要演示优先使用子组件的无障碍文本进行朗读。
```

```TypeScript
### 示例3（设置首焦点和组件的下一个焦点）

该示例主要演示accessibilityDefaultFocus屏幕朗读当前页默认首焦点和accessibilityNextFocusId走焦过程中组件的下一个焦点。
```

```TypeScript
### 示例4（设置无障碍组件类型和文本提示信息）

该示例主要演示accessibilityRole无障碍组件类型和accessibilityTextHint设置组件的文本提示信息（仅在与车机交互的场景下供车机的无障碍服务监听并响应）。
```

```TypeScript
### 示例5（设置无障碍屏幕朗读滚动和焦点绿框绘制）

该示例主要演示accessibilityScrollTriggerable设置无障碍节点是否支持屏幕朗读滚动、accessibilityFocusDrawLevel设置无障碍焦点绿框的绘制层级和accessibilityUseSamePage为跨进程嵌入式显示的组件（如[EmbeddedComponent](ts-container-embedded-component.md)）设置同page模式。


```

```TypeScript
### 示例6（设置无障碍聚合功能下的子组件状态和操作接管功能）

该示例主要演示使用accessibilityGroup的可选参数stateControllerRoleType或者stateControllerId来选择一个特定子组件接管其无障碍状态信息，可选参数actionControllerRoleType或者actionControllerId来选择一个特定子组件接管其无障碍控制操作。
```

```TypeScript
### 示例7（设置无障碍组件状态播报信息）

该示例主要通过[accessibilityStateDescription](#accessibilitystatedescription23)接口修改组件的状态播报。在开启无障碍功能后，组件发生聚焦或者点击后，屏幕朗读进行组件的状态信息播报。

从API version 23开始，新增accessibilityStateDescription接口。
```

```TypeScript
### 示例8（设置无障碍操作选项修改组件滑动步数）

本示例主要演示如何通过[accessibilityActionOptions](ts-types.md#accessibilityactionoptions23对象说明)中的scrollStep参数，自定义组件的滑动步数。以下将以slider组件在屏幕朗读场景下滑动距离变化为例进行说明。

从API version 23开始，新增AccessibilityActionOptions。
```

```TypeScript
### 示例9（设置自定义无障碍操作）

本示例主要演示如何使用[accessibilityCustomActions](arkts-arkui-commonmethod-c.md#accessibilitycustomactions)为组件设置自定义无障碍操作。开发者可以按操作名为组件进行自定义操作的回调绑定。

从API版本26.0.0开始，新增accessibilityCustomActions。
```

```TypeScript
### 示例1（设置Text多态样式）

该示例展示了[stateStyles](#statestyles)设置状态为hovered、pressed和disabled时Text组件的样式变化。

从API版本26.0.0开始，[stateStyles](#statestyles)新增hovered属性。


```

```TypeScript
### 示例2（设置Radio多态样式）

该示例展示了状态为selected时Radio组件的样式变化。


```

```TypeScript
### 示例3（设置Builder多态样式）

该示例展示了状态为pressed时@Builder中自定义组件的样式变化。
```

```TypeScript
该示例主要展示如何通过组件标识接口，获取特定id组件的属性，以及如何向该id的组件触发事件。
```

```TypeScript
该示例通过animation实现了组件的属性动画。
```

```TypeScript
### 示例1（不同高度的半模态弹窗）

该示例通过height设置不同高度的半模态弹窗。


```

```TypeScript
### 示例2（设置三个不同高度的挡位）

使用bindSheet的detents属性设置三个不同高度的挡位。

dragBar控制条只在多个挡位高度时生效；

区别于height属性在不同时刻设置不同挡位的能力，多挡位能力有手势切换挡位高度的效果，且更适合固定高度区间的场景；

若高度范围不确定，且可能存在大于3个不同高度的场景，不建议使用detents属性。


```

```TypeScript
### 示例3（使用边框宽度和颜色）

bindSheet属性的borderWidth、borderColor属性值使用LocalizedEdgeWidths类型和LocalizedEdgeColors类型。

从左至右显示语言模式示例图



从右至左显示语言模式示例图


```

```TypeScript
### 示例4（使用关闭回调函数）

bindSheet注册onWillDismiss与onWillSpringBackWhenDismiss。


```

```TypeScript
### 示例5（设置内容区刷新时机）

ScrollSizeMode.CONTINUOUS持续更新内容适合detents多挡位切换场景。

建议在builder内减少UI加载耗时的操作，滑动时内容实时刷新对性能要求较高。

跟手触发挡位切换时，松手才触发面板内容高度刷新。



跟手触发挡位切换时，跟手时期就会触发面板内容高度刷新。


```

```TypeScript
### 示例6（设置压缩模态内容）

通过设置SheetKeyboardAvoidMode为RESIZE_ONLY，当键盘高度变化时，根据高度变化实现滚动组件的滚动。


```

```TypeScript
### 示例7（镜像场景下如何设置圆角属性）

此示例为说明镜像场景而设置了不同的圆角半径，通常不建议开发者设置不同的值，会造成视觉体验不佳。

其中，从API version 15开始，半模态的radius属性值使用LocalizedBorderRadiuses类型。

从左至右显示语言模式示例图



从右至左显示语言模式示例图


```

```TypeScript
### 示例8（半模态Side侧边样式）

从API version 20开始，此示例实现半模态侧边样式。


```

```TypeScript
### 示例9（半模态ContentCover全屏样式）

从API version 20开始，此示例实现半模态的全屏显示效果。


```

```TypeScript
### 示例10（半模态设置系统材质）

该示例通过半模态systemMaterial属性设置系统材质。

该示例配图为高算力设备强档效果，组件沉浸光感效果会根据设备算力与用户在系统中设置的沉浸光感效果自适应调整，开发者无需额外适配。

从API版本26.0.0开始，[SheetOptions](arkts-arkui-sheetoptions-i.md)新增systemMaterial属性。


```

```TypeScript
### 示例11（半模态自定义按钮材质）

该示例通过closeButtonMaterial属性自定义半模态关闭按钮的材质效果，对比未设置（使用systemMaterial内置材质）、关闭材质、自定义材质三种状态。

从API版本26.1.0开始，[SheetOptions](arkts-arkui-sheetoptions-i.md)新增closeButtonMaterial属性。

未设置closeButtonMaterial时，关闭按钮使用systemMaterial带来的内置材质效果。



设置closeButtonMaterial为uiMaterial.Material.empty时，关闭按钮无材质效果。



设置closeButtonMaterial为自定义材质时，关闭按钮使用自定义材质效果。


```

```TypeScript
### 示例12（半模态标题栏背景模糊）

该示例通过titleBarBackgroundBlur属性设置半模态标题栏背景渐变模糊效果。同时配合titleBarHoverMode设置为STACK堆叠模式，使标题栏悬浮于内容区上方时模糊效果可见。

从API版本26.1.0开始，[SheetOptions](arkts-arkui-sheetoptions-i.md)新增titleBarBackgroundBlur属性。


```

```TypeScript
### 示例13（半模态标题栏悬浮模式）

该示例通过titleBarHoverMode属性设置半模态标题栏为STACK堆叠模式，标题栏悬浮在内容区上方。

从API版本26.1.0开始，[SheetOptions](arkts-arkui-sheetoptions-i.md)新增titleBarHoverMode属性。


```

```TypeScript
### 示例14（半模态滚动条状态）

该示例通过scrollBarState属性设置半模态内容区滚动条的显示状态，点击按钮在[BarState](ts-appendix-enums.md#barstate)的Off、On、Auto和未设置之间切换。

从API版本26.1.0开始，[SheetOptions](arkts-arkui-sheetoptions-i.md)新增scrollBarState属性。
```

```TypeScript
### 示例1（支持滚动手势）

该示例通过设置[enableScrollInteraction](#enablescrollinteraction11)属性，实现了使用手势滚动纵向列表，并在当前显示界面发生改变时回调索引。

ListDataSource说明及完整代码参考[示例1（添加滚动事件）](./ts-container-list.md#示例1添加滚动事件)。


```

```TypeScript
### 示例2（设置边缘渐隐）

该示例通过设置[fadingEdge](#fadingedge14)属性，实现了[List](ts-container-list.md)组件开启边缘渐隐效果并设置边缘渐隐长度。

ListDataSource说明及完整代码参考[示例1（添加滚动事件）](./ts-container-list.md#示例1添加滚动事件)。


```

```TypeScript
### 示例3（设置裁剪区域）

该示例通过设置[clipContent](arkts-arkui-scrollablecommonmethod-c.md#clipcontent)属性，改变组件的内容层裁剪区域。


```

```TypeScript
### 示例4（设置滚动条边距）

从API version 20开始，该示例通过设置[scrollBarMargin](#scrollbarmargin20)属性，调整滚动组件的滚动条边距。

ListDataSource说明及完整代码参考[示例1（添加滚动事件）](./ts-container-list.md#示例1添加滚动事件)。
```

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  @State isShow: boolean = false

  build() {
    Stack({ alignContent: Alignment.Center }) {
      if (this.isShow) {
        Image($r('app.media.pic'))
          .autoResize(false)
          .clip(true)
          .width(300)
          .height(400)
          .offset({ y: 100 })
          .geometryTransition("picture", { hierarchyStrategy: TransitionHierarchyStrategy.ADAPTIVE })
          .transition(TransitionEffect.OPACITY)
      } else {
        // geometryTransition此处绑定的是容器，那么容器内的子组件需设为相对布局跟随父容器变化，
        // 套多层容器为了说明相对布局约束传递
        Column() {
          Column() {
            Image($r('app.media.icon'))
              .width('100%').height('100%')
          }.width('100%').height('100%')
        }
        .width(80)
        .height(80)
        // geometryTransition会同步圆角，但仅限于geometryTransition绑定处，此处绑定的是容器
        // 则对容器本身有圆角同步而不会操作容器内部子组件的borderRadius
        .borderRadius(20)
        .clip(true)
        .geometryTransition("picture", { hierarchyStrategy: TransitionHierarchyStrategy.ADAPTIVE })
        // transition保证组件离场不被立即析构，可设置其他转场效果
        .transition(TransitionEffect.OPACITY)
      }
    }
    .onClick(() => {
      this.getUIContext()?.animateTo({ duration: 1000 }, () => {
        this.isShow = !this.isShow;
      })
    })
  }
}
```

```TypeScript
### 示例1（弹出不同类型的气泡）

该示例通过配置[PopupOptions](#popupoptions类型说明)或[CustomPopupOptions](#custompopupoptions8类型说明)中的keyboardAvoidMode属性，设置气泡是否避让软键盘。

从API version 15开始，分别在PopupOptions和CustomPopupOptions中新增了keyboardAvoidMode属性。


```

```TypeScript
### 示例2（设置气泡的文本样式）

该示例通过配置[PopupOptions](#popupoptions类型说明)中的messageOptions属性，实现了弹出自定义文本样式的气泡。


```

```TypeScript
### 示例3（设置气泡的样式）

该示例通过配置[PopupOptions](#popupoptions类型说明)中的arrowHeight、arrowWidth、radius、shadow和popupColor属性，实现了气泡箭头以及气泡本身的样式。


```

```TypeScript
### 示例4（设置气泡的动效）

该示例通过配置[PopupOptions](#popupoptions类型说明)或[CustomPopupOptions](#custompopupoptions8类型说明)中的transition属性，实现了气泡显示以及退出的动效。


```

```TypeScript
### 示例5（为气泡添加事件）

该示例通过配置[PopupOptions](#popupoptions类型说明)中的onWillDismiss属性，实现了当气泡退出时，拦截退出事件并执行回调函数。


```

```TypeScript
### 示例6（为气泡拦截退出事件）

该示例将[PopupOptions](#popupoptions类型说明)的onWillDismiss属性设为false，使气泡不响应退出事件。同时，配置[PopupOptions](#popupoptions类型说明)的followTransformOfTarget属性，设置气泡是否跟随宿主组件变换。


```

```TypeScript
### 示例7（为气泡内外描边设置线性渐变）

该示例通过配置[PopupOptions](#popupoptions类型说明)中的outlineWidth、borderWidth、outlineLinearGradient、borderLinearGradient属性，为气泡设置内外描边线性渐变的颜色和方向。

从API version 20开始，在PopupOptions中新增了outlineWidth、borderWidth、outlineLinearGradient、borderLinearGradient属性。


```

```TypeScript
### 示例8（设置气泡避让绑定的组件模式）

该示例通过配置[PopupOptions](#popupoptions类型说明)的avoidTarget属性，实现气泡对其绑定组件的避让。

从API version 20开始，在PopupOptions中新增了avoidTarget属性。


```

```TypeScript
### 示例9（设置Popup的沉浸光感视觉效果）

该示例通过[PopupOptions](#popupoptions类型说明)中的systemMaterial属性设置组件的系统材质，实现了Popup的沉浸光感视效。

该示例配图为高算力设备强档效果，组件沉浸光感效果会根据设备算力与用户在系统中设置的沉浸光感效果自适应调整，开发者无需额外适配。

从API版本26.0.0开始，在PopupOptions中新增了systemMaterial属性。

未设置系统材质时：



设置系统材质后：


```

```TypeScript
### 示例10（自定义气泡背景效果参数）

该示例通过配置[PopupOptions](#popupoptions类型说明)的backgroundBlurStyleOptions和backgroundEffect属性，实现自定义气泡背景效果。

从API版本26.0.0开始，在PopupOptions中新增了backgroundBlurStyleOptions和backgroundEffect属性。


```

```TypeScript
### 示例11（设置气泡的显示层级模式）

该示例通过配置[PopupOptions](#popupoptions类型说明)的levelMode属性，实现气泡在页面内嵌入显示。点击按钮后页面级的气泡不会显示在下一个路由页面中。

从API版本26.0.0开始，在PopupOptions中新增了levelMode属性。
```

```TypeScript
PageTwo页面：
```

```TypeScript
### 示例1（获取轴事件相关参数）

该示例中，对按钮设置轴事件，通过滚动鼠标滚轮可获取轴事件的相关参数。从API version 21开始，该示例通过[BaseEvent](./ts-universal-events-click.md#baseevent8)的属性和[getPinchAxisScaleValue](arkts-arkui-axisevent-i.md#getpinchaxisscalevalue)获取双指缩放比例；从API version 22开始，该示例通过[hasAxis](arkts-arkui-axisevent-i.md#hasaxis)判断轴事件是否包含指定的轴类型。

鼠标滚轮滚动时：


```

```TypeScript
### 示例2（获取组件实时位置）

该示例通过[getCurrentLocalPosition](#getcurrentlocalposition)方法获取鼠标光标位置相对于当前组件实时位置左上角的坐标。

从API版本26.0.0开始，新增支持getCurrentLocalPosition接口。
```

```TypeScript
### 示例1（设置组件宽高比）

通过aspectRatio设置不同的宽高比。

图1 竖屏显示

图2 横屏显示
```

```TypeScript
### 示例2（设置组件显示优先级）

使用displayPriority为子组件设置显示优先级。
```

```TypeScript
### 示例1（触发onKeyEvent回调）

该示例为按钮设置按键事件。按钮获焦时，按下按键可触发onKeyEvent回调。按键事件触发的流程和具体时机参考[按键事件数据流](../../../ui/arkts-interaction-development-guide-keyboard.md#按键事件数据流)。


```

```TypeScript
### 示例2（获取Unicode码值）

该示例通过按键事件获取所按按键的Unicode码值。


```

```TypeScript
### 示例3（触发onKeyPreIme回调）

该示例使用onKeyPreIme屏蔽输入框中的方向左键。
```

```TypeScript
### 示例4（使用stopPropagation阻止冒泡）

该示例使用stopPropagation阻止事件冒泡。即，通过在Button的onKeyEvent回调中加入event.stopPropagation()方法，达到“仅Button响应键盘事件，Column不响应”的效果。

> 说明：
> 
> onKeyEvent事件默认是冒泡的。
> 
> 事件冒泡：在一个树形结构中，当子节点处理完一个事件后，再将该事件交给它的父节点处理。
> 
> 可以在[onKeyEvent15+](#onkeyevent15)中，通过返回true消费按键事件阻止冒泡，效果等同于stopPropagation。
```

```TypeScript
### 示例1（设置onAccessibilityActionIntercept拦截点击事件）

该示例演示在无障碍模式下，通过onAccessibilityActionIntercept事件在Toggle组件点击事件触发前进行拦截，并弹出确认对话框由用户确认是否放行该点击事件。
```

```TypeScript
### 示例2（设置onAccessibilityFocus回调函数）

从API version 18开始，当获焦、失焦状态发生变化时，触发该回调函数。本示例展示了[onAccessibilityFocus](arkts-arkui-commonmethod-c.md#onaccessibilityfocus)的基本用法，聚焦到"onAccessibilityFocus takes effect"时，会打印"[testingTag] isFocus current is true"，当聚焦到"onAccessibilityFocus takes effect"以外的位置时，会打印"[testingTag] isFocus current is false"。
```

```TypeScript
该示例通过onTouchIntercept修改组件的HitTestMode属性。
```

```TypeScript
### 示例1（基本样式用法）

设置边框的宽度、颜色、圆角半径以及点、线样式。


```

```TypeScript
### 示例2（边框宽度、圆角半径和颜色类型）

border属性的width、radius、color属性值分别使用LocalizedEdgeWidths类型、LocalizedBorderRadiuses类型和LocalizedEdgeColors类型。

从左至右（LTR）显示语言示例图



从右至左（RTL）显示语言示例图


```

```TypeScript
### 示例3（设置离屏圆角）

从API version 22开始，该示例支持设置组件绘制圆角的模式。

快速绘制模式（RenderStrategy.FAST）通过GPU硬件加速进行实时绘制，适用于普通圆角场景；离屏绘制模式（RenderStrategy.OFFSCREEN）将组件先绘制到离屏缓冲区再合成，适用于包含模糊、滚动等复杂内容的圆角场景，可避免圆角裁剪异常。设置在线绘制模式（上方）以及离屏绘制模式（下方）的示例图如下：


```

```TypeScript
### 示例4（设置异形圆角）

该示例通过[borderRadius](#borderradius)设置四个不同圆角值。当其中一个圆角值超过高度或宽度最小值的一半时，按值的比例绘制异形圆角。
```

```TypeScript
### 示例1（设置组件堆叠顺序）

该示例通过zIndex设置组件堆叠顺序。

Stack容器内子组件不设置zIndex时，默认按照声明顺序显示，后声明的组件会覆盖在先声明的组件上方。



Stack容器子组件设置zIndex后的效果。


```

```TypeScript
### 示例2（动态修改zIndex属性）

该示例使用Button组件动态修改zIndex属性。

不点击Button修改zIndex值的效果。



点击Button动态修改zIndex，使Text1和Text2的zIndex相等，因为在点击Button前的层级顺序上根据zIndex进行稳定排序，层级顺序不发生改变。



点击Button动态修改zIndex，使Text2的zIndex大于Text1，层级顺序发生改变。


```

```TypeScript
### 示例3（设置不同容器内组件的zIndex属性）

该示例在不同容器内设置zIndex属性。其中，Text1、Text2在同一个Stack容器内，Text3在另一个Stack容器内。虽然Text3的zIndex值最小，但Text1、Text2仍无法根据zIndex值显示在Text3的上方。
```

```TypeScript
### 示例1（设置组件的宽高和边距）

设置组件的宽度、高度、内边距及外边距。


```

```TypeScript
### 示例2（LocalizedPadding和LocalizedMargin类型的使用）

使用LocalizedPadding类型和LocalizedMargin类型定义padding和margin属性。

从左至右显示语言示例图



从右至左显示语言示例图


```

```TypeScript
### 示例3（设置组件级安全区）

对容器设置组件级安全区。


```

```TypeScript
### 示例4（使用attributeModifier动态设置安全区）

使用attributeModifier对容器设置组件级安全区。


```

```TypeScript
### 示例5（设置布局策略）

对容器大小设置布局策略。


```

```TypeScript
### 示例6（子组件单方向设置matchParent效果）

该示例展示Column组件自适应子组件且子组件仅单方向设置matchParent时的布局效果。从API版本26.0.0开始，Column组件高度自适应第一个和第二个子组件，宽度自适应第一个和第三个子组件。
```

```TypeScript
### 示例1（逐帧布局的效果）

以下示例通过改变Text组件宽度实现逐帧布局的效果。


```

```TypeScript
### 示例2（折线的动画效果）

以下示例实现折线的动画效果。
```

```TypeScript
### 示例1（对齐方式和主轴方向上的布局）

设置内容在元素内的对齐方式和子元素在父组件主轴方向上的布局。


```

```TypeScript
### 示例2（位置偏移）

基于父组件、相对定位、锚点作出位置偏移。


```

```TypeScript
### 示例3（绝对定位和相对偏移）

使用position设置绝对定位，确定子组件相对父组件的位置。使用offset设置相对偏移，组件相对原本的布局位置进行偏移。


```

```TypeScript
### 示例4（镜像效果）

通用布局属性支持[使用镜像能力](./../../../ui/arkts-internationalization.md#使用镜像能力)。下述示例从上到下依次通过[position](#position)、[offset](#offset)和[markAnchor](#markanchor)实现镜像效果，为对比镜像前后的差异，浅蓝色对应镜像前效果，深蓝色对应镜像后效果。

镜像前效果：



镜像后效果如下，镜像生效条件请参考[使用镜像能力](./../../../ui/arkts-internationalization.md#使用镜像能力)：


```

```TypeScript
### 示例5（align属性适配镜像特性）

设置内容在元素内的对齐方式和子元素在父组件主轴方向上的布局。


```

```TypeScript
### 示例6（layoutGravity属性单独设置Stack组件中子组件的对齐规则）

更改Stack中Text的位置。
```

```TypeScript
该示例主要显示通过[opacity](#opacity)设置组件的不透明度。
```

```TypeScript
该示例通过为[Navigation](ts-basic-components-navigation.md)下的[Button](ts-basic-components-button.md)组件绑定toolbar通用属性，为标题栏NavBar分栏开头位置添加包含两个[Button](ts-basic-components-button.md)组件的工具栏项。为[NavDestination](ts-basic-components-navdestination.md)下的[Text](ts-basic-components-text.md)组件绑定toolbar通用属性，为标题栏NavDestination分栏末尾位置添加两个工具栏项，分别包含一个滑动条组件和一个搜索框组件。
```

```TypeScript
### 示例1（允许拖拽和落入）

示例1通过配置[allowDrop](arkts-arkui-commonmethod-c.md#allowdrop)设置组件是否可落入，通过配置[draggable](#draggable)设置组件是否可拖拽。


```

```TypeScript
### 示例2（设置预览图）

示例2通过配置[dragPreview](#dragpreview11)设置拖拽过程的预览图。


```

```TypeScript
### 示例3（设置背板图样式）

示例3通过配置[dragPreviewOptions](#dragpreviewoptions11)为ENABLE_DEFAULT_SHADOW、ENABLE_DEFAULT_RADIUS设置默认阴影和统一圆角效果。从API version 18开始，通过配置[dragPreviewOptions](#dragpreviewoptions11)为ENABLE_DRAG_ITEM_GRAY_EFFECT设置灰显效果。


```

```TypeScript
### 示例4（设置多选拖拽）

示例4通过配置[isMultiSelectionEnabled](arkts-arkui-draginteractionoptions-i.md)实现Grid组件的多选拖拽效果。


```

```TypeScript
### 示例5（设置默认点按效果）

示例5通过配置[defaultAnimationBeforeLifting](arkts-arkui-draginteractionoptions-i.md)实现Grid组件的默认点按效果。


```

```TypeScript
### 示例6（自定义背板图样式）

示例6通过配置[ImageModifier](arkts-arkui-imagemodifier-t.md)实现Image组件的自定义背板图样式。


```

```TypeScript
### 示例7（图片拖拽设置）

示例7展示了不同图片（在线图片资源、本地图片资源和PixelMap）在拖拽时组件的设置。

使用网络图片时，需要申请权限ohos.permission.INTERNET。具体申请方式请参考[声明权限](../../../security/AccessToken/declare-permissions.md)。


```

```TypeScript
### 示例8（设置图片拖拽震动）

从API version 18开始，示例8通过设置[enableHapticFeedback](arkts-arkui-draginteractionoptions-i.md)实现图片拖拽的震动效果。
```

```TypeScript
### 示例9（自定义预览图）

从API version 15开始，示例9通过配置[onlyForLifting](./ts-universal-events-drag-drop.md#previewconfiguration15)实现自定义预览图，仅用于浮起效果以及配置[isLiftingDisabled](arkts-arkui-draginteractionoptions-i.md)实现禁用浮起效果。

自定义预览图用于浮起效果。



自定义预览图禁用浮起效果。


```

```TypeScript
### 示例10（以拖拽预览图初始尺寸计算跟手点位置）

从API version 19开始，示例10通过配置[DragPreviewMode](#dragpreviewmode11枚举说明)为ENABLE_TOUCH_POINT_CALCULATION_BASED_ON_FINAL_PREVIEW实现基于最终拖拽预览图的原始尺寸来计算拖拽过程中跟手点位置。当设置[DragPreviewMode](#dragpreviewmode11枚举说明)为ENABLE_MULTI_TILE_EFFECT时，该属性不生效。


```

```TypeScript
### 示例11（长按浮起预览图与拖拽预览图过渡动效）

从API version 19开始，示例11通过配置[DraggingSizeChangeEffect](#draggingsizechangeeffect19枚举说明)实现不同拖拽过渡效果。


```

```TypeScript
### 示例12（设置自定义组件落入）

从API version 23开始，示例12通过组件的[onDragStart](ts-universal-events-drag-drop.md#ondragstart)接口传递其类型，并在目标组件的[allowDrop](arkts-arkui-commonmethod-c.md#allowdrop)属性中设置允许该类型落入，即可实现自定义组件的拖拽落入功能。


```

```TypeScript
### 示例13（设置背板图材质效果）

该示例通过配置[ImageModifier](arkts-arkui-imagemodifier-t.md)中的[systemMaterial](ts-universal-attributes-image-effect.md#systemmaterial)属性，设置拖拽背板的材质效果。

从API版本26.0.0开始，[DragPreviewOptions](#dragpreviewoptions11-1)接口中的modifier参数新增支持[systemMaterial](ts-universal-attributes-image-effect.md#systemmaterial)属性。
```

```TypeScript
### 示例1（if else范式下的共享元素实现）

该示例主要演示if else范式下的共享元素效果集成。


```

```TypeScript
### 示例2（if范式下使用follow实现跟随效果）

该示例主要演示if范式下使用follow参数实现不下树的组件的跟随效果。
```

```TypeScript
该示例通过按钮控制组件的挂载和卸载，触发onAttach和onDetach事件。
```

```TypeScript
### 示例1（使用前景色设置）

该示例主要演示通过foregroundColor设置前景色。


```

```TypeScript
### 示例2（设置前景色为组件背景色反色）

该示例通过[ColoringStrategy](ts-appendix-enums.md#coloringstrategy10).INVERT将前景色设置为背景色反色。


```

```TypeScript
### 示例3（前景色未继承父组件）

该示例主要演示组件同时设置前景色和背景色与只设置背景色的效果对比。
```

```TypeScript
### 示例1（通过responseRegion接口设置触摸热区）

该示例通过responseRegion设置按钮的触摸热区以响应点击事件。


```

```TypeScript
### 示例2（通过responseRegionList接口设置触摸热区）

该示例通过[responseRegionList](arkts-arkui-commonmethod-c.md#responseregionlist)设置按钮的触摸热区以响应点击事件。

从API version 22开始，新增responseRegionList接口。


```

```TypeScript
### 示例3（设置鼠标的触摸热区以响应点击事件）

该示例通过[mouseResponseRegion](arkts-arkui-commonmethod-c.md#mouseresponseregion)设置鼠标的触摸热区以响应点击事件。
```

```TypeScript
该示例通过obscured对Text、Image组件实现了隐私遮罩效果。
```

```TypeScript
设置不同设备类型下的栅格配置。gridSpan和gridOffset用于设置默认占用列数和偏移列数，仅在useSizeType未配置对应尺寸时生效。示例中useSizeType配置了sm尺寸的值（span: 2, offset: 1），若要在其他未配置的尺寸下实现相同的栅格效果，可通过gridSpan和gridOffset设置默认值。

> 说明：
> 
> 本示例展示的是已废弃接口的用法。建议使用新组件[GridCol](ts-container-gridcol.md)、[GridRow](ts-container-gridrow.md)来实现栅格布局。
```

```TypeScript
该示例主要演示不同组件的点击回弹效果。
```

```TypeScript
### 示例1（为组件添加图形变换效果）

该示例通过[rotate](#rotate)、[translate](#translate)、[scale](#scale)、[transform](#transform)为组件添加旋转、平移、缩放、变换矩阵效果。


```

```TypeScript
### 示例2（设置旋转视距）

该示例通过[perspective](#rotateoptions对象说明)为组件添加视距效果。


```

```TypeScript
### 示例3（按中心点旋转）

该示例通过设置[rotate](#rotate)和[transform](#transform)为不同的参数实现相同的旋转效果。


```

```TypeScript
### 示例4（通过transform3D实现图形变换）

从API version 20开始，该示例通过设置[transform3D](arkts-arkui-commonmethod-c.md#transform3d)实现图形变换效果。


```

```TypeScript
### 示例5（按各轴旋转角的方式实现旋转）

从API version 20开始，该示例通过设置rotate的[RotateAngleOptions](#rotateangleoptions20对象说明)参数实现旋转效果。
```

```TypeScript
示例代码为点击图片所在区域跳转页面时，显示共享元素图片的自定义转场动效。
```

```TypeScript
// PageB.ets
@Entry
@Component
struct PageBExample {
  build() {
    Stack() {
      // $r('app.media.ic_health_heart')需要替换为开发者所需的图像资源文件。
      Image($r('app.media.ic_health_heart')).width(150).height(150)
        .sharedTransition('sharedImage', { duration: 800, curve: Curve.Linear, delay: 100 })
    }.width('100%').height('100%')
  }

  pageTransition() {
    PageTransitionEnter({ type: RouteType.None, duration: 0 })
    PageTransitionExit({ type: RouteType.None, duration: 0 })
  }
}
```

```TypeScript
### 示例1（实现沉浸式效果）

该示例通过设置expandSafeArea属性向顶部和底部扩展安全区实现沉浸式效果。


```

```TypeScript
### 示例2（同时设置固定宽高和expandSafeArea属性）

该示例展示了同时设置固定宽高和expandSafeArea属性的效果。

如下图：Column组件扩展至了顶部状态栏[SafeAreaEdge.TOP]，未扩展至底部导航条[SafeAreaEdge.BOTTOM]，扩展后的组件高度维持设置值不变。


```

```TypeScript
### 示例3（键盘避让时固定背景图位置）

该示例通过为背景图组件设置expandSafeArea属性，来实现拉起键盘进行避让时，背景图保持不动的效果。


```

```TypeScript
### 示例4（设置键盘避让模式为压缩）

该示例通过调用setKeyboardAvoidMode设置键盘避让模式为RESIZE模式，实现键盘抬起时page的压缩效果。
```

```TypeScript

```

```TypeScript
### 示例5（设置键盘避让模式为上抬）

该示例通过调用setKeyboardAvoidMode设置键盘避让模式为OFFSET模式，实现键盘抬起时page的上抬效果。但当输入光标距离屏幕底部的高度大于键盘高度时，page不会抬起，如本例中所示。
```

```TypeScript

```

```TypeScript
### 示例6（切换避让模式）

该示例通过调用setKeyboardAvoidMode来实现OFFSET、RESIZE和NONE模式之间的切换，实现三种不同的键盘避让效果。


```

```TypeScript
### 示例7（滚动类容器扩展安全区）

该示例通过在滚动类容器内调用expandSafeArea属性实现沉浸式效果，Scroll内的Swiper可以延伸到状态栏上。


```

```TypeScript
### 示例8（ignoreLayoutSafeArea延伸组件布局范围）

该示例利用[ignoreLayoutSafeArea](#ignorelayoutsafearea20)改变组件位置。相比未使用该属性，配置ignoreLayoutSafeArea后，Row组件基于Stack内容区、Stack组件级安全区、系统状态栏共同组成的范围，取其左上部分，作左上对齐。


```

```TypeScript
### 示例9（ignoreLayoutSafeArea配合LayoutPolicy.matchParent延伸组件布局范围）

该示例利用[ignoreLayoutSafeArea](#ignorelayoutsafearea20)和[LayoutPolicy.matchParent](ts-universal-attributes-size.md#layoutpolicy15)同时改变组件大小和位置。相比未使用该属性，配置ignoreLayoutSafeArea后，Row组件基于Stack内容区、Stack组件级安全区，取其右下部分并撑满可用空间。


```

```TypeScript
### 示例10（expandSafeArea与ignoreLayoutSafeArea的区别）

该示例展示了容器分别设置了expandSafeArea和ignoreLayoutSafeArea的布局效果和各自对子组件布局效果的影响。两种设置下，容器都可见地进行了延伸，但前者的子组件不受延伸影响，后者的子组件因父容器的延伸改变了位置。
```

```TypeScript
该示例通过enabled设置按钮是否可交互。
```

```TypeScript
### 示例1（设置渐变色边框）

通过[borderImage](arkts-arkui-commonmethod-c.md#borderimage)接口为组件设置渐变色边框。


```

```TypeScript
### 示例2（动态调整属性值）

通过[Slider](../../apis-arkui/arkui-js/js-components-basic-slider.md)接口动态调整[borderImage](arkts-arkui-commonmethod-c.md#borderimage)接口中属性值。


```

```TypeScript
### 示例3（使用LocalizedEdgeWidths类型值）

通过[borderImage](arkts-arkui-commonmethod-c.md#borderimage)接口中的slice、width和outset属性值使用[LocalizedEdgeWidths](ts-types.md#localizededgewidths12)类型。
```

```TypeScript
### 示例1（父组件优先识别手势和父子组件同时触发手势）

该示例通过配置priorityGesture和parallelGesture分别实现了父组件优先识别手势和父子组件同时触发手势。


```

```TypeScript
### 示例2（实时监测参与滑动手势的有效触点数量）

该示例通过读取fingerInfos实时监测参与滑动手势的有效触点数量。
```

```TypeScript
### 示例1 (使用onAccessibilityHover事件)

该示例主要演示使用onAccessibilityHover事件，对无障碍模式下的按钮进行设置。
```

```TypeScript
### 示例2 (捕获无法无障碍聚焦的组件的触摸事件)

该示例代码在无障碍模式下通过onAccessibilityHoverTransparent接口捕获无法无障碍聚焦的组件的触摸事件，最后再将事件信息显示在组件下方的文本中。

从API version 20开始，新增了[onAccessibilityHoverTransparent](arkts-arkui-commonmethod-c.md#onaccessibilityhovertransparent)接口。
```

```TypeScript
### 示例1（设置背景基础样式）

该示例通过配置backgroundColor、backgroundImage、backgroundImageSize和backgroundImagePosition设置背景的基础样式。


```

```TypeScript
### 示例2（设置背景模糊样式）

该示例通过backgroundBlurStyle设置背景模糊样式。


```

```TypeScript
### 示例3（设置组件背景）

该示例通过background设置组件背景。


```

```TypeScript
### 示例4（设置组件背景提亮效果）

该示例通过backgroundBrightness设置组件背景提亮效果。

效果图如下：

rate和lightUpDegree参数值为0.5,0.5：



修改rate和lightUpDegree参数值为0.5,-0.1：



去掉backgroundBrightness的设置，效果如下：


```

```TypeScript
### 示例5（设置模糊属性）

该示例提供了模糊属性的实现方法。通过blur设置内容模糊，通过backdropBlur设置背景模糊。


```

```TypeScript
### 示例6（设置文字异形模糊效果）

该示例通过[blendMode](ts-universal-attributes-image-effect.md#blendmode11)和backgroundEffect实现文字异形模糊效果。如果出现漏线问题，开发者应首先确保两个blendMode所在组件大小严格相同。如果确认相同，可能是组件边界落在浮点数坐标上导致，可尝试设置[pixelRound](ts-universal-attributes-pixelRoundForComponent.md#pixelround)通用属性，使产生的白线、暗线两侧的组件边界对齐到整数像素坐标上。


```

```TypeScript
### 示例7（模糊效果对比）

该示例对比了[backgroundEffect11+](#backgroundeffect11)、[backdropBlur](arkts-arkui-commonmethod-c.md#backdropblur)和[backgroundBlurStyle9+](#backgroundblurstyle9)三种不同的模糊效果。


```

```TypeScript
### 示例8（设置P3色域背景效果）

从API version 20开始，该示例通过[backgroundColor](#backgroundcolor20)设置P3色域背景效果。


```

```TypeScript
### 示例9（设置组件背景扩展）

从API version 20开始，该示例通过[background](#background10)实现组件背景扩展到父组件的安全区。
```

```TypeScript
该示例主要演示通过renderFit设置宽高动画过程中的组件内容不同填充方式。
```

```TypeScript
该示例演示背景模糊等特效的绘制合并。
```

```TypeScript
该示例通过reuseId标识自定义组件的复用组。
```

```TypeScript
### 示例1（弹出普通菜单）

该示例为bindMenu通过配置[MenuElement](arkts-arkui-menuelement-i.md)弹出普通菜单。


```

```TypeScript
### 示例2（弹出自定义菜单）

该示例为bindMenu通过配置CustomBuilder弹出自定义菜单。同时，从API version 18开始支持通过配置[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中的hapticFeedbackMode属性实现菜单弹出时的振动效果。


```

```TypeScript
### 示例3（长按弹出菜单）

该示例为bindContextMenu通过配置[responseType](ts-appendix-enums.md#responsetype8).LongPress弹出菜单。


```

```TypeScript
### 示例4（右键弹出指向型菜单）

该示例为bindContextMenu通过配置[responseType](ts-appendix-enums.md#responsetype8).RightClick和[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中的enableArrow属性弹出指向型菜单。同时，从API version 18开始支持通过配置[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中的hapticFeedbackMode属性实现菜单弹出时的振动效果。


```

```TypeScript
### 示例5（长按弹出菜单的截图预览样式）

该示例为bindContextMenu通过配置[responseType](ts-appendix-enums.md#responsetype8).LongPress和[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中preview属性的[MenuPreviewMode](arkts-arkui-menupreviewmode-e.md)类型弹出菜单预览样式。


```

```TypeScript
### 示例6（长按弹出菜单的自定义预览样式）

该示例为bindContextMenu通过配置[responseType](ts-appendix-enums.md#responsetype8).LongPress和[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中preview属性的[CustomBuilder](ts-types.md#custombuilder8)类型弹出菜单自定义预览样式。


```

```TypeScript
### 示例7（设置状态变量弹出菜单）

该示例为[bindContextMenu](arkts-arkui-commonmethod-c.md#bindcontextmenu)通过配置isShown弹出菜单预览样式。


```

```TypeScript
### 示例8（设置菜单和预览的动效）

该示例为bindContextMenu通过配置[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中的transition属性，实现自定义菜单以及菜单预览时的显示和退出动效。


```

```TypeScript
### 示例9（设置symbol类型图标）

该示例为bindMenu通过配置[MenuElement](arkts-arkui-menuelement-i.md)的symbolIcon弹出菜单。


```

```TypeScript
### 示例10（设置一镜到底动效）

该示例为bindContextMenu通过配置[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中previewAnimationOptions属性的hoverScale，实现组件截图到自定义预览图的一镜到底过渡动效。


```

```TypeScript
### 示例11（自定义背景模糊效果参数）

该示例为bindMenu通过配置[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中的backgroundBlurStyleOptions属性，实现了自定义菜单背景模糊效果。

从API version 18开始，在ContextMenuOptions中新增了backgroundBlurStyleOptions属性。


```

```TypeScript
### 示例12（自定义背景效果参数）

该示例为bindMenu通过配置[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中的backgroundEffect属性，实现了自定义菜单背景效果。

从API version 18开始，在ContextMenuOptions中新增了backgroundEffect属性。


```

```TypeScript
### 示例13（设置一镜到底动效支持抬手打断）

该示例通过为bindContextMenu配置[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中的previewAnimationOptions属性实现了一镜到底过渡动效的同时，再配置hoverScaleInterruption控制是否允许长按抬手取消菜单弹出。

从API version 20开始，在previewAnimationOptions的类型[ContextMenuAnimationOptions](arkts-arkui-contextmenuanimationoptions-i.md)中新增了hoverScaleInterruption属性。


```

```TypeScript
### 示例14（设置预览图边框圆角半径）

该示例通过bindContextMenu配置[responseType](ts-appendix-enums.md#responsetype8).LongPress来实现功能。同时，在[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中配置preview属性的[MenuPreviewMode](arkts-arkui-menupreviewmode-e.md)类型来设置菜单预览样式。最后，通过设置previewBorderRadius来实现预览图边框的圆角半径。

从API version 19开始，在[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中新增了previewBorderRadius属性。


```

```TypeScript
### 示例15（bindMenu配置生命周期回调）

该示例为bindMenu11+配置生命周期回调。

从API version 20开始，在[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中新增了onWillAppear、onDidAppear、onWillDisappear和onDidDisappear属性。


```

```TypeScript
### 示例16（设置菜单蒙层）

该示例为bindMenu通过配置mask属性设置菜单蒙层。

从API version 20开始，在[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中新增了mask属性。


```

```TypeScript
### 示例17（bindMenu设置下拉菜单外描边样式）

该示例为bindMenu通过配置outlineWidth和outlineColor属性设置下拉菜单外描边样式。

从API version 20开始，在[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中新增了outlineWidth和outlineColor属性。


```

```TypeScript
### 示例18（bindMenu传入带参数的CustomBuilder）

该示例通过在bindMenu中传入带参数的CustomBuilder来配置菜单的具体属性。


```

```TypeScript
### 示例19（根据触发方式弹出不同内容的菜单）

该示例通过在[bindContextMenuWithResponse](arkts-arkui-commonmethod-c.md#bindcontextmenuwithresponse)中传入CustomBuilderT<ResponseType>给目标组件绑定菜单，组件会在UI函数中返回弹出菜单的触发方式，开发者可根据返回的触发方式实现差异化显示。

从API version 23开始，新增了bindContextMenuWithResponse的接口。


```

```TypeScript
### 示例20（设置菜单避让软键盘）

该示例通过在bindMenu中配置keyboardAvoidMode设置菜单避让软键盘，通过minKeyboardAvoidDistance设置菜单避让软键盘的最小距离。

从API version 23开始，[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中新增keyboardAvoidMode、minKeyboardAvoidDistance属性。


```

```TypeScript
### 示例21（设置菜单相对于绑定组件左上角的弹出位置）

该示例通过设置[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中的anchorPosition属性，实现了菜单相对于绑定组件左上角弹出的效果。

从API version 20开始，在ContextMenuOptions中新增了anchorPosition属性。


```

```TypeScript
### 示例22（设置菜单的最大高度）

该示例为bindContextMenu通过配置[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中的maxHeight属性，设置菜单的最大高度。

未设置maxHeight属性时，默认按照菜单的最大高度（可用高度的80%），可展示全部列表项，通过设置最大高度为窗口可用高度的50%时，仅能显示8个列表项。

从API版本26.0.0开始，在ContextMenuOptions中新增了maxHeight属性。


```

```TypeScript
### 示例23（设置菜单与目标组件间距）

该示例通过设置[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中的targetSpace属性，介绍如何增加菜单与目标组件之间的间距。

从API版本26.0.0开始，在ContextMenuOptions中新增了targetSpace属性。


```

```TypeScript
### 示例24（设置菜单的沉浸光感）

该示例通过[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中的systemMaterial属性设置组件的系统材质，实现了菜单的沉浸光感视效。设置系统材质后，Menu弹出过程中会有非线性形变和边缘流光。

该示例配图为高算力设备强档效果，组件沉浸光感效果会根据设备算力与用户在系统中设置的沉浸光感效果自适应调整，开发者无需额外适配。

从API版本26.0.0开始，在ContextMenuOptions中新增了systemMaterial属性。

未设置系统材质时：



设置系统材质后：


```

```TypeScript
### 示例25（使用gridStyle设置栅格菜单）

该示例展示了如何在[bindContextMenuByIsShow](arkts-arkui-commonmethod-c.md#bindcontextmenubyisshow)中使用gridStyle设置栅格菜单样式。通过设置count、horizontalSize和position属性，可以自定义菜单的栅格布局。

从API版本26.0.0开始，新增了[bindContextMenuByIsShow](arkts-arkui-commonmethod-c.md#bindcontextmenubyisshow)的接口；在[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中新增了gridStyle属性。
```

```TypeScript
### 示例1（获取鼠标事件相关参数）

该示例通过按钮设置了鼠标事件，通过鼠标点击按钮可以触发[onMouse](#onmouse)事件，获取鼠标事件相关参数。从API version 15开始，可以获取鼠标事件[MouseEvent](#mouseevent对象说明)的targetDisplayId、rawDeltaX、rawDeltaY、pressedButtons等参数。

鼠标滚轮的处理请参考[轴事件示例](ts-universal-events-axis.md#示例)。

示意图：

鼠标点击时：


```

```TypeScript
### 示例2（获取当前帧历史点）

该示例通过调用[getHistoricalPoints](#gethistoricalpoints)接口，获取当前帧的历史点，可以用来实现更平滑的绘制等操作。

从API版本26.0.0开始，新增getHistoricalPoints接口。
```

```TypeScript
### 示例3（获取组件实时位置）

该示例通过[getCurrentLocalPosition](#getcurrentlocalposition)方法获取鼠标位置相对于当前组件实时位置左上角的坐标。

从API版本26.0.0开始，新增支持getCurrentLocalPosition接口。
```

```TypeScript
该示例通过配置visibility的不同值，实现不同的显隐控制效果。
```

```TypeScript
### 示例1（设置事件派发策略为FORWARD_COMPETITION）

在该示例中，点击List下方空白区域后拖动，可使List滑动。点击Button按钮时，Button会响应onClick事件。


```

```TypeScript
### 示例2（设置事件派发策略为FORWARD）

点击List下方空白区域后拖动，可以滑动List。点击Button按钮时，Button不会响应onClick事件。


```

```TypeScript
### 示例3（设置事件派发策略为DEFAULT）

点击List下方空白区域后拖动，List不会滑动。点击Button按钮时，Button会响应onClick事件。
```

```TypeScript
// xxx.ets
@Entry
@Component
struct TouchableExample {
  @State text1: string = '';
  @State text2: string = '';

  build() {
    Stack() {
      Rect()
        .fill(Color.Gray).width(150).height(150)
        .onClick(() => {
          console.info(this.text1 = 'Rect Clicked');
        })
        .overlay(this.text1, { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
      Ellipse()
        .fill(Color.Pink).width(150).height(80)
        .touchable(false) // 点击Ellipse区域，不会打印 “Ellipse Clicked”
        .onClick(() => {
          console.info(this.text2 = 'Ellipse Clicked');
        })
        .overlay(this.text2, { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
    }.margin(100);
  }
}
```

```TypeScript
该示例通过restoreId设置了List组件的分布式迁移标识。
```

```TypeScript
该示例主要演示使用[animateToImmediately](#animatetoimmediately)接口实现显式动画立即下发。
```

```TypeScript
该示例主要演示如何设置组件进行位移动画时的运动路径。此方法仅配置运动路径参数，需配合animateTo等动画触发方法及组件属性状态变化才能产生实际的位移动画效果，单独设置motionPath不会触发动画。
```

```TypeScript
### 示例1（获取点击事件相关参数）

该示例通过按钮设置点击事件[ClickEvent](arkts-arkui-clickevent-i.md)，点击按钮可获取点击事件的相关参数。


```

```TypeScript
### 示例2（获取组件实时位置）

该示例通过[getCurrentLocalPosition](#getcurrentlocalposition)方法获取当前组件基于其实时位置的左上角坐标。

从API版本26.0.0开始，新增支持getCurrentLocalPosition接口。
```

```TypeScript
当父组件出现1px的缝隙时，应利用pixelRound来指导布局调整。
```

```TypeScript
### 示例1（获取指定范围的文本内容）

该示例主要演示如何通过[TextAreaController](ts-basic-components-textarea.md#textareacontroller8)控制器调用[getText](#gettext19)接口，获取输入框中指定范围内的文本内容。

从API version 19开始，新增getText接口。
```

```TypeScript
### 示例1（使用同一接口实现图片出现消失）

该示例主要演示如何通过同一[TransitionEffect](#transitioneffect10对象说明)来实现图片的出现与消失，出现和消失互为逆过程。

示意图：
```

```TypeScript
### 示例2（使用不同接口实现图片出现消失）

该示例主要演示使用不同[TransitionEffect](#transitioneffect10对象说明)来实现图片的出现和消失。

示意图：
```

```TypeScript
### 示例3（设置父子组件为transition）

该示例主要演示通过父子组件都配置[transition](#transition)来实现图片的出现和消失。

示意图：
```

```TypeScript
### 示例4（visibility切换时的双动画复合效果）

该示例演示当[visibility](ts-universal-attributes-visibility.md#visibility)在Visibility.Visible与Visibility.None之间切换时，[transition](#transition)动画与布局动画叠加形成双动画复合表现的效果。
```

```TypeScript
### 示例1（嵌套滚动）

该示例通过shouldBuiltInRecognizerParallelWith和onGestureRecognizerJudgeBegin实现了嵌套滚动的功能。内部组件优先响应滑动手势，当内部组件滑动至顶部或底部时，外部组件能够接替滑动。


```

```TypeScript
### 示例2（嵌套场景下拦截内部容器手势）

本示例通过将参数exposeInnerGesture设置为true，实现了一级Tabs容器在嵌套二级Tabs的场景下，能够屏蔽二级Tabs内置Swiper的滑动手势，从而触发一级Tabs内置Swiper滑动手势的功能。

开发者自行定义变量记录内层Tabs的索引值，并通过该索引值判断滑动是否达到内层Tabs的边界。达到边界时，触发回调返回拒绝结果，屏蔽内层Tabs的滑动手势，使外层Tabs产生滑动手势。


```

```TypeScript
### 示例3（拦截手势获取属性）

该示例通过配置onGestureRecognizerJudgeBegin判定手势，获取手势的距离、手指数、是否限制手指数、重复触发状态、持续时间、点击次数、旋转角度、滑动方向和速度阈值等属性参数。


```

```TypeScript
### 示例4（手势触发成功时取消子组件上的Touch事件）

该示例通过配置onGestureRecognizerJudgeBegin判定手势，在父容器手势触发成功时，调用cancelTouch()强制取消子组件上的Touch事件，实现父子组件手势控制的精准切换。


```

```TypeScript
### 示例5（自定义手势识别器是否参与手势处理）

从API version 20开始，该示例通过配置[onTouchTestDone](arkts-arkui-commonmethod-c.md#ontouchtestdone)指定手势识别器不参与后续手势处理，触发回调时，调用[preventBegin](./ts-gesture-common.md#preventbegin20)阻止手势识别器参与后续处理。点击Tap2和Tap1的重合区域，不调用preventBegin时，触发Tap2对应的手势；调用preventBegin阻止Tap2时，触发Tap1对应的手势。


```

```TypeScript
### 示例6（自定义干预事件和手势的收集结果）

该示例通过配置[onGestureCollectIntercept](arkts-arkui-commonmethod-c.md#ongesturecollectintercept)指定手势识别器或者触摸识别器是否透传到其他节点。点击button2时，不透传触摸事件到Column。点击button1时，透传触摸事件到Column，Column变色。

从API版本26.0.0开始，新增onGestureCollectIntercept接口。
```

```TypeScript


示例对应的组件树如下图所示。
```

```TypeScript
### 示例7（非内置手势嵌套滚动）

该示例通过[shouldRecognizerParallelWith](arkts-arkui-commonmethod-c.md#shouldrecognizerparallelwith)和[onGestureRecognizerJudgeBegin](arkts-arkui-commonmethod-c.md#ongesturerecognizerjudgebegin)实现了嵌套滚动的功能。内部组件优先响应滑动手势，当内部组件滑动至顶部或底部时，外部组件能够接替滑动。

从API版本26.0.0开始，新增shouldRecognizerParallelWith接口。
```

```TypeScript
### 示例1（设置跟手变形拖拽动画）

该示例通过设置[dragAnimationType](#属性)为FOLLOW_HAND_MORPH实现跟手变形拖拽动画效果，并在拖拽结束时通过[executeFollowHandMorphDropAnimation](arkts-arkui-dragevent-i-sys.md#executefollowhandmorphdropanimation)执行自定义落位动效。

从API版本26.0.0开始，新增[dragAnimationType](#属性)属性、[executeFollowHandMorphDropAnimation](arkts-arkui-dragevent-i-sys.md#executefollowhandmorphdropanimation)方法、[interruptFollowHandMorphDropAnimation](../arkts-apis/arkts-arkui-arkui-uicontext-dragcontroller-c-sys.md#interruptfollowhandmorphdropanimation)方法。
```

```TypeScript
### 示例1（获取触摸事件相关参数）

该示例中，按钮设置触摸事件，在点击按钮时可获取事件的相关参数。


```

```TypeScript
### 示例2（获取组件实时位置）

该示例通过[getCurrentLocalPosition](#getcurrentlocalposition)方法获取触摸位置相对于当前组件实时位置左上角的坐标。

从API版本26.0.0开始，新增支持getCurrentLocalPosition接口。
```

```TypeScript
### 示例1（颜色线性渐变）

该示例通过[linearGradient](#lineargradient)来实现组件的颜色线性渐变。


```

```TypeScript
### 示例2（颜色按旋转角度渐变）

该示例通过[sweepGradient](arkts-arkui-commonmethod-c.md#sweepgradient)来实现组件颜色旋转角度渐变。


```

```TypeScript
### 示例3（颜色按径向渐变）

该示例通过[radialGradient](arkts-arkui-commonmethod-c.md#radialgradient)来实现组件颜色径向渐变。
```

```TypeScript
@Entry
@ComponentV2
struct Index {
  build() {
    Column() {
      ReusableV2Component()
        .reuse({reuseId: () => 'reuseComponent'}) // 使用'reuseComponent'作为reuseId
      ReusableV2Component()
        .reuse({reuseId: () => ''}) // 使用空字符串将默认使用组件名'ReusableV2Component'作为reuseId
      ReusableV2Component() // 未指定reuseId将默认使用组件名'ReusableV2Component'作为reuseId
    }
  }
}
@ReusableV2
@ComponentV2
struct ReusableV2Component {
  build() {
    Text('content')
  }
}
```

```TypeScript
### 示例1（通过string设置浮层）

该示例通过传入string设置浮层。


```

```TypeScript
### 示例2（通过builder设置浮层）

该示例通过传入builder设置浮层。


```

```TypeScript
### 示例3（通过ComponentContent设置浮层）

该示例通过overlay传入ComponentContent，并通过update方法更新ComponentContent参数，使backgroundColor不断发生变化。
```

```TypeScript
### 示例1（在组件出现时创建动画）

> 说明：
> 
> 直接使用animateTo可能导致[UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)的问题，建议使用getUIContext()获取[UIContext](../arkts-apis-uicontext-uicontext.md)实例，并使用[animateTo](../arkts-apis-uicontext-uicontext.md#animateto)调用绑定实例的animateTo。

该示例通过在onAppear方法中创建组件出现时的动画效果。


```

```TypeScript
### 示例2（动画执行结束后组件消失）

该示例主要演示如何实现在动画执行结束后组件消失。
```

```TypeScript
通过配置flexBasis/flexGrow/flexShrink/alignSelf属性设置Flex布局。
```

```TypeScript
### 示例1（设置图片不同属性效果）

设置图片的效果，包括阴影、灰度、高光、饱和度、对比度、图像反转、叠色、色相旋转等。


```

```TypeScript
### 示例2（设置组件线性渐变模糊效果）

该示例主要演示通过[linearGradientBlur](arkts-arkui-commonmethod-c.md#lineargradientblur)设置组件的内容线性渐变模糊效果。


```

```TypeScript
### 示例3（设置离屏渲染效果）

该示例主要演示通过[renderGroup](arkts-arkui-commonmethod-c.md#rendergroup)来设置组件是否先整体离屏渲染绘制后，再与父组件融合绘制。


```

```TypeScript
### 示例4（当前组件内容与下方画布内容混合）

该示例主要演示通过[blendMode](#blendmode11)将当前组件内容与下方画布内容混合。


```

```TypeScript
### 示例5（前景智能取反色）

该示例主要通过[InvertOptions](#invertoptions11对象说明)来实现前景智能取反色。


```

```TypeScript
### 示例6（设置同层阴影不重叠效果）

该示例主要通过[useShadowBatching](arkts-arkui-commonmethod-c.md#useshadowbatching)搭配[shadow](#shadow)实现同层阴影不重叠效果。


```

```TypeScript
### 示例7（设置组件图像球面效果）

该示例主要演示通过[sphericalEffect](arkts-arkui-commonmethod-c.md#sphericaleffect)设置组件的图像球面效果。

效果图如下：



去掉sphericalEffect的设置，效果如下：


```

```TypeScript
### 示例8（设置组件图像渐亮效果）

该示例主要演示通过[lightUpEffect](arkts-arkui-commonmethod-c.md#lightupeffect)设置组件的图像渐亮效果。

效果图如下：



修改lightUpEffect参数值为0.2：



去掉lightUpEffect的设置，效果如下：


```

```TypeScript
### 示例9（设置组件图像边缘像素扩展效果）

该示例主要演示通过[pixelStretchEffect](arkts-arkui-commonmethod-c.md#pixelstretcheffect)设置组件的图像边缘像素扩展效果。

效果图如下：



去掉pixelStretchEffect的设置，原图效果如下：


```

```TypeScript
### 示例10（系统导航条智能反色）

该示例主要演示通过[systemBarEffect](arkts-arkui-commonmethod-c.md#systembareffect)来实现系统导航条智能反色。

效果图如下：


```

```TypeScript
### 示例11（设置组件是否双面绘制）

该示例主要演示通过[doubleSided](arkts-arkui-commonmethod-c.md#doublesided)来设置组件是否双面绘制。

从API版本26.0.0开始，新增doubleSided方法。
```

```TypeScript
通过ContentModifier实现自定义复选框样式的功能，用一个五边形复选框替换原本Checkbox的样式。如果选中，内部会出现红色三角图案，标题会显示选中字样；如果取消选中，红色三角图案消失，标题会显示非选中字样。
```

```TypeScript
// 组件添加allowForceDark(false)属性后，说明对当前组件及其所有子组件均不使用反色相关能力。
@Entry
@Component
struct ComponentPage {
  build() {
    Column() {
      Column() {
        Text("Hello World")
          .fontSize(20)
          .fontColor(Color.Blue)
          .onClick(() => {
            console.info(`Text is clicked`);
          })
      }
      .allowForceDark(false) // Column及其子组件Text不使用反色能力，不受父组件Column使用反色能力的影响。

      Row() {
        Button('BUTTON')
          .backgroundColor(Color.Grey)
          .allowForceDark(true)
          .onClick(() => {
            console.info(`Button is clicked`);
          })
      }
      .allowForceDark(false) // Row及其子组件Button不使用反色能力，不受父组件Column使用反色能力的影响。
    }
    .allowForceDark(true)
    .width('100%')
    .height('100%')
  }
}
```

```TypeScript
该示例演示如何通过配置monopolizeEvents设置组件是否独占事件。
```

```TypeScript
### 示例1（设置组件拖拽和落入）

示例1展示了部分组件（如Image和Text等）拖拽和可落入区域的设置。


```

```TypeScript
### 示例2（自定义落位动效）

从API version 18开始，示例2展示了通过[executeDropAnimation](arkts-arkui-dragevent-i.md#executedropanimation)接口，实现自定义落位动效。


```

```TypeScript
### 示例3（拖拽异步获取数据）

从API version 15开始，示例3展示了通过[startDataLoading](arkts-arkui-dragevent-i.md#startdataloading)实现拖拽异步获取数据。
```

```TypeScript
### 示例4（获取当前拖拽的屏幕ID）

从API version 20开始，示例4展示了通过onDragXXX（不支持onDragEnd）接口获取拖拽事件，并调用拖拽事件的[getDisplayId](#getdisplayid20)接口获取屏幕ID。


```

```TypeScript
### 示例5（获取包名和是否是跨设备）

从API version 20开始，示例5展示了通过onDragXXX接口获取拖拽事件，调用拖拽事件的[getDragSource](arkts-arkui-dragevent-i.md#getdragsource)接口获取包名，调用isRemote接口判断是否为跨设备拖拽。


```

```TypeScript
### 示例6（拖拽支持悬停检测）

从API version 20开始，示例6展示了通过[onDragSpringLoading](arkts-arkui-commonmethod-c.md#ondragspringloading)接口注册回调，并通过回调中的[SpringLoadingContext](#springloadingcontext20)获取上下文信息（当前状态、通知序列）。


```

```TypeScript
### 示例7（拖起方延迟提供数据）

从API version 20开始，示例7展示了在[onDragStart](#ondragstart)中调用[setDataLoadParams](arkts-arkui-dragevent-i.md#setdataloadparams)延迟提供数据接口，并在[onDrop](#ondrop)中调用[startDataLoading](arkts-arkui-dragevent-i.md#startdataloading)异步获取数据接口。


```

```TypeScript
### 示例8（拖拽自动隐藏指定组件）

该示例通过DragEvent的[autoHideComponentUniqueIds](#属性)属性，在拖拽成功发起后自动隐藏指定组件。

从API版本26.0.0开始，DragEvent新增autoHideComponentUniqueIds属性。
```

```TypeScript
### 示例1（自定义布局代码示例）

自定义布局代码示例。


```

```TypeScript
### 示例2（判断是否参与布局计算）

通过组件的位置灵活判断是否参与布局计算。


```

```TypeScript
### 示例3（获取子组件FrameNode并设置相关属性）

通过uniqueId获取子组件的FrameNode，并调用FrameNode的API接口修改尺寸、背景颜色。


```

```TypeScript
### 示例4（子组件超过父组件大小约束）

在自定义布局的自定义组件中，为子组件设置了[LayoutPolicy](./ts-universal-attributes-size.md#layoutpolicy15)对象的fixAtIdealSize属性。
```
