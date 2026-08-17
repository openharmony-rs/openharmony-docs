# list

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ExtendableList](arkts-na-list-extendablelist-c.md) | 定义可扩展List组件。 |
| [ListScroller](arkts-na-list-listscroller-c.md) | List组件的滚动控制器，通过它控制List组件的滚动，仅支持一对一绑定到List组件。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CloseSwipeActionOptions](arkts-na-list-closeswipeactionoptions-i.md) | 定义收起滑动操作选项。 |
| [ListBackPressBehavior](arkts-na-list-listbackpressbehavior-i.md) | 定义List组件的系统返回键行为。 |
| [ListDividerOptions](arkts-na-list-listdivideroptions-i.md) | 定义List或ListItemGroup组件的分割线样式。 |
| [ListOptions](arkts-na-list-listoptions-i.md) | 定义List组件参数。 &lt;p&gt;&lt;strong&gt;说明&lt;/strong&gt;: <br>- List组件通用属性clip的默认值为true。 &lt;/p&gt; |
| [UIListEvent](arkts-na-list-uilistevent-i.md) | frameNode中getEvent('List')方法的返回值，可用于给List 节点设置滚动事件。 UIListEvent继承于UIScrollableCommonEvent。 |
| [VisibleListContentInfo](arkts-na-list-visiblelistcontentinfo-i.md) | 定义List可见内容区子组件的详细信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ChainAnimationOptions](arkts-na-list-chainanimationoptions-i-sys.md) | 定义链式联动动效选项。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ListItemAlign](arkts-na-list-listitemalign-e.md) | 设置子组件在List交叉轴方向的对齐方式。 |
| [ListItemGroupArea](arkts-na-list-listitemgrouparea-e.md) | 枚举了ListItemGroup各个区域。 |
| [ScrollSnapAlign](arkts-na-list-scrollsnapalign-e.md) | 设置列表项滚动结束对齐效果。 |
| [ScrollSnapAnimationSpeed](arkts-na-list-scrollsnapanimationspeed-e.md) | 设置列表项滚动限位动画速度。 |
| [ScrollState](arkts-na-list-scrollstate-e.md) | 滑动状态枚举。 |
| [StickyStyle](arkts-na-list-stickystyle-e.md) | ListItemGroup吸顶或吸底效果枚举。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ChainEdgeEffect](arkts-na-list-chainedgeeffect-e-sys.md) | 链式动效边缘效果枚举。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnListScrollIndexCallback](arkts-na-onlistscrollindexcallback-t.md) | List组件可见区域item变化事件的回调类型。 |
| [OnScrollVisibleContentChangeCallback](arkts-na-onscrollvisiblecontentchangecallback-t.md) | 有子组件划入或划出List显示区域时触发。 List从有子组件变成空的List时，上报的start和end参数会保留上次有子组件时的值。 start和end的index同时返回0，代表List内只有一个子组件。 |

