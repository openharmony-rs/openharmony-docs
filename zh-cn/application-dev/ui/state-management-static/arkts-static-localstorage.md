# LocalStorage：页面级UI状态存储

LocalStorage是页面级的UI状态存储，通过[\@Entry](./arkts-static-create-component.md#entry)装饰器接收的参数可以在页面内共享同一个LocalStorage实例。LocalStorage支持UIAbility实例内多个页面间状态共享。

本文仅介绍LocalStorage使用场景和相关的装饰器：[\@LocalStoragePropRef](#localstoragepropref)和[\@LocalStorageLink](#localstoragelink)。

在阅读本文档前，建议开发者对状态管理框架有基本的了解。建议提前阅读：[状态管理概述](../state-management/arkts-state-management-overview.md)。

LocalStorage还提供了API接口，可以让开发者通过接口在自定义组件外手动触发Storage对应key的增删改查，建议配合[LocalStorage API文档](../../reference/apis-arkui/arkui-ts/ts-state-management-1.2.md#localstorage9)阅读。

## 概述

LocalStorage是ArkTS为构建页面级别状态变量提供存储的内存内的“数据库”。

- 应用程序可以创建多个LocalStorage实例，LocalStorage实例可以在页面内共享，也可以通过getSharedLocalStorage接口，实现跨页面、跨UIAbility实例共享。

- 组件树的根节点，即被\@Entry装饰的[\@Component](./arkts-static-create-component.md#component)，可以被分配一个LocalStorage实例，此组件的所有子组件实例将自动获得对该LocalStorage实例的访问权限。

- LocalStorage中的所有属性都是可变的。

应用程序决定LocalStorage对象的生命周期。当应用释放最后一个指向LocalStorage的引用时，比如销毁最后一个自定义组件，LocalStorage将被JS Engine垃圾回收。

LocalStorage根据与\@Component装饰的组件的同步类型不同，提供了两个装饰器：

- \@LocalStoragePropRef：\@LocalStoragePropRef装饰的变量与LocalStorage中给定属性建立单向同步关系。

- \@LocalStorageLink：\@LocalStorageLink装饰的变量与LocalStorage中给定属性建立双向同步关系。

在静态上下文中使用时，需导入LocalStorage：

```ts
import { LocalStorage } from '@ohos.arkui.stateManagement';
```

## \@LocalStoragePropRef

在上文中已经提到，如果要建立LocalStorage和自定义组件的联系，需要使用\@LocalStoragePropRef和\@LocalStorageLink装饰器。使用\@LocalStoragePropRef(key)或\@LocalStorageLink(key)装饰组件内的变量，key标识了LocalStorage的属性。

当自定义组件初始化的时候，\@LocalStoragePropRef(key)/\@LocalStorageLink(key)装饰的变量会通过给定的key，绑定LocalStorage对应的属性，完成初始化。本地初始化是必要的，因为无法保证LocalStorage一定存在给定的key（这取决于应用逻辑是否在组件初始化之前在LocalStorage实例中存入对应的属性）。

> **说明：**
>
> 从API version 23开始，该装饰器支持在静态ArkTS中使用。

在静态上下文中使用时，需导入装饰器：

```ts
import { LocalStoragePropRef } from '@ohos.arkui.stateManagement';
```

1. 不同于动态Arkts的[@LocalStorageProp](../state-management/arkts-localstorage.md#localstorageprop)，@LocalStoragePropRef不会对数据做深拷贝，而是获得数据源的引用，本地修改时，该修改不会被写回AppStorage中。但对于复杂类型，修改属性会在LocalStorage中体现。
2. LocalStorage修改key对应的属性时，该修改会被同步到所有绑定LocalStorage对应key的属性上，覆盖本地的修改。


### 装饰器使用规则

| \@LocalStoragePropRef变量装饰器 | 说明                                                         |
| ---------------------------- | ------------------------------------------------------------ |
| 装饰器参数                   | key：常量字符串，必填（字符串需要有引号）。                  |
| 允许装饰的变量类型           | Object、class、string、number、boolean、enum类型，以及这些类型的数组。<br/>支持Map、Set、Date、undefined和null类型。嵌套类型的场景请参考[观察变化和行为表现](#观察变化和行为表现)。<br/>类型必须被指定，建议和LocalStorage中对应属性类型相同，否则会发生类型隐式转换，从而导致应用行为异常。<br/>支持上述支持类型的联合类型，比如string \| number, string \| undefined 或者 ClassA \| null，示例见[LocalStorage支持联合类型](#localstorage支持联合类型)。<br/>不支持any。 <br/>**注意**<br/>当使用undefined和null的时候，必须显式指定类型，遵循静态ArkTS类型校验，比如：`@LocalStoragePropRef('AA') a: number \| null = null`能通过编译，`@LocalStoragePropRef('AA') a: number = null`无法通过编译。 |
| 同步类型                     | 单向同步：从LocalStorage的对应属性到组件的状态变量。组件本地的修改是允许的，但是LocalStorage中给定的属性一旦发生变化，将覆盖本地的修改。 |
| 被装饰变量的初始值           | 必须指定，如果LocalStorage实例中不存在属性，则用该初始值初始化该属性，并存入LocalStorage中。 |


### 变量的传递/访问规则

| 传递/访问规则        | 说明                                                         |
| -------------------- | ------------------------------------------------------------ |
| 从父节点初始化和更新 | 禁止，\@LocalStoragePropRef不支持从父节点初始化，只能从LocalStorage中key对应的属性初始化，如果没有对应的key，将使用本地默认值初始化。 |
| 初始化子节点         | 支持，可用于初始化[\@State](./arkts-static-state.md)、[\@Link](./arkts-static-link.md)、[\@PropRef](./arkts-static-propref.md)、[\@Provide](./arkts-static-provide-and-consume.md)。       |
| 是否支持组件外访问   | 否。                                                         |

### 观察变化和行为表现

**观察变化**

- 当装饰的数据类型为boolean、string、number类型时，可以观察到数值的变化。

- 当装饰的对象是array时，可以观察到数组添加、删除、更新数组单元的变化。

- 当装饰的对象是Date时，可以观察到Date整体的赋值，同时可通过调用Date的接口`setFullYear`, `setMonth`, `setDate`, `setHours`, `setMinutes`, `setSeconds`, `setMilliseconds`, `setTime`, `setUTCFullYear`, `setUTCMonth`, `setUTCDate`, `setUTCHours`, `setUTCMinutes`, `setUTCSeconds`, `setUTCMilliseconds` 更新Date的属性。详见[装饰Date类型变量](#装饰date类型变量)。

- 当装饰的变量是Map时，可以观察到Map整体的赋值，同时可通过调用Map的接口`set`, `clear`, `delete` 更新Map的值。详见[装饰Map类型变量](#装饰map类型变量)。

- 当装饰的变量是Set时，可以观察到Set整体的赋值，同时可通过调用Set的接口`add`, `clear`, `delete` 更新Set的值。详见[装饰Set类型变量](#装饰set类型变量)。


**框架行为**

1. 使用\@LocalStoragePropRef(key)装饰的变量更新时，不会写回LocalStorage，但会触发当前自定义组件的重新渲染，对于复杂类型，由于\@LocalStoragePropRef拿到的是数据源的引用，修改属性会在AppStorage中体现。。

2. 当LocalStorage中对应key的值发生变化时，所有使用\@LocalStoragePropRef(key)装饰的变量都会同步更新，覆盖本地修改。

## \@LocalStorageLink

> **说明：**
>
> 从API version 23开始，该装饰器支持在静态ArkTS中使用。

在静态上下文中使用时，需导入装饰器：

```ts
import { LocalStorageLink } from '@ohos.arkui.stateManagement';
```

如果我们需要将自定义组件的状态变量的更新同步回LocalStorage，就需要用到\@LocalStorageLink。

\@LocalStorageLink(key)是和LocalStorage中key对应的属性建立双向数据同步：

1. 本地修改发生，该修改会被写回LocalStorage中。

2. LocalStorage中的修改发生后，该修改会被同步到所有绑定LocalStorage对应key的属性上，包括单向（\@LocalStoragePropRef）、双向（\@LocalStorageLink和通过link创建的双向绑定变量）变量。

### 装饰器使用规则

| \@LocalStorageLink变量装饰器 | 说明                                                         |
| ---------------------------- | ------------------------------------------------------------ |
| 装饰器参数                   | key：常量字符串，必填（字符串需要有引号）。                  |
| 允许装饰的变量类型           | Object、class、string、number、boolean、enum类型，以及这些类型的数组。<br/>支持Map、Set、Date、undefined和null类型。嵌套类型的场景请参考[观察变化和行为表现](#观察变化和行为表现)。<br/>类型必须被指定，建议和LocalStorage中对应属性类型相同，否则会发生类型隐式转换，从而导致应用行为异常。<br/>支持上述类型的联合类型，比如string \| number, string \| undefined 或者 ClassA \| null，示例见[LocalStorage支持联合类型](#localstorage支持联合类型)。<br/>不支持any。 <br/>**注意**<br/>当使用undefined和null的时候，必须显式指定类型，遵循静态ArkTS类型校验，比如：`@LocalStoragePropRef('AA') a: number \| null = null`能通过编译，`@LocalStoragePropRef('AA') a: number = null`无法通过编译。 |
| 同步类型                     | 双向同步：从LocalStorage的对应属性到自定义组件，从自定义组件到LocalStorage对应属性。 |
| 被装饰变量的初始值           | 必须指定，如果LocalStorage实例中不存在属性，则用该初始值初始化该属性，并存入LocalStorage中。 |

### 变量的传递/访问规则

| 传递/访问规则        | 说明                                                         |
| -------------------- | ------------------------------------------------------------ |
| 从父节点初始化和更新 | 禁止，\@LocalStorageLink不支持从父节点初始化，只能从LocalStorage中key对应的属性初始化，如果没有对应的key，将使用本地默认值初始化。 |
| 初始化子节点         | 支持，可用于初始化\@State、\@Link、\@PropRef、\@Provide。       |
| 是否支持组件外访问   | 否。                                                         |

### 观察变化和行为表现

**观察变化**

- 当装饰的数据类型为boolean、string、number类型时，可以观察到数值的变化。

- 当装饰的对象是array时，可以观察到数组添加、删除、更新数组单元的变化。

- 当装饰的对象是Date时，可以观察到Date整体的赋值，同时可通过调用Date的接口`setFullYear`, `setMonth`, `setDate`, `setHours`, `setMinutes`, `setSeconds`, `setMilliseconds`, `setTime`, `setUTCFullYear`, `setUTCMonth`, `setUTCDate`, `setUTCHours`, `setUTCMinutes`, `setUTCSeconds`, `setUTCMilliseconds` 更新Date的属性。详见[装饰Date类型变量](#装饰date类型变量)。

- 当装饰的变量是Map时，可以观察到Map整体的赋值，同时可通过调用Map的接口`set`, `clear`, `delete` 更新Map的值。详见[装饰Map类型变量](#装饰map类型变量)。

- 当装饰的变量是Set时，可以观察到Set整体的赋值，同时可通过调用Set的接口`add`, `clear`, `delete` 更新Set的值。详见[装饰Set类型变量](#装饰set类型变量)。

**框架行为**

1. 使用\@LocalStorageLink(key)装饰的变量更新时，会同步写回LocalStorage对应的key，还会引起所属的自定义组件的重新渲染。

2. 当LocalStorage中对应key的值发生变化时，所有绑定该key的数据（包括双向\@LocalStorageLink和单向\@LocalStoragePropRef）都会同步更新。

## 限制条件

1. \@LocalStoragePropRef/\@LocalStorageLink的参数必须为string类型，否则编译期会报错。

    ```ts
    'use static'

    import { Entry, Column, Component, Text } from '@ohos.arkui.component';
    import { LocalStorage, LocalStoragePropRef, LocalStorageLink } from '@ohos.arkui.stateManagement';

    let storage = new LocalStorage();
    storage.setOrCreate('PropA', 48);
    let storageFunc = (): LocalStorage => {
      return storage;
    }


    @Entry({ storage: 'storageFunc' })
    @Component
    struct Index {
      // 错误写法，编译报错
      // @LocalStoragePropRef() localStorageProp: int = 1;
      // @LocalStorageLink() localStorageLink: int = 2;

      // 正确写法
      @LocalStoragePropRef('PropA') localStorageProp: int = 1;
      @LocalStorageLink('PropA') localStorageLink: int = 2;

      build() {
        Column() {
          Text(`localStorageProp ${this.localStorageProp}`)
          Text(`localStorageLink ${this.localStorageLink}`)
        }
      }
    }
    ```

2. LocalStorage创建后，命名属性的类型不可更改。后续调用Set时必须使用相同类型的值。

3. LocalStorage是页面级存储，[getSharedLocalStorage](../../reference/apis-arkui/js-apis-arkui-UIContext.md#getsharedlocalstorage12)接口仅能获取当前Stage通过[windowStage.loadContent](../../reference/apis-arkui/arkts-apis-window-Window.md#loadcontent9)传入的LocalStorage实例，否则返回undefined。例子可见[将LocalStorage实例从UIAbility共享到一个或多个页面](#将localstorage实例从uiability共享到一个或多个页面)。

4. \@LocalStoragePropRef/\@LocalStorageLink不支持装饰Function 与() => void类型的变量，API version 23之前，框架会抛出运行时错误。
从API version 23开始，添加对\@LocalStoragePropRef/\@LocalStorageLink装饰Function与() => void类型变量的校验，编译期会报错。

## 使用场景

### 应用逻辑使用LocalStorage

```ts
import { LocalStorage, SubscribedAbstractProperty } from '@ohos.arkui.stateManagement';

let para: Record<string, Any> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(para); // 创建新实例并使用给定对象初始化
let propA: number | undefined = storage.get<number>('PropA'); // propA == 47
let link1: SubscribedAbstractProperty<number> = storage.link<number>('PropA')!; // link1.get() == 47
let link2: SubscribedAbstractProperty<number> = storage.link<number>('PropA')!; // link2.get() == 47
link1.set(48); // 双向同步: link1.get() == link2.get() == prop.get() == 48
link1.set(49); // 双向同步: link1.get() == link2.get() == prop.get() == 49
```

### 从UI内部使用LocalStorage

除了应用程序逻辑使用LocalStorage，还可以借助LocalStorage相关的两个装饰器\@LocalStoragePropRef和\@LocalStorageLink，在UI组件内部获取到LocalStorage实例中存储的状态变量。

本示例以\@LocalStorageLink为例，展示了：

- 使用构造函数创建LocalStorage实例storage。

- 使用\@Entry装饰器将storage添加到Parent顶层组件中。

- \@LocalStorageLink绑定LocalStorage对给定的属性，建立双向数据同步。

  ```ts
  'use static'

  import { Entry, Text, Row, Column, Component, Button, ClickEvent } from '@ohos.arkui.component';
  import { LocalStorage, LocalStorageLink } from '@ohos.arkui.stateManagement';

  class Data {
    code: number;

    constructor(code: number) {
      this.code = code;
    }
  }
  // 创建新实例并使用给定对象初始化
  let para: Record<string, Any> = { 'PropA': 47 };
  let storageA: LocalStorage = new LocalStorage(para);
  storageA.setOrCreate('PropB', new Data(50));
  let storageFunc = (): LocalStorage => {
    return storageA;
  }

  // 静态ArkTS，@Entry只支持传入字符串，因次必须传入匿名函数
  @Entry({storage: 'storageFunc'})
  @Component
  struct Parent {
    // @LocalStorageLink变量装饰器与LocalStorage中的'PropA'属性建立双向绑定
    @LocalStorageLink('PropA') parentLinkNumber: int = 1;
    // @LocalStorageLink变量装饰器与LocalStorage中的'PropB'属性建立双向绑定
    @LocalStorageLink('PropB') parentLinkObject: Data = new Data(0);

    build() {
      Column() {
        // 由于LocalStorage中PropA已经被初始化，因此this.parentLinkNumber的值为47
        Button(`Parent from LocalStorage ${this.parentLinkNumber}`)
          .onClick((e: ClickEvent) => {
            this.parentLinkNumber += 1;
          })
        // 由于LocalStorage中PropB已经被初始化，因此this.parentLinkObject.code的值为50
        // 类属性观测需要使用@Observed装饰class，因此不支持刷新
        Button(`Parent from LocalStorage ${this.parentLinkObject.code}`)
          .onClick((e: ClickEvent) => {
            this.parentLinkObject.code += 1;
          })
        // @Component子组件自动获得对Parent LocalStorage实例的访问权限
        Child()
      }
    }
  }

  @Component
  struct Child {
    // @LocalStorageLink变量装饰器与LocalStorage中的'PropA'属性建立双向绑定
    @LocalStorageLink('PropA') childLinkNumber: int = 1;
    // @LocalStorageLink变量装饰器与LocalStorage中的'PropB'属性建立双向绑定
    @LocalStorageLink('PropB') childLinkObject: Data = new Data(0);

    build() {
      Column() {
        // 更改将同步至LocalStorage中的'PropA'以及Parent.parentLinkNumber
        Button(`Child from LocalStorage ${this.childLinkNumber}`)
          .onClick((e: ClickEvent) => {
            this.childLinkNumber += 1;
          })
        // 更改将同步至LocalStorage中的'PropB'以及Parent.parentLinkObject.code
        // 类属性观测需要使用@Observed装饰class，因此不支持刷新
        Button(`Child from LocalStorage ${this.childLinkObject.code}`)
          .onClick((e: ClickEvent) => {
            this.childLinkObject.code += 1;
          })
      }
    }
  }
  ```

### \@LocalStoragePropRef和LocalStorage单向同步的简单场景

本示例展示了Parent和Child组件各自在本地创建与storage中'PropA'属性的单向数据同步：

- Parent中对this.storageProp1的修改，只会在Parent中生效，并没有同步回storage。

- Child组件中，Text绑定的storageProp2 依旧显示47。

  ```ts
  'use static'

  import { Entry, Text, Row, Column, Component, Button, ClickEvent } from '@ohos.arkui.component';
  import { LocalStorage, LocalStoragePropRef } from '@ohos.arkui.stateManagement';

  // 创建新实例并使用给定对象初始化
  let para: Record<string, Any> = { 'PropA': 47 };
  let storageA: LocalStorage = new LocalStorage(para);
  let storageFunc = (): LocalStorage => {
    return storageA;
  }

  // 使LocalStorage可从@Component组件访问
  @Entry({storage: 'storageFunc'})
  @Component
  struct Parent {
    // @LocalStorageProp变量装饰器与LocalStorage中的'PropA'属性建立单向绑定
    @LocalStoragePropRef('PropA') storageProp1: int = 1;

    build() {
      Column() {
        // 点击后从47开始加1，只改变当前组件显示的storageProp1，不会同步到LocalStorage中
        Button(`Parent from LocalStorage ${this.storageProp1}`)
          .onClick((e: ClickEvent) => {
            this.storageProp1 += 1;
          })
        Child()
      }
    }
  }

  @Component
  struct Child {
    // @LocalStorageProp变量装饰器与LocalStorage中的'PropA'属性建立单向绑定
    @LocalStoragePropRef('PropA') storageProp2: int = 2;

    build() {
      Column() {
        // 当Parent改变时，当前storageProp2不会改变，显示47
        Text(`Parent from LocalStorage ${this.storageProp2}`)
      }
    }
  }
  ```

### \@LocalStorageLink和LocalStorage双向同步的简单场景

下面的示例展示了\@LocalStorageLink装饰的数据和LocalStorage双向同步的场景：

```ts
'use static'

import { Entry, Text, Row, Column, Component, Button, ClickEvent } from '@ohos.arkui.component';
import { LocalStorage, LocalStorageLink, SubscribedAbstractProperty } from '@ohos.arkui.stateManagement';

// 构造LocalStorage实例
let para: Record<string, Any> = { 'PropA': 47 };
let storageA: LocalStorage = new LocalStorage(para);
let storageFunc = (): LocalStorage => {
  return storageA;
}

// linkToPropA 是全局变量
let linkToPropA: SubscribedAbstractProperty<int> = storageA.link<int>('PropA')!;

@Entry({storage: 'storageFunc'})
@Component
struct Parent {

  // @LocalStorageLink('PropA')在Parent自定义组件中创建'PropA'的双向同步数据，初始值为47，因为在构造LocalStorage已经给“PropA”设置47
  @LocalStorageLink('PropA') storageLink: int = 1;

  build() {
    Column() {
      Text(`incr @LocalStorageLink variable`)
        // 点击“incr @LocalStorageLink variable”，this.storageLink加1，改变同步回storage，全局变量linkToPropA也会同步改变

        .onClick((e: ClickEvent) => {
          this.storageLink += 1;
        })

      // 并不建议在组件内使用全局变量linkToPropA.get()，因为可能会有生命周期不同引起的错误。
      Text(`@LocalStorageLink: ${this.storageLink} - linkToPropA: ${linkToPropA.get()}`)
    }
  }
}
```

### 兄弟组件之间同步状态变量

下面的示例展示了通过\@LocalStorageLink双向同步兄弟组件之间的状态。

先看Parent自定义组件中发生的变化：

1. 点击“playCount ${this.playCount} dec by 1”，this.playCount减1，修改同步回LocalStorage中，Child组件中的playCountLink绑定的组件会同步刷新。

2. 点击“countStorage ${this.playCount} incr by 1”，调用LocalStorage的set接口，更新LocalStorage中“countStorage”对应的属性，Child组件中的playCountLink绑定的组件会同步刷新。

3. Text组件“playCount in LocalStorage for debug ${storage.get&lt;number&gt;('countStorage')}”没有同步刷新，因为storage.get&lt;number&gt;('countStorage')返回的是常规变量，常规变量的更新并不会引起Text组件的重新渲染。

Child自定义组件中的变化：

1. playCountLink的刷新会同步回LocalStorage，并且引起兄弟组件和父组件相应的刷新。

    ```ts
    'use static'

    import { Entry, Text, Row, Column, Component, Button, ClickEvent } from '@ohos.arkui.component';
    import { LocalStorage, LocalStorageLink } from '@ohos.arkui.stateManagement'

    let count: Record<string, Any> = { 'countStorage': 1 };
    let storageA: LocalStorage = new LocalStorage(count);
    let storageFunc = (): LocalStorage => {
      return storageA;
    }

    @Component
    struct Child {
      // 子组件实例的名字
      label: string = 'no name';
      // 和LocalStorage中“countStorage”的双向绑定数据
      @LocalStorageLink('countStorage') playCountLink: int = 0;

      build() {
        Row() {
          Text(this.label)
            .width(50).height(60).fontSize(12)
          Text(`playCountLink ${this.playCountLink}: inc by 1`)
            .onClick((e: ClickEvent) => {
              this.playCountLink += 1;
            })
            .width(200).height(60).fontSize(12)
        }.width(300).height(60)
      }
    }

    @Entry({storage: 'storageFunc'})
    @Component
    struct Parent {
      @LocalStorageLink('countStorage') playCount: int = 0;

      build() {
        Column() {
          Row() {
            Text('Parent')
              .width(50).height(60).fontSize(12)
            Text(`playCount ${this.playCount} dec by 1`)
              .onClick((e: ClickEvent) => {
                this.playCount -= 1;
              })
              .width(250).height(60).fontSize(12)
          }.width(300).height(60)

          Row() {
            Text('LocalStorage')
              .width(50).height(60).fontSize(12)
            Text(`countStorage ${this.playCount} incr by 1`)
              .onClick((e: ClickEvent) => {
                storageA.set<int>('countStorage', storageA.get<int>('countStorage')! + 1);
              })
              .width(250).height(60).fontSize(12)
          }.width(300).height(60)

          Child({ label: 'ChildA' })
          Child({ label: 'ChildB' })

          Text(`playCount in LocalStorage for debug ${storageA.get<int>('countStorage')}`)
            .width(300).height(60).fontSize(12)
        }
      }
    }
    ```

### 将LocalStorage实例从UIAbility共享到一个或多个页面

上面的实例中，LocalStorage的实例仅仅在一个\@Entry装饰的组件和其所属的子组件（一个页面）中共享，如果希望其在多个页面中共享，可以在所属UIAbility中创建LocalStorage实例，并调用windowStage.[loadContent](../../reference/apis-arkui/arkts-apis-window-Window.md#loadcontent9)。

```ts
// EntryAbility.ets
'use static'

import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { LocalStorage } from '@ohos.arkui.stateManagement'

export default class EntryAbility extends UIAbility {
  para: Record<string, Any> = {
    'PropA': 47
  };
  storage: LocalStorage = new LocalStorage(this.para);

  onWindowStageCreate(windowStage: window.WindowStage) {
    windowStage.loadContent('pages/Index', this.storage);
  }
}
```

> **说明：**
>
> 在UI页面通过getSharedLocalStorage获取当前stage共享的LocalStorage实例。
>
> this.getUIContext().getSharedLocalStorage()只在模拟器或者实机上才有效，在Previewer预览器中使用不生效。

在下面的用例中，Index页面中的propA通过使用共享的LocalStorage实例,数值为loadContent传入的storage实例中的'PropA'。

```ts
// index.ets
'use static'

import { Entry, Text, Row, Column, Component, Button, ClickEvent } from '@ohos.arkui.component';
import { LocalStorage, LocalStorageLink } from '@ohos.arkui.stateManagement'

// 预览器上不支持获取页面共享的LocalStorage实例。
@Entry({ useSharedStorage: true })
@Component
struct Index {
  // 可以使用@LocalStorageLink/LocalStoragePropRef与LocalStorage实例中的变量建立联系
  @LocalStorageLink('PropA') propA: int = 1;

  build() {
    Row(){
      Column() {
        Text(`${this.propA}`)
          .fontSize(50)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

> **说明：**
>
> 对于开发者更建议使用这个方式来构建LocalStorage的实例，并且在创建LocalStorage实例的时候就写入默认值，因为默认值可以作为运行异常的备份，也可以用作页面的单元测试。

### 自定义组件接收LocalStorage实例

除了根节点可通过\@Entry来接收LocalStorage实例，自定义组件（子节点）也可以通过构造参数来传递LocalStorage实例。

本示例以\@LocalStorageLink为例，展示了：

- 父组件通过\@Entry接收LocalStorage实例localStorage1，使得父组件中PropA的值为“PropA”。

- Child组件接收参数中的LocalStorage实例localStorage2，使得Child组件中PropB的值为“PropB”。

> **说明：**
>
> 从API version 23开始，自定义组件支持接收LocalStorage实例。
> 当自定义组件作为子节点，定义了成员属性时，LocalStorage实例必须要放在第二个参数位置传递，否则会报类型不匹配的编译问题。
> 如果定义的属性不需要从父组件初始化变量，则第一个参数需要传{}。
> 作为构造参数传给子组件的LocalStorage实例在初始化时就会被决定，可以通过@LocalStorageLink或者LocalStorage的API修改LocalStorage实例中保存的属性值，但LocalStorage实例自身不能被动态修改。

```ts
'use static'

import { Entry, Text, Row, Column, Component, Button, ClickEvent } from '@ohos.arkui.component';
import { LocalStorage, LocalStorageLink, State, Link } from '@ohos.arkui.stateManagement';

let localStorage1: LocalStorage = new LocalStorage();
localStorage1.setOrCreate('PropA', 'PropA');
let storageFunc1 = (): LocalStorage => {
    return localStorage1;
}

let localStorage2: LocalStorage = new LocalStorage();
localStorage2.setOrCreate('PropB', 'PropB');

@Entry({storage: 'storageFunc1'})
@Component
struct Index {
  // 变量PropA和localStorage1中'PropA'的双向同步
  @LocalStorageLink('PropA') PropA: string = 'Hello World';
  @State count: number = 0;

  build() {
    Row() {
      Column() {
        Text(this.PropA)
          .fontSize(50)
        // 使用LocalStorage实例localStorage2
        Child({ count: this.count }, localStorage2)
      }
      .width('100%')
    }
    .height('100%')
  }
}


@Component
struct Child {
  @Link count: number;
  // 变量PropB和localStorage2中'PropB'的双向同步，如果localStorage2中没有'PropB'，则使用默认值'Hello World'
  @LocalStorageLink('PropB') PropB: string = 'Hello World';

  build() {
    Text(this.PropB)
      .fontSize(50)
  }
}
```

当定义的属性不需要从父组件初始化变量时，第一个参数需要传{}。

```ts
'use static'

import { Entry, Text, Row, Column, Component, Button, ClickEvent } from '@ohos.arkui.component';
import { LocalStorage, LocalStorageLink, State } from '@ohos.arkui.stateManagement';

let localStorage1: LocalStorage = new LocalStorage();
localStorage1.setOrCreate('PropA', 'PropA');
let storageFunc1 = (): LocalStorage => {
    return localStorage1;
}

let localStorage2: LocalStorage = new LocalStorage();
localStorage2.setOrCreate('PropB', 'PropB');

@Entry({storage: 'storageFunc1'})
@Component
struct Index {
  // 变量PropA和localStorage1中'PropA'的双向同步
  @LocalStorageLink('PropA') PropA: string = 'Hello World';
  @State count: number = 0;

  build() {
    Row() {
      Column() {
        Text(this.PropA)
          .fontSize(50)
        // 使用LocalStorage实例localStorage2
        Child({}, localStorage2)
      }
      .width('100%')
    }
    .height('100%')
  }
}


@Component
struct Child {
  @State count: number = 5;
  // 变量PropB和localStorage2中'PropB'的双向同步，如果localStorage2中没有'PropB'，则使用默认值'Hello World'
  @LocalStorageLink('PropB') PropB: string = 'Hello World';

  build() {
    Text(this.PropB)
      .fontSize(50)
  }
}
```

### LocalStorage支持联合类型

在下面的示例中，变量A的类型为number | null，变量B的类型为number | undefined。Text组件初始化分别显示为null和undefined，点击切换为数字，再次点击切换回null和undefined。

```ts
'use static'

import { Entry, Text, Row, Column, Component, Button, ClickEvent } from '@ohos.arkui.component';
import { LocalStorageLink, LocalStoragePropRef } from '@ohos.arkui.stateManagement';

@Component
struct StorageLinkComponent {
  @LocalStorageLink('LinkA') LinkA: number | null = null;
  @LocalStorageLink('LinkB') LinkB: number | undefined = undefined;

  build() {
    Column() {
      Text('@LocalStorageLink接口初始化，@LocalStorageLink取值')
      Text(`${this.LinkA}`).fontSize(20).onClick((e: ClickEvent) => {
        this.LinkA ? this.LinkA = null : this.LinkA = 1;
      })
      Text(`${this.LinkB}`).fontSize(20).onClick((e: ClickEvent) => {
        this.LinkB ? this.LinkB = undefined : this.LinkB = 1;
      })
    }
    .borderWidth(3)

  }
}

@Component
struct StoragePropComponent {
  @LocalStoragePropRef('PropA') PropA: number | null = null;
  @LocalStoragePropRef('PropB') PropB: number | undefined = undefined;

  build() {
    Column() {
      Text('@LocalStoragePropRef接口初始化，@LocalStoragePropRef取值')
      Text(`${this.PropA}`).fontSize(20).onClick((e: ClickEvent) => {
        this.PropA ? this.PropA = null : this.PropA = 1;
      })
      Text(`${this.PropB}`).fontSize(20).onClick((e: ClickEvent) => {
        this.PropB ? this.PropB = undefined : this.PropB = 1;
      })
    }
    .borderWidth(3)
  }
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        StorageLinkComponent()
        StoragePropComponent()
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### 装饰Date类型变量

在下面的示例中，\@LocalStorageLink装饰的selectedDate类型为Date，点击Button改变selectedDate的值，UI会随之刷新。

```ts
'use static'

import { Entry, Text, Column, Component, Button, ClickEvent } from '@ohos.arkui.component';
import { LocalStorageLink } from '@ohos.arkui.stateManagement';

@Entry
@Component
struct DateSample {
  @LocalStorageLink('date') selectedDate: Date = new Date('2021-08-08');

  build() {
    Column() {
      Text(`${this.selectedDate}`)
      Button('set selectedDate to 2023-07-08')
        .margin(10)
        .onClick((e: ClickEvent) => {
          this.selectedDate = new Date('2023-07-08');
        })
      Button('increase the year by 1')
        .margin(10)
        .onClick((e: ClickEvent) => {
          this.selectedDate.setFullYear(this.selectedDate.getFullYear() + 1);
        })
      Button('increase the month by 1')
        .margin(10)
        .onClick((e: ClickEvent) => {
          this.selectedDate.setMonth(this.selectedDate.getMonth() + 1);
        })
      Button('increase the day by 1')
        .margin(10)
        .onClick((e: ClickEvent) => {
          this.selectedDate.setDate(this.selectedDate.getDate() + 1);
        })
    }.width('100%')
  }
}
```

### 装饰Map类型变量

在下面的示例中，\@LocalStorageLink装饰的message类型为Map\<number, string\>，点击Button改变message的值，UI会随之刷新。

```ts
'use static'

import { Entry, Text, Row, Column, Component, Button, ClickEvent } from '@ohos.arkui.component';
import { LocalStorageLink } from '@ohos.arkui.stateManagement';

@Entry
@Component
struct MapSample {
  @LocalStorageLink('map') message: Map<number, string> = new Map<number, string>([[0, 'a'], [1, 'b'], [3, 'c']]);

  build() {
    Row() {
      Column() {
        Text(`${this.message}`)
        Button('init map').onClick((e: ClickEvent) => {
          this.message = new Map<number, string>([[0, 'a'], [1, 'b'], [3, 'c']]);
        })
        Button('set new one').onClick((e: ClickEvent) => {
          this.message.set(4, 'd');
        })
        Button('clear').onClick((e: ClickEvent) => {
          this.message.clear();
        })
        Button('replace the existing one').onClick((e: ClickEvent) => {
          this.message.set(0, 'aa');
        })
        Button('delete the existing one').onClick((e: ClickEvent) => {
          this.message.delete(0);
        })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### 装饰Set类型变量

在下面的示例中，\@LocalStorageLink装饰的memberSet类型为Set\<number\>，点击Button改变memberSet的值，UI会随之刷新。

```ts
'use static'

import { Entry, Text, Row, Column, Component, Button, ClickEvent } from '@ohos.arkui.component';
import { LocalStorageLink } from '@ohos.arkui.stateManagement';

@Entry
@Component
struct SetSample {
  @LocalStorageLink('set') memberSet: Set<number> = new Set<number>([0, 1, 2, 3, 4]);

  build() {
    Row() {
      Column() {
        Text(`${this.memberSet}`)
        Button('init set')
          .onClick((e: ClickEvent) => {
            this.memberSet = new Set<number>([0, 1, 2, 3, 4]);
          })
        Button('set new one')
          .onClick((e: ClickEvent) => {
            this.memberSet.add(5);
          })
        Button('clear')
          .onClick((e: ClickEvent) => {
            this.memberSet.clear();
          })
        Button('delete the first one')
          .onClick((e: ClickEvent) => {
            this.memberSet.delete(0);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### 自定义组件外改变状态变量

```ts
'use static'

import { Entry, Text, Row, Column, Component, Button, ClickEvent } from '@ohos.arkui.component';
import { LocalStorageLink, LocalStorage } from '@ohos.arkui.stateManagement';

let storageA = new LocalStorage();
storageA.setOrCreate<number>('count', 47);
let storageFunc = () => {
  return storageA;
}

class Model {
  storage: LocalStorage = storageA;

  call(propName: string, value: number) {
    this.storage.setOrCreate<number>(propName, value);
  }
}

let model: Model = new Model();

@Entry({ storage: 'storageFunc' })
@Component
struct Test {
  @LocalStorageLink('count') count: number = 0;

  build() {
    Column() {
      Text(`count值: ${this.count}`)
      Button('change')
        .onClick((e: ClickEvent) => {
          model.call('count', this.count + 1);
        })
    }
  }
}
```