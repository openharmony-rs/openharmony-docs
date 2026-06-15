# 术语

## A

### abc文件

方舟字节码（ArkCompiler Bytecode）文件，是ArkCompiler的编译工具链以源代码作为输入编译生成的产物，其文件后缀名为.abc。在发布态，abc文件会被打包到HAP中。

### @AnimatableExtend；可动画属性装饰器

ArkUI装饰器，用于定义自定义可动画属性方法，使原本不支持动画插值的属性也能参与属性动画过渡。区别于内置animation属性仅对预定义可动画属性生效。

### AnimatableArithmetic\<T\>；可动画运算接口

ArkUI接口，定义plus/subtract/multiply/equals算术规则，使自定义非数值数据类型（数组、结构体、颜色等）能进行动画插值运算。使用@AnimatableExtend对非数值类型做动画时必须实现此接口。

### animateToImmediately；显式动画立即下发

ArkUI显式动画接口，绕过vsync信号对齐，将动画命令立即下发至渲染层。当主线程繁忙时，可优先保障特定视觉更新的即时性，区别于animateTo需等待vsync对齐。

### AppLinking

基于操作系统基础能力（DeepLink/URL Scheme等技术），为开发者提供的用户增长服务。在目标方本地已安装的场景下，可以直达内容，未安装时，开发者可以定制跳转目标。而且，该服务可以保证跳转的安全性，目标方不会被仿冒。

### ArkCompiler；方舟编译器

OpenHarmony内置的组件化、可配置的多语言编译和运行平台，包含编译器、工具链、运行时等关键部件，支持高级语言在多种芯片平台的编译与运行，并支撑OpenHarmony标准操作系统及其应用和服务运行在手机、个人电脑、平板、电视、汽车和智能穿戴等多种设备上的需求。

### ArkTS

OpenHarmony生态的应用开发语言。它在TypeScript（简称 TS）的基础上，扩展了声明式UI、状态管理等能力，让开发者可以以更简洁、更自然的方式开发应用。

### ArkUI；方舟开发框架

OpenHarmony上原生UI框架，是一套极简、高性能、跨设备应用设计研发的UI开发框架，支撑开发者高效地构建跨设备应用UI界面。

## B

### bindSheet；半模态页面

非全屏模态弹出页面，保持部分父页面可见，适用于简单任务面板和信息表单等场景。

### bindContentCover；全屏模态

绑定到组件的全屏模态转场机制，支持三种系统转场样式（DEFAULT纵向滑入、NONE无动画、ALPHA淡入淡出）及自定义TransitionEffect转场。API 20起模态内容默认在安全区内布局。

### Bundle Manager Service (BMS)

包管理服务。

## C

### Common Event Service (CES)

OpenHarmony中负责处理公共事件的订阅、发布和退订的系统服务。

### customNavContentTransition；自定义导航内容转场

Navigation组件提供的导航转场定制能力，允许开发者定义页面切换时的动画效果，包括共享元素转场等。

## D

### Distributed Management Service (DMS)

分布式管理服务。

## E

### EdgeLight；边缘流光

沿组件边缘从指定位置移动的发光动画效果，用于增强视觉显著性。

### EffectComponent；特效合并容器组件

ArkUI容器组件，将子组件的视觉效果（如背景模糊）合并到单一绘制通道中渲染，以优化绘制性能。区别于普通容器仅做布局聚合。

### EffectLayer；特效层

EffectComponent内的专用渲染层，用于在特定z-order层级绘制内容，如充电动画叠加层。

### EffectType；效果模板

系统预定义或窗口级预定义的视觉效果参数集合（模糊半径、饱和度、亮度、颜色等），可通过useEffect属性整体应用。DEFAULT继承自EffectComponent；WINDOW_EFFECT使用窗口内置模板，因设备类型（手机/二合一/平板）而异。

### ExtensionAbility

Stage模型中的组件类型名，即ExtensionAbility组件，提供特定场景（如卡片、输入法）的扩展能力，满足更多的使用场景。

## F
   
### FA模型

API version 8及更早版本支持的应用模型，已经不再主推。建议使用新的Stage模型进行开发。

## G

### geometryTransition；隐式共享元素转场

