# repeat

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [RepeatAttribute](arkts-arkui-repeat-repeatattribute-c.md) | 除支持[拖拽排序](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)属性外，还支持以下属性。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [RepeatItem](arkts-arkui-repeat-repeatitem-i.md) | 数据项类型。 |
| [TemplateOptions](arkts-arkui-repeat-templateoptions-i.md) | 当cachedCount值被设置为当前template在容器组件显示区域的最大节点数量时，Repeat会做到最大程度的复用。当容器组件显示区域内没有当前template的节点时，缓存列表不会释放，同时应用内存增大。开发者需要根据具体情况自行把控，推荐cachedCount值设置为容器组件显示区域内节点个数。需要注意，不建议设置cachedCount小于2，这会导致在快速滑动场景下频繁创建新的节点，从而造成性能劣化。 |
| [VirtualScrollOptions](arkts-arkui-repeat-virtualscrolloptions-i.md) | 配置懒加载模式下期望加载的数据项总数、复用能力、数据精准懒加载能力。从API版本26.0.0开始，支持配置内存优化策略。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [RepeatMemOptStrategy](arkts-arkui-repeat-repeatmemoptstrategy-e.md) | Repeat内存优化策略枚举。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [RepeatArray](arkts-arkui-repeatarray-t.md) | Repeat数据源参数联合类型。 |
| [RepeatInterface](arkts-arkui-repeatinterface-t.md) | Indicates the type of Repeat. |
| [RepeatItemBuilder](arkts-arkui-repeatitembuilder-t.md) | 组件生成函数类型。 |
| [TemplateTypedFunc](arkts-arkui-templatetypedfunc-t.md) | 渲染模版类型字符串获取函数类型。 |

### 常量

| 名称 | 说明 |
| --- | --- |
| [Repeat](arkts-arkui-repeat-con.md#repeat) | Defines Repeat Component. |

