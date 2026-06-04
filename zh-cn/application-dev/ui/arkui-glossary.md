# ArkUI术语
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @mayaolll-->
<!--Designer: @jiangdayuan-->
<!--Tester: @zhangwenhan12-->
<!--Adviser: @Brilliantry_Rui-->

## A

### Atomic Layout；原子布局

ArkUI面向服务卡片（JS卡片）提供的屏幕自适应布局能力集合，包含隐藏能力（按优先级隐藏空间不足的子元素）、占比能力（按权值比例分配容器空间）和固定比例（按宽高比调整组件尺寸）三种子能力，适用于JS UI框架中支持flex布局的容器组件。

### Avoid Area；避让区

ArkUI页面显示区域中由系统划定的、默认不与应用界面重叠的区域，包括状态栏、导航栏、刘海屏或挖孔屏区域、软键盘区域等。页面内容默认布局在避让区之外的安全区域内，通过expandSafeArea等属性可使组件延伸至避让区内实现沉浸式效果。

## B

### Bias；偏置

RelativeContainer中组件在两个约束锚点之间的位置比例参数，值为到左/上侧锚点的距离与锚点间总距离的比值（0~1），用于精细控制组件在约束空间内的相对位置。

### Breakpoints Reference；断点参照物

栅格容器判断当前断点区间时所依据的尺寸对象，可选择以应用窗口宽度（WindowSize）或容器自身宽度（ComponentSize）为参照。当应用以非全屏窗口形式显示时，以窗口宽度为参照更为通用。

## C

### Chain Style；链样式

RelativeContainer中定义链内组件在约束锚点间分布方式的风格选项，包括SPREAD（均匀分布）、SPREAD_INSIDE（两端对齐后均匀分布）和PACKED（紧凑排列）三种模式。

### Chain Weight；链权重

RelativeContainer中按权重比例为链上的组件重新分配水平或竖直方向的尺寸，使同一条链上的兄弟组件按权重比例自适应占满剩余空间。

### Container Reader；容器断点

基于组件容器自身实际尺寸和断点阈值数组确定的响应式断点机制。与窗口级断点不同，容器断点仅作用于当前组件及其子组件，同一页面中的多个容器可拥有各自独立的断点状态，用于在动态场景下根据容器尺寸进行差异化布局。宽度断点基于组件实际宽度（单位vp）划分，高度断点基于组件高宽比划分。

### Custom Layout；自定义布局

自定义组件中通过实现onMeasureSize和onPlaceChildren回调，手动计算和控制子组件尺寸与位置的布局机制。onMeasureSize用于测量子组件大小并返回自定义组件自身尺寸，onPlaceChildren用于设置子组件在父容器中的放置位置，两者配合使用可替代系统布局容器（如Flex、Column、Row）实现任意自定义排列。

## D

### Display Priority；显示优先级

ArkUI的Row、Column、单行Flex容器中用于控制子组件在父容器空间不足时被隐藏先后顺序的属性。数值越大优先级越高，空间不足时低优先级子组件先被隐藏，且某一优先级被隐藏后更低优先级的子组件也一并隐藏，用于在有限容器空间内保证关键内容的可见性。

### Dynamic Layout；动态布局

ArkUI提供的一种容器布局能力，允许在运行时通过切换布局算法对象来改变子组件的排列方式（如从线性布局切换为网格布局），同时保持子组件的状态（如输入框内容、滚动位置等）不被重置，用于实现同一内容在不同场景下的多种布局展示。

## E

### Expand Safe Area；安全区域扩展

ArkUI中允许组件在不改变自身布局位置和尺寸的前提下，将绘制区域延伸至安全区域之外的机制。通过expandSafeArea属性设置，可指定延伸的安全区域类型（系统区域、挖孔区域、键盘区域）和延伸的边缘方向，用于实现沉浸式显示效果。

## F

### Fold Status；折叠状态

可折叠屏设备的物理形态状态，包括FOLDED（完全折叠）、HALF_FOLDED（半折叠/悬停态）、EXPANDED（完全展开）等，用于驱动UI在不同设备形态间自适应切换布局。

## G

### Grid Breakpoint；栅格断点

栅格容器以水平宽度为依据划分的设备尺寸区间，默认分为xs/sm/md/lg四个断点，开发者可通过单调递增数组自定义断点位置，最多启用六个断点（含xl、xxl），用于在不同宽度设备上实现差异化的栅格布局。

