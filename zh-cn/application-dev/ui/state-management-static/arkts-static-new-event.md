# \@Event装饰器：规范组件输出

开发者可以使用\@Event装饰器实现子组件向父组件要求更新\@Param装饰变量的能力。

使用\@Event装饰回调方法是一种规范，表明子组件需要传入更新数据源的回调。

## 概述

\@Param装饰的变量在本地无法更改，而使用\@Event装饰器装饰回调方法并进行调用，可以实现更改数据源的变量，再通过\@Local的同步机制，将修改同步回\@Param，以此达到主动更新\@Param装饰变量的效果。

\@Event用于装饰组件的输出方法：

- \@Event装饰的回调方法中参数以及返回值由开发者决定。
- \@Event装饰非回调类型的变量不会生效。
- **在静态语言上下文中，当\@Event没有本地初始化时，不会生成空的函数作为默认回调，需要开发者提供外部传入值或本地初始值。当同时存在外部传入值和本地默认值时，优先使用外部传入的函数进行处理。**

\@Param标志着组件的输入，表明该变量受父组件影响，而\@Event标志着组件的输出，可以通过该方法影响父组件。使用\@Event装饰回调方法是一种规范，表明该回调作为自定义组件的输出。父组件需要判断是否提供对应方法用于子组件更改\@Param变量的数据源。

在静态语言上下文中使用时，需导入装饰器：

```ts
import { Event } from '@ohos.arkui.stateManagement';
```

## 装饰器说明

| \@Event属性装饰器 | 说明 |
| ------------------- | ------------------------------------------------------------ |
| 装饰器参数 | 无。 |
| 允许装饰的变量类型 | 回调方法，例如() => void、(x: number) => boolean等。<br/>回调方法是否含有参数以及返回值由开发者决定。 |
| 初始化规则 | - 必须提供外部传入值或本地初始值。<br/>- 当\@Event没有本地初始化时，不会生成空的函数作为默认回调。<br/>- 当同时存在外部传入值和本地默认值时，优先使用外部传入的函数进行处理。 |

## 限制条件

\@Event只能用在\@ComponentV2装饰的自定义组件中。当装饰非方法类型的变量时，不会有任何作用。

```ts
@ComponentV2
struct Index {
  @Event changeFactory: () => void = () => {}; //正确用法
  @Event message: string = 'abcd'; // 错误用法，装饰非函数类型变量，@Event无作用
}
@Component
struct Index {
  @Event changeFactory: () => void = () => {}; // 错误用法，编译时报错
}
```

## 使用场景

### 更改父组件中变量

使用\@Event可以修改父组件中变量，当该变量作为子组件\@Param变量的数据源时，该变化将同步更新到子组件的\@Param变量。

```ts
'use static'

import { Entry, ComponentV2, Column, Text, Button, ClickEvent, Color } from '@ohos.arkui.component';
import { Local, Param, Event } from '@ohos.arkui.stateManagement';

@Entry
@ComponentV2
struct Index {
  @Local title: string = 'Title One';
  @Local fontColor: Color = Color.Red;

  build() {
    Column() {
      Child({
        title: this.title,
        fontColor: this.fontColor,
        changeFactory: (type: number) => {
          if (type == 1) {
            this.title = 'Title One';
            this.fontColor = Color.Red;
          } else if (type == 2) {
            this.title = 'Title Two';
            this.fontColor = Color.Green;
          }
        }
      })
    }
  }
}

@ComponentV2
struct Child {
  @Param title: string = '';
  @Param fontColor: Color = Color.Black;
  @Event changeFactory: (x: number) => void = (x: number) => {};

  build() {
    Column() {
      Text(`${this.title}`)
        .fontColor(this.fontColor)
      Button('change to Title Two')
        .onClick((e: ClickEvent) => {
          this.changeFactory(2);
        })
      Button('change to Title One')
        .onClick((e: ClickEvent) => {
          this.changeFactory(1);
        })
    }
  }
}
```

值得注意的是，使用\@Event修改父组件的值是立刻生效的，但从父组件将变化同步回子组件的过程是异步的，即在调用完\@Event的方法后，子组件内的值不会立刻修改。这是因为\@Event将子组件值实际的变化能力交由父组件处理，在父组件实际决定如何处理后，将最终值在渲染之前同步回子组件。

```ts
'use static'

import { Entry, ComponentV2, Column, Text, ClickEvent } from '@ohos.arkui.component';
import { Local, Param, Event } from '@ohos.arkui.stateManagement';

@ComponentV2
struct Child {
  @Param index: number = 0;
  @Event changeIndex: (val: number) => void;

  build() {
    Column() {
      Text(`Child index: ${this.index}`)
        .onClick((e: ClickEvent) => {
          this.changeIndex(20);
          console.info(`after changeIndex ${this.index}`);
        })
    }
  }
}
@Entry
@ComponentV2
struct Index {
  @Local index: number = 0;

  build() {
    Column() {
      Child({
        index: this.index,
        changeIndex: (val: number) => {
          this.index = val;
          console.info(`in changeIndex ${this.index}`);
        }
      })
    }
  }
}
```

在上述示例中，点击文字触发\@Event回调方法改变子组件的值，打印出的日志为：

```
in changeIndex 20
after changeIndex 0
```

这表明在调用changeIndex之后，父组件的index值已变化，但子组件的index值还没有同步变化。