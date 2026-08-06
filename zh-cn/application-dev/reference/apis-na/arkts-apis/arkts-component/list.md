# component/list

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ExtendableList](list-extendablelist-c.md) | 定义可扩展List组件。 |
| [ListScroller](list-listscroller-c.md) | List组件的滚动控制器，通过它控制List组件的滚动，仅支持一对一绑定到List组件。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CloseSwipeActionOptions](list-closeswipeactionoptions-i.md) | 定义收起滑动操作选项。 |
| [ListBackPressBehavior](list-listbackpressbehavior-i.md) | 定义List组件的系统返回键行为。 |
| [ListDividerOptions](list-listdivideroptions-i.md) | 定义List或ListItemGroup组件的分割线样式。 |
| [ListOptions](list-listoptions-i.md) | 定义List组件参数。 \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_说明\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_: \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_- List组件通用属性clip的默认值为true。 \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_4\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ |
| [UIListEvent](list-uilistevent-i.md) | frameNode中\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_方法的返回值，可用于给List 节点设置滚动事件。 UIListEvent继承于[UIScrollableCommonEvent]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| [VisibleListContentInfo](list-visiblelistcontentinfo-i.md) | 定义List可见内容区子组件的详细信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ChainAnimationOptions](list-chainanimationoptions-i-sys.md) | 定义链式联动动效选项。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ListItemAlign](list-listitemalign-e.md) | 设置子组件在List交叉轴方向的对齐方式。 |
| [ListItemGroupArea](list-listitemgrouparea-e.md) | 枚举了ListItemGroup各个区域。 |
| [ScrollSnapAlign](list-scrollsnapalign-e.md) | 设置列表项滚动结束对齐效果。 |
| [ScrollSnapAnimationSpeed](list-scrollsnapanimationspeed-e.md) | 设置列表项滚动限位动画速度。 |
| [ScrollState](list-scrollstate-e.md) | 滑动状态枚举。 |
| [StickyStyle](list-stickystyle-e.md) | ListItemGroup吸顶或吸底效果枚举。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ChainEdgeEffect](list-chainedgeeffect-e-sys.md) | 链式动效边缘效果枚举。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnListScrollIndexCallback](arkts-na-onlistscrollindexcallback-t.md) | List组件可见区域item变化事件的回调类型。 |
| [OnScrollVisibleContentChangeCallback](arkts-na-onscrollvisiblecontentchangecallback-t.md) | 有子组件划入或划出List显示区域时触发。 List从有子组件变成空的List时，上报的start和end参数会保留上次有子组件时的值。 start和end的index同时返回0，代表List内只有一个子组件。 |

