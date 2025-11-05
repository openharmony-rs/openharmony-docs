# \@ObjectLink装饰器和\@Observed装饰器：嵌套类对象属性变化

装饰器[\@State](arkts-static-state.md)、[\@PropRef](arkts-static-propref.md)、[\@Link](arkts-static-link.md)、[\@Provide和\@Consume](arkts-static-provide-and-consume.md)仅能观察到第一层的变化，但是在实际应用开发中，应用会根据开发需要，封装自己的数据模型。对于多层嵌套的情况，比如对象数组项class，或者嵌套类，他们的第二层的属性变化是无法观察到的。这就引出了\@Observed和\@ObjectLink装饰器。

## 概述

\@ObjectLink和\@Observed类装饰器用于在涉及嵌套对象或数组的场景中进行双向数据同步：

- 使用new创建被\@Observed装饰的类，可以被观察到属性的变化。

- 子组件中\@ObjectLink装饰器装饰的状态变量用于接收\@Observed装饰的类的实例，和父组件中对应的状态变量建立双向数据绑定。这个实例可以是数组中的被\@Observed装饰的项，或者是class object中的属性，这个属性同样也需要被\@Observed装饰。

- \@Observed用于嵌套类场景中，观察对象类属性变化，要配合自定义组件使用（示例详见[嵌套对象](#嵌套对象)），如果要做数据双向同步，需要搭配\@ObjectLink使用。

在静态上下文中使用时，需要导入装饰器：

```ts
import { ObjectLink, Observed } from '@ohos.arkui.stateManagement';
```

## 装饰器说明

| \@Observed类装饰器 | 说明                                |
| -------------- | --------------------------------- |
| 装饰器参数          | 无。                                 |
| 使用方式           | 装饰class。需要放在class的定义前，使用new创建类对象。 |

| \@ObjectLink变量装饰器 | 说明                                       |
| ----------------- | ---------------------------------------- |
| 装饰器参数             | 无。                                       |
| 允许装饰的变量类型         | 必须为class类型或interface字面量类型，其中未被\@Observed装饰的class类型无法被观测。<br/>\@ObjectLink不支持简单类型，如果开发者需要使用简单类型，可以使用\@PropRef。<br/>\@Observed装饰类和undefined或null组成的联合类型，比如ClassA \| ClassB, ClassA \| undefined 或者 ClassA \| null, 示例见[@ObjectLink支持联合类型](#objectlink支持联合类型)。|
| 初始化规则         | 不允许定义本地默认值。<br/>初始化\@ObjectLink装饰的变量必须同时满足以下场景：<br/>-&nbsp;类型必须是\@Observed装饰的class。<br/>-&nbsp;初始化的数值需要是数组项，或者class的属性。<br/>-&nbsp;同步源的class或者数组必须是\@State，\@Link，\@Provide，\@Consume或者\@ObjectLink装饰的数据。<br/>初始化的class的示例请参考[嵌套对象](#嵌套对象)。                                     |
| 同步规则           | **在子组件使用时：**<br/>与父组件中的源对象双向同步。<br/>**在父组件使用时：**<br/>可以初始化子组件的常规变量、[\@State](arkts-static-state.md)、[\@Link](arkts-static-link.md)、[\@PropRef](arkts-static-propref.md)、[\@Provide](arkts-static-provide-and-consume.md)。|

```ts
// 允许@ObjectLink装饰的数据属性赋值
this.objLink.a= ...
// 不允许@ObjectLink装饰的数据自身赋值
this.objLink= ...
```

> **说明：**
>
> \@ObjectLink装饰的变量不能被赋值，如果要使用赋值操作，请使用@PropRef。

## 观察变化和行为表现


### 观察变化

当使用\@Observed装饰一个类时，如果该类的属性为非内置类型(非Array/Map/Set/Date)的Object类型，则该熟悉的类也必须被\@Observed装饰，否则改属性内部的变化将无法被观察到。


```ts
'use static'

import { Observed } from '@ohos.arkui.statemanagement';

class Child {
  public num: number;

  constructor(num: number) {
    this.num = num;
  }
}

@Observed
class Parent {
  public child: Child;
  public count: number;

  constructor(child: Child, count: number) {
    this.child = child;
    this.count = count;
  }
}
```

以上示例中，Parent被\@Observed装饰，其成员变量的赋值的变化是可以被观察到的，但对于Child，没有被\@Observed装饰，其属性的修改不能被观察到。


```ts
@ObjectLink parent: Parent;

// 赋值变化可以被观察到
this.parent.child = new Child(5);
this.parent.count = 5;

// Child没有被@Observed装饰，其属性的变化观察不到
this.parent.child.num = 5;
```

\@ObjectLink：\@ObjectLink只能接收被\@Observed装饰class的实例，推荐设计单独的自定义组件来渲染每一个数组或对象。此时，对象数组或嵌套对象（属性是对象的对象称为嵌套对象）需要两个自定义组件，一个自定义组件呈现外部数组/对象，另一个自定义组件呈现嵌套在数组/对象内的类对象。可以观察到：

- 其属性的数值的变化，其中属性是指Object.keys(observedObject)返回的所有属性，示例请参考[嵌套对象](#嵌套对象)。

- 如果数据源是数组，则可以观察到数组item的替换，如果数据源是class，可观察到class的属性的变化，示例请参考[对象数组](#对象数组)。

## 限制条件

1. \@ObjectLink装饰器不能在\@Entry装饰的自定义组件中使用。

2. \@ObjectLink装饰的变量必须是class类型或interface字面量类型，否则会有编译时报错。

3. \@ObjectLink装饰的变量必须要指定类型，否则会有编译时报错。

    ```ts
    'use static'

    import { Component, Text } from '@ohos.arkui.component';
    import { ObjectLink, Observed } from '@ohos.arkui.stateManagement';

    @Observed
    class Info {
      count: number;
  
      constructor(count: number) {
        this.count = count;
      }
    }
  
    class Test {
      msg: number;
  
      constructor(msg: number) {
        this.msg = msg;
      }
    }
  
    @Component
    struct Child {
      // 错误写法，count未指定类型，编译报错
      @ObjectLink count;
  
      // 正确写法
      @ObjectLink count: Info;

      build() {
        Text(`${this.count.count}`)
      }
    }
    ```
  
4. \@ObjectLink装饰的变量不能本地初始化，仅能通过构造参数从父组件传入初始值，否则编译时会报错。

    ```ts
    'use static'

    import { Entry, Column, Component, Text } from '@ohos.arkui.component';
    import { State, ObjectLink, Observed } from '@ohos.arkui.stateManagement';

    @Observed
    class Info {
      count: number;
  
      constructor(count: number) {
        this.count = count;
      }
    }
  
    @Component
    struct Child {
      // 错误写法，编译报错
      @ObjectLink count: Info = new Info(10);
  
      // 正确写法
      @ObjectLink count: Info;

      build() {
        Text(`${this.count.count}`)
      }
    }

    @Entry
    @Component
    struct Parent {
      @State info: Info = new Info(0)
      build() {
        Column() {
          // 正确写法：从父组件传入初始值
          Child({count: this.info})
        }
      }
    }
    ```

5. \@ObjectLink装饰的变量是只读的，不能被赋值，否则会有运行时报错提示`Cannot assign to this property because it is readonly`。如果需要对\@ObjectLink装饰的变量进行整体替换，可以在父组件对其进行整体替换。

    【反例】
  
    ```ts
    'use static'

    import { Column, Component, Text, Entry } from '@ohos.arkui.component';
    import { ObjectLink, Observed, State } from '@ohos.arkui.stateManagement';

    @Observed
    class Info {
      count: number;
  
      constructor(count: number) {
        this.count = count;
      }
    }
  
    @Component
    struct Child {
      @ObjectLink num: Info;
  
      build() {
        Column() {
          Text(`num的值: ${this.num.count}`)
            .onClick((e) => {
              // 错误写法，@ObjectLink装饰的变量不能被赋值
              this.num = new Info(10);
            })
        }
      }
    }

    @Entry
    @Component
    struct Parent {
      @State num: Info = new Info(10);
  
      build() {
        Column() {
          Text(`count的值: ${this.num.count}`)
          Child({num: this.num})
        }
      }
    }
    ```
  
    【正例】
  
    ```ts
    'use static'

    import { Button, Column, Component, Text, Entry } from '@ohos.arkui.component';
    import { ObjectLink, Observed, State } from '@ohos.arkui.stateManagement';

    @Observed
    class Info {
      count: number;
  
      constructor(count: number) {
        this.count = count;
      }
    }
  
    @Component
    struct Child {
      @ObjectLink num: Info;
  
      build() {
        Column() {
          Text(`num的值: ${this.num.count}`)
            .onClick((e) => {
              // 正确写法，可以更改@ObjectLink装饰变量的成员属性
              this.num.count = 20;
            })
        }
      }
    }
  
    @Entry
    @Component
    struct Parent {
      @State num: Info = new Info(10);
  
      build() {
        Column() {
          Text(`count的值: ${this.num.count}`)
          Button('click')
            .onClick((e) => {
              // 可以在父组件做整体替换
              this.num = new Info(30);
            })
          Child({num: this.num})
        }
      }
    }
    ```

## 使用场景

### 继承对象

```ts
'use static'

import { Button, Column, CommonMethod, Component, Entry, Text, TextAlign, TextAttribute } from '@ohos.arkui.component';
import { Observed, State } from '@ohos.arkui.stateManagement';

@Observed
class Animal {
  name: string;
  age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}

@Observed
class Dog extends Animal {
  kinds: string;

  constructor(name: string, age: number, kinds: string) {
    super(name, age);
    this.kinds = kinds;
  }
}

function commonStyles(this: TextAttribute): this {
  return this.width(320).margin(10).fontSize(30).textAlign(TextAlign.Center);
}

@Entry
@Component
struct Index {
  @State dog: Dog = new Dog('Molly', 2, 'Husky');

  pressedStyles(instance: CommonMethod) {
    instance.backgroundColor('#ffd5d5d5');
  }

  normalStyles(instance: CommonMethod) {
    instance.backgroundColor('#ffffff');
  }

  build() {
    Column() {
      Text(`${this.dog.name}`)
        .commonStyles()
        .stateStyles({
          pressed: this.pressedStyles,
          normal: this.normalStyles
        })
        .onClick((e) => {
          this.dog.name = 'DouDou';
        })

      Text(`${this.dog.age}`)
        .commonStyles()
        .stateStyles({
          pressed: this.pressedStyles,
          normal: this.normalStyles
        })
        .onClick((e) => {
          this.dog.age = 3;
        })

      Text(`${this.dog.kinds}`)
        .commonStyles()
        .stateStyles({
          pressed: this.pressedStyles,
          normal: this.normalStyles
        })
        .onClick((e) => {
          this.dog.kinds = 'Samoyed';
        })
    }
  }
}
```

上述示例中，Dog类中的部分属性（name、age）继承自Animal类，直接修改\@State装饰的变量dog中的属性name和age可以正常触发UI刷新。

### 嵌套对象

```ts
'use static'

import { Button, Column, Component, Entry, Text, TextAlign } from '@ohos.arkui.component';
import { Observed, ObjectLink, State } from '@ohos.arkui.stateManagement';

@Observed
class Book {
  name: string;

  constructor(name: string) {
    this.name = name;
  }
}

@Observed
class Bag {
  book: Book;

  constructor(book: Book) {
    this.book = book;
  }
}

@Component
struct BookCard {
  @ObjectLink book: Book;

  build() {
    Column() {
      Text(`BookCard: ${this.book.name}`) // 可以观察到name的变化
        .width(320)
        .margin(10)
        .textAlign(TextAlign.Center)

      Button('change book.name')
        .width(320)
        .margin(10)
        .onClick((e) => {
          this.book.name = 'C++';
        })
    }
  }
}

@Entry
@Component
struct Index {
  @State bag: Bag = new Bag(new Book('JS'));

  build() {
    Column() {
      Text(`Index: ${this.bag.book.name}`) // 无法观察到name的变化
        .width(320)
        .margin(10)
        .textAlign(TextAlign.Center)

      Button('change bag.book.name')
        .width(320)
        .margin(10)
        .onClick((e) => {
          this.bag.book.name = 'TS';
        })

      BookCard({ book: this.bag.book })
    }
  }
}
```

上述示例中，Index组件中的Text组件不刷新，因为该变化属于第二层的变化，\@State无法观察到第二层的变化。但是Book被\@Observed装饰，Book的属性name可以被\@ObjectLink观察到，所以无论点击哪个Button，BookCard组件中的Text组件都会刷新。

### 对象数组

对象数组是一种常用的数据结构。以下示例展示了数组对象的用法。

> **说明：**
>
> NextID是用来在ForEach循环渲染过程中，为每个数组元素生成一个唯一且持久的键值，用于标识对应的组件。

```ts
'use static'

import { Button, Column, Component, Entry, ForEach, Row } from '@ohos.arkui.component';
import { ObjectLink, Observed, State } from '@ohos.arkui.stateManagement';

let NextID: number = 1;

@Observed
class Info {
  public id: number;
  public info: number;

  constructor(info: number) {
    this.id = NextID++;
    this.info = info;
  }
}

@Component
struct Child {
  // 子组件Child的@ObjectLink的类型是Info
  @ObjectLink info: Info;
  label: string = 'ViewChild';

  build() {
    Row() {
      Button(`ViewChild [${this.label}] this.info.info = ${this.info ? this.info.info : "undefined"}`)
        .width(320)
        .margin(10)
        .onClick((e) => {
          this.info.info += 1;
        })
    }
  }
}

@Entry
@Component
struct Parent {
  // Parent中有@State装饰的Info[]
  @State arrA: Info[] = [new Info(0), new Info(0)];

  build() {
    Column() {
      ForEach(this.arrA,
        (item: Info) => {
          Child({ label: `#${item.id}`, info: item })
        },
        (item: Info): string => item.id.toString()
      )
      // 使用@State装饰的数组的数组项初始化@ObjectLink，其中数组项是被@Observed装饰的Info的实例
      Child({ label: `ViewChild this.arrA[first]`, info: this.arrA[0] })
      Child({ label: `ViewChild this.arrA[last]`, info: this.arrA[this.arrA.length-1] })

      Button(`ViewParent: reset array`)
        .width(320)
        .margin(10)
        .onClick((e) => {
          this.arrA = [new Info(0), new Info(0)];
        })
      Button(`ViewParent: push`)
        .width(320)
        .margin(10)
        .onClick((e) => {
          this.arrA.push(new Info(0));
        })
      Button(`ViewParent: shift`)
        .width(320)
        .margin(10)
        .onClick((e) => {
          if (this.arrA.length > 0) {
            this.arrA.shift();
          } else {
            console.info("length <= 0");
          }
        })
      Button(`ViewParent: item property in middle`)
        .width(320)
        .margin(10)
        .onClick((e) => {
          this.arrA[Math.floor(this.arrA.length / 2) as int].info = 10;
        })
      Button(`ViewParent: item property in middle`)
        .width(320)
        .margin(10)
        .onClick((e) => {
          this.arrA[Math.floor(this.arrA.length / 2) as int] = new Info(11);
        })
    }
  }
}
```


- this.arrA[Math.floor(this.arrA.length/2)] = new Info(..) ：该状态变量的改变触发2次更新：
  1. ForEach：数组项的赋值导致ForEach的itemGenerator被修改，因此数组项被识别为有更改，ForEach的item builder将执行，创建新的Child组件实例。
  2. Child({ label: `ViewChild this.arrA[last]`, info: this.arrA[this.arrA.length-1] })：上述更改改变了数组中第二个元素，所以绑定this.arrA[1]的Child将被更新。

- this.arrA.push(new Info(0)) ： 将触发2次不同效果的更新：
  1. ForEach：新添加的Info对象对于ForEach是未知的itemGenerator，ForEach的item builder将执行，创建新的Child组件实例。
  2. Child({ label: `ViewChild this.arrA[last]`, info: this.arrA[this.arrA.length-1] })：数组的最后一项有更改，因此引起第二个Child的实例的更改。对于Child({ label: `ViewChild this.arrA[first]`, info: this.arrA[0] })，数组的更改并没有触发一个数组项更改的改变，所以第一个Child不会刷新。

- this.arrA[Math.floor(this.arrA.length/2)].info：@State无法观察到第二层的变化，但是Info被\@Observed装饰，Info的属性的变化将被\@ObjectLink观察到。

### 序列化和反序列化

使用无参构造函数的@Observed装饰的类可以使用JSON.stringify序列化和JSON.parse反序列化。

使用有参构造函数的@Observed装饰的类可以使用JSON.stringify进行序列化，但在反序列化时，需要先使用JSON.parseJsonElement创建JsonElement实例，并且需要开发者实现从JsonElement实例到@Observed装饰类的转换。

**无参构造**

```ts
'use static'

