# List属性/事件

除支持通用属性和[滚动组件通用属性](arkts-arkui-scrollablecommonmethod-c.md)外，还 支持以下属性：除支持通用事件和滚动组件通用事件外，还 支持以下事件：

**继承/实现关系：** ListAttribute extends ScrollableCommonMethod<ListAttribute>

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## alignListItem

```TypeScript
alignListItem(value: ListItemAlign)
```

设置List交叉轴方向宽度大于ListItem交叉轴宽度 * lanes + (lanes - 1) * gutter时，ListItem在List交叉轴方向的布局方式。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ListItemAlign](arkts-arkui-listitemalign-e.md) | 是 | 交叉轴方向的布局方式。默认值：ListItemAlign.Start |

## backPressBehavior

```TypeScript
backPressBehavior(behavior: ListBackPressBehavior | undefined)
```

设置List组件的系统返回键行为。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| behavior | [ListBackPressBehavior](arkts-arkui-listbackpressbehavior-i.md) \| undefined | 是 | List组件的系统返回键行为选项。当前支持通过 [ListBackPressBehavior](arkts-arkui-listbackpressbehavior-i.md)参数，配置系统返回键生效时，是否收起已展开的ListItem的划出组件。设置为undefined时，恢复默认 行为，即系统返回键生效时，收起已展开的ListItem的划出组件。 |

## cachedCount

```TypeScript
cachedCount(value: number)
```

