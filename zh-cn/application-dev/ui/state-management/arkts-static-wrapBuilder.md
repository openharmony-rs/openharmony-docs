# wrapBuilder：封装全局@Builder（ArkTS-Sta）

  当在一个struct内使用多个全局@Builder函数实现UI的不同效果时，代码维护将变得非常困难，且页面不够整洁。此时，可以使用wrapBuilder封装全局@Builder。

  在阅读本文档前，建议提前阅读：[\@Builder](./arkts-builder.md)。

> **说明：**
>
> 从API version 22开始使用。

> **说明：**
>
> 在ArkTS-Sta中，可以将@Builder函数赋值给一个用@Builder装饰的函数类型的变量，参考[\@Builder: 用变量存储@Builder函数](./arkts-builder.md#用变量存储builder函数仅适用于arkts-sta上下文)

## 导入模块

```js
import { WrappedBuilder, wrapBuilder } from '@kit.ArkUI';
```

## 接口说明

wrapBuilder是一个模板函数，返回一个`WrappedBuilder`对象。

```ts
declare function wrapBuilder<T>(builder: T): WrappedBuilder<T>;
```

同时 `WrappedBuilder`对象也是一个模板类。

```ts
declare class WrappedBuilder<T> {
  builder: T;

  constructor(builder: T);
}
```

> **说明：**
>
> 模板参数`T`是需要包装的builder函数的类型声明。

使用方法：

```ts
let builderVar: WrappedBuilder<@Builder (p1: string, p2: number) => void> = wrapBuilder(MyBuilder)
let builderArr: WrappedBuilder<@Builder (p1: string, p2: number) => void>[] = [wrapBuilder(MyBuilder)] //可以放入数组
```

## 限制条件

1. wrapBuilder方法只能传入[全局\@Builder](arkts-builder.md#全局自定义构建函数)方法。

2. WrappedBuilder对象的builder属性方法仅限在struct内部使用。

## @Builder方法赋值给变量

使用`@Builder`装饰器装饰的方法`MyBuilder`作为`wrapBuilder`的参数，再将`wrapBuilder`函数的返回值赋值给变量`globalBuilder`，以解决`@Builder`方法赋值给变量后无法使用的问题。

```ts
'use static'

import { Builder, Component, Column, Entry, Row, Text, WrappedBuilder, wrapBuilder, State } from '@kit.ArkUI';

@Builder
function MyBuilder(value: string, size: number) {
  Text(value)
    .fontSize(size)
}

// 使用wrapBuilder封装@Builder函数
let globalBuilder: WrappedBuilder<@Builder (p1: string, p2: number) => void> = wrapBuilder(MyBuilder);

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    Row() {
      Column() {
        //使用WrappedBuilder类builder属性方法构建UI组件
        globalBuilder.builder(this.message, 50)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

示例效果图：

![arkts-sta-wrapbuilder.png](../figures/arkts-sta-wrapbuilder.png)

##  @Builder方法赋值给变量在UI语法中使用

自定义组件Index使用`ForEach`进行不同`@Builder`函数的渲染，可以使用`builderArr`声明的`wrapBuilder`数组来实现不同的`@Builder`函数效果。整体代码会更加整洁。

```ts
'use static'

import { Builder, Color, Column, Component, Entry, ForEach, Row, Text, WrappedBuilder, wrapBuilder, State } from '@kit.ArkUI';

@Builder
function MyBuilder(value: string, size: number) {
  Text(value)
    .fontSize(size)
}

@Builder
function YourBuilder(value: string, size: number) {
  Text(value)
    .fontSize(size)
    .fontColor(Color.Pink)
}

// 使用wrapBuilder封装@Builder函数列表，包含的@Builder函数需要有相同的签名
const builderArr: WrappedBuilder<@Builder (p1: string, p2: number) => void>[] = [wrapBuilder(MyBuilder), wrapBuilder(YourBuilder)];


@Entry
@Component
struct Index {
  @Builder 
  testBuilder() {
    // 使用ForEach展开WrappedBuilder列表
    ForEach(builderArr, (item: WrappedBuilder<@Builder (p1: string, p2: number) => void>) => {
      item.builder('Hello World', 30)
    })
  }

  build() {
    Row() {
      Column() {
        this.testBuilder()
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

示例效果图：

![arkts-sta-wrapbuilder-foreach.png](../figures/arkts-sta-wrapbuilder-foreach.png)

## 引用传递

按引用传递参数时，传递的状态变量的改变会引起@Builder方法内的UI刷新。

```ts
'use static'

import { Builder, Button, ClickEvent, Column, Component, Entry, Text, WrappedBuilder, wrapBuilder, Observed, State } from '@kit.ArkUI';

interface Tmp {
  paramA2: string;
}

@Builder 
function overBuilder(param: Tmp) {
  Column() {
    Text(`wrapBuilder value: ${param.paramA2}`)
  }.width('100%')
}

const wBuilder: WrappedBuilder<@Builder (param: Tmp) => void> = wrapBuilder(overBuilder);

@Entry
@Component
struct Parent{
  @State label: string = 'Hello';
  build() {
    Column() {
      wBuilder.builder({ paramA2: this.label })
      Button('Click me')
        .onClick(() => {
          this.label += '!';
        })
    }.width('100%')
  }
}
```

示例效果图：

![arkts-sta-wrapbuilder-reference.gif](../figures/arkts-sta-wrapbuilder-reference.gif)

## 动态切换

使用wrapBuilder封装全局@Builder，实现全局@Builder的动态切换。

```ts
'use static'

import { Builder, Button, Column, ComponentV2, Entry, Text, WrappedBuilder, wrapBuilder, Local } from '@kit.ArkUI';

class TextContent {
  text: string = '';
}

@Builder
function textBuilder(p: TextContent) {
  Text(p.text)
    .margin(31)
}

@Builder
function buttonBuilder(p: TextContent) {
  Button(p.text)
    .margin(20)
}

let counter: number = 1;
@Entry
@ComponentV2
struct MyApp {
  @Local message: string = '';
  @Local switchingBuilder: WrappedBuilder<@Builder (p: TextContent) => void> = wrapBuilder(textBuilder);
  build() {
    Column() {
      Button('Click to change')
        .onClick(() => {
          counter++; // 每次点击按钮修改counter来动态改变全局@Builder
          if(counter % 2 === 0) {
            this.message += 'Hello';
            this.switchingBuilder = wrapBuilder(buttonBuilder); // textBuilder--->buttonBuilder
          } else {
            this.message += 'World';
            this.switchingBuilder = wrapBuilder(textBuilder); // buttonBuilder--->textBuilder
          }
        })
        this.switchingBuilder.builder({ text: this.message })
    }
    .position({x: 120, y: 60})
  }
}
```

示例效果图：

![dynamic-switch](../figures/dynamic-switch.gif)