import { Entry, Text, Column, Component, Button } from '@ohos.arkui.component';
import { State, Observed } from '@ohos.arkui.stateManagement';

@Observed
class Source {
  public source: int = 123;
}

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';
  @State source: Source = new Source();

  build() {
    Column() {
      Text(`Source ${this.source.source} and message ${this.message}`)
      Button('+1')
        .onClick((e) => {
          this.source.source += 1;
        })
      Button('Serialize')
        .onClick((e) => {
          this.message = JSON.stringify(this.source);
        })
      Button('Deserialize')
        .onClick((e) => {
          // 反序列化生成@Observed类并赋值
          this.source = JSON.parse<Source>('{"source": 123}', Type.from<Source>())!;
        })
    }
  }
}
```

**有参构造**

```ts
'use static'

import { Entry, Text, Column, Component, Button } from '@ohos.arkui.component'
import { State, Observed } from '@ohos.arkui.stateManagement'

@Observed
class Source {
  public source: int;

  constructor(s: int) {
    // 有参构造
    this.source = s;
  }

  // 用户自定义静态函数
  static FromJSON(e: jsonx.JsonElement): Source {
    return new Source(e.getInteger('source'))
  }
}

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';
  @State source: Source = new Source(1);

  build() {
    Column() {
      Text(`Source ${this.source.source} and message ${this.message}`)
      Button('+1')
        .onClick((e) => {
          this.source.source += 1;
        })
      Button('Serialize')
        .onClick((e) => {
          this.message = JSON.stringify(this.source);
        })
      Button('Deserialize')
        .onClick((e) => {
          // 使用JSON.parseJsonElement反序列生成JSONElement，再传入静态方法构建实例
          this.source = Source.FromJSON(JSON.parseJsonElement('{"source": 123}'))!;
        })
    }
  }
}
```

## ObjectLink支持联合类型

\@ObjectLink支持\@Observed装饰类和undefined或null组成的联合类型，在下面的示例中，count类型为Source | Data | undefined，点击父组件Parent中的Button改变count的属性或者类型，Child中也会对应刷新。

```ts
'use static'

