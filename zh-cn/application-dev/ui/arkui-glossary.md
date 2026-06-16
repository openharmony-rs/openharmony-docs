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

## E

### Entity Node；实体节点

由后端创建的Native节点，是前端节点对象在底层的实际载体。前端节点通过引用关系与实体节点绑定，当调用dispose解除绑定后，前端节点不再对应任何实体节点，再次调用接口可能导致crash或返回默认值。

## I

### Imperative Node；命令式节点

通过new FrameNode()等构造函数直接创建的节点。命令式节点可对自身属性及子节点结构进行修改。
### Affine Property；仿射属性

组件的变换类属性（缩放、旋转、平移），基于组件坐标系和锚点进行仿射变换。组件平移后仿射属性的坐标系仍保持固定，与布局类属性（宽、高等）直接改变内容位置的方式不同。变更仿射属性不会触发测量布局，性能开销低于布局属性变更。

### Animatable Property；可动画属性

支持动画插值的组件属性，当属性值发生变化时产生平滑过渡而非直接跳变。布局类可动画属性（宽、高）变化时内容默认以左上对齐方式跳至终值，需配合renderFit属性控制过渡绘制行为。区别于不可动画属性变化时瞬间生效无过渡。

### Appear/Disappear Transition；出现/消失转场

组件插入或移除渲染树（通过if/ForEach/visibility变化触发）时的转场动画类别，可通过TransitionEffect的组合使用定义各式效果。出现转场和消失转场可独立配置为非对称效果（asymmetric）。区别于页面转场（两个路由页面间切换）和共享元素转场（元素位置/尺寸匹配）。

### Asymmetric Transition；非对称转场

组件出现与消失使用两套独立不同动画的转场模式，出现和消失效果不互为逆过程，通过TransitionEffect.asymmetric()配置。区别于对称转场中出现和消失为互逆效果。

### Attribute Animation；属性动画

通过可动画属性值变化引起UI连续视觉效果的动画方式，是ArkUI最基础的动画类别。提供animateTo（闭包驱动）、animation（属性绑定自动检测）、keyframeAnimateTo（多段关键帧）三种接口。区别于组件转场（出现/消失触发）和页面转场（路由切换触发）。

## B

### Background Brightness Enhancement；背景提亮

根据像素亮度值动态提升背景内容亮度的视觉效果，可配置rate（亮度衰减速率）和lightUpDegree（峰值提亮幅度）。计算公式：ΔY = -rate·Y + lightUpDegree。区别于全局亮度调整，背景提亮按像素亮度差异化处理。

## C

### Click Bounce Effect；点击回弹效果

组件被点击时短暂缩小再恢复的视觉反馈效果，提供LIGHT/MIDDLE/HEAVY三个强度等级，各等级有默认缩放比例且可自定义覆盖。区别于一般点击高亮效果仅改变颜色或透明度。

## D

### Detent；挡位

半模态面板的预定义高度停靠点，用户可通过拖拽在挡位间切换，面板自动吸附至各挡位高度。支持最多3个挡位，切换受速度阈值（1000）和距离规则（超过下一挡位50%即切换）控制。区别于通过height属性直接设定的固定高度。

### Depth Blur；景深模糊

按模拟景深距离分级的后台模糊效果，分为近景（BACKGROUND_THIN）、中景（BACKGROUND_REGULAR）、远景（BACKGROUND_THICK）和超远景（BACKGROUND_ULTRA_THICK）四个等级，逐级增强模糊强度以营造视觉层次。区别于前景组件级模糊（COMPONENT_THIN等）。

## E

### Explicit Animation；显式动画

通过调用animateTo并传入闭包函数显式触发状态变化所产生的动画，系统自动对闭包内可动画属性变化插入过渡动画。需要明确的UIContext上下文执行环境。区别于隐式属性动画（animation接口自动检测属性变化触发），显式动画需开发者主动控制动画触发时机和参数。

## G

### Grayscale Blur；灰阶模糊

调整图像黑白灰阶朝灰色方向偏移的模糊参数，使视觉过渡更柔和，不影响彩色内容。配置为[min, max]灰阶范围对，默认值为[0,0]。区别于一般半径模糊仅控制模糊强度。

## K

### Keyframe Animation；关键帧动画

同一属性上定义多个连续关键帧状态的分段动画，每帧可独立控制时长和曲线，适用于同一属性需要做多段连续动画的场景。关键帧动画不支持弹簧曲线。区别于显式动画仅做单次属性过渡，关键帧动画实现多段连续过渡且无需在结束回调中串联新动画。

### Keyframe Animation Parameter (KeyframeAnimateParam)；关键帧动画参数

关键帧动画的整体配置参数对象，包含延时、播放次数、结束回调、期望帧率等，区别于每段关键帧内部的局部参数（时长、曲线、闭包）。

## L

### Long Tail State；长尾状态

弹簧动画逻辑结束后的视觉微振衰减阶段。FinishCallbackType.LOGICALLY回调在此阶段触发，而REMOVED回调在动画完全移除时触发。对于弹簧曲线动画，长尾状态中的视觉运动已微乎其微但仍未完全停止。

## M

### Material Blur；材质模糊

将模糊半径、遮罩颜色、遮罩透明度、饱和度、亮度封装为命名厚度等级（Thin/Regular/Thick及Ultra变体）的预定义模糊样式，模拟物理材质外观。区别于backdropBlur需手动配置模糊半径等参数。

### Motion Path Animation；路径动画

组件位移时沿指定SVG路径行进的动画方式，支持配置起止位置（from/to，取值范围0~1）和路径方向旋转对齐（rotatable）。通过animateTo触发位移变化后组件按定义路径运动。区别于线性位移动画仅做起点到终点的直线路径。

## N

### Named Route；命名路由

通过名称标识而非URL路径进行页面跳转的路由方式，主要用于跨包（HAR或HSP共享包）重定向到包内页面。

## P

### Page Stack；页面栈

Router模块管理的页面跳转栈结构，记录页面进出顺序，最多容纳32个页面。

### Pre-loading Area；预加载区域

懒加载模式下紧邻容器组件显示范围的区域，该区域内的子组件会在系统空闲时提前创建并布局以提升列表滑动性能。
### Page Transition；页面转场

两个路由页面间发生跳转时，通过pageTransition配置PageTransitionEnter和PageTransitionExit定义页面进入和退出的动画效果。路由类型（RouteType.Push/Pop/None）区分push入栈和pop出栈两种入场形式。区别于组件转场（同一页面内组件出现/消失）和共享元素转场（元素跨页面位置匹配）。

## R

### Route Map；路由表

Navigation中定义页面路由名称、源文件路径及自定义字段的配置映射，用于路由跳转时查找目标页面。

### Route Stack；路由栈

Navigation组件中由NavPathStack管理的NavDestination页面进出顺序栈结构，与Router管理的页面栈属不同导航模型。

## S

### System Adaptive Regulation；系统自适应调节

低算力设备上系统自动降低视觉效果品质（如模糊近似化）以保障性能的能力，根据芯片能力和负载条件决定调节幅度。可通过disableSystemAdaptation标记按效果逐项关闭。仅在设备制造商定义的低算力设备上生效。

## T

### Theme Skinning；主题换肤

应用内视觉主题切换机制，可定制应用的全局配色风格和局部配色风格。
