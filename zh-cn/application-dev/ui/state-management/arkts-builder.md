# \@Builder装饰器：自定义构建函数
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

ArkUI提供轻量的UI元素复用机制\@Builder，其内部UI结构固定，仅与使用方进行数据传递。开发者可将重复使用的UI元素抽象成函数，在build函数中调用。

\@Builder装饰的函数也称为“自定义构建函数”。

在阅读本文档前，建议提前阅读：[基本语法概述](./arkts-basic-syntax-overview.md)、[声明式UI描述](./arkts-declarative-ui-description.md)、[自定义组件-创建自定义组件](./arkts-create-custom-components.md)。

@Builder装饰器和@Component装饰器在功能和使用方式上的主要差异：

1. @Builder装饰器用于封装可复用的UI结构，通过提取重复的布局代码提高开发效率。该装饰器严格禁止在其内部定义状态变量或使用生命周期函数，必须通过参数传递或者访问所属组件的状态变量完成数据交互。

2. 在ArkUI框架中，@Component装饰器作为封装复杂UI组件的核心机制，允许开发者通过组合多个基础组件来构建可复用的复合界面。该装饰器不仅支持内部状态变量的定义，还能完整管理组件的生命周期。

> **说明：**
>
> 从API version 9开始，该装饰器支持在ArkTS卡片中使用。
>
> 从API version 11开始，该装饰器支持在原子化服务中使用。


## 装饰器使用说明

