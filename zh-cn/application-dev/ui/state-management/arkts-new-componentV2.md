# \@ComponentV2装饰器：自定义组件
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiyujia926-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

为了在自定义组件中使用V2版本状态变量装饰器的能力，开发者可以使用\@ComponentV2装饰器装饰自定义组件。

\@ComponentV2主要配合状态管理V2使用。阅读本文档前，建议提前阅读[状态管理概述](./arkts-state-management-overview.md)。

>**说明：**
>
> \@ComponentV2装饰器从API version 12开始支持。
>
> 从API version 12开始，该装饰器支持在原子化服务中使用。


## 概述

和[\@Component装饰器](arkts-create-custom-components.md#component)一样，\@ComponentV2装饰器用于装饰自定义组件：

- 在\@ComponentV2装饰的自定义组件中，开发者仅可以使用全新的状态变量装饰器，包括[\@Local](arkts-new-local.md)、[\@Param](arkts-new-param.md)、[\@Once](arkts-new-once.md)、[\@Event](arkts-new-event.md)、[\@Provider](arkts-new-Provider-and-Consumer.md)、[\@Consumer](arkts-new-Provider-and-Consumer.md)等。
- \@ComponentV2装饰的自定义组件暂不支持[LocalStorage](arkts-localstorage.md)等现有自定义组件的能力。
- 无法同时使用\@ComponentV2与\@Component装饰同一个struct结构。
- \@ComponentV2支持一个可选的boolean类型参数freezeWhenInactive，来实现[组件冻结功能](arkts-custom-components-freezeV2.md)。

- 一个简单的\@ComponentV2装饰的自定义组件应具有以下部分：


    <!-- @[ComponentV2_page_componentV2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/wrapbuilder/entry/src/main/ets/pages/PageComponentV2.ets) -->
    
    ``` TypeScript
    @Entry
    @ComponentV2 // 装饰器
    struct ComponentV2Test { // struct声明的数据结构
      @Local message: string = 'Hello World';
      build() { // build定义的UI
        RelativeContainer() {
          Text(this.message)
            .id('HelloWorld')
            // $r('app.float.page_text_font_size')需要替换为开发者所需的资源文件;
            .fontSize($r('app.float.page_text_font_size'))
            .fontWeight(FontWeight.Bold)
            .alignRules({
              center: { anchor: '__container__', align: VerticalAlign.Center },
              middle: { anchor: '__container__', align: HorizontalAlign.Center }
            })
            .onClick(() => {
              this.message = 'Welcome';
            })
        }
        .height('100%')
        .width('100%')
      }
    }
    ```


除非特别说明，\@ComponentV2装饰的自定义组件将与\@Component装饰的自定义组件保持相同的行为。

## 限制条件

在将\@Component装饰的自定义组件与\@ComponentV2装饰的自定义组件混合使用时，可参考[混用文档](./arkts-custom-component-mixed-scenarios.md)。
