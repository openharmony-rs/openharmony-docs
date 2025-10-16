# \@Reusable装饰器：组件复用
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyujie43-->
<!--Designer: @lizhan-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

\@Reusable装饰器标记的自定义组件支持视图节点、组件实例和状态上下文的复用，避免重复创建和销毁，提升性能。

## 概述

使用\@Reusable装饰器时，表示该自定义组件可以复用。与[\@Component装饰器](arkts-create-custom-components.md#component)结合使用，标记为\@Reusable的自定义组件在从组件树中移除时，组件及其对应的JS对象将被放入复用缓存中。后续创建新自定义组件节点时，将复用缓存中的节点，从而节约组件重新创建的时间。

> **说明：**
>
> API version 10开始支持@Reusable，支持在ArkTS中使用。
>
> 关于组件复用的原理与使用、优化方法、适用场景，请参考最佳实践[组件复用最佳实践](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-component-reuse)。
>
> \@Reusable标识之后，在组件上下树时ArkUI框架会调用该组件的[aboutToReuse](../../../application-dev/reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttoreuse10)方法和[aboutToRecycle](../../../application-dev/reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttorecycle10)方法，因此，开发者在实现复用时，大部分代码都集中在这两个生命周期方法中。
>
> 如果一个组件里可复用的组件不止一个，可以使用[reuseId](../../../application-dev/reference/apis-arkui/arkui-ts/ts-universal-attributes-reuse-id.md)来区分不同结构的复用组件。
>

## 限制条件

- \@Reusable装饰器仅用于自定义组件。

- \@Reusable不支持跟[\@ComponentV2](./arkts-new-componentV2.md)搭配使用，\@ComponentV2组件复用推荐[\@ReusableV2装饰器](./arkts-new-reusableV2.md)。

    <!-- @[reusable_for_custom_components](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ReusableComponent/entry/src/main/ets/pages/ReusableForCustomComponents.ets) -->

- 被@Reusable装饰的自定义组件在复用时，会递归调用该自定义组件及其所有子组件的aboutToReuse回调函数。若在子组件的aboutToReuse函数中修改了父组件的状态变量，此次修改将不会生效，请避免此类用法。若需设置父组件的状态变量，可使用setTimeout设置延迟执行，将任务抛出组件复用的作用范围，使修改生效。


  【反例】

  在子组件的aboutToReuse中，直接修改父组件的状态变量。

  <!-- @[reusable_for_incorrect_sample](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ReusableComponent/entry/src/main/ets/pages/ReusableIncorrectSample.ets) -->


  【正例】

  在子组件的aboutToReuse中，使用setTimeout，将修改抛出组件复用的作用范围。

  <!-- @[reusable_for_correct_sample](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ReusableComponent/entry/src/main/ets/pages/ReusableCorrectSample.ets) -->


- ComponentContent不支持传入\@Reusable装饰器装饰的自定义组件。

  <!-- @[component_content_not_support_reusable_custom_components](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ReusableComponent/entry/src/main/ets/pages/ComponentContentNotSupportReusable.ets) -->

- \@Reusable装饰器不建议嵌套使用，会增加内存，降低复用效率，加大维护难度。嵌套使用会导致额外缓存池的生成，各缓存池拥有相同树状结构，复用效率低下。此外，嵌套使用会使生命周期管理复杂，资源和变量共享困难。


## 使用场景

### 动态布局更新

重复创建与移除视图可能引起频繁的布局计算，从而影响帧率。采用组件复用可以避免不必要的视图创建与布局计算，提升性能。
以下示例中，将Child自定义组件标记为复用组件，通过Button点击更新Child，触发复用。

<!-- @[dynamic_layout_update](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ReusableComponent/entry/src/main/ets/pages/DynamicLayoutUpdate.ets) -->

### 列表滚动配合LazyForEach使用

- 当应用展示大量数据的列表并进行滚动操作时，频繁创建和销毁列表项视图可能导致卡顿和性能问题。使用列表组件的组件复用机制可以重用已创建的列表项视图，提高滚动流畅度。

- 以下示例代码将CardView自定义组件标记为复用组件，List上下滑动，触发CardView复用。

  <!-- @[list_scrolling_with_lazy_for_each](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ReusableComponent/entry/src/main/ets/pages/ListScrollingWithLazyForEach.ets) -->

### 列表滚动-if使用场景

以下示例代码将OneMoment自定义组件标记为复用组件。当List上下滑动时，会触发OneMoment的复用。设置reuseId可为复用组件分配复用组，相同reuseId的组件将在同一复用组中复用。单个复用组件无需设置reuseId。使用reuseId标识复用组件，可避免重复执行if语句的删除和重新创建逻辑，提高复用效率和性能。

<!-- @[list_scrolling_with_if_statements](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ReusableComponent/entry/src/main/ets/pages/ListScrollingWithIfStatements.ets) -->

### 列表滚动-Foreach使用场景

使用Foreach创建可复用的自定义组件，由于Foreach渲染控制语法的全展开属性，导致复用组件无法复用。示例中点击update，数据刷新成功，但滑动列表时，ListItemView无法复用。点击clear，再次点击update，ListItemView复用成功，因为一帧内重复创建多个已被销毁的自定义组件。

<!-- @[list_scrolling_with_for_each](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ReusableComponent/entry/src/main/ets/pages/ListScrollingWithForEach.ets) -->

### Grid使用场景

示例中使用\@Reusable装饰器修饰GridItem中的自定义组件ReusableChildComponent，即表示其具备组件复用的能力。
使用aboutToReuse可以在 Grid 滑动时，从复用缓存中加入到组件树之前触发，从而更新组件状态变量，展示正确内容。
需要注意的是无需在aboutToReuse中对[\@Link](arkts-link.md)、[\@StorageLink](arkts-appstorage.md#storagelink)、[\@ObjectLink](arkts-observed-and-objectlink.md)、[\@Consume](arkts-provide-and-consume.md)等自动更新值的状态变量进行更新，可能触发不必要的组件刷新。

<!-- @[reusable_for_grid_usage_scenario](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ReusableComponent/entry/src/main/ets/pages/ReusableForGridUsageScenario.ets) -->

### WaterFlow使用场景

- 在WaterFlow滑动场景中，FlowItem及其子组件频繁创建和销毁。可以将FlowItem中的组件封装成自定义组件，并使用\@Reusable装饰器修饰，实现组件复用。

  <!-- @[reusable_for_water_flow_usage_scenario](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ReusableComponent/entry/src/main/ets/pages/ReusableForWaterFlowUsageScenario.ets) -->

### Swiper使用场景

- 在Swiper滑动场景中，条目中的子组件频繁创建和销毁。可以将这些子组件封装成自定义组件，并使用\@Reusable装饰器修饰，以实现组件复用。

  <!-- @[reusable_for_swiper_usage_scenario](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ReusableComponent/entry/src/main/ets/pages/ReusableForSwiperUsageScenario.ets) -->

### 列表滚动-ListItemGroup使用场景

- 可以视作特殊List滑动场景，将ListItem需要移除重建的子组件封装成自定义组件，并使用\@Reusable装饰器修饰，使其具备组件复用能力。

  <!-- @[reusable_for_list_item_group_usage_scenario](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ReusableComponent/entry/src/main/ets/pages/ReusableForListItemGroupUsageScenario.ets) -->

### 多种条目类型使用场景

**标准型**

复用组件的布局相同，示例参见本文列表滚动部分的描述。

**有限变化型**

复用组件间存在差异，但类型有限。例如，可以通过显式设置两个reuseId或使用两个自定义组件来实现复用。

<!-- @[reusable_for_limited_variation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ReusableComponent/entry/src/main/ets/pages/ReusableForLimitedVariation.ets) -->

**组合型**

复用组件间存在多种差异，但通常具备共同的子组件。将三种复用组件以组合型方式转换为Builder函数后，内部的共享子组件将统一置于父组件MyComponent之下。复用这些子组件时，缓存池在父组件层面实现共享，减少组件创建过程中的资源消耗。

<!-- @[reusable_for_composite](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ReusableComponent/entry/src/main/ets/pages/ReusableForComposite.ets) -->
