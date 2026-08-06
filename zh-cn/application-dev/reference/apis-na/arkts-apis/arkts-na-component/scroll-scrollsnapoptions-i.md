# ScrollSnapOptions

限位滚动模式对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface ScrollSnapOptions--><!--Device-unnamed-export declare interface ScrollSnapOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableSnapToEnd

```TypeScript
enableSnapToEnd?: boolean
```

在Scroll组件限位滚动模式下，该属性设置为true后，不允许Scroll在最后一页和末尾间自由滑动，该属性设置为false后，允许Scroll在最后一页和末尾间自由滑动。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_说明\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_。 \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_该属性仅当snapPagination属性为Array&lt;Dimension&gt;时生效，不支持Dimension。 \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_

**类型：** boolean

**默认值：** true

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScrollSnapOptions-enableSnapToEnd?: boolean--><!--Device-ScrollSnapOptions-enableSnapToEnd?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableSnapToStart

```TypeScript
enableSnapToStart?: boolean
```

在Scroll组件限位滚动模式下，该属性设置为true后，不允许Scroll在开头和第一页间自由滑动，该属性设置为false后，允许Scroll在开头和第一页间自由滑动。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_说明\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_。 \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_该属性仅当snapPagination属性为Array&lt;Dimension&gt;时生效，不支持Dimension。 \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_

**类型：** boolean

**默认值：** true

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScrollSnapOptions-enableSnapToStart?: boolean--><!--Device-ScrollSnapOptions-enableSnapToStart?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## snapAlign

```TypeScript
snapAlign: ScrollSnapAlign
```

设置Scroll组件限位滚动时的对齐方式。

**类型：** ScrollSnapAlign

**默认值：** ScrollSnapAlign.NONE

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScrollSnapOptions-snapAlign: ScrollSnapAlign--><!--Device-ScrollSnapOptions-snapAlign: ScrollSnapAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## snapPagination

```TypeScript
snapPagination?: Dimension | Array<Dimension>
```

设置Scroll组件限位滚动时的分页点。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_说明\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_。 \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_1.当属性为Dimension时，Dimension表示每页的大小，系统按照该大小进行分页。 \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_2.当属性为Array&lt;Dimension&gt;时，每个Dimension表示分页点，系统按照分页点进行分页。每个Dimension的范围为[0,可滑动距离]。 \_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_3.当该属性不填或者Dimension为小于等于0的输入时，按异常值，无限位滚动处理。当该属性值为Array&lt;Dimension&gt;数组时，数组中的数值必须为单调递增。 \_\_\_HTML\_TAG\_DESC\_USD\_6\_\_\_4.当输入为百分比时，实际的大小为Scroll组件的视口与百分比数值之积。 \_\_\_HTML\_TAG\_DESC\_USD\_7\_\_\_

**类型：** Dimension \| Array&lt;Dimension&gt;

**默认值：** 100%

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScrollSnapOptions-snapPagination?: Dimension | Array<Dimension>--><!--Device-ScrollSnapOptions-snapPagination?: Dimension | Array<Dimension>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

