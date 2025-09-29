# 创建自定义组件

在ArkUI中，UI显示的内容均为组件，框架直接提供的称为系统组件，开发者定义的称为自定义组件。进行UI界面开发时，需组合使用系统组件，确保代码的可复用性、业务逻辑与UI的分离，以及后续版本的演进。因此，将UI和部分业务逻辑封装成自定义组件是必需的。此外，自定义组件需要通过import才能使用，而动态自定义组件则不需要。

自定义组件具有以下特点：

- 可组合：允许开发者组合使用系统组件及其属性和方法。

- 可重用：自定义组件可以被其他组件重用，并作为不同的实例在不同的父组件或容器中使用。

- 数据驱动UI更新：通过状态变量的改变，来驱动UI的刷新。

## 自定义组件的基本用法

以下示例展示了自定义组件的基本用法。

```typescript
'use static'

import { Text, Entry, Column, Component, ClickEvent } from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';

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

import { Text, Entry, Column, Component, Divider, ClickEvent } from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';
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
  import { Component } from '@ohos.arkui.component';
  @Component
  struct MyComponent {
  }
  ```

  ### \@ComponentV2

[@ComponentV2](./arkts-static-componentv2.md)主要配合状态管理V2使用。除非特别说明，自定义组件使用@ComponentV2装饰后将与@Component装饰的组件保持相同的行为。

  > **说明：**
  >
  >
  > - 在\@ComponentV2装饰的自定义组件中，开发者仅可以使用全新的状态变量装饰器，包括[\@Local](arkts-static-new-local.md)、[\@Param](arkts-static-new-param.md)、[\@Once](arkts-static-new-once.md)、[\@Event](arkts-static-new-event.md)等。
  >
  > - \@ComponentV2装饰的自定义组件暂不支持LocalStorage等现有能力。
  >
  > - 无法同时用\@ComponentV2与\@Component装饰同一个struct。
  
 
一个简单的\@ComponentV2装饰的自定义组件应包含以下部分：
  ```typescript
  'use static'

  //  @ComponentV2装饰器需要import。
  import { ComponentV2, Button } from '@ohos.arkui.component';
  @ComponentV2
  struct MyComponent {
  }
  ```

### build()函数
build()函数用于定义自定义组件的声明式UI描述，自定义组件必须实现build()函数。

  ```typescript
  'use static'

  import {Component, Button } from '@ohos.arkui.component';
  @Component
  struct MyComponent {
    build() {
    }
  }
  ```
### \@Entry

@Entry装饰的自定义组件是UI页面的入口。每个UI页面只能有一个@Entry装饰的组件。@Entry可接受一个可选的 [LocalStorage](arkts-static-localstorage.md) 参数。
 
  ```typescript
  'use static'

  import { Entry, Component } from '@ohos.arkui.component';
  @Entry
  @Component
  struct MyComponent {
  }
  ```

## 成员函数/变量

自定义组件可包含成员变量或成员函数， 如果声明的成员函数或变量是私有的， 不可将成员函数或成员变量声明为静态的。

## 自定义组件的参数规定

下面示例中，开发者可以在build方法里创建静态自定义组件，并在创建过程中根据装饰器的规则来初始化自定义组件的参数。

```typescript
'use static'

import { Text, Entry, Column, Component, Color } from '@ohos.arkui.component';
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

  import { Text, Entry, Component, Row } from '@ohos.arkui.component';

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
## build()函数支持写非UI的逻辑

`build()`函数支持编写非 UI 逻辑，如变量声明、`switch/case` 语句和打印日志。但是，不能执行耗时操作，否则会阻塞 UI 主线程，影响应用界面的渲染性能。
### 推荐用法

**在build()根节点中进行变量声明**

```typescript
  'use static'

  import { Entry, Text, Column, Component } from '@ohos.arkui.component';

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

import { Entry, Text, Column, Component, Button, ClickEvent } from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';
import hilog from '@ohos.hilog';

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

import { Entry, Text, Column, Component, Button, ClickEvent } from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';

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

import { Text, Entry, Component } from '@ohos.arkui.component';

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

import { Entry, Text, Column, Component, ClickEvent } from '@ohos.arkui.component'
import { State } from '@ohos.arkui.stateManagement'
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


### 不推荐用法

**在 build() 函数中调用耗时的同步接口示例**

在build()函数中，不建议编写非UI逻辑，如调用剪切板接口[getDataSync](../../../application-dev/reference/apis-basic-services-kit/js-apis-pasteboard.md)获取剪切板数据或执行for循环等。这些操作会增加构建时间，影响UI性能。

```typescript
'use static'

import { Text, Entry, Column, Component } from "@ohos.arkui.component";
import { State } from "@ohos.arkui.stateManagement";
import pasteboard from '@ohos.pasteboard';
import { BusinessError } from "@kit.BasicServicesKit";

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

import { Text, Entry, Column, Component } from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';

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
**在build()过程中不建议修改状态变量**

```typescript
'use static'

import { Text, Entry, Column, Button, Component, Color, ClickEvent } from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';

@Entry
@Component
struct MyComponent {
  @State textColor: Color = Color.Yellow;
  @State columnColor: Color = Color.Green;
  @State count: number = 1;
  build() {
    Column() {
      // 应避免直接在Text组件内改变count的值
      Text(`${this.count++}`) // 不建议在build过程修改状态变量，渲染异常
        .width(50)
        .height(50)
        .fontColor(this.textColor)
        .onClick((e: ClickEvent) => {
          this.columnColor = Color.Red;
        })
      Button("change textColor").onClick((e: ClickEvent) =>{
        this.textColor = Color.Pink;
      })
    }
    .backgroundColor(this.columnColor)
  }
}
```
  > **说明：**
  >
  > 在 `build()` 过程中修改 `this.count`，会导致页面渲染异常。

