# ArkUI术语
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @mayaolll-->
<!--Designer: @jiangdayuan-->
<!--Tester: @zhangwenhan12-->
<!--Adviser: @Brilliantry_Rui-->

## A

### Accessibility Virtual Node；无障碍虚拟子节点

当开发者使用自绘制组件进行自定义绘制时，这些组件内部的内容（如绘制的图形、文字）通常无法被无障碍服务直接感知。无障碍虚拟子节点是为自绘制组件补充的不可见无障碍节点，用于让辅助应用识别自绘区域内的可感知内容。

### Affine Property；仿射属性

组件的变换类属性（缩放、旋转、平移），基于组件坐标系和锚点进行仿射变换。组件平移后仿射属性的坐标系仍保持固定，与布局类属性（宽、高等）直接改变内容位置的方式不同。变更仿射属性不会触发测量布局，性能开销低于布局属性变更。

### Animatable Property；可动画属性

当属性值在可动画的闭包函数内发生变化时产生平滑的动画过渡而非直接跳变。区别于不可动画属性变化时瞬间生效无过渡。

### Appear/Disappear Transition；出现/消失转场

组件插入或移除渲染树（通过if/ForEach/visibility变化触发）时的转场动画类别，可通过TransitionEffect的组合使用定义各式效果。出现转场和消失转场可独立配置为非对称效果（asymmetric）。区别于页面转场（两个路由页面间切换）和共享元素转场（元素位置/尺寸匹配）。

## E

### Entity Node；实体节点

由后端创建的Native节点，是前端节点对象在底层的实际载体。前端节点通过引用关系与实体节点绑定，当调用dispose解除绑定后，前端节点不再对应任何实体节点，再次调用接口可能导致crash或返回默认值。

### Explicit Animation；显式动画

通过调用animateTo并传入闭包函数显式触发状态变化所产生的动画，系统自动对闭包内可动画属性变化插入过渡动画。需要明确的UIContext上下文执行环境。区别于隐式属性动画（animation接口自动检测属性变化触发），显式动画需开发者主动控制动画触发时机和参数。

## I

### Imperative Node；命令式节点

通过new FrameNode()等构造函数直接创建的节点。命令式节点可对自身属性及子节点结构进行修改。

## K

### Keyframe Animation；关键帧动画

同一属性上定义多个连续关键帧状态的分段动画，每帧可独立控制时长和曲线，适用于同一属性需要做多段连续动画的场景。关键帧动画不支持弹簧曲线。区别于显式动画仅做单次属性过渡，关键帧动画实现多段连续过渡且无需在结束回调中串联新动画。

## L

### Long Tail State；长尾状态

弹簧动画逻辑结束后的视觉微振衰减阶段。FinishCallbackType.LOGICALLY回调在此阶段触发，而REMOVED回调在动画完全移除时触发。对于弹簧曲线动画，长尾状态中的视觉运动已微乎其微但仍未完全停止。

## M

### Motion Path Animation；路径动画

组件位移时沿指定SVG路径行进的动画方式。通过animateTo触发位移变化后组件按定义路径运动。区别于线性位移动画仅做起点到终点的直线路径。

## N

### Named Route；命名路由

通过名称标识而非URL路径进行页面跳转的路由方式，主要用于跨包（HAR或HSP共享包）重定向到包内页面。

## P

### Page Stack；页面栈

Router模块管理的页面跳转栈结构，记录页面进出顺序，最多容纳32个页面。

### Pre-loading Area；预加载区域

懒加载模式下紧邻容器组件显示范围的区域，该区域内的子组件会在系统空闲时提前创建并布局以提升列表滑动性能。

## R

### Route Map；路由表

Navigation中定义页面路由名称、源文件路径及自定义字段的配置映射，用于路由跳转时查找目标页面。

### Route Stack；路由栈

Navigation组件中由NavPathStack管理的NavDestination页面进出顺序栈结构，与Router管理的页面栈属不同导航模型。

## T

### Theme Skinning；主题换肤

应用内视觉主题切换机制，可定制应用的全局配色风格和局部配色风格。

## 组件坐标系

以组件左上角为坐标原点的坐标系，其中向右为x正轴，向下为y正轴。如果为三维坐标系，则由屏幕向外为z正轴。

![coordinates](../reference/apis-arkui/arkui-ts/figures/coordinates.png)