## H

### Hover Mode；悬停态

可折叠设备处于半折叠状态（屏幕呈L形放置）时的交互模式，此时屏幕上半部分作为显示区域、下半部分作为触控操作区域，系统自动避让折痕区域并对UI布局进行上下分屏适配。

## K

### Keyboard Avoid Mode；键盘避让模式

软键盘弹出时ArkUI页面采用的避让策略，包含OFFSET（页面上抬直到露出光标）、RESIZE（压缩页面为减去键盘高度的尺寸）、NONE（不做避让处理）三种模式。通过setKeyboardAvoidMode接口配置，用于确保输入光标不被键盘遮挡。

## L

### Layout Algorithm；布局算法

动态布局容器所使用的布局策略对象，用于定义子组件的排列方式。内置算法包括线性（Row）、列式（Column）、堆叠（Stack）和栅格（Grid）四种，支持通过继承CustomLayoutAlgorithm实现自定义布局算法（如瀑布流），并可在运行时动态切换。

### Layout Policy；布局策略

ArkUI中控制组件宽高自适应行为的策略选项，包含matchParent（组件大小与父组件内容区相等）、wrapContent（组件大小与子组件内容相等，不超过父组件内容区）、fixAtIdealSize（组件大小与子组件内容相等，可超过父组件内容区）。优先级低于constraintSize。

### Layout Weight；布局权重

线性布局中当父容器尺寸确定时，按所设权重值将主轴剩余空间按比例分配给各子元素的机制，分配时忽略元素本身的尺寸设置。使多个子元素在任意屏幕尺寸下按固定比例自适应占满可用空间。

## M

### Mirroring；镜像

ArkUI提供的将显示内容在X轴上进行反转的能力，用于适配从右到左（RTL）阅读方向的语言（如阿拉伯语、维吾尔语）。当组件direction属性设为Direction.Rtl或Direction.Auto且系统语言为RTL语言时自动生效。ArkUI已为基础组件、高级组件和通用属性默认适配了镜像能力。

## N

### Named Route；命名路由

通过名称标识而非URL路径进行页面跳转的路由方式，主要用于跨包（HAR或HSP共享包）重定向到包内页面。

## P

### Page Stack；页面栈

Router模块管理的页面跳转栈结构，记录页面进出顺序，最多容纳32个页面。

### Pixel Rounding；像素取整

ArkUI中将组件边界的浮点像素值取整为整像素的机制，用于消除因浮点精度导致的渲染视觉异常（如1px缝隙、组件重叠、动画抖动等）。分为页面级和组件级两个层面：页面级像素取整通过setPixelRoundMode设置全局取整时机（布局完成后取整或测量后取整），作用于整个页面；组件级像素取整通过pixelRound属性设置特定组件在指定方向（start、top、end、bottom）上的取整对齐策略。

## R

### Route Map；路由表

Navigation中定义页面路由名称、源文件路径及自定义字段的配置映射，用于路由跳转时查找目标页面。

### Route Stack；路由栈

Navigation组件中由NavPathStack管理的NavDestination页面进出顺序栈结构，与Router管理的页面栈属不同导航模型。

## S

### Safe Area；安全区域

ArkUI页面中默认用于布局UI内容的显示区域，不与系统避让区（状态栏、导航栏、挖孔区域、软键盘区域等）重叠。通过expandSafeArea或setWindowLayoutFullScreen等机制可突破安全区域限制实现沉浸式效果。

### Safe Area Padding；安全区域边距

通过safeAreaPadding属性为容器组件设置的组件级安全区域边距。与普通padding不同，safeAreaPadding定义的区域不会被内容填充，而是作为可供子组件延伸利用的安全区范围，可与系统级避让区一起参与递归累积计算，用于精细控制子组件的布局延伸范围。

### Shape Viewport；形状视口

Shape绘制组件中定义的矩形区域，由起始点坐标和尺寸描述，用于建立绘图坐标空间与组件实际显示区域之间的映射关系。当视口尺寸小于组件尺寸时图形被放大，大于组件尺寸时图形被缩小，通过设置视口偏移可让边框等元素完全显示在可视区域内。

## T

### Theme Skinning；主题换肤

应用内视觉主题切换机制，可定制应用的全局配色风格和局部配色风格。
