# ReactiveComponentContent

定义 ReactiveComponentContent

**继承/实现关系：** ReactiveComponentContent extends [ComponentContentBase](arkts-na-componentcontent-componentcontentbase-c.md#ComponentContentBase)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare class ReactiveComponentContent--><!--Device-unnamed-export declare class ReactiveComponentContent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(uiContext: UIContext, builder: CustomBuilder, options?: BuildOptions)
```

构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ReactiveComponentContent-constructor(uiContext: UIContext, builder: CustomBuilder, options?: BuildOptions)--><!--Device-ReactiveComponentContent-constructor(uiContext: UIContext, builder: CustomBuilder, options?: BuildOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | [UIContext](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md) | 是 | 用于创建 ReactiveComponentContent 的 UIContext对象 |
| builder | CustomBuilder | 是 | 将被调用来构建 ReactiveComponentContent 的builder。 |
| options | [BuildOptions](../../apis-arkui/arkts-apis/arkts-arkui-buildernode-buildoptions-i.md) | 否 | 构建时要使用的选项。 |

## dispose

```TypeScript
dispose(): void
```

立即解绑 ReactiveComponentContent。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ReactiveComponentContent-dispose(): void--><!--Device-ReactiveComponentContent-dispose(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## flushState

```TypeScript
flushState(): void
```

立即刷新当前状态变更以更新ReactiveComponentContent。 这会强制组件使用最新的状态值进行同步更新。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ReactiveComponentContent-flushState(): void--><!--Device-ReactiveComponentContent-flushState(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isDisposed

```TypeScript
isDisposed(): boolean
```

获取 ReactiveComponentContent 是否已被解绑。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ReactiveComponentContent-isDisposed(): boolean--><!--Device-ReactiveComponentContent-isDisposed(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果 ReactiveComponentContent 已被解绑则返回 true，否则返回 false。 |

## isTransferred

```TypeScript
isTransferred(): boolean
```

返回一个标志位，表示当前ReactiveComponentContent是否通过动态-静态转换获取。 该转换包含两个方向：从动态转换为静态，以及从静态转换为动态。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ReactiveComponentContent-isTransferred(): boolean--><!--Device-ReactiveComponentContent-isTransferred(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果 ReactiveComponentContent 是经过动态和静态状态之间转换得到的，则返回 true，否则返回 false。 |

## recycle

```TypeScript
recycle(): void
```

回收 ReactiveComponentContent。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ReactiveComponentContent-recycle(): void--><!--Device-ReactiveComponentContent-recycle(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## reuse

```TypeScript
reuse(param?: RecordData): void
```

基于提供的参数重用ReactiveComponentContent

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ReactiveComponentContent-reuse(param?: RecordData): void--><!--Device-ReactiveComponentContent-reuse(param?: RecordData): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [RecordData](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-recorddata-t.md) | 否 | 用于复用ReactiveComponentContent的参数。该参数将直接用于ReactiveComponentContent中所有顶层自定义组件的复用，应该包含每个自定义组件的构造函数参数所需内容，否则，会导致未定义行为。调用此方法将同步触发内部自定义组件的aboutToReuse生命周期回调，并将该参数作为回调的入参。默认值为undefined，此时ReactiveComponentContent中的自定义组件将直接使用构造时的数据源。 |

## updateConfiguration

```TypeScript
updateConfiguration(): void
```

通知 ReactiveComponentContent 更新配置以触发重新加载。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ReactiveComponentContent-updateConfiguration(): void--><!--Device-ReactiveComponentContent-updateConfiguration(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

