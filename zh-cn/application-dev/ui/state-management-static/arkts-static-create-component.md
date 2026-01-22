# \@Component装饰器: 自定义组件

在ArkUI中，UI显示的内容均为组件，框架直接提供的称为系统组件，开发者定义的称为自定义组件。进行UI界面开发时，需组合使用系统组件，确保代码的可复用性、业务逻辑与UI的分离，以及后续版本的演进。因此，将UI和部分业务逻辑封装成自定义组件是必需的。此外，自定义组件需要通过import才能使用，而动态自定义组件则不需要。

自定义组件具有以下特点：

- 可组合：允许开发者组合使用系统组件及其属性和方法。

- 可重用：自定义组件可以被其他组件重用，并作为不同的实例在不同的父组件或容器中使用。

- 数据驱动UI更新：通过状态变量的改变，来驱动UI的刷新。

## 自定义组件的基本用法

以下示例展示了自定义组件的基本用法。

```typescript
'use static'

import { Text, Entry, Column, Component, ClickEvent } from '@kit.ArkUI';
import { State } from '@kit.ArkUI';

@Component
struct HelloComponent {
  @State message: string = 'Hello, World!';

  build() {
    // HelloComponent自定义组件组合系统组件Row和Text
    Column() {
      Text(this.message)
        .onClick((e: ClickEvent) => {
          this.message = 'Hello, ArkUI!';
        })
    }
  }
}
```
> **说明：**
>
> 如果在其他文件中引用自定义组件，需要使用`export`关键字导出组件，并在页面中使用`import`语句导入该组件。

在其他自定义组件的`build()`函数中多次创建`HelloComponent`实例，可以实现自定义组件的重用。

```typescript
'use static'

import { Text, Entry, Column, Component, Divider, ClickEvent } from '@kit.ArkUI';
import { State } from '@kit.ArkUI';
@Entry
@Component
struct ParentComponent {
  build() {
    Column() {
      Text('ArkUI message')
      HelloComponent({ message: 'Hello World!' });
      Divider()
      HelloComponent({ message: '你好，世界!' });
    }
  }
}
```

要完全理解上面的示例，需要了解自定义组件的以下概念定义，本文将在后面的小节中介绍：