\@Builder装饰器有两种使用方式，分别是定义在自定义组件内部的[私有自定义构建函数](#私有自定义构建函数)和定义在全局的[全局自定义构建函数](#全局自定义构建函数)。

### 私有自定义构建函数

示例：

<!-- @[private_custom_constructor](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/BuilderComponent/entry/src/main/ets/pages/PrivateCustomConstructor.ets) -->

``` TypeScript
@Entry
@Component
struct BuilderDemo {
  @Builder
  showTextBuilder() {
    // @Builder装饰此函数，使其能以链式调用的方式配置并构建Text组件
    Text('Hello World')
      .fontSize(30)
      .fontWeight(FontWeight.Bold)
  }

  @Builder
  showTextValueBuilder(param: string) {
    Text(param)
      .fontSize(30)
      .fontWeight(FontWeight.Bold)
  }

  build() {
    Column() {
      // 无参数
      this.showTextBuilder()
      // 有参数
      this.showTextValueBuilder('Hello @Builder')
    }
  }
}
```

使用方法：

- 允许在自定义组件内定义一个或多个@Builder函数，该函数被认为是该组件的私有、特殊类型的成员函数。

- 私有自定义构建函数允许在自定义组件内、build函数和其他自定义构建函数中调用。

- 在自定义组件中，`this`指代当前所属组件，组件的状态变量可在自定义构建函数内访问。建议通过`this`访问组件的状态变量，而不是通过参数传递。

### 全局自定义构建函数

示例：

<!-- @[global_custom_constructor](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/BuilderComponent/entry/src/main/ets/pages/GlobalCustomConstructor.ets) -->

``` TypeScript
@Builder
function showTextBuilder() {
  Text('Hello World')
    .fontSize(30)
    .fontWeight(FontWeight.Bold)
}
@Entry
@Component
struct BuilderSample {
  build() {
    Column() {
      showTextBuilder()
    }
  }
}
```

- 如果不涉及组件状态变量变化，建议使用全局的自定义构建函数。

- 全局自定义构建函数允许在build函数和其他自定义构建函数中调用。


## 参数传递规则

自定义构建函数的参数传递有[按回调传递](#按回调传递参数)，[按引用传递](#按引用传递参数)和[按值传递](#按值传递参数)，均需遵守以下规则：

- \@Builder装饰的函数参数类型不允许为undefined、null和返回undefined、null的表达式。

- 在\@Builder装饰的函数内部，不允许改变参数值。

- \@Builder内UI语法遵循[UI语法规则](arkts-create-custom-components.md#build函数)。

- 按回调传递和按引用传递时，支持\@Builder函数内UI组件刷新。按引用传递只在传入一个参数且该参数直接传入对象字面量时生效，有多个参数时不支持@Builder函数内UI组件刷新。

- 使用引用传递时，在@Builder函数中不能修改参数的属性，但使用`UIUtils.makeBinding`并传入写回调时，我们可以在@Builder函数内修改属性，并同步到调用@Builder的组件中。

### 按回调传递参数

从API version 20开始，开发者可以通过使用`UIUtils.makeBinding()`函数、`Binding`类和`MutableBinding`类实现\@Builder函数中状态变量的刷新。详细用例见[\@Builder支持状态变量刷新](#builder支持状态变量刷新)。

使用`UIUtils.makeBinding()`包装读取状态变量的回调函数作为参数传入@Builder函数，可以支持@Builder函数中UI组件刷新；`UIUTils.makeBinding()`中额外传入写状态变量的回调函数可以进一步将@Builder内对参数改变，传递到调用Builder函数的组件中。

<!-- @[by_makebinding_parameter_passing](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/BuilderComponent/entry/src/main/ets/pages/ParameterMakeBinding.ets) -->

``` TypeScript
import { Binding, MutableBinding, UIUtils } from '@kit.ArkUI';

@Builder
function customButton(num1: Binding<number>, num2: MutableBinding<number>) {
  Row() {
    Column() {
      Text(`number1: ${num1.value}, number2: ${num2.value}`)
      Button(`only change number2`)
        .onClick(() => {
          // 赋值MutableBinding类型传递该修改到父组件中。
          num2.value += 1;
        })
    }
  }
}

@Entry
@ComponentV2
struct ParameterMakeBinding {
  @Local number1: number = 5;
  @Local number2: number = 12;

  build() {
    Column() {
      customButton(
        // 使用makeBinding传入参数，需要传入读回调，返回Binding类型，支持@Builder内组件UI刷新。
        UIUtils.makeBinding<number>(() => this.number1),
        // makeBinding额外传入写回调时返回MutableBinding类型，支持@Builder内组件UI刷新并且同步属性修改。
        UIUtils.makeBinding<number>(
          () => this.number2,
          (val: number) => {
            this.number2 = val;
          })
      )
    }
  }
}
```

### 按引用传递参数

按引用传递参数时，传递的参数可为状态变量，且状态变量的改变会引起\@Builder函数内的UI刷新。

<!-- @[by_reference_parameter_passing](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/BuilderComponent/entry/src/main/ets/pages/ParameterReference.ets) -->

### 按值传递参数

调用\@Builder装饰的函数默认按值传递。当传递的参数为状态变量时，状态变量的改变不会引起\@Builder函数内的UI刷新。所以当使用状态变量的时候，推荐使用[按回调传递](#按回调传递参数)或[按引用传递](#按引用传递参数)。

<!-- @[by_value_parameter_passing](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/BuilderComponent/entry/src/main/ets/pages/ParameterValue.ets) -->

## 限制条件

1. \@Builder装饰的函数内部在没有使用[MutableBinding](../../reference/apis-arkui/js-apis-StateManagement.md#mutablebindingt20)时不允许修改参数值，修改不会触发UI刷新。若[按引用传递参数](#按引用传递参数)且仅传入一个参数时，修改参数内部的属性会抛出运行时错误。使用MutableBinding可以帮助开发者在\@Builder装饰的函数内部修改参数值，请参考[在@Builder装饰的函数内部修改入参内容](#在builder装饰的函数内部修改入参内容)。

2. \@Builder按引用传递且仅传入一个参数时，才会触发动态渲染UI。请参考[按引用传递参数](#按引用传递参数)。

3. 如果\@Builder传入的参数是两个或两个以上，不会触发动态渲染UI，请参考[@Builder存在两个或两个以上参数](#builder存在两个或两个以上参数)。

4. \@Builder传入的参数中同时包含按值传递和按引用传递，不会触发动态渲染UI，请参考[@Builder存在两个或两个以上参数](#builder存在两个或两个以上参数)。

5. \@Builder的参数必须按照对象字面量的形式，把所需属性一一传入，才会触发动态渲染UI，请参考[@Builder存在两个或两个以上参数](#builder存在两个或两个以上参数)。


## 使用场景

### 自定义组件内使用自定义构建函数

创建私有的`@Builder`函数，在`Column`中使用`this.builder()`调用。通过`aboutToAppear`生命周期函数和按钮的点击事件更新`builder_value`，实现UI的动态渲染。

<!-- @[using_custom_builder_function_in_custom_component](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/BuilderComponent/entry/src/main/ets/pages/InCustomComponent.ets) -->
示例效果图

![arkts-builder-usage-scenario1](figures/arkts-builder-usage-scenario1.gif)

### 全局自定义构建函数

创建全局的`@Builder`函数，并在`Column`中通过`overBuilder()`方式调用。传递参数时，可以使用对象字面量形式，无论是简单类型还是复杂类型，值的任何变化都会触发UI界面的刷新。

<!-- @[global_custom_builder_function](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/BuilderComponent/entry/src/main/ets/pages/GlobalCustomBuilder.ets) -->
示例效果图

![arkts-builder-usage-scenario2](figures/arkts-builder-usage-scenario2.gif)

### 修改装饰器修饰的变量触发UI刷新

在该场景中，`@Builder`被用来展示Text组件，不会参与动态UI刷新。Text组件中值的变化是通过使用装饰器的特性，监听到值的改变触发的UI刷新，而不是通过`@Builder`的能力触发的。

<!-- @[changing_by_the_decorator_triggers_ui_rerendering](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/BuilderComponent/entry/src/main/ets/pages/ChangingByDecorator.ets) -->
示例效果图

![arkts-builder-usage-scenario3](figures/arkts-builder-usage-scenario3.gif)

### 将@Builder装饰的函数当作CustomBuilder类型使用

当参数类型为`CustomBuilder`时，可以传入定义的`@Builder`函数。因为`CustomBuilder`实际上是`Function(() => any)`或`void`类型，而`@Builder`也是`Function`类型。所以通过传入`@Builder`可以实现特定效果。
全局`@Builder`函数当作`CustomBuilder`类型传递时需要绑定this上下文，开发者可以直接调用全局`@Builder`函数，编译工具链会自动生成绑定this上下文的代码。

<!-- @[using_function_decorated_with_builder_as_custom_builder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/BuilderComponent/entry/src/main/ets/pages/AsCustomBuilder.ets) -->
示例效果图

![arkts-builder-usage-scenario4](figures/arkts-builder-usage-scenario4.gif)

### 多层\@Builder函数嵌套

在\@Builder函数内调用自定义组件或其他\@Builder函数，实现多个\@Builder嵌套使用。若要实现最内层的\@Builder动态UI刷新功能，每层调用\@Builder的地方必须使用按引用传递的方式。这里`$$`不是必须的参数形式，可以换成其他名称。

<!-- @[nested_builder_functions](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/BuilderComponent/entry/src/main/ets/pages/NestedBuilderFunctions.ets) -->
示例效果图

![arkts-builder-usage-scenario5](figures/arkts-builder-usage-scenario5.gif)

### \@Builder函数联合V2装饰器

由[@ObservedV2](./arkts-new-observedV2-and-trace.md)和[@Trace](./arkts-new-observedV2-and-trace.md)装饰的类对象实例具备深度观测属性变化的能力。在`@ComponentV2`装饰的自定义组件中，当调用全局Builder或局部Builder且使用值传递的方式传递参数时，修改`@Trace`装饰的对象属性可以触发UI刷新。
<!-- @[builder_function_combined_with_the_v2_decorator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/BuilderComponent/entry/src/main/ets/pages/BuilderCombined.ets) -->
示例效果图

![arkts-builder-usage-scenario6](figures/arkts-builder-usage-scenario6.gif)

当通过引用传递方式向`@Builder`传递参数时，若参数为`@Local`装饰的对象，对该对象进行整体赋值会触发`@Builder`中UI刷新。

<!-- @[builder_function_combined_with_the_v2_decorator_and_local](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/BuilderComponent/entry/src/main/ets/pages/BuilderCombinedLocal.ets) -->
示例效果图

![arkts-builder-usage-scenario8](figures/arkts-builder-usage-scenario8.gif)

### 跨组件复用的全局\@Builder

在跨组件的场景中调用全局\@Builder，通过按引用传递的方式传递参数，可以实现UI的动态刷新功能。

<!-- @[global_builder_reused_across_components](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/BuilderComponent/entry/src/main/ets/pages/AcrossComponents.ets) -->
示例效果图

![arkts-builder-usage-scenario7](figures/arkts-builder-usage-scenario7.gif)

### \@Builder支持状态变量刷新

从API version 20开始，开发者可以通过使用`UIUtils.makeBinding()`函数、`Binding`类和`MutableBinding`类实现\@Builder函数中状态变量的刷新。详情请参考[状态管理API文档](../../reference/apis-arkui/js-apis-StateManagement.md#makebinding20)。

<!-- @[builder_supports_state_variable_refresh](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/BuilderComponent/entry/src/main/ets/pages/BuilderSupports.ets) -->
示例效果图

![arkts-builder-refresh](figures/arkts-builder-refresh.gif)

## 常见问题

### @Builder存在两个或两个以上参数

当存在两个或两个以上的参数时，即使通过对象字面量形式传递，值的改变也不会触发UI刷新。

【反例】

<!-- @[multiple_parameters_in_builder_incorrect_usage_1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/BuilderComponent/entry/src/main/ets/pages/MultipleIncorrectUsage1.ets) -->

【反例】

<!-- @[multiple_parameters_in_builder_incorrect_usage_2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/BuilderComponent/entry/src/main/ets/pages/MultipleIncorrectUsage2.ets) -->

\@Builder只接受一个参数。当传入一个参数的时候，通过对象字面量的形式传递，值的改变会引起UI的刷新。

【正例】

<!-- @[multiple_parameters_in_builder_correct_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/BuilderComponent/entry/src/main/ets/pages/MultipleCorrectUsage.ets) -->

### 使用@ComponentV2装饰器触发动态刷新

在@ComponentV2装饰的组件中，配合@ObservedV2和@Trace装饰器，通过按值传递实现UI刷新功能。

【反例】

在@ComponentV2装饰的自定义组件中，使用简单数据类型不可以触发UI的刷新。

<!-- @[dynamic_rerendering_with_component_v2_incorrect_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/BuilderComponent/entry/src/main/ets/pages/DynamicIncorrectUsage.ets) -->

【正例】

在@ComponentV2装饰器装饰的自定义组件中，只有使用@ObservedV2装饰的ParamTmpClass类和使用@Trace装饰的count属性才能触发UI刷新。

<!-- @[dynamic_rerendering_with_component_v2_correct_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/BuilderComponent/entry/src/main/ets/pages/DynamicCorrectUsage.ets) -->

### 在\@Builder内创建自定义组件传递参数不刷新问题

在parentBuilder1函数中创建自定义组件HelloComponent1，传递参数为class对象并修改对象内的值时，UI不会触发刷新功能。

【反例】

<!-- @[builder_parameter_update_propagation_incorrect_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/BuilderComponent/entry/src/main/ets/pages/BuilderIncorrectUsage.ets) -->

在parentBuilder2函数中创建自定义组件HelloComponent2，传递参数为对象字面量形式并修改对象内的值时，UI触发刷新功能。

【正例】

<!-- @[builder_parameter_update_propagation_correct_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/BuilderComponent/entry/src/main/ets/pages/BuilderCorrectUsage.ets) -->

### 在UI语句外调用\@Builder函数或方法影响节点正常刷新

当\@Builder方法赋值给变量或者数组后，在UI方法中无法使用，且会造成刷新时节点显示异常。

【反例】
<!-- @[calling_builder_outside_incorrect_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/BuilderComponent/entry/src/main/ets/pages/OutsideIncorrectUsage.ets) -->
\@Builder方法赋值给变量或数组后在UI方法中无法使用，开发者应避免将\@Builder赋值给变量或数组后再使用。

【正例】
<!-- @[calling_builder_outside_correct_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/BuilderComponent/entry/src/main/ets/pages/OutsideCorrectUsage.ets) -->

### 在\@Builder方法中使用MutableBinding未传递set访问器

\@Builder方法定义时使用MutableBinding，构造时没有给MutableBinding类型参数传递set访问器，触发set访问器会造成运行时错误。

【反例】
<!-- @[not_passed_set_accessor_builder_incorrect_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/BuilderComponent/entry/src/main/ets/pages/AccessorIncorrectUsage.ets) -->
MutableBinding的使用规格详见[状态管理API文档](../../reference/apis-arkui/js-apis-StateManagement.md#mutablebindingt20)。

【正例】
<!-- @[not_passed_set_accessor_builder_correct_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/BuilderComponent/entry/src/main/ets/pages/AccessorCorrectUsage.ets) -->

### 在\@Builder装饰的函数内部修改入参内容

不使用[MutableBinding](../../reference/apis-arkui/js-apis-StateManagement.md#mutablebindingt20)的情况下，在\@Builder装饰的函数内部修改参数值，修改不会生效且可能造成运行时错误。

【反例】
<!-- @[changing_input_parameters_builder_incorrect_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/BuilderComponent/entry/src/main/ets/pages/ChangingIncorrectUsage.ets) -->
正确使用[MutableBinding](../../reference/apis-arkui/js-apis-StateManagement.md#mutablebindingt20)可以帮助开发者在\@Builder装饰的函数内部修改参数值。

【正例】
<!-- @[changing_input_parameters_builder_correct_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/BuilderComponent/entry/src/main/ets/pages/ChangingCorrectUsage.ets) -->

### 在\@Watch函数中执行\@Builder函数

在\@Watch函数中执行\@Builder函数，会导致UI刷新异常。

【反例】
<!-- @[executing_builder_function_watch_incorrect_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/BuilderComponent/entry/src/main/ets/pages/WatchIncorrectUsage.ets) -->
Button按钮会出现UI异常的情况，开发者需要避免在\@Watch函数中使用\@Builder函数。

【正例】
<!-- @[executing_builder_function_watch_correct_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/BuilderComponent/entry/src/main/ets/pages/WatchCorrectUsage.ets) -->
