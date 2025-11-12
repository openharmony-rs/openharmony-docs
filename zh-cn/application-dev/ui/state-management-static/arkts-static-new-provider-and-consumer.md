# \@Provider装饰器和\@Consumer装饰器：跨组件层级双向同步

\@Provider和\@Consumer用于跨组件层级数据双向同步，方便开发者不用拘泥于组件层级。

## 概述

\@Provider，即数据提供方，其所有的子组件都可以通过\@Consumer绑定相同的key来获取\@Provider提供的数据。

\@Consumer，即数据消费方，可以通过绑定同样的key获取其最近父节点的\@Provider的数据，当查找不到\@Provider的数据时，使用本地默认值。

\@Provider和\@Consumer装饰的数据类型需要一致。

在静态语言上下文中使用时，需导入装饰器：

```ts
import { Provider, Consumer } from '@ohos.arkui.stateManagement';
```

## \@Provider/\@Consumer与\@Provide/\@Consume能力对比
在状态管理V1版本中，提供跨组件层级双向的装饰器为[\@Provide和\@Consume](./arkts-static-provide-and-consume.md)，当前文档介绍的是状态管理V2装饰器\@Provider和\@Consumer。虽然两者名字和功能类似，但在特性上还存在一些差异。
如果开发者不了解状态管理V1中的\@Provide和\@Consume，可以直接跳过本节。

| 能力 | V2装饰器\@Provider和\@Consumer                                             |V1装饰器\@Provide和\@Consume|
| ------------------ | ----------------------------------------------------- |----------------------------------------------------- |
| \@Consume(r)         |需要本地初始化，当找不到\@Provider的时候使用本地默认值。| 禁止本地初始化，当找不到对应的\@Provide时候，会抛出异常。 |
| 支持类型           | 支持function。 | 不支持function。 |
| 观察能力           | 仅能观察自身赋值变化，如果要观察嵌套场景，配合\@Trace一起使用。 | 观察第一层变化，如果要观察嵌套场景，配合\@Observed和\@ObjectLink一起使用。 |
| alias和属性名         | alias是唯一匹配的key，缺省时默认属性名为alias。 | alias和属性名都为key，优先匹配alias，匹配不到可以匹配属性名。|
| \@Provide(r) 从父组件初始化      | 不允许。 | 允许。|
| \@Provide(r)支持重载  | 默认开启，即\@Provider可以重名，\@Consumer向上查找最近的\@Provider。 | 默认关闭，即在组件树上不允许有同名\@Provide。如果需要重载，则需要配置allowOverride。|

## 装饰器说明

### 基本规则
\@Provider语法：

```
@Provider(alias?: string) varName: varType = initValue;
@Provider varName: varType = initValue;
@Provider({alias?: string}) varName: varType = initValue;
```

