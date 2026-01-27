# \@ComponentV2装饰器：自定义组件

为了在自定义组件中使用V2版本状态变量装饰器的能力，开发者可以使用\@ComponentV2装饰器装饰自定义组件。

\@ComponentV2主要配合状态管理V2使用。

## 概述

### \@ComponentV2

\@ComponentV2装饰器用于装饰自定义组件：

- 在\@ComponentV2装饰的自定义组件中，开发者仅可以使用全新的状态变量装饰器，包括[\@Local](./arkts-static-new-local.md)、[\@Param](./arkts-static-new-param.md)、[\@Once](./arkts-static-new-once.md)、[\@Event](./arkts-static-new-event.md)、[\@Provider、\@Consumer](./arkts-static-new-provider-and-consumer.md)。



- 一个简单的\@ComponentV2装饰的自定义组件应具有以下部分：

    ```ts
    'use static'
    
    import { Entry, ComponentV2, Local } from '@kit.ArkUI';
    
    @ComponentV2 // 装饰器
    struct Index { // struct声明的数据结构
      @Local local: number = 1; // 声明为@Local的装饰器变量
      build() { // build定义的UI
      }
    }
    ```

除非特别说明，\@ComponentV2装饰的自定义组件将与\@Component装饰的自定义组件保持相同的行为。

## 支持自定义组件扩展

从API version 23开始，开发者可以在自定义组件中重写通用属性的方法，并使用`super`关键字调用基类的通用属性的方法。当使用“.”链式调用自定义组件方法时，需注意以下事项：
1. 实现链式调用的关键是：每个方法必须返回`this`，以允许连续调用。如果某个方法未返回`this`，则无法作为链式调用的中间步骤，导致后续调用无法解析，从而引发编译错误。
2. 通过链式调用的方法，其调用时机是在创建自定义组件时，所以在方法内，不能改变关联其他组件或方法的状态变量，否则会有运行时报错。

示例如下。

```typescript
'use static'

import { Text, Entry, Color, ComponentV2, ResourceColor, Column, ColorMetrics } from '@kit.ArkUI';
import { Provider, Consumer, Local } from '@kit.ArkUI';
import hilog from '@ohos.hilog';

@ComponentV2
struct ChildComponent {
  @Consumer() message: string = 'default';
  @Local info: string = 'default';

  // override关键字可缺省
  override backgroundColor(value: ResourceColor | ColorMetrics | undefined): this {
    hilog.info(0X0000, 'testTag', `override backgroundColor`);
    // this.message = 'Change'; // 运行时报错，禁止在构建组件树的过程中修改有依赖的状态变量
    this.info = 'Change'; // 正常运行，可以在构建组件树的过程中修改没有依赖的状态变量
    super.backgroundColor(Color.Pink); // 背景颜色显示为粉色，开发者可以选择不调用基类的backgroundColor方法，即不设置背景颜色
    return this;
  }

  // overload
  backgroundColor(value: Array<number>): this {
    hilog.info(0X0000, 'testTag', `overload backgroundColor`);
    return this;
  }

  // myStyle没有返回this，仅可以在链式调用的最后一项被调用
  myStyle(): void {
    hilog.info(0X0000, 'testTag', `myStyle`);
  }

  build() {
    Column() {
      Text(`ChildComponent info ${this.info}`)
      Text(`ChildComponent message ${this.message}`)
    }
  }
}

@Entry
@ComponentV2
struct MyComponent {
  @Provider() message: string = 'Hello World';

  build() {
    Column() {
      Text(`MyComponent message ${this.message}`)

      ChildComponent()
        .width(300)
        .height(300)
        .backgroundColor(Color.Red)
        .backgroundColor([0])
        .myStyle()
    }
    .height(500)
    .width(300)
  }
}
```

## 限制

- \@ComponentV2装饰的自定义组件不支持[LocalStorage](./arkts-static-localstorage.md)。
- 无法同时使用\@ComponentV2与\@Component装饰同一个struct结构。
- [\@Entry](./arkts-static-create-component.md#entry)搭配自定义组件装饰器\@ComponentV2使用时，仅接受routeName作为参数。如果\@Entry传入storage或useSharedStorage参数，会编译报错。