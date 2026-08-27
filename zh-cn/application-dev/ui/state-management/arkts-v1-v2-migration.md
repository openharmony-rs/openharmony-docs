# V1-V2迁移概述
<!--Kit: ArkUI--> 
<!--Subsystem: ArkUI-->
<!--Owner: @katabanga-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

## 概述

<!--RP1-->
在状态管理框架的迭代演进中，先后推出了状态管理V1（简称V1）和状态管理V2（简称V2）。V1侧重于组件层级的状态管理，例如，需要开发者通过\@ObjectLink逐层拆解嵌套类以使深层次数据具备观测能力。V2则实现了能力升级，增强了对数据对象的深度观察与管理能力，例如，V2的\@Monitor不仅能够感知变化后的数据，还能获取变化前的数据。通过V2版本，开发者可以更灵活地操控数据与状态，实现更高效的UI刷新，提升开发体验与应用性能。
<!--RP1End-->

<!--RP2-->
为帮助已基于V1开发的应用平滑迁移至V2，本文提供了状态管理V1向V2的迁移指导，涵盖迁移过程中的常见场景，便于开发者结合自身业务灵活适配。同时，针对迁移过渡阶段可能出现的状态管理V1和V2混用场景，文章讲解了V1和V2组件混用的规则和实操方法，并根据API version 19前后的差异，分别提供了针对性解决方案，帮助开发者实现逐步改造。
<!--RP2End-->


## V1V2使用指引

针对V1与V2的使用，建议依据应用需求选择。鉴于V2为V1的增强版本，且正持续迭代优化，功能上更推荐新开发时使用。主要参考策略如下：

1. 对于新开发的应用，建议直接采用V2版本进行开发。

2. 对于已使用V1的应用，如果V1的功能和性能满足需求，无需立即切换至V2。

3. 对于需要在现阶段混用V1和V2的场景，<!--RP3-->请参阅状态管理V1和V2混用场景文档<!--RP3End-->。编译器、工具链、DevEco Studio会对某些误用和混用场景进行校验，建议开发者遵循该文档，避免因双重代理（数据被V1和V2同时代理监听）等问题给应用带来不确定性。


## V1与V2差异对比

关于V1与V2部分的差异，具体V1和V2的区别可以参见状态管理概述以及状态管理V1和V2更新机制差异。这部分内容，可以帮助开发者理解V1与V2运行背后的差异点，在适配时，起到事半功倍的效果。


## V1与V2能力对照迁移表

| V1装饰器名称\场景 | V2装饰器名称\API | 说明 |
| -------- | -------- | -------- |
| \@Component | \@ComponentV2 | \@Component为搭配V1状态变量使用的自定义组件装饰器。<br/>\@ComponentV2为搭配V2状态变量使用的自定义组件装饰器。 |
| \@State | 无外部初始化：\@Local<br/>外部初始化一次：\@Param、\@Once | \@State和\@Local类似都是数据源的概念，在不需要外部传入初始化时，可直接迁移。如果需要外部传入初始化，则可以迁移为\@Param \@Once。详情见迁移场景--\@State->\@Local。如果使用滚动组件关联的WaterFlowSections/ChildrenMainSize，需要使用makeObserved，详情见迁移场景--滚动组件。 |
| \@Prop | \@Param | \@Prop和\@Param类似都是自定义组件参数的概念。当输入参数为复杂类型时，\@Prop为深拷贝，\@Param为引用。详情见迁移场景--@Prop -> @Param。 |
| \@Link | \@Param、@Event | \@Link是框架自己封装实现的双向同步，对于V2开发者可以通过\@Param\@Event自己实现双向同步。详情见迁移场景--\@Link -> \@Param/\@Event。 |
| \@Observed | \@ObservedV2 | 表明当前对象为可观察对象。但两者能力并不相同。<br/>\@Observed可观察第一层的属性，需要搭配\@ObjectLink使用才能生效。<br/>\@ObservedV2本身无观察能力，仅代表当前class可被观察，如果要观察其属性，需要搭配\@Trace使用。详情见迁移场景---@ObjectLink/@Observed/@Track -> @ObservedV2/@Trace。 |
| \@ObjectLink | \@ObservedV2、\@Trace | 直接兼容，\@ObjectLink需要被\@Observed装饰的class的实例初始化，主要应用于观察嵌套类场景。在状态管理V2中可以使用\@ObservedV2\@Trace。详情见迁移场景---@ObjectLink/@Observed/@Track -> @ObservedV2/@Trace。 |
| @Track | @Trace | V1装饰器\@Track为精确观察，不使用则无法做到类属性的精准观察。<br/>V2\@Trace装饰的属性可以被精确跟踪观察。详情见迁移场景---@ObjectLink/@Observed/@Track -> @ObservedV2/@Trace。 |
| @Provide、@Consume | @Provider、@Consumer | 兼容。详情见@Provide/@Consume迁移场景。 |
| @Watch | @Monitor | \@Watch用于监听V1状态变量的变化，具有监听状态变量本身和其第一层属性变化的能力。状态变量可观察到的变化会触发其\@Watch监听事件，详情见迁移场景--@Watch -> @Monitor。<br/>\@Monitor用于监听V2状态变量的变化，搭配\@ObservedV2和\@Trace一起使用，可有深层监听的能力。状态变量在一次事件中多次变化时，仅会以最终的结果判断是否触发\@Monitor监听事件。 |
| 无计算属性能力 | @Computed | 状态管理V1无计算属性相关能力，状态管理V2可使用\@Computed避免重复计算。详情见迁移场景--重复计算->@Computed计算属性。 |
| LocalStorage | @ObservedV2、@Trace | 兼容。详情见迁移场景--LocalStorage->@ObservedV2/@Trace。 |
| AppStorage | AppStorageV2 | 兼容。详情见迁移场景--AppStorage->AppStorageV2。 |
| Environment | 调用Ability接口获取系统环境变量 | Environment获取环境变量能力和AppStorage耦合。在V2中可直接调用Ability接口获取系统环境变量。详情见迁移场景--Environment->调用Ability接口直接获取系统环境变量。 |
| PersistentStorage | PersistenceV2 | PersistentStorage持久化能力和AppStorage耦合，PersistenceV2持久化能力可独立使用。详情见迁移场景--PersistentStorage->PersistenceV2。 |


## 状态管理V1向V2逐步迁移策略

对于已经使用V1开发的大型应用，通常难以一次性从V1迁移到V2，而是需要分批次、分组件地逐步迁移；首先考虑将V1组件迁移为V2组件，<!--RP5-->这部分可以参考状态管理V1向V2迁移场景进行适配<!--RP5End-->。

迁移过程中由于V1与V2存在共存的情况，这就必然会带来V1和V2的混用。针对混用的场景，<!--RP4-->可以参考状态管理V1和V2混用场景进行适配，并最终完成V1->V2的全量适配<!--RP4End-->。