| \@Provider属性装饰器 | 说明                                                  |
| ------------------ | ----------------------------------------------------- |
| 装饰器参数         | `alias?: string`，别名，常量字符串，可选。<br/>如果指定了别名，则通过别名来绑定变量；如果未指定别名，则通过变量名绑定变量。<br/>默认允许重写，即可以存在同名的\@Provider变量。 |
| 允许装饰的变量类型 | - 支持Object、class、number、string、boolean、enum、interface等基本类型。<br/>- 支持[Array](#装饰数组类型变量)、[Date](#装饰date类型变量)、[Map](#装饰map类型变量)、[Set](#装饰set类型变量)等内嵌类型。<br/>- 支持null、undefined以及联合类型。 |
| 初始化规则 | 必须本地初始化，不支持从父组件传入初始化。 |
| 同步规则      | **在子组件使用时：**<br/>\@Provider装饰的变量仅允许本地初始化，不允许从外部传入初始化。<br/>**在父组件使用时：**<br/>- 可以初始化子组件中\@Param装饰的变量。<br/>- 与后代子组件中别名匹配的@Consumer变量双向同步。 |

\@Consumer语法：

```
@Consumer(alias?: string) varName: varType = initValue;
@Consumer varName: varType = initValue;
@Consumer({alias?: string}) varName: varType = initValue;
```

| \@Consumer属性装饰器 | 说明                                                         |
| --------------------- | ------------------------------------------------------------ |
| 装饰器参数            | `alias?: string`，别名，常量字符串，可选。<br/>如果指定了别名，则通过别名向上查找最近的\@Provider；如果未指定别名，则通过变量名绑定\@Provider。 |
| 允许装饰的变量类型 | - 支持Object、class、number、string、boolean、enum、interface等基本类型。<br/>- 支持Array、Date、Map、Set等内嵌类型。<br/>- 支持null、undefined以及联合类型。 |
| 初始化规则   | 必须本地初始化，不支持从父组件传入初始化。 |
| 同步规则    | **在子组件使用时：**<br/>与祖先组件匹配的\@Provider变量双向同步。<br/>**在父组件使用时：**<br/>可以初始化子组件中\@Param装饰的变量。 |

### alias和属性名

\@Provider和\@Consumer接受可选参数alias，没有配置参数时，使用属性名作为默认的alias。

>**说明：**
>
> alias是用于\@Provider和\@Consumer进行匹配的唯一指定key。

\@Provider和\@Consumer使用alias进行查找匹配，示例如下。

**示例1：**

```ts
@ComponentV2
struct Parent {
  // 未定义别名，使用属性名'str'
  @Provider() str: string = 'hello';
}

@ComponentV2
struct Child {
  // 定义别名为'str'，使用别名去寻找
  // 能够在Parent组件上找到，使用@Provider的值'hello'
  @Consumer('str') str: string = 'world';
}
```

**示例2：**

```ts
@ComponentV2
struct Parent {
  // 定义别名为'alias'
  @Provider('alias') str: string = 'hello';
}

@ComponentV2 
struct Child {
  // 定义别名为'alias'，找到@Provider并获得值'hello'
  @Consumer('alias') str: string = 'world';
}
```

**示例3：**

```ts
@ComponentV2
struct Parent {
  // 定义别名为'alias'
  @Provider('alias') str: string = 'hello';
}

@ComponentV2
struct Child {
  // 未定义别名，使用属性名'str'
  // 没有找到对应的@Provider，使用本地值'world'
  @Consumer() str: string = 'world';
}
```

## 使用限制

1. \@Provider和\@Consumer为自定义组件的属性装饰器，只能装饰自定义组件内的属性，不能装饰class的属性。

   ```ts
   'use static'
   
   import { Entry, ComponentV2 } from '@ohos.arkui.component';
   import { Provider, Consumer } from '@ohos.arkui.stateManagement';
   
   @Provider // 错误用法
   class Info {
     name: string;
   
     constructor(name: string) {
       this.name = name;
     }
   }
   
   @Entry
   @ComponentV2
   struct Parent {
     @Provider() message: string = 'Hello World'; // 正确用法
     build() {
     }
   }
   
   @ComponentV2
   struct Child {
     @Consumer() message: string = 'Hello World'; // 正确用法
     build() {
     }
   }
   ```

2. \@Provider和\@Consumer为状态管理V2装饰器，只能在\@ComponentV2中使用，不能在\@Component中使用。

   ```ts
   'use static'
   
   import { Entry, Component, ComponentV2 } from '@ohos.arkui.component';
   import { Provider, Consumer } from '@ohos.arkui.stateManagement';
   
   @Entry
   @ComponentV2
   struct Parent {
     @Provider() message: string = 'Hello World'; // 正确用法
     build() {
     }
   }
   
   @ComponentV2
   struct Child {
     @Consumer() message: string = 'Hello World'; // 正确用法
     build() {
     }
   }
   
   @Component
   struct Test {
     @Provider() message: string = 'Hello World'; // 错误用法，编译时报错
     build() {
     }
   }
   ```

3. \@Provider和\@Consumer只支持本地初始化，不支持外部传入初始化。

   ```ts
   'use static'
   
   import { Entry, ComponentV2, Column } from '@ohos.arkui.component';
   import { Provider, Consumer } from '@ohos.arkui.stateManagement';
   
   @ComponentV2
   struct ProviderComponent {
     @Provider() message: string = 'Hello World';
     build() {
     }
   }
   
   @ComponentV2
   struct ConsumerComponent {
     @Consumer() message: string = 'Hello World';
     build() {
     }
   }
   
   @Entry
   @ComponentV2
   struct MyComponent {
     build() {
       Column() {
         ProviderComponent({ message: 'Hello' }) // 错误用法，编译时报错
         ConsumerComponent({ message: 'Hello' }) // 错误用法，编译时报错
       }
     }
   }
   ```

## 使用场景

### \@Provider和\@Consumer双向同步
**建立双向绑定**

1. 自定义组件Parent和Child初始化。
    - Child中`@Consumer() str: string = 'world'`向上查找，查找到Parent中声明的`@Provider() str: string = 'hello'`。
    - `@Consumer() str: string = 'world'`初始化为其查找到的`@Provider`的值，即‘hello’。
    - 两者建立双向同步关系。
2. 点击Parent中的Button，改变\@Provider装饰的str，通知其对应的\@Consumer，刷新对应UI组件。
3. 点击Child中Button，改变\@Consumer装饰的str，通知其对应的\@Provider，刷新对应UI组件。

```ts
'use static'

import { Entry, ComponentV2, Column, Button, ClickEvent } from '@ohos.arkui.component';
import { Provider, Consumer } from '@ohos.arkui.stateManagement';

@Entry
@ComponentV2
struct Parent {
  @Provider() str: string = 'hello';

  build() {
    Column() {
      Button(this.str)
        .onClick((e: ClickEvent) => {
          this.str += '0';
        })
      Child()
    }
  }
}

@ComponentV2
struct Child {
  // @Consumer装饰的属性str和Parent组件中@Provider装饰的属性str名称相同，因此建立了双向绑定关系
  @Consumer() str: string = 'world';

  build() {
    Column() {
      Button(this.str)
        .onClick((e: ClickEvent) => {
          this.str += '0';
        })
    }
  }
}
```
**未建立双向绑定**

以下示例中，由于别名不同，\@Provider和\@Consumer无法建立双向同步关系。
1. 自定义组件Parent和Child初始化。
    - Child中`@Consumer() str: string = 'world'`向上查找，未查找到其数据提供方@Provider。
    - `@Consumer() str: string = 'world'`使用其本地默认值为‘world’。
    - 两者未建立双向同步关系。
2. 点击Parent中的Button，改变\@Provider装饰的str1，仅刷新\@Provider关联的Button组件。
3. 点击Child中Button，改变\@Consumer装饰的str，仅刷新\@Consumer关联的Button组件。

```ts
'use static'

import { Entry, ComponentV2, Column, Button, ClickEvent } from '@ohos.arkui.component';
import { Provider, Consumer } from '@ohos.arkui.stateManagement';

@Entry
@ComponentV2
struct Parent {
  @Provider() str1: string = 'hello';

  build() {
    Column() {
      Button(this.str1)
        .onClick((e: ClickEvent) => {
          this.str1 += '0';
        })
      Child()
    }
  }
}

@ComponentV2
struct Child {
  // @Consumer装饰的属性str和Parent组件中@Provider装饰的属性str1名称不同，无法建立双向绑定关系
  @Consumer() str: string = 'world';

  build() {
    Column() {
      Button(this.str)
        .onClick((e: ClickEvent) => {
          this.str += '0';
        })
    }
  }
}
```

### 装饰字面量类型变量

当装饰interface字面量类型时，仅可以观察到字面量整体的变化，无法观察到属性的变化，可以使用[makeObserved接口](./arkts-static-new-makeObserved.md)实现对字面量属性的观察。

```ts
'use static'

import { Entry, ComponentV2, Column, Text, Button, ClickEvent } from '@ohos.arkui.component';
import { Provider, Consumer } from '@ohos.arkui.stateManagement';

interface Info {
  name: string;
}

@Entry
@ComponentV2
struct Parent {
  // 装饰字面量
  @Provider() info: Info = { name: 'Bob' } as Info;
  build() {
    Column() {
      Text(`parent name: ${this.info.name}`)
      Button('parent change whole interface')
        .onClick((e: ClickEvent) => {
          this.info = { name: 'Tom' } as Info; // 变化可观察
        })
      Button('parent change interface name')
        .onClick((e: ClickEvent) => {
          this.info.name += '~'; // 变化无法观察
        })
      Child()
    }
  }
}

@ComponentV2
struct Child {
  // 装饰字面量
  @Consumer() info: Info = { name: 'Mary' } as Info;
  build() {
    Column() {
      Text(`child name: ${this.info.name}`)
      Button('child change whole interface')
        .onClick((e: ClickEvent) => {
          this.info = { name: 'Jerry' } as Info; // 变化可观察
        })
      Button('child change interface name')
        .onClick((e: ClickEvent) => {
          this.info.name += '*'; // 变化无法观察
        })
    }
  }
}
```

### 装饰数组类型变量

当装饰数组时，可以观察到数组整体和数组项的变化，同时可以通过调用Array的接口`push`、`pop`、`shift`、`unshift`、`splice`、`copyWithin`、`fill`、`reverse`、`sort`更新Array的数据。

```ts
'use static'

import { Entry, ComponentV2, Column, Button, ClickEvent, ForEach, Text } from '@ohos.arkui.component';
import { Provider, Consumer } from '@ohos.arkui.stateManagement';

@ComponentV2
struct Child {
  @Consumer() arr: number[] = [6.0, 7.0, 8.0];

  build() {
    Column() {
      Button('child change arr item')
        .onClick((e: ClickEvent) => {
          this.arr[0]++;
          this.arr[1] += 2;
        })
      Button('child reverse arr')
        .onClick((e: ClickEvent) => {
          this.arr.reverse();
        })
    }
  }
}

@Entry
@ComponentV2
struct Parent {
  @Provider() arr: number[] = [1.0, 2.0, 3.0];

  build() {
    Column() {
      ForEach(this.arr,
        (item: number) => {
          Text(`${item}`)
        })
      Button('parent change whole arr')
        .onClick((e: ClickEvent) => {
          this.arr = [100, 200, 300];
        })
      Button('parent push new item')
        .onClick((e: ClickEvent) => {
          this.arr.push(111);
        })
      Child()
    }
  }
}
```

### 装饰Date类型变量

当装饰Date类型变量时，可以观察到数据源对Date整体的赋值，以及调用Date的接口`setFullYear`, `setMonth`, `setDate`, `setHours`, `setMinutes`, `setSeconds`, `setMilliseconds`, `setTime`, `setUTCFullYear`, `setUTCMonth`, `setUTCDate`, `setUTCHours`, `setUTCMinutes`, `setUTCSeconds`, `setUTCMilliseconds`带来的变化。

```ts
'use static'

import { Entry, ComponentV2, Column, Button, ClickEvent, Text } from '@ohos.arkui.component';
import { Provider, Consumer } from '@ohos.arkui.stateManagement';

@Entry
@ComponentV2
struct Parent {
  @Provider() SelectedDate: Date = new Date('2021-08-08');

  build() {
    Column() {
      Text(`parent: ${this.SelectedDate}`)
      Button('parent update the new date')
        .onClick((e: ClickEvent) => {
          this.SelectedDate = new Date('2023-07-07');
        })
      Button('parent increase the year by 1')
        .onClick((e: ClickEvent) => {
          this.SelectedDate.setFullYear(this.SelectedDate.getFullYear() + 1);
        })
      Child()
    }
  }
}
@ComponentV2
struct Child {
  @Consumer() SelectedDate: Date = new Date('2022-07-07');

  build() {
    Column() {
      Text(`child: ${this.SelectedDate}`)
      Button('child update the new date')
        .onClick((e: ClickEvent) => {
          this.SelectedDate = new Date('2025-01-01');
        })
      Button('child increase the month by 1')
        .onClick((e: ClickEvent) => {
          this.SelectedDate.setMonth(this.SelectedDate.getMonth() + 1);
        })
      Button('child increase the day by 1')
        .onClick((e: ClickEvent) => {
          this.SelectedDate.setDate(this.SelectedDate.getDate() + 1);
        })
    }
  }
}
```

### 装饰Map类型变量

当装饰Map类型变量时，可以观察到数据源对Map整体的赋值，以及调用Map的接口`set`、`clear`、`delete`带来的变化。

```ts
'use static'

import { Entry, ComponentV2, Column, Button, ClickEvent, ForEach, Text, Divider } from '@ohos.arkui.component';
import { Provider, Consumer } from '@ohos.arkui.stateManagement';

@Entry
@ComponentV2
struct Parent {
  @Provider() message: Map<number, string> = new Map<number, string>([[0, 'a'], [1, 'b'], [2, 'c']]);

  build() {
    Column() {
      ForEach(Array.from(this.message.entries()), (item: [number, string]) => {
        Text(`${item[0]}`).fontSize(30)
        Text(`${item[1]}`).fontSize(30)
        Divider()
      })
      Button('parent init map').onClick((e: ClickEvent) => {
        this.message = new Map<number, string>([[0, 'aa'], [1, 'bb'], [2, 'cc']]);
      })
      Button('parent set new one').onClick((e: ClickEvent) => {
        this.message.set(4, 'd');
      })
      Button('clear').onClick((e: ClickEvent) => {
        this.message.clear();
      })
      Child()
    }
  }
}
@ComponentV2
struct Child {
  @Consumer() message: Map<number, string> = new Map<number, string>([[0, 'd'], [1, 'e'], [2, 'f']]);

  build() {
    Column() {
      Button('child init map').onClick((e: ClickEvent) => {
        this.message = new Map<number, string>([[0, 'dd'], [1, 'ee'], [2, 'ff']]);
      })
      Button('child replace the first one').onClick((e: ClickEvent) => {
        this.message.set(0, 'a*');
      })
      Button('child delete the first one').onClick((e: ClickEvent) => {
        this.message.delete(0);
      })
    }
  }
}
```

### 装饰Set类型变量

当装饰Set类型变量时，可以观察到数据源对Set整体的赋值，以及调用Set的接口`add`、`clear`、`delete`带来的变化。

```ts
'use static'

import { Entry, ComponentV2, Column, Button, ClickEvent, ForEach, Text, Divider } from '@ohos.arkui.component';
import { Provider, Consumer } from '@ohos.arkui.stateManagement';

@Entry
@ComponentV2
struct Parent {
  @Provider() message: Set<number> = new Set<number>([1, 2, 3, 4]);

  build() {
    Column() {
      ForEach(Array.from(this.message.entries()), (item: [number, number]) => {
        Text(`${item[0]}`).fontSize(30)
        Divider()
      })
      Button('parent init set').onClick((e: ClickEvent) => {
        this.message = new Set<number>([1, 2, 3, 4]);
      })
      Button('parent set new one').onClick((e: ClickEvent) => {
        this.message.add(5);
      })
      Child()
    }
  }
}
@ComponentV2
struct Child {
  @Consumer() message: Set<number> = new Set<number>([1, 2, 3, 4, 5, 6]);

  build() {
    Column() {
      Button('child init set').onClick((e: ClickEvent) => {
        this.message = new Set<number>([1, 2, 3, 4, 5, 6]);
      })
      Button('child clear').onClick((e: ClickEvent) => {
        this.message.clear();
      })
      Button('child delete the first one').onClick((e: ClickEvent) => {
        this.message.delete(1);
      })
    }
  }
}
```

### \@Provider和\@Consumer装饰箭头函数

\@Provider和\@Consumer支持装饰箭头函数。

```ts
'use static'

import { Entry, ComponentV2, Column, Button, ClickEvent, Text } from '@ohos.arkui.component';
import { Provider, Consumer, Local } from '@ohos.arkui.stateManagement';

@Entry
@ComponentV2
struct Parent {
  @Local childSub: number = 0;
  @Local childSum: number = 1;
  @Provider() onChange: (x: number, y: number) => void = (x: number, y: number): void => {
    this.childSub = x - y;
    this.childSum = x + y;
  }

  build() {
    Column() {
      Text(`childSub: ${this.childSub}, childSum: ${this.childSum}`)
      Child()
    }
  }
}

@ComponentV2
struct Child {
  @Local x: number = 0;
  @Local y: number = 1;
  @Consumer() onChange: (x: number, y: number) => void = (x: number, y: number): void => {};

  build() {
    Button('changed')
      .onClick((e: ClickEvent) => {
        this.onChange(this.x, this.y);
      })
  }
}
```

### \@Provider和\@Consumer装饰复杂类型

1. \@Provider和\@Consumer仅能观察到数据本身的变化。若需观察其装饰的复杂数据类型的属性变化，必须配合\@Trace一起使用。
2. 装饰内置类型Array、Map、Set、Date时，可以观察到某些API的变化，观察能力同\@Trace。

```ts
'use static'

import { Entry, ComponentV2, Column, Button, ClickEvent, Text, ForEach, Divider } from '@ohos.arkui.component';
import { Provider, Consumer, ObservedV2, Trace } from '@ohos.arkui.stateManagement';

@ObservedV2
class User {
  @Trace name: string;
  @Trace age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}
const data: User[] = [new User('Json', 10), new User('Eric', 15)];
@Entry
@ComponentV2
struct Parent {
  @Provider('data') users: User[] = data;

  build() {
    Column() {
      Child()
      Button('add new user')
        .onClick((e: ClickEvent) => {
          this.users.push(new User('Molly', 18));
        })
      Button('age++')
        .onClick((e: ClickEvent) => {
          this.users[0].age++;
        })
      Button('change name')
        .onClick((e: ClickEvent) => {
          this.users[0].name = 'Shelly';
        })
    }
  }
}

@ComponentV2
struct Child {
  @Consumer('data') users: User[] = [];

  build() {
    Column() {
      ForEach(this.users, (item: User) => {
        Column() {
          Text(`name: ${item.name}`).fontSize(30)
          Text(`age: ${item.age}`).fontSize(30)
          Divider()
        }
      })
    }
  }
}
```

### \@Provider重名时，\@Consumer向上查找其最近的\@Provider

\@Provider可以在组件树上重名，当重名时\@Consumer会向上查找其最近父节点的\@Provider的数据。

```ts
'use static'

import { Entry, ComponentV2, Column, Text } from '@ohos.arkui.component';
import { Provider, Consumer } from '@ohos.arkui.stateManagement';

@Entry
@ComponentV2
struct Index {
  @Provider() val: number = 10;

  build() {
    Column() {
      Parent()
    }
  }
}

@ComponentV2
struct Parent {
  @Provider() val: number = 20;
  @Consumer('val') val2: number = 0; // 10

  build() {
    Column() {
      Text(`${this.val2}`)
      Child()
    }
  }
}

@ComponentV2
struct Child {
  @Consumer() val: number = 0; // 20

  build() {
    Column() {
      Text(`${this.val}`)
    }
  }
}
```

以上示例中：

- Parent中的\@Consumer向上查找，查找到Index中定义的`@Provider() val: number = 10`，初始化为10。
- Child中的\@Consumer向上查找，查找到Parent中定义的`@Provider() val: number = 20`后停止，初始化为20。

### \@Provider和\@Consumer初始化\@Param

- 点击Text(\`Parent @Consumer val: ${this.val}\`)，触发`@Consumer() val`的变化，变化同步给Index中`@Provider() val`，从而触发子组件`Text(Parent @Param val2: ${this.val2})`的刷新。
- `Parent @Consumer() val`的变化同步给Child，从而触发`Text(Child @Param val ${this.val})`的刷新。

```ts
'use static'

import { Entry, ComponentV2, Column, Text, ClickEvent, Color } from '@ohos.arkui.component';
import { Provider, Consumer, Param } from '@ohos.arkui.stateManagement';

@Entry
@ComponentV2
struct Index {
  @Provider() val: number = 10;

  build() {
    Column() {
      Parent({ val2: this.val })
    }
  }
}

@ComponentV2
struct Parent {
  @Consumer() val: number = 0;
  @Param val2: number = 0;

  build() {
    Column() {
      Text(`Parent @Consumer val: ${this.val}`).fontSize(30).onClick((e: ClickEvent) => {
        this.val++;
      })
      Text(`Parent @Param val2: ${this.val2}`).fontSize(30)
      Child({ val: this.val })
    }.border({ width: 2, color: Color.Green })
  }
}

@ComponentV2
struct Child {
  @Param val: number = 0;

  build() {
    Column() {
      Text(`Child @Param val ${this.val}`).fontSize(30)
    }.border({ width: 2, color: Color.Pink })
  }
}
```