将绑定的出入组件在视图切换时进行位置和尺寸的空间联动动画，实现"一镜到底"的上下文连贯感。区别于显式共享元素转场（sharedTransition）需在两个页面分别声明。

## H

### Harmony Ability Package (HAP)

一个HAP文件包含应用的所有内容，由代码、资源、三方库及应用配置文件组成，其文件后缀名为.hap。

### Hardware Driver Foundation (HDF)；硬件驱动框架

提供统一外设访问能力以及驱动开发、管理框架。

### HDF Configuration Generator (HC-GEN)

HCS配置转换工具，可以将HDF配置文件转换为软件可读取的文件格式。

### HDF Configuration Source (HCS)

HDF驱动框架的配置描述语言，是一种以Key-Value为主体的文本格式，用于实现配置代码与驱动代码解耦、便于配置管理。

### Hypium

Hyper Automation + ium 的组合词，OpenHarmony自动化测试框架名称，以超自动化测试为理想目标，ium意指稳定、可靠的测试框架能力底座。

## I

### ImmersiveMaterial；沉浸式材质

系统级材质类型，在不同厚度层级（超薄至超厚）提供沉浸式模糊、高光和交互视觉效果，设备自适应呈现。

### Immersive System Material；沉浸式系统材质

系统级UI材质框架，提供设备自适应视觉效果（模糊、阴影、高光、颜色反转），按设备算力高低分级呈现，可通过module.json5中ohos.arkui.UIMaterial.state配置项控制。

### Intelligent Distributed Networking (IDN)

OpenHarmony特有的分布式组网能力单元。开发者可以通过IDN获取分布式网络内的设备列表和设备状态信息，以及注册分布式网络内设备的在网状态变化信息。

### interpolatingSpring；插值弹簧曲线

弹簧物理曲线，生成0到1的归一化插值轨迹，动画时长完全由弹簧物理参数（质量、刚度、阻尼）决定，覆盖外部设定的动画时长。仅支持正向单次播放，不支持反转。

## K

### 卡片转场

卡片专属转场样式，卡片展开至详情页面时，周围组件纵向分离（展开）形成视觉过渡。

## L

### LuminanceSampler；亮度取色器

监测组件背景亮度跨越阈值变化的采样器，触发自适应回调以实现动态UI样式调整。

## M

### module.json5

OpenHarmony模块级配置文件，采用JSON5语法，定义模块元数据、Ability声明和系统材质状态等。仅entry类型模块中的配置项影响材质配置。

### modal transition；半模态转场

将半模态弹出页面绑定到组件的转场机制，支持四种展示样式——底部弹板、居中弹窗、跟手弹板和侧边弹板，每种样式具有不同的交互模式和避让策略。区别于全屏模态转场。

### Module

模块，应用的一部分，每个模块都有单独的module.json5配置文件。项目工程中，Entry、Feature、HSP和HAR均为应用的一个模块。

## N

### NavPathStack；导航路径栈

Navigation组件的导航管理栈，支持push/pop操作，并协调目的地之间的自定义转场动画。

### NodeContainer；节点容器

ArkUI容器组件，将NodeController管理的节点渲染为自定义占位组件插入UI树。

## O

### Obscured；隐私遮罩

ArkUI隐私保护特性，用占位符式遮罩遮盖Image和Text组件内容。区别于一般裁剪/遮罩控制视觉形状，隐私遮罩的核心目的是内容可见性安全保护。

## P

### Particle Disturbance Field；粒子扰动场

ArkUI粒子动画系统中的力场，对区域内粒子施加可配置的排斥/吸引力并附带噪声调制。区别于速度场（添加定向速度）和波动场（添加振荡扩散）。

### Particle Ripple Field；粒子波动场 

ArkUI粒子动画系统中的波动力场，对区域内粒子施加振荡力产生涟漪扩散效果，可配置振幅、波长、波速和衰减。

### Particle Velocity Field；粒子速度场

ArkUI粒子动画系统中的定向力场，对区域内粒子添加固定速度向量作为运动补充；粒子离开场区域后即失去该附加速度。

## R

### renderFit；组件内容填充方式

