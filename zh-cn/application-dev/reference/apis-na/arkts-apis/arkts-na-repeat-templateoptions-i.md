# TemplateOptions

当cachedCount值被设置为当前template在屏上显示的最大节点数量时，Repeat会做到最大程度的复用。然而当屏上没有当前template的节点时，缓存池不会释放的同时应用内存增大。需要开发者根据具体情况自行把控。 - 当cachedCount缺省时，框架会分别对不同template，根据屏上节点+预加载节点的个数之和来计算cachedCount。当屏上节点+预加载节点的个数之和增多时，cachedCount也会对应增长。需要注意 cachedCount数量不会减少。 - 显式指定cachedCount，推荐设置成和屏幕上节点个数一致。需要注意，设置cachedCount小于2会导致在快速滑动场景下创建新的节点，可能造成性能劣化。 > **注意：** > > 滚动容器组件属性`.cachedCount()`和Repeat组件属性`.template()`的参数`cachedCount`都是为了平衡性能和内存，但是含义是不同的。 > > - 滚动容器组件`.cachedCount()`：是指在可见范围外预加载的节点，这些节点会位于组件树上，但不是可见范围内。List/Grid等容器组件会额外渲染这些可见范围外的节点，从而达到其性能收益。Repeat会将这些节点视为 > “可见”的。 > > - `.template()`中的`cachedCount`: 是指Repeat视其为“不可见”的节点，这些空闲的节点框架会暂时保存，在需要使用时进行更新，从而实现复用。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface TemplateOptions--><!--Device-unnamed-export interface TemplateOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## cachedCount

```TypeScript
cachedCount?: int
```

当前template的缓存池中可缓存子组件节点的最大数量。取值范围是 [0, +∞)。默认值为屏上节点与预加载节点的个数之和。当屏上节点与预加载节点的个数之和增多时，cachedCount也会对应增长。需要注意cachedCount数量不会减少。 取值限定为整数。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TemplateOptions-cachedCount?: int--><!--Device-TemplateOptions-cachedCount?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

