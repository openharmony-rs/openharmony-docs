# ScrollSnapOptions

限位滚动模式对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface ScrollSnapOptions--><!--Device-unnamed-export declare interface ScrollSnapOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableSnapToEnd

```TypeScript
enableSnapToEnd?: boolean
```

在Scroll组件限位滚动模式下，该属性设置为true后，不允许Scroll在最后一页和末尾间自由滑动，该属性设置为false后，允许Scroll在最后一页和末尾间自由滑动。 &lt;p&gt;&lt;strong&gt;说明&lt;/strong&gt;。 &lt;br&gt;该属性仅当snapPagination属性为Array&lt;Dimension&gt;时生效，不支持Dimension。 &lt;/p&gt;

**类型：** boolean

**默认值：** true

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScrollSnapOptions-enableSnapToEnd?: boolean--><!--Device-ScrollSnapOptions-enableSnapToEnd?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableSnapToStart

```TypeScript
enableSnapToStart?: boolean
```

在Scroll组件限位滚动模式下，该属性设置为true后，不允许Scroll在开头和第一页间自由滑动，该属性设置为false后，允许Scroll在开头和第一页间自由滑动。 &lt;p&gt;&lt;strong&gt;说明&lt;/strong&gt;。 &lt;br&gt;该属性仅当snapPagination属性为Array&lt;Dimension&gt;时生效，不支持Dimension。 &lt;/p&gt;

**类型：** boolean

**默认值：** true

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScrollSnapOptions-enableSnapToStart?: boolean--><!--Device-ScrollSnapOptions-enableSnapToStart?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## snapAlign

```TypeScript
snapAlign: ScrollSnapAlign
```

设置Scroll组件限位滚动时的对齐方式。

**类型：** [ScrollSnapAlign](../../apis-arkui/arkts-components/arkts-arkui-scrollsnapalign-e.md)

**默认值：** ScrollSnapAlign.NONE

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScrollSnapOptions-snapAlign: ScrollSnapAlign--><!--Device-ScrollSnapOptions-snapAlign: ScrollSnapAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## snapPagination

```TypeScript
snapPagination?: Dimension | Array<Dimension>
```

设置Scroll组件限位滚动时的分页点。 &lt;p&gt;&lt;strong&gt;说明&lt;/strong&gt;。 &lt;br&gt;1.当属性为Dimension时，Dimension表示每页的大小，系统按照该大小进行分页。 &lt;br&gt;2.当属性为Array&lt;Dimension&gt;时，每个Dimension表示分页点，系统按照分页点进行分页。每个Dimension的范围为[0,可滑动距离]。 &lt;br&gt;3.当该属性不填或者Dimension为小于等于0的输入时，按异常值，无限位滚动处理。当该属性值为Array&lt;Dimension&gt;数组时，数组中的数值必须为单调递增。 &lt;br&gt;4.当输入为百分比时，实际的大小为Scroll组件的视口与百分比数值之积。 &lt;/p&gt;

**类型：** [Dimension](../../apis-arkui/arkts-apis/arkts-arkui-dimension-t.md) \| Array&lt;[Dimension](../../apis-arkui/arkts-apis/arkts-arkui-dimension-t.md)&gt;

**默认值：** 100%

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScrollSnapOptions-snapPagination?: Dimension | Array<Dimension>--><!--Device-ScrollSnapOptions-snapPagination?: Dimension | Array<Dimension>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