ArkUI属性，控制组件在宽高动画过渡期间内容的对齐和缩放绘制行为。未设置时，内容会以左上对齐方式直接跳至最终尺寸。

### renderGroup；渲染组合

ArkUI性能优化属性，将组件及其子树的绘制操作缓存到离屏画布后统一合成，减少逐帧重绘开销。子树内容不变时提升性能，但频繁变化的子树反而可能因缓存失效而降低性能。

## S

### Service widget；服务卡片

将用户应用程序的重要信息以服务卡片的形式展示在桌面，用户可通过快捷手势使用卡片，以达到服务直达、减少层级跳转的目的。

### sharedTransition；共享元素转场

页面路由导航时，源页面和目标页面中具有相同sharedTransition ID的匹配元素在视觉上产生位置和尺寸的交换动画，可选配运动轨迹路径，营造空间连贯过渡感。

### springMotion；弹性动画曲线

支持速度继承的弹簧物理曲线：当多个弹簧动画作用于同一属性时，新动画继承当前速度而非中断重启，产生自然衔接过渡。

### Stage模型

API version 9开始新增的应用模型，提供UIAbility、ExtensionAbility两大类应用组件。由于该模型还提供了AbilityStage、WindowStage等类作为应用组件和Window窗口的“舞台”，因此称之为Stage模型。

### Super virtual device；超级虚拟终端

亦称超级终端，通过分布式技术将多个终端的能力进行整合，存放在一个虚拟的硬件资源池里，根据业务需要统一管理和调度终端能力，来对外提供服务。

### System Capability (SysCap)；系统能力

不同值用于指代OpenHarmony中各个相对独立的特性/系统能力，如蓝牙、Wi-Fi、NFC等。每个特性/系统能力对应多个API，每个API定义上包含了相应的SysCap标签。

### System Type；系统类型
- Mini System，轻量系统：面向MCU（Microcontroller Unit，微控制单元）类处理器，例如ARM Cortex-M、RISC-V 32位的设备，资源极其有限，参考内存≥128KiB，提供丰富的近距连接能力以及丰富的外设总线访问能力。典型产品有智能家居领域的联接类模组、传感器设备等。
- Small System，小型系统：面向应用处理器，例如Arm Cortex-A的设备，参考内存≥1MiB，提供更高的安全能力，提供标准的图形框架，提供视频编解码的多媒体能力。典型产品有智能家居领域的IPCamera、电子猫眼、路由器以及智慧出行域的行车记录仪等。
- Standard System，标准系统：面向应用处理器，例如Arm Cortex-A的设备，参考内存≥128MiB，提供增强的交互能力，提供3D GPU以及硬件合成能力，提供更多控件以及动效更丰富的图形能力，提供完整的应用框架。典型产品有高端的冰箱显示屏等。

## T

### TransitionEffect；组件内转场

组件插入或移除渲染树（通过if/ForEach/visibility变化触发）时的转场动画机制。TransitionEffect提供可组合的类型安全API（OPACITY、SLIDE、SLIDE_SWITCH、asymmetric、combine等），区别于页面级转场。

### responsiveSpringMotion；弹性跟手动画曲线

springMotion的跟手优化变体，默认响应时间更短（0.15s vs 0.55s）、阻尼更高，专为手势跟随场景设计，使动画对象紧密追踪手指位置，减少延迟和过冲。

## U

### UIAbility

Stage模型中的组件类型名，即UIAbility组件，包含UI，提供展示UI的能力，主要用于和用户交互。

### Union Effect；形状融合

ArkUI视觉效果，将后代组件形状收集并融合为有机形态，产生粘性/非线性变形效果，支持平滑融合和重力融合两种模式。

### useEffect；特效绘制合并

允许子组件继承并合并父组件视觉效果参数（模糊、亮度等）到单一合成绘制通道的机制，减少逐组件重复效果渲染以提升性能。

## Z

### 中轴避让

二合一折叠屏设备上的布局适配策略，避免内容出现在中间铰链区域，将内容限制在屏幕上半或下半区域。

### 组件坐标系

ArkUI中以组件左上角为原点的坐标系。组件平移后该坐标系仍保持固定，旋转/缩放锚点和偏移量始终基于原始位置而非位移后位置。
