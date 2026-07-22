# ScrollSnapOptions

限位滚动模式对象。

**起始版本：** 10

<!--Device-unnamed-declare interface ScrollSnapOptions--><!--Device-unnamed-declare interface ScrollSnapOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableSnapToEnd

```TypeScript
enableSnapToEnd?: boolean
```

在Scroll组件限位滚动模式下，该属性设置为true后，不允许Scroll在最后一页和末尾间自由滑动，该属性设置为false后，允许Scroll在最后一页和末尾间自由滑动。

<p><strong>说明</strong><br>1. 该属性值默认为true。<br>2. 该属性仅当snapPagination属性为Array\&lt;Dimension\&gt;时生效，不支持Dimension。</p>

**类型：** boolean

**默认值：** true

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollSnapOptions-enableSnapToEnd?: boolean--><!--Device-ScrollSnapOptions-enableSnapToEnd?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableSnapToStart

```TypeScript
enableSnapToStart?: boolean
```

在Scroll组件限位滚动模式下，该属性设置为true后，不允许Scroll在开头和第一页间自由滑动，该属性设置为false后，允许Scroll在开头和第一页间自由滑动。

<p><strong>说明</strong><br>1. 该属性值默认为true。<br>2. 该属性仅当snapPagination属性为Array\&lt;Dimension\&gt;时生效，不支持Dimension。</p>

**类型：** boolean

**默认值：** true

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollSnapOptions-enableSnapToStart?: boolean--><!--Device-ScrollSnapOptions-enableSnapToStart?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## snapAlign

```TypeScript
snapAlign: ScrollSnapAlign
```

限位滚动时的对齐方式。

**类型：** ScrollSnapAlign

**默认值：** ScrollSnapAlign.NONE [since 11]

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollSnapOptions-snapAlign: ScrollSnapAlign--><!--Device-ScrollSnapOptions-snapAlign: ScrollSnapAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## snapPagination

```TypeScript
snapPagination?: Dimension | Array<Dimension>
```

限位滚动时的分页点。

<p><strong>说明</strong><br>1.当属性为Dimension时，Dimension表示每页的大小，系统按照该大小进行分页。<br>2.当属性为Array\&lt;Dimension\&gt;时，每个Dimension表示分页点，系统按照分页点进行分页。每个Dimension的范围为[0,可滑动距离]。<br>3.当该属性不填或者Dimension为小于等于0的输入时，按异常值，无限位滚动处理。当该属性值为Array\&lt;Dimension\&gt;数组时，数组中的数值必须为单调递增。<br>4.当输入为百分比时，实际的大小为Scroll组件的视口与百分比数值之积。</p>

**类型：** Dimension \| Array&lt;Dimension&gt;

**默认值：** 100%

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollSnapOptions-snapPagination?: Dimension | Array<Dimension>--><!--Device-ScrollSnapOptions-snapPagination?: Dimension | Array<Dimension>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

