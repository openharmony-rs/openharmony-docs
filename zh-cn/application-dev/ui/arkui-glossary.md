# ArkUI术语
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @huangxiaolinabc-->
<!--Designer: @jiangdayuan-->
<!--Tester: @zhangwenhan12-->
<!--Adviser: @Brilliantry_Rui-->

## A

### Accessibility Virtual Node；无障碍虚拟子节点

当开发者使用自绘制组件进行自定义绘制时，这些组件内部的内容（如绘制的图形、文字）通常无法被无障碍服务直接感知。无障碍虚拟子节点是为自绘制组件补充的不可见无障碍节点，用于让辅助应用识别自绘区域内的可感知内容。

## E

### Entity Node；实体节点

由后端创建的Native节点，是前端节点对象在底层的实际载体。前端节点通过引用关系与实体节点绑定，当调用dispose解除绑定后，前端节点不再对应任何实体节点，再次调用接口可能导致crash或返回默认值。

## F

### Frame Animation；帧动画

由多帧图像按时间顺序播放形成的动画形式，用于展示连续动态效果，适用于需要呈现动画序列的场景。

## I

### Imperative Node；命令式节点

通过new FrameNode()等构造函数直接创建的节点。命令式节点可对自身属性及子节点结构进行修改。

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