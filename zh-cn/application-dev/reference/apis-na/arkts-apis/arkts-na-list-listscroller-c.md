# ListScroller

List组件的滚动控制器，通过它控制List组件的滚动，仅支持一对一绑定到List组件。 > **说明：** > > ListScroller继承自Scroller，具有Scroller的全部方法。

**继承/实现关系：** ListScroller extends Scroller

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class ListScroller--><!--Device-unnamed-export declare class ListScroller-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## closeAllSwipeActions

```TypeScript
closeAllSwipeActions(options?: CloseSwipeActionOptions): void
```

将EXPANDED状态的ListItem收起，并设置回调事件。 &lt;p&gt;&lt;strong&gt;注意&lt;/strong&gt;： <br>-一个&lt;em&gt;ListScroller&lt;/em&gt;必须绑定到&lt;em&gt;List&lt;/em&gt;组件。 &lt;/p&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ListScroller-closeAllSwipeActions(options?: CloseSwipeActionOptions): void--><!--Device-ListScroller-closeAllSwipeActions(options?: CloseSwipeActionOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [CloseSwipeActionOptions](arkts-na-list-closeswipeactionoptions-i.md) | 否 | 收起EXPANDED状态的ListItem 的回调事件集合。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100004](../../apis-arkui/errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Controller not bound to a component. |

## getItemRectInGroup

```TypeScript
getItemRectInGroup(index: int, indexInGroup: int): RectResult
```

获取ListItemGroup中的ListItem的大小和相对于List的位置。 &lt;p&gt;&lt;strong&gt;注意&lt;/strong&gt;： <br>-&lt;em&gt;index&lt;/em&gt;的值必须是显示区域中可见的子组件的索引。 否则，该值将被视为无效值。 <br>-设置&lt;em&gt;index&lt;/em&gt;的子组件必须是列表项组。否则， &lt;em&gt;index &lt;/em&gt;值被认为是无效的。 <br>-&lt;em&gt;indexInGroup&lt;/em&gt;的值必须是列表项组中某个列表项的索引 在显示区域中可见。否则，该值将被视为无效值。 <br>-当&lt;em&gt;index&lt;/em&gt;或&lt;em&gt;indexInGroup&lt;/em&gt;设置为无效值时，返回的大小和位置均为&lt;em&gt;0&lt;/em&gt;。 &lt;/p&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ListScroller-getItemRectInGroup(index: int, indexInGroup: int): RectResult--><!--Device-ListScroller-getItemRectInGroup(index: int, indexInGroup: int): RectResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | ListItemGroup在List中的索引值。 <br>取值限定为整数。 |
| indexInGroup | int | 是 | ListItemGroup在List中的索引值。 <br>取值限定为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RectResult](../../apis-arkui/arkts-components/arkts-arkui-rectresult-i.md) | ListItemGroup中的ListItem的大小和相对于List的位置。<br/>单位：vp。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100004](../../apis-arkui/errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Controller not bound to a component. |

## getVisibleListContentInfo

```TypeScript
getVisibleListContentInfo(x: double, y: double): VisibleListContentInfo
```

根据坐标获取子组件的索引信息。 &lt;p&gt;&lt;strong&gt;注意&lt;/strong&gt;： <br>-如果提供的&lt;em&gt;x&lt;/em&gt;或&lt;em&gt;y&lt;/em&gt;的值无效， 返回的VisibleListContentInfo对象的&lt;em&gt;index&lt;/em&gt;属性设置为&lt;em&gt;-1&lt;/em&gt;。 且&lt;em&gt;itemGroupArea&lt;/em&gt;和&lt;em&gt;itemIndexInGroup&lt;/em&gt;均为&lt;em&gt;未定义&lt;/em&gt;。 &lt;/p&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ListScroller-getVisibleListContentInfo(x: double, y: double): VisibleListContentInfo--><!--Device-ListScroller-getVisibleListContentInfo(x: double, y: double): VisibleListContentInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | double | 是 | x轴坐标，单位为vp。 |
| y | double | 是 | y轴坐标，单位为vp。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [VisibleListContentInfo](arkts-na-list-visiblelistcontentinfo-i.md) | 入参坐标处的子组件的索引信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100004](../../apis-arkui/errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Controller not bound to a component. |

## scrollToItemInGroup

```TypeScript
scrollToItemInGroup(index: int, indexInGroup: int, smooth?: boolean, align?: ScrollAlign): void
```

滑动到指定的ListItemGroup中指定的ListItem。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ListScroller-scrollToItemInGroup(index: int, indexInGroup: int, smooth?: boolean, align?: ScrollAlign): void--><!--Device-ListScroller-scrollToItemInGroup(index: int, indexInGroup: int, smooth?: boolean, align?: ScrollAlign): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 要滑动到的目标元素所在的ListItemGroup在当前容器中的索引值。 <br/>**说明：** <br/>index值设置成负值或者大于当前容器子组件的最大索引值，视 为异常值，本次跳转不生效。 <br>取值限定为整数。 <br> &lt;em&gt;注意&lt;/em&gt; <br>如果设置的值为负值或大于容器中项目的最大索引，则 则认为值异常，不进行滚动。 |
| indexInGroup | int | 是 | 要滑动到的目标元素所在的ListItemGroup在当前容器中的索引值。 <br/>**说明：** <br/>index值设置成负值或者大于当前容器子组件的最大索引值，视 为异常值，本次跳转不生效。 <br>取值限定为整数。 <br> &lt;em&gt;注意&lt;/em&gt; <br>如果设置的值为负值或大于容器中项目的最大索引，则 则认为值异常，不进行滚动。 |
| smooth | boolean | 否 | 设置该次滑动是否有动效，true表示有动效，false表示没有动效。<br/>。 <br>默认值：false<br/>**说明：** <br/>开启动效时，会对经过的所有item 进行加载和布局计算，当大量加载item时会导致性能问题。 |
| align | [ScrollAlign](../../apis-arkui/arkts-components/arkts-arkui-scrollalign-e.md) | 否 | 指定滑动到的元素与当前容器的对齐方式。<br/>。 <br>默认值：&lt;em&gt;ScrollAlign.START&lt;/em&gt;。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100004](../../apis-arkui/errorcode-router.md#100004-命名路由页面跳转时输入的name错误) | Controller not bound to a component. |

