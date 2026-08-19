# BuilderNode

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [BuilderNode](arkts-arkui-buildernode-c.md) | 提供能够挂载系统组件的自定义节点BuilderNode。BuilderNode仅可作为叶子节点使用，支持通过@Builder生成组件树、实现组件复用与回收、跨节点事件分发以及状态同步，适用于在应用内动态创建和管理自定义组件节点的场景。 使用方式参考[BuilderNode开发指南](../../../ui/arkts-user-defined-arktsNode-builderNode.md)。 与BuilderNode相比，ReactiveBuilderNode能通过多参数的无状态UI方法@Builder生成组件树，适用于需要多参数数据绑定和响应式UI动态更新的场景。 @internal/component/ets/span}、ContainerSpan、 > SymbolSpan或自定义组件，将额外生成一个FrameNode，在节点树中显示为“ > BuilderProxyNode”，这会导致树结构变化，影响事件传递等测试流程。详情参见 > [BuilderNode内的BuilderProxyNode导致树结构发生变化](../../../ui/arkts-user-defined-arktsNode-builderNode.md#buildernode内的builderproxynode导致树结构发生变化)。 > > - 如果在跨页面复用BuilderNode时显示异常，可参考[跨页面复用注意事项](../../../ui/arkts-user-defined-arktsNode-builderNode.md#跨页面复用注意事项)。 > > - 当前不支持在预览器中使用BuilderNode。 > > - BuilderNode下的自定义组件支持使用[@Prop装饰器](../../../ui/state-management/arkts-prop.md)。不支持使用 > [@Link装饰器](../../../ui/state-management/arkts-link.md)来跨越BuilderNode同步外界的数据和状态。 > > - 如果BuilderNode的子节点是自定义组件，不支持该自定义组件使用[@Reusable装饰器](../../../ui/state-management/arkts-reusable.md)，详细内容参见 > [BuilderNode在子自定义组件中使用@Reusable装饰器](../../../ui/arkts-user-defined-arktsNode-builderNode.md#buildernode在子自定义组件中使用reusable装饰器)。 > > - 从API version 12开始，自定义组件支持接收[LocalStorage](../../../ui/state-management/arkts-localstorage.md)实例。可以通过 > [传递LocalStorage实例](../../../ui/state-management/arkts-localstorage.md#自定义组件接收localstorage实例)来使用LocalStorage相关的装饰器 > [@LocalStorageProp](../../../ui/state-management/arkts-localstorage.md#localstorageprop)、 > [@LocalStorageLink](../../../ui/state-management/arkts-localstorage.md#localstoragelink)。 > > - 从API version 20开始，通过配置[BuildOptions](arkts-arkui-buildernode-buildoptions-i.md)，内部自定义组件的 > [@Consume](../../../ui/state-management/arkts-provide-and-consume.md)支持接收所在页面的 > [@Provide](../../../ui/state-management/arkts-provide-and-consume.md)数据。 > > - 其余装饰器行为未定义，不建议使用。 > > - 仅支持在自定义组件中使用[Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)。 > > - BuilderNode对象不支持使用JSON序列化。 |
| [ReactiveBuilderNode](arkts-arkui-buildernode-reactivebuildernode-c.md) | ReactiveBuilderNode支持通过无状态的UI方法[@Builder](../../../ui/state-management/arkts-builder.md)生成组件树，并持有该组件树的根节点，不支持定义为状态变 量。ReactiveBuilderNode中持有的FrameNode仅用于将此ReactiveBuilderNode作为子节点挂载到其他FrameNode上。对 ReactiveBuilderNode持有的FrameNode进行属性设置与子节点操作可能会导致未定义行为，因此不建议通过ReactiveBuilderNode的 [getFrameNode](arkts-arkui-buildernode-c.md#getframenode)方法和FrameNode节点的 [getRenderNode](arkts-arkui-framenode-c.md#getrendernode)方法获取RenderNode，并通过 [RenderNode](../../apis-na/arkts-apis/arkts-na-rendernode-c.md)的接口对其进行属性设置与子节点操作。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [BuildOptions](arkts-arkui-buildernode-buildoptions-i.md) | build的可选参数。 |
| [RenderOptions](arkts-arkui-buildernode-renderoptions-i.md) | 创建BuilderNode时的可选参数。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [NodeRenderType](arkts-arkui-buildernode-noderendertype-e.md) | 节点渲染类型枚举。 @internal/component/ets/badge} > 、Blank、Button、 > CanvasGradient、CanvasPattern、 > CanvasRenderingContext2D、 > Canvas、CheckboxGroup、 > Checkbox、Circle、 > ColumnSplit、Column、 > ContainerSpan、 > Counter、DataPanel、 > Divider、Ellipse、 > Flex、Gauge、 > Hyperlink、ImageBitmap、 > ImageData、Image、 > Line、LoadingProgress、 > Marquee、Matrix2D、 > OffscreenCanvasRenderingContext2D、 > OffscreenCanvas、Path2D、 > Path、PatternLock、 > Polygon、Polyline、 > Progress、QRCode、 > Radio、Rating、 > Rect、 > RelativeContainer、 > RowSplit、Row、 > Shape、Slider、 > Span、Stack、 > TextArea、TextClock、 > TextInput、TextTimer、 > Text、Toggle、 > Video（不含全屏播放能力）、Web、 > XComponent。 > > - 从API version 12开始，新增以下组件支持纹理导出：DatePicker、 > ForEach、Grid、 > [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、 > LazyForEach、List、 > Scroll、Swiper、 > TimePicker、 > [@Component](../../../ui/state-management/arkts-create-custom-components.md#component)修饰的自定义组件、 > NodeContainer以及 > NodeContainer下挂载的FrameNode和 > [RenderNode](../../apis-na/arkts-apis/arkts-na-rendernode-c.md)。 > > - 使用方式可参考[同层渲染绘制](../../../web/web-same-layer.md)。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [InputEventType](arkts-arkui-inputeventtype-t.md) | [postInputEvent](arkts-arkui-buildernode-c.md#postinputevent)的参数，定义要发送的输入事件类型。 |