- [自定义组件的基本结构](#自定义组件的基本结构)

- [成员函数/变量](#成员函数变量)

- [自定义组件的参数规定](#自定义组件的参数规定)

- [build()函数](#build函数)


## 自定义组件的基本结构

### struct

自定义组件通过 `struct` 实现，由自定义组件名及大括号内的内容构成，不允许有继承关系。实例化 `struct` 时可省略 `new`。

  > **说明：**
  >
  > 自定义组件名、类名、函数名不能与系统组件名重复。

### \@Component

struct被\@Component装饰后具备组件化能力，需实现build方法描述UI。每个struct仅能被一个\@Component装饰。

  ```typescript
  'use static'

  // @Component装饰器需要import。
  import { Component } from '@kit.ArkUI';
  @Component
  struct MyComponent {
  }
  ```

### build()函数
build()函数用于定义自定义组件的声明式UI描述，自定义组件必须实现build()函数。

  ```typescript
  'use static'

  import {Component, Button } from '@kit.ArkUI';
  @Component
  struct MyComponent {
    build() {
    }
  }
  ```
### \@Entry

\@Entry装饰的自定义组件是UI页面的入口。每个UI页面只能有一个@Entry装饰的组件。\@Entry搭配自定义组件装饰器\@Component使用时，可以接受的参数如下表所示。

| 参数名   | 类型   | 必填 | 说明                                                           |
| ------ | ------ | ------------------------------------------------------------- | ------------------------------------------------------------- |
| routeName | string | 否 | 表示作为命名路由页面的名字。 |
| storage | string | 否 | 返回[LocalStorage](../state-management/arkts-localstorage.md)实例对象的函数名。 |
| useSharedStorage | boolean | 否 | 是否使用UIContext.getSharedLocalStorage()接口返回的共享的[LocalStorage](../state-management/arkts-localstorage.md)实例对象，默认值false。<br>true表示使用共享的[LocalStorage](../state-management/arkts-localstorage.md)实例对象。<br>false表示不使用共享的[LocalStorage](../state-management/arkts-localstorage.md)实例对象。 |


```ts
'use static'

import { Component, Entry } from '@kit.ArkUI';
import { LocalStorage } from '@kit.ArkUI';

const myStorage: () => LocalStorage = () => new LocalStorage();

@Entry({routeName: 'myPage', storage: 'myStorage', useSharedStorage: false})
@Component
struct MyComponent {
  build() {
  }
}
```

## 成员函数/变量

自定义组件可包含成员变量或成员函数， 如果声明的成员函数或变量是私有的， 不可将成员函数或成员变量声明为静态的。

## 自定义组件的参数规定

下面示例中，开发者可以在build方法里创建静态自定义组件，并在创建过程中根据装饰器的规则来初始化自定义组件的参数。

```typescript
'use static'

import { Text, Entry, Column, Component, Color } from '@kit.ArkUI';
@Component
struct MyComponent {
  private countDownFrom: number = 0;
  private color: Color = Color.Blue;

  build() {
  }
}

@Entry
@Component
struct ParentComponent {
  private someColor: Color = Color.Pink;

  build() {
    Column() {
      // 创建MyComponent实例，并将成员变量countDownFrom初始化为10，将成员变量color初始化为this.someColor。
      MyComponent({ countDownFrom: 10, color: this.someColor })
    }
  }
}
```
## build()

在 `build()` 函数中声明的所有语句统称为UI描述，这些描述需遵循以下规则：

-  @Entry装饰的自定义组件，其build()函数下的根节点是容器组件，并且必须和唯一存在。ForEach不能作为根节点。
- 使用 `@Component` 或 `@ComponentV2` 装饰的自定义组件，其`build()` 函数下的根节点必须唯一且必要，可以是非容器组件，但 `ForEach` 不能作为根节点。

```typescript
  'use static'

  import { Text, Entry, Component, Row } from '@kit.ArkUI';

  @Entry
  @Component
  struct MyComponent {
    build() {
      // 根节点唯一且必要，必须为容器组件
      Row() {
        ChildComponent()
      }
    }
  }

  @Component
  struct ChildComponent {
    build() {
      // 根节点唯一且必要，可为非容器组件
      Text('Hello world')
    }
  }
```
### build()函数支持写非UI的逻辑

`build()`函数支持编写非 UI 逻辑，如变量声明、`switch/case` 语句和打印日志。但是，不能执行耗时操作，否则会阻塞 UI 主线程，影响应用界面的渲染性能。
**建议用法**

**在build()根节点中进行变量声明**

```typescript
  'use static'

  import { Entry, Text, Column, Component } from '@kit.ArkUI';

  @Entry
  @Component
  struct MyStateSample {
    build() {
      Column() {
        let num: int = 1; // 在build()根节点中进行变量声明
        Text('show text1')
      }
      .width('100%')
      .height('100%')
    }
  }
```

**在build()根节点中添加日志打印**

```typescript
'use static'

import { Entry, Text, Column, Component, Button, ClickEvent } from '@kit.ArkUI';
import { State } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct MyStateSample {
  @State stateVar: int = 1;

  build() {
    Column() {
      hilog.info(0X0000, 'testTag', `${this.stateVar}`); // 在build()根节点中打印日志
      Text('show text1')
      Button('change stateVar')
        .onClick((e: ClickEvent) => {
          this.stateVar = (this.stateVar + 1) % 4;
        })
    }
    .width('100%')
    .height('100%')
  }
}
```


**在build()函数中使用switch/case结构**

```typescript
'use static'

import { Entry, Text, Column, Component, Button, ClickEvent } from '@kit.ArkUI';
import { State } from '@kit.ArkUI';

@Entry
@Component
struct MyStateSample {
  @State stateVar: int = 1;

  build() {
    Column() {
      switch(this.stateVar) {
        case 1:
          Text('show text1')
          break;  // 不加break会执行下一个case分支
        case 2:
          Text('show text2');
          break;
        default:
          Text('show default');
          break;
      }
      Button('change stateVar')
        .onClick((e: ClickEvent) => {
          this.stateVar = (this.stateVar + 1) % 4;
        })
    }
    .width('100%')
    .height('100%')
  }
}
```
  > **说明：**
  >
  > 上述 `switch` 示例包含两个 `case` 分支和一个 `default` 分支。当 `condition` 满足某个 `case` 分支的常量表达式时，执行对应的 `case` 分支。如果所有 `case` 分支都不匹配，则执行 `default` 分支。


**允许创建本地的作用域**

```typescript
'use static'

import { Text, Entry, Component } from '@kit.ArkUI';

@Entry
@Component
struct MyComponent {
  build() {
    {  // 允许本地作用域
      Text('hello world')
    }
  }
}
```

**允许使用表达式**

```typescript
'use static'

import { Entry, Text, Column, Component, ClickEvent } from '@kit.ArkUI';
import { State } from '@kit.ArkUI';
@Entry
@Component
struct MyComponent {
  @State stateVar: int = 1;
  build() {
    Column() {
      this.stateVar == 1 ? Text('is equal to 1'): Text('is not euqal to 1'); // 支持使用表达式
      Text('hello world')
        .onClick((e: ClickEvent) => {
          this.stateVar++;
        })
    }
  }
}

```
  > **说明：**
  >
  > 上述代码中，通过三元表达式，也能实现条件渲染。


**不建议用法**

**在 build() 函数中调用耗时的同步接口示例**

在build()函数中，不建议编写非UI逻辑，如调用剪切板接口[getDataSync](../../../application-dev/reference/apis-basic-services-kit/js-apis-pasteboard.md)获取剪切板数据或执行for循环等。这些操作会增加构建时间，影响UI性能。

```typescript
'use static'

import { Text, Entry, Column, Component, State } from '@kit.ArkUI';
import pasteboard from '@ohos.pasteboard';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct MyStateSample {
  @State stateVar: string = 'testPasteBoard';

  build() {
    let systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
    try {
      let result: pasteboard.PasteData = systemPasteboard.getDataSync(); // 获取通过同步接口获取剪切板数据，不推荐
    } catch (err: BusinessError) {
      console.error('Failed to get PasteData, Cause:' + err.message);
    }
    Column() {
      Text(this.stateVar)
    }
    .width('100%')
    .height('100%')
  }
}
```

**在组件中编写复杂的计算逻辑**

```typescript
'use static'

import { Text, Entry, Column, Component } from '@kit.ArkUI';
import { State } from '@kit.ArkUI';

@Entry
@Component
struct MyStateSample {
  @State stateVar: string = 'hello';

  build() {
    let sum: int = 0;
    for(let i = 0; i < 100000; i++) {
      sum += i * i; // 在build中执行复杂的计算逻辑
    }
    Column() {
      Text(this.stateVar)
    }
    .width('100%')
    .height('100%')
  }
}
```
### 在build()过程中不允许修改状态变量

不允许在`build()`函数的UI组件中改变状态变量的值，否则编译时会提示报错。
```typescript
'use static'

import { Text, Entry, Column, Button, Component, Color, ClickEvent } from '@kit.ArkUI';
import { State } from '@kit.ArkUI';

@Entry
@Component
struct MyComponent {
  @State textColor: Color = Color.Yellow;
  @State columnColor: Color = Color.Green;
  @State count: number = 1;
  build() {
    Column() {
      // 不允许在build过程修改状态变量，编译时报错
      Text(`${this.count++}`)
        .width(50)
        .height(50)
        .fontColor(this.textColor)
        .onClick((e: ClickEvent) => {
          this.columnColor = Color.Red;
        })
      Button('change textColor')
        .onClick((e: ClickEvent) => {
          this.textColor = Color.Pink;
        })
    }
    .backgroundColor(this.columnColor)
  }
}
```

## 自定义组件通用样式

自定义组件通过“.”链式调用设置通用样式。

```typescript
'use static'

import { Button, Entry, Row, Color, Component } from '@kit.ArkUI';

@Component
struct ChildComponent {
  build() {
    Button(`Hello World`)
  }
}

@Entry
@Component
struct MyComponent {
  build() {
    Row() {
      ChildComponent()
        .width(200)
        .height(300)
        .backgroundColor(Color.Red)
    }
  }
}
```
在ArkUI中，给自定义组件设置样式时，实际上是将样式应用到一个不可见的容器组件上，而不是直接应用到ChildComponent的Button组件上。因此，背景颜色红色会显示在Button所在的不可见容器组件上。