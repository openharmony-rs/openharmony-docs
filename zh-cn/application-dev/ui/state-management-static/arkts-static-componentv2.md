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

## 限制

- \@ComponentV2装饰的自定义组件不支持[LocalStorage](./arkts-static-localstorage.md)。
- 无法同时使用\@ComponentV2与\@Component装饰同一个struct结构。
- [\@Entry](./arkts-static-create-component.md#entry)搭配自定义组件装饰器\@ComponentV2使用时，仅接受routeName作为参数。如果\@Entry传入storage或useSharedStorage参数，会编译报错。