设置列表中ListItem/ListItemGroup的预加载数量，懒加载场景只会预加载List显示区域外上下各cachedCount行的ListItem，非懒加载场景会全部加载。懒加载、非懒加载都只布局List显示区域+List 显示区域外cachedCount的内容。<!--Del-->具体使用可参考 [减少应用白块说明](../../../performance/arkts-performance-improvement-recommendation.md#减少应用滑动白块)。<!--DelEnd-->List设置cachedCount后，显示区域外上下各会预加载并布局cachedCount行ListItem。计算ListItem行数时，会计算ListItemGroup内部的ListItem行数。如果ListItemGroup内 没有ListItem，则整个ListItemGroup算一行。List下嵌套使用LazyForEach，并且LazyForEach下嵌套使用ListItemGroup时，LazyForEach会在List显示区域外上下各创建cachedCount个ListItemGroup。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | ListItem/ListItemGroup的预加载数量。默认值：根据屏幕内显示的节点个数设置，最大值为16。取值范围： 0, +∞)，设置为小于0的值时，按1处理。 |

## cachedCount

```TypeScript
cachedCount(count: number, show: boolean)
```

设置列表的预加载行数，并配置是否显示预加载节点。懒加载场景才会预加载List显示区域外上下各cachedCount行，非懒加载场景会全量加载。List设置cachedCount后，显示区域外上下各会预加载并布局cachedCount行。计算预加载行数时，会计算ListItemGroup内部的ListItem行数。如果ListItemGroup内没有ListItem，则整 个ListItemGroup算一行。配合裁剪[clip或内容裁剪 [clipContent](arkts-arkui-scrollablecommonmethod-c.md#clipcontent)属性可以显示出预加载节点。

> **说明：**
> 
> 通常建议设置cachedCount=n/2（n代表一屏显示的列表项数量），同时需考虑其他因素以实现体验和内存使用的平衡。最佳实践请参考
> [优化长列表加载慢丢帧问题-缓存列表项](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-best-practices-number-list#section11667144010222)

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本14开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| count | number | 是 | 列表的预加载行数。默认值：根据屏幕内显示的节点个数设置，最大值为16。 取值范围：0, +∞)，设置为小于0的值时，按1处理。 |
| show | boolean | 是 | 被预加载的ListItem/ListItemGroup是否需要显示。设置为true时显示预加载的ListItem/ListItemGroup，设置为false时不显示预加载的 ListItem/ListItemGroup。 默认值：false |

## cachedCount

```TypeScript
cachedCount(count: number | CacheCountInfo, show: boolean)
```

设置列表的预加载行数，并配置是否显示预加载节点。懒加载场景才会根据count或CacheCountInfo在List显示区域外预加载，非懒加载场景会全量加载。若cachedCount属性的第一个参数为number类型，在帧间空闲时隙会在显示区域外上下各预加载并布局count行。若cachedCount属性的第一个参数为CacheCountInfo类型，当已缓存行数小于CacheCountInfo.minCount时，会在帧间空闲时隙预加载和布局。当已缓存行数大于 CacheCountInfo.maxCount时，会将超出范围的节点销毁或回收复用。UI空闲时（无动画或用户操作），会在显示区域外上下各预加载CacheCountInfo.maxCount行。计算预加载行数时，会计算ListItemGroup内部的ListItem行数。如果ListItemGroup内没有ListItem，则整个ListItemGroup算一行。配合 [clip或 [clipContent](arkts-arkui-scrollablecommonmethod-c.md#clipcontent)属性可以显示出预加载节点。默认行为：count参数默认为number类型，数值根据屏幕内显示的节点个数设置，最大值为16。预加载的ListItem默认不参与绘制。

> **说明：**
> 
> 通常建议设置cachedCount=n/2（n代表一屏显示的列表项数量），同时需考虑其他因素以实现体验和内存使用的平衡。从API version 22开始，支持设置最大最小缓存数，可以将最大缓存数设置稍大，如设置为最小缓存数的
> 两倍，利用UI线程空闲时间创建节点，减少滚动过程中预加载创建节点，提升滚动流畅性。最佳实践请参考
> [优化长列表加载慢丢帧问题-缓存列表项](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-best-practices-number-list#section11667144010222)

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| count | number \| [CacheCountInfo](../arkts-apis/arkts-arkui-cachecountinfo-i.md) | 是 | 当参数类型为number时，表示列表的预加载行数。 取值范围：[0, +∞)，设置为小于0的值时，按1处理。 当参数类型为CacheCountInfo时，表示预加载的最大最小范围。 |
| show | boolean | 是 | 被预加载的ListItem/ListItemGroup是否需要显示。true：显示预加载的ListItem/ListItemGroup。false：不显示预加 载的ListItem/ListItemGroup。 |

## chainAnimation

```TypeScript
chainAnimation(value: boolean)
```

设置当前List是否启用链式联动动效。

> **说明：**
> 
> - 链式联动效果是指在手指划动过程中，手指拖动的ListItem是主动对象，相邻的ListItem为从动对象，主动对象驱动从动对象联动，驱动效果遵循弹簧物理动效。
> 
> - 链式动效的驱动效果体现在ListItem之间的间距上。静止状态下的间距可以通过List组件space参数设置，如果不设置space参数并且启用了链式动效，该间距默认为20vp。
> 
> - 链式动效启用后，List的分割线不显示。
> 
> - 链式动效生效的前提是List处于单列模式并且边缘效果为EdgeEffect.Spring类型。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否启用链式联动动效。默认值：false，不启用链式联动。true，启用链式联动。 |

## childrenMainSize

```TypeScript
childrenMainSize(value: ChildrenMainSize)
```

设置List组件的子组件在主轴方向的大小信息。

> **说明：**
> 
> - 该属性通过向List组件提供所有子组件在主轴方向的大小信息，确保在面对子组件主轴大小不一致、增删子组件、使用[scrollToIndex](arkts-arkui-scroller-c.md#scrolltoindex)等场景时，List组件能
> 够维护其滑动位置准确性。这样，scrollTo可以准确地跳转到指定位置，currentOffset可以获取到
> 当前准确的滑动位置，内置滚动条可以实现平滑移动无跳变。
> 
> - 当子组件是ListItemGroup时，需要根据ListItemGroup的列数、ListItemGroup中ListItem在主轴方向的间距以及ListItemGroup中header、footer和ListItem的大
> 小，来准确计算出ListItemGroup在主轴方向的整体大小，并传递给List组件。
> 
> - 如果子组件有ListItemGroup，必须为每一个ListItemGroup设置childrenMainSize属性。
> List组件和每一个ListItemGroup组件都要通过childrenMainSize属性接口一对一绑定一个ChildrenMainSize对象。
> 
> - 多列场景使用LazyForEach生成子组件时，需确保LazyForEach全部生成ListItemGroup组件或者全部生成ListItem组件。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ChildrenMainSize](arkts-arkui-childrenmainsize-c.md) | 是 | 该对象用来维护子组件在主轴方向的大小信息。 |

## contentEndOffset

```TypeScript
contentEndOffset(value: number)
```

设置内容区末尾偏移量。列表滚动到末尾位置时，列表内容与列表显示区域边界保留指定距离。contentStartOffset + contentEndOffset超过List内容区长度后contentStartOffset和contentEndOffset会置0。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 内容区末尾偏移量。默认值：0单位：vp    **说明：**设置为负数时，按默认值处理。取值范围：[0, +∞) |

## contentEndOffset

```TypeScript
contentEndOffset(offset: number | Resource)
```

设置内容区末尾偏移量。列表滚动到末尾位置时，列表内容与列表显示区域边界保留指定距离。与 [contentEndOffset&lt;sup&gt;11+&lt;/sup&gt;](#contentendoffset)相比，参数名改为offset，并开始支持Resource类 型。contentStartOffset + contentEndOffset超过List内容区长度后contentStartOffset和contentEndOffset会置0。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number \| Resource | 是 | 内容区末尾偏移量。默认值：0参数类型为number时单位为vp。 设置异常值如负数、非数字Resource时，按默认值处理。 参数类型为number时取值范围：[0, +∞) |

## contentStartOffset

```TypeScript
contentStartOffset(value: number)
```

设置内容区域起始偏移量。列表滚动到起始位置时，列表内容与列表显示区域边界保留指定距离。contentStartOffset + contentEndOffset超过List内容区长度后contentStartOffset和contentEndOffset会置0。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 内容区域起始偏移量。默认值：0单位：vp    **说明：**设置为负数时，按默认值处理。取值范围：[0, +∞) |

## contentStartOffset

```TypeScript
contentStartOffset(offset: number | Resource)
```

设置内容区域起始偏移量。列表滚动到起始位置时，列表内容与列表显示区域边界保留指定距离。与 [contentStartOffset&lt;sup&gt;11+&lt;/sup&gt;](#contentstartoffset)相比，参数名改为offset，并开始支持 Resource类型。contentStartOffset + contentEndOffset超过List内容区长度后contentStartOffset和contentEndOffset会置0。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number \| Resource | 是 | 内容区域起始偏移量。默认值：0参数类型为number时单位为vp。 设置异常值如负数、非数字Resource时，按默认值处 理。参数类型为number时取值范围：0, +∞) |

## divider

```TypeScript
divider(
    value: ListDividerOptions | null,
  )
```

设置ListItem分割线样式，默认无分割线。List的分割线画在主轴方向两个子组件之间，第一个子组件上方和最后一个子组件下方不会绘制分割线。多列模式下，ListItem与ListItem之间的分割线起始边距从每一列的交叉轴方向起始边开始计算，单列模式从List交叉轴方向起始边开始计算。ListItem设置[多态样式时，被按压的子组件上下的分割线不绘制。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ListDividerOptions](arkts-arkui-listdivideroptions-i.md) \| null | 是 | ListItem分割线样式。默认值：null<br>**起始版本：** 18 |

## edgeEffect

```TypeScript
edgeEffect(value: EdgeEffect, options?: EdgeEffectOptions)
```

设置边缘滑动效果。

> **说明：**
> 
> 当List组件的内容区小于一屏时，默认没有回弹效果。若要启用回弹效果，设置edgeEffect属性的options参数为{ alwaysEnabled: true }即可。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [EdgeEffect](../arkts-apis/arkts-arkui-edgeeffect-e.md) | 是 | List组件的边缘滑动效果，支持弹簧效果和阴影效果。默认值：EdgeEffect.Spring |
| options | [EdgeEffectOptions](arkts-arkui-edgeeffectoptions-i.md) | 否 | 组件内容大小小于组件自身时，是否开启滑动效果。设置为{ alwaysEnabled: true }会开启滑动效果，{ alwaysEnabled: false }不开启。默认值：{ alwaysEnabled: false }<br>**起始版本：** 11 |

## editMode

```TypeScript
editMode(value: boolean)
```

设置当前List组件是否处于可编辑模式。

> **说明：**
> 
> 从API version 7开始支持，从API version 9开始废弃。此接口已完全移除，无替代接口。如需实现编辑状态切换和删除列表项，可通过自定义状态变量控制删除按钮的显示与隐藏，并在删除按钮的点击事件中更新数据源，具体
> 实现方式请参考示例3。

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 当前List组件是否处于可编辑模式。true表示当前List组件处于可编辑模式，false表示当前List组件不处于可编辑模式。默认值：false |

## editModeOptions

```TypeScript
editModeOptions(options?: EditModeOptions)
```

配置List组件编辑模式的行为选项，包括多选聚拢动画开关、预览徽标获取、默认多选样式等。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [EditModeOptions](arkts-arkui-editmodeoptions-i.md) | 否 | 编辑模式选项，用于自定义List编辑模式的特性行为。当需要自定义编辑模式行为时传入此参数，不传入时使用默认配置。 |

## enableEditMode

```TypeScript
enableEditMode(enabled: boolean | undefined)
```

设置List是否启用编辑模式，启用编辑模式后可以在List组件内滑动多选ListItem。未通过该接口设置时，不启用编辑模式。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean \| undefined | 是 | 是否启用编辑模式，该参数支持[!!](../../../ui/state-management/arkts-new-binding.md)双向绑定 变量。设置为true时启用编辑模式，可以滑动多选；设置为false或undefined时关闭编辑模式，不可滑动多选。 |

## enableScrollInteraction

```TypeScript
enableScrollInteraction(value: boolean)
```

设置是否支持滚动手势。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否支持滚动手势。设置为true时可以通过手指或者鼠标滚动，设置为false时无法通过手指或者鼠标滚动，但不影响控制器[Scroller](arkts-arkui-scroller-c.md)的滚动 接口。默认值：true |

## focusWrapMode

```TypeScript
focusWrapMode(mode: Optional<FocusWrapMode>)
```

设置方向键走焦模式。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [Optional](arkts-arkui-optional-t.md)&lt;[FocusWrapMode](../arkts-apis/arkts-arkui-focuswrapmode-e.md)&gt; | 是 | 交叉轴方向键走焦模式。默认值：FocusWrapMode.DEFAULT   **说明：** 异常值按默认值处理，即交叉轴 方向键不能换行。 |

## friction

```TypeScript
friction(value: number | Resource)
```

设置摩擦系数，手动划动滚动区域时生效，仅影响惯性滚动过程。设置为小于等于0的值时，按默认值处理。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| Resource | 是 | 摩擦系数。默认值：非Wearable设备为0.6，Wearable设备为0.9。从API version 11开始，非Wearable设 备默认值为0.7。从API version 12开始，非Wearable设备默认值为0.75。取值范围：(0, +∞) |

## lanes

```TypeScript
lanes(value: number | LengthConstrain, gutter?: Dimension)
```

设置List组件的布局列数或行数（List垂直滚动时表示列数，水平滚动时表示行数）。以列数作为示例，介绍设置规则如下：  
- value为number类型时，根据number类型数值指定列数。  
- value为LengthConstrain类型时，LengthConstrain中的minLength表示最小列宽，List组件会根据自身宽度在满足最小列宽情况下计算最大列数。同时，LengthConstrain会作为最大最小  
布局宽度约束传递给List的子组件，子组件没有设置宽度时会生效该最大最小布局约束。  
- &nbsp;ListItemGroup在多列模式下也是独占一行，ListItemGroup中的ListItem按照List组件的lanes属性设置值来布局。  
- value为LengthConstrain类型时，计算ListItemGroup中的列数时会按照ListItemGroup的自身宽度计算。因此ListItemGroup宽度与List宽度不一致时，ListItemGroup中的  
列数与List中的列数可能不一样。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| LengthConstrain | 是 | List组件的布局列数或行数。默认值：1 取值范围：[1, +∞)，传入小于1的值时按默认值处理。 |
| gutter | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | 否 | 列间距或行间距。默认值：0参数类型为number时单位为vp。取值范围： [0, +∞)，传入负值时按默认值处理。   **说明：**gutter为列间距或行间距，当列数或行数大于1时生效。<br>**起始版本：** 10 |

## lanes

```TypeScript
lanes(value: number | LengthConstrain | ItemFillPolicy, gutter?: Dimension)
```

设置List组件交叉轴方向的布局数量和间距。List垂直滚动时，设置列数和列间距；List水平滚动时，设置行数和行间距。默认按一列或一行显示。在多列或多行模式下，ListItemGroup在垂直滚动时独占一行，在水平滚动时独占一 列；ListItemGroup中的ListItem按照List组件的lanes属性设置值来布局。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| LengthConstrain \| [ItemFillPolicy](../arkts-apis/arkts-arkui-itemfillpolicy-i.md) | 是 | 当前List组件交叉轴方向的布局数量。List垂直滚动时表示列数，水平滚动时表示行数。设置为 number类型时，根据number类型的数值确定列数或行数，number类型取值范围： [1, +∞)，传入小于1的值时按默认值处理。设置为LengthConstrain类型时，垂直滚动时根据列宽的最大值和最小值确定列数，水平滚动时根据行高的最大值和最小值确定行数。设置为ItemFillPolicy类型时，根据List组件宽度对应[断点类型](../../../ui/arkts-layout-development-grid-layout.md#栅格容器断点)确定列数，该类型只在List滚动方向为垂直方向时才生效。 |
| gutter | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | 否 | List垂直滚动时表示列间距，水平滚动时表示行间距。默认值：0参数类型为number时单位为vp。取值范围： [0, +∞)，传入负值时按默认值处理。   **说明：**当列数或行数大于1时生效。 |

## listDirection

```TypeScript
listDirection(value: Axis)
```

设置List组件排列方向。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Axis | 是 | 组件的排列方向。默认值：Axis.Vertical |

## maintainVisibleContentPosition

```TypeScript
maintainVisibleContentPosition(enabled: boolean)
```

设置显示区域上方插入或删除数据时是否要保持可见内容位置不变。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 设置显示区域上方插入或删除数据时是否要保持可见内容位置不变。默认值：false，显示区域上方插入或删除数据时可见内容位置会跟随变化。 true：显示区域上方插入或 删除数据时可见内容位置不变。 |

## multiSelectable

```TypeScript
multiSelectable(value: boolean)
```

设置是否开启鼠标框选。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否开启鼠标框选。默认值：false，关闭框选。true，开启框选。 |

## nestedScroll

```TypeScript
nestedScroll(value: NestedScrollOptions)
```

设置前后两个方向的嵌套滚动模式，实现与父组件的滚动联动。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [NestedScrollOptions](arkts-arkui-nestedscrolloptions-i.md) | 是 | 嵌套滚动选项。默认值：{ scrollForward: NestedScrollMode.SELF_ONLY, scrollBackward: NestedScrollMode.SELF_ONLY } |

## onEditModeChange

```TypeScript
onEditModeChange(callback: Callback<boolean> | undefined)
```

编辑模式状态变化时触发该回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback & lt;boolean & gt; \ | undefined | 是 | 编辑模式状态变化时触发的回调。 true表示进入编辑模式，false表示退出编辑模式。 传入undefined时取消回调。 |

## onItemDelete

```TypeScript
onItemDelete(event: (index: number) => boolean)
```

当List组件在编辑模式时，点击ListItem右边出现的删除按钮时触发。

> **说明：**
> 
> 从API version 7开始支持，从API version 9开始废弃。此接口已完全移除，无替代接口。如需实现删除列表项，可在自定义删除按钮的点击事件中更新数据源，具体实现方式请参考
> 示例3。

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (index: number) = & gt; boolean | 是 |  |

## onItemDragEnter

```TypeScript
onItemDragEnter(event: (event: ItemDragInfo) => void)
```

拖拽List的子组件ListItem进入列表范围内时触发。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: ItemDragInfo) = & gt; void | 是 | 拖拽点的信息。 |

## onItemDragLeave

```TypeScript
onItemDragLeave(event: (event: ItemDragInfo, itemIndex: number) => void)
```

拖拽List的子组件ListItem离开列表范围时触发。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: ItemDragInfo, itemIndex: number) = & gt; void | 是 |  |

## onItemDragMove

```TypeScript
onItemDragMove(event: (event: ItemDragInfo, itemIndex: number, insertIndex: number) => void)
```

拖拽List的子组件ListItem在列表范围内移动时触发。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: ItemDragInfo, itemIndex: number, insertIndex: number) = & gt; void | 是 |  |

## onItemDragStart

```TypeScript
onItemDragStart(event: OnItemDragStartCallback)
```

开始拖拽List的子组件ListItem时触发。不支持拖动到List边缘时触发List的自动滚动，可以使用ForEach、LazyForEach、Repeat的 [onMove](arkts-arkui-dynamicnode-c.md#onmove)接口实现该效果，参考 示例12（使用onMove进行拖拽）。但需注意 [onMove](arkts-arkui-dynamicnode-c.md#onmove)接口不支持跨ListItemGroup 拖拽。

> **说明：**
> 
> 从API version 14开始，该接口支持在attributeModifier中调用。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [OnItemDragStartCallback](arkts-arkui-onitemdragstartcallback-t.md) | 是 | List的子组件ListItem拖拽开始时触发的回调。 API version 22及之前版本，该参数类型为(event: ItemDragInfo, itemIndex: number) = & gt; (() = & gt; any) \ | void，其中event和itemIndex 参数含义参考[OnItemDragStartCallback](arkts-arkui-onitemdragstartcallback-t.md)。<br>**起始版本：** 23 |

## onItemDrop

```TypeScript
onItemDrop(event: (event: ItemDragInfo, itemIndex: number, insertIndex: number, isSuccess: boolean) => void)
```

绑定该事件的列表可作为拖拽释放目标，当在列表范围内停止拖拽时触发。跨List拖拽时，当拖拽释放的位置绑定了onItemDrop时isSuccess为true，否则为false。List内部拖拽时，isSuccess为onItemMove事件的返回值。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: ItemDragInfo, itemIndex: number, insertIndex: number, isSuccess: boolean) = & gt; void | 是 | 拖拽点的信息。 |

## onItemMove

```TypeScript
onItemMove(event: (from: number, to: number) => boolean)
```

List的子组件ListItem发生移动时触发。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (from: number, to: number) = & gt; boolean | 是 |  |

## onReachEnd

```TypeScript
onReachEnd(event: () => void)
```

列表到达末尾位置时触发事件。当最后一个子组件因滚动或内容/布局变化出现在列表视窗中时，触发此回调。当子组件未撑满列表，无须滚动即可直接在列表内完整展示时，首次加载也会触发此事件。List边缘效果为弹簧效果时，划动经过末尾位置时触发一次，回弹回末尾位置时再触发一次。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () = & gt; void | 是 | 列表到达末尾位置时触发的回调。 |

## onReachStart

```TypeScript
onReachStart(event: () => void)
```

列表到达起始位置时触发。List初始化时如果initialIndex为0会触发一次，List滚动到起始位置时触发一次。List边缘效果为弹簧效果时，划动经过起始位置时触发一次，回弹回起始位置时再触发一次。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () = & gt; void | 是 | 列表到达起始位置时触发的回调。 |

## onScroll

```TypeScript
onScroll(event: (scrollOffset: number, scrollState: ScrollState) => void)
```

列表滑动时触发。

> **说明：**
> 
> 从API version 7开始支持，从API version 12开始废弃，建议使用
> onDidScroll替代。

**起始版本：** 7

**废弃版本：** 12

**替代接口：** onDidScroll

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (scrollOffset: number, scrollState: ScrollState) = & gt; void | 是 | Callback when scroll, scrollOffset: 相对于上一帧的偏移量，List的内容向上滚动时偏移量为正，向下滚动时偏移量为负。单位vp。 scrollState: 当前滑动状态。 |

## onScrollFrameBegin

```TypeScript
onScrollFrameBegin(event: OnScrollFrameBeginCallback)
```

该接口回调时，事件参数传入即将发生的滑动量，事件处理函数中可根据应用场景计算实际需要的滑动量并作为事件处理函数的返回值返回，列表将按照返回值的实际滑动量进行滑动。当listDirection的值为Axis.Vertical时，返回垂直方向滑动量，当listDirection的值为Axis.Horizontal时，返回水平方向滑动量。满足以下任一条件时触发该事件：
1. 用户交互（如手指滑动、键鼠操作等）触发滚动。
2. List惯性滚动。
3. 调用fling接口触发滚动。
不触发该事件的条件：
1. 调用除fling接口外的其他滚动控制接口。
2. 越界回弹。
3. 拖动滚动条。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [OnScrollFrameBeginCallback](arkts-arkui-onscrollframebegincallback-t.md) | 是 | 每帧滚动开始回调函数。<br>**起始版本：** 20 |

## onScrollIndex

```TypeScript
onScrollIndex(event: (start: number, end: number, center: number) => void)
```

有子组件划入或划出List显示区域时触发。计算索引值时，ListItemGroup作为一个整体占一个索引值，不计算ListItemGroup内部ListItem的索引值。

> **说明：**
> 
> 与[onScrollVisibleContentChange](#onscrollvisiblecontentchange)相比，onScrollIndex将ListItemGroup整体
> 计为一个索引值，且回调仅返回首尾及中间索引值。如需获取ListItemGroup内部header、footer或ListItem的详细索引信息，请使用onScrollVisibleContentChange。
> List的边缘效果为弹簧效果时，在List划动到边缘继续划动和松手回弹过程不会触发onScrollIndex事件。
触发该事件的条件：列表初始化时会触发一次，List显示区域内第一个子组件的索引值或最后一个子组件的索引值有变化时会触发。从API version 10开始，List显示区域中间位置子组件变化时也会触发该事件。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (start: number, end: number, center: number) = & gt; void | 是 |  |

## onScrollStart

```TypeScript
onScrollStart(event: () => void)
```

列表滑动开始时触发。手指拖动列表或列表的滚动条触发的滑动开始时，会触发该事件。使用[Scroller](arkts-arkui-scroller-c.md)滑动控制器触发的带动画的滑动，动画开始时会触发该事件。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () = & gt; void | 是 | 列表滑动开始时触发的回调。 |

## onScrollStop

```TypeScript
onScrollStop(event: () => void)
```

列表滑动停止时触发。手指拖动列表或列表的滚动条触发的滑动，手离开屏幕后滑动停止时会触发该事件。使用[Scroller](arkts-arkui-scroller-c.md)滑动控制器触发的带动画的滑动，动画停止会触发该事件。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () = & gt; void | 是 | 列表滑动停止时触发的回调。 |

## onScrollVisibleContentChange

```TypeScript
onScrollVisibleContentChange(handler: OnScrollVisibleContentChangeCallback)
```

有子组件划入或划出List显示区域时触发。计算触发条件时，每一个ListItem、ListItemGroup中的header或footer都算一个子组件。List的边缘效果为弹簧效果时，在List划动到边缘继续划动和松手回弹过程不会触发onScrollVisibleContentChange事件。触发该事件的条件：列表初始化时会触发一次，List显示区域内第一个子组件的索引值或最后一个子组件的索引值有变化时会触发。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [OnScrollVisibleContentChangeCallback](arkts-arkui-onscrollvisiblecontentchangecallback-t.md) | 是 | 当前显示内容发生改变的时候触发回调。 |

## scrollBar

```TypeScript
scrollBar(value: BarState)
```

设置滚动条状态。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [BarState](../arkts-apis/arkts-arkui-barstate-e.md) | 是 | 滚动条状态。默认值：API version 9及以下版本默认值为BarState.Off，API version 10及以上版本的默认值为 BarState.Auto。 |

## scrollSnapAlign

```TypeScript
scrollSnapAlign(value: ScrollSnapAlign)
```

设置列表项滚动结束对齐效果。只支持item等高场景限位，不等高场景可能存在不准确的情况。对齐动画期间 onWillScroll事件上报的滚动操作来源 类型为ScrollSource.FLING。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ScrollSnapAlign](arkts-arkui-scrollsnapalign-e.md) | 是 | 列表项滚动结束对齐效果。默认值：ScrollSnapAlign.NONE |

## scrollSnapAnimationSpeed

```TypeScript
scrollSnapAnimationSpeed(speed: ScrollSnapAnimationSpeed)
```

设置列表项滚动限位动画速度。只在列表设置了滚动结束对齐效果后才生效。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| speed | [ScrollSnapAnimationSpeed](arkts-arkui-scrollsnapanimationspeed-e.md) | 是 | 列表滚动限位动画速度。默认值：ScrollSnapAnimationSpeed.NORMAL |

## stackFromEnd

```TypeScript
stackFromEnd(enabled: boolean)
```

设置List组件是否从末尾开始布局。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 设置List组件是否从末尾开始布局。默认值：false，List从顶部开始布局。 true：List组件从末尾开始布局。 |

## sticky

```TypeScript
sticky(value: StickyStyle)
```

配合ListItemGroup组件使用，设置ListItemGroup中header是否要吸顶或footer是否要吸底。从API version 20开始，sticky属性支持 StickyStyle.BOTH枚举值，可直接设置为StickyStyle.BOTH以同时支持header吸顶和footer吸底，效果与StickyStyle.Header | StickyStyle.Footer相同。API version 20之前，可通过StickyStyle.Header | StickyStyle.Footer达到相同效果。

> **说明：**
> 
> 由于浮点数计算精度，设置sticky后，在List滑动过程中小概率产生缝隙，可以通过[pixelRound](arkts-arkui-commonmethod-c.md#pixelround)指定当前组件向下像素取整解决该问题。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [StickyStyle](arkts-arkui-stickystyle-e.md) | 是 | ListItemGroup吸顶或吸底效果。默认值：StickyStyle.None |

## supportEmptyBranchInLazyLoading

```TypeScript
supportEmptyBranchInLazyLoading(supported: boolean | undefined)
```

设置当前List组件是否支持在LazyForEach或Repeat中使用if/else渲染控制语法生成不包含任何子组件的空分支节点。未设置时不支持空分支节点。此属性初次赋值后不支持更新，所以赋值后无法在支持空分支、不支持空分支行为 之间切换。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| supported | boolean \| undefined | 是 | 当前List组件是否支持在 [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)或 [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)中使用 [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)渲染控制语法生成一个不含任何子组件的空分支节点。true表示支 持空分支节点；false表示不支持空分支节点。值为undefined时，按false处理。 |

## syncLoad

```TypeScript
syncLoad(enable: boolean)
```

设置是否同步加载List区域内所有子组件。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否同步加载List区域内所有子组件。true表示同步加载，false表示异步加载。默认值：true。   **说明：** 设置为false时，在首次 显示、不带动画scrollToIndex跳转场景，若当帧布局耗时超过50ms，会将List区域内尚未布局的子组件延后到下一帧进行布局。 |