import { Button, Column, Component, Entry, Text } from '@ohos.arkui.component';
import { ObjectLink, Observed, State } from '@ohos.arkui.stateManagement';

@Observed
class Source {
  public source: number;

  constructor(source: number) {
    this.source = source;
  }
}

@Observed
class Data {
  public data: number;

  constructor(data: number) {
    this.data = data;
  }
}

@Entry
@Component
struct Parent {
  @State count: Source | Data | undefined = new Source(10);

  build() {
    Column() {
      Child({ count: this.count })

      Button('change count property')
        .margin(10)
        .onClick((e) => {
          // 判断count的类型，做属性的更新
          if (this.count instanceof Source) {
            (this.count as Source).source += 1;
          } else if (this.count instanceof Data) {
            (this.count as Data).data += 1;
          } else {
            console.info('count is undefined, cannot change property');
          }
        })

      Button('change count to Source')
        .margin(10)
        .onClick((e) => {
          // 赋值为Source的实例
          this.count = new Source(100);
        })

      Button('change count to Data')
        .margin(10)
        .onClick((e) => {
          // 赋值为Data的实例
          this.count = new Data(100);
        })

      Button('change count to undefined')
        .margin(10)
        .onClick((e) => {
          // 赋值为undefined
          this.count = undefined;
        })
    }.width('100%')
  }
}

@Component
struct Child {
  @ObjectLink count: Source | Data | undefined;

  build() {
    Column() {
      Text(`count is instanceof ${this.count instanceof Source ? 'Source' :
        this.count instanceof Data ? 'Data' : 'undefined'}`)
        .fontSize(30)
        .margin(10)

      Text(`count's property is  ${this.count instanceof Source ? (this.count as Source).source :
        (this.count as Data | undefined)?.data}`).fontSize(15)

    }.width('100%')
  }
}
```