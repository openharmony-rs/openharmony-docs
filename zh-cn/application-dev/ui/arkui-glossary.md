# ArkUI术语
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @mayaolll-->
<!--Designer: @jiangdayuan-->
<!--Tester: @zhangwenhan12-->
<!--Adviser: @Brilliantry_Rui-->

## N

### Named Route；命名路由

通过名称标识而非URL路径进行页面跳转的路由方式，主要用于跨包（HAR或HSP共享包）重定向到包内页面。

## P

### Page Stack；页面栈

Router模块管理的页面跳转栈结构，记录页面进出顺序，最多容纳32个页面。

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