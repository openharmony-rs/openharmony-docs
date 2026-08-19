# ComponentContent

Defines ComponentContent.

**继承/实现关系：** ComponentContent extends [ComponentContentBase](arkts-na-componentcontent-componentcontentbase-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class ComponentContent--><!--Device-unnamed-export declare class ComponentContent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(uiContext: UIContext, builder: WrappedBuilder<CustomBuilder>)
```

Constructor.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComponentContent-constructor(uiContext: UIContext, builder: WrappedBuilder<CustomBuilder>)--><!--Device-ComponentContent-constructor(uiContext: UIContext, builder: WrappedBuilder<CustomBuilder>)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | [UIContext](arkts-na-arkui-uicontext-uicontext-c.md) | 是 | uiContext used to create the ComponentContent |
| builder | WrappedBuilder&lt;CustomBuilder&gt; | 是 | Defines the builder that will be called to build ComponentContent. |

## constructor

```TypeScript
constructor(uiContext: UIContext, builder: WrappedBuilder<CustomBuilderT<T>>, args: T)
```

Constructor.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComponentContent-constructor(uiContext: UIContext, builder: WrappedBuilder<CustomBuilderT<T>>, args: T)--><!--Device-ComponentContent-constructor(uiContext: UIContext, builder: WrappedBuilder<CustomBuilderT<T>>, args: T)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | [UIContext](arkts-na-arkui-uicontext-uicontext-c.md) | 是 | uiContext used to create the ComponentContent |
| builder | WrappedBuilder&lt;CustomBuilderT&lt;T&gt;&gt; | 是 | Defines the builder that will be called to build ComponentContent. |
| args | T | 是 | Parameters used to update the ComponentContent. |

## constructor

```TypeScript
constructor(uiContext: UIContext, builder: WrappedBuilder<CustomBuilderT<T>>, args: T, options: BuildOptions)
```

Constructor.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComponentContent-constructor(uiContext: UIContext, builder: WrappedBuilder<CustomBuilderT<T>>, args: T, options: BuildOptions)--><!--Device-ComponentContent-constructor(uiContext: UIContext, builder: WrappedBuilder<CustomBuilderT<T>>, args: T, options: BuildOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | [UIContext](arkts-na-arkui-uicontext-uicontext-c.md) | 是 | uiContext used to create the ComponentContent |
| builder | WrappedBuilder&lt;CustomBuilderT&lt;T&gt;&gt; | 是 | Defines the builder that will be called to build ComponentContent. ComponentContent. |
| args | T | 是 | Parameters used to update the ComponentContent. |
| options | [BuildOptions](../../apis-arkui/arkts-apis/arkts-arkui-buildernode-buildoptions-i.md) | 是 | Defines the options that will be used when building. |

## dispose

```TypeScript
dispose(): void
```

Dispose the ComponentContent immediately.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComponentContent-dispose(): void--><!--Device-ComponentContent-dispose(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isDisposed

```TypeScript
isDisposed(): boolean
```

获取 ComponentContent 是否已被解绑。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComponentContent-isDisposed(): boolean--><!--Device-ComponentContent-isDisposed(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果 ComponentContent 已被解绑则返回 true，否则返回 false。 |

## isTransferred

```TypeScript
isTransferred(): boolean
```

返回一个标志位，表示当前 ComponentContent 是否通过动态-静态转换获取。 该转换包含两个方向：从动态转换为静态，以及从静态转换为动态。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComponentContent-isTransferred(): boolean--><!--Device-ComponentContent-isTransferred(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果ComponentContent在动态和静态状态之间转换，则返回true。 否则返回false。 |

## recycle

```TypeScript
recycle(): void
```

Recycle the ComponentContent.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComponentContent-recycle(): void--><!--Device-ComponentContent-recycle(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## reuse

```TypeScript
reuse(param?: RecordData): void
```

基于提供的参数复用ComponentContent。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComponentContent-reuse(param?: RecordData): void--><!--Device-ComponentContent-reuse(param?: RecordData): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [RecordData](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-recorddata-t.md) | 否 | 用于复用ComponentContent的参数。该参数将直接用于ComponentContent中所有顶层自定义组件的复用，应该包含每个自定义组件的构造函数参数所需内容，否则，会导致未定义行为。调用此方法将同步触发内部自定义组件的aboutToReuse生命周期回调，并将该参数作为回调的入参。默认值为undefined，此时ComponentContent中的自定义组件将直接使用构造时的数据源。 |

## update

```TypeScript
update(args: T): void
```

Update the ComponentContent based on the provided parameters.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComponentContent-update(args: T): void--><!--Device-ComponentContent-update(args: T): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| args | T | 是 | Parameters used to update the ComponentContent, which must match the types required by the builder bound to the ComponentContent. |

## updateConfiguration

```TypeScript
updateConfiguration(): void
```

Notify ComponentContent to update the configuration to trigger a reload of the ComponentContent.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComponentContent-updateConfiguration(): void--><!--Device-ComponentContent-updateConfiguration(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

