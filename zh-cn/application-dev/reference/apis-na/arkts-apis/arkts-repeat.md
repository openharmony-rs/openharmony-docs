# repeat

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [Repeat](arkts-na-repeat-repeat-f.md#Repeat) | 定义Repeat组件。需要在组件属性设置开始时调用setRepeatOptions，并在组件属性设置结束时调用applyAttributeFinish。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [RepeatItem](arkts-na-repeat-repeatitem-i.md) | 数据项类型。 |
| [TemplateOptions](arkts-na-repeat-templateoptions-i.md) | 当cachedCount值被设置为当前template在屏上显示的最大节点数量时，Repeat会做到最大程度的复用。然而当屏上没有当前template的节点时，缓存池不会释放的同时应用内存增大。需要开发者根据具体情况自行把控。 - 当cachedCount缺省时，框架会分别对不同template，根据屏上节点+预加载节点的个数之和来计算cachedCount。当屏上节点+预加载节点的个数之和增多时，cachedCount也会对应增长。需要注意 cachedCount数量不会减少。 - 显式指定cachedCount，推荐设置成和屏幕上节点个数一致。需要注意，设置cachedCount小于2会导致在快速滑动场景下创建新的节点，可能造成性能劣化。 > **注意：** > > 滚动容器组件属性`.cachedCount()`和Repeat组件属性`.template()`的参数`cachedCount`都是为了平衡性能和内存，但是含义是不同的。 > > - 滚动容器组件`.cachedCount()`：是指在可见范围外预加载的节点，这些节点会位于组件树上，但不是可见范围内。List/Grid等容器组件会额外渲染这些可见范围外的节点，从而达到其性能收益。Repeat会将这些节点视为 > “可见”的。 > > - `.template()`中的`cachedCount`: 是指Repeat视其为“不可见”的节点，这些空闲的节点框架会暂时保存，在需要使用时进行更新，从而实现复用。 |
| [VirtualScrollOptions](arkts-na-repeat-virtualscrolloptions-i.md) | 配置懒加载模式下期望加载的数据项总数、复用能力、数据精准懒加载能力。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [RepeatMemOptStrategy](arkts-na-repeat-repeatmemoptstrategy-e.md) | 定义内存优化策略的类型。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [KeyGeneratorFunc](arkts-na-keygeneratorfunc-t.md) | 键值生成函数类型。 |
| [OnLazyLoadingFunc](arkts-na-onlazyloadingfunc-t.md) | 懒加载函数类型。 |
| [OnTotalCountFunc](arkts-na-ontotalcountfunc-t.md) | 用于计算期望加载的数据项总数的函数类型。 |
| [RepeatArray](arkts-na-repeatarray-t.md) | Repeat数据源参数联合类型。 |
| [RepeatItemBuilder](arkts-na-repeatitembuilder-t.md) | 组件生成函数类型。 |
| [TemplateTypedFunc](arkts-na-templatetypedfunc-t.md) | 渲染模版类型字符串获取函数类型。 |

