# AppStorage：应用全局的UI状态存储

在阅读本文档前，建议提前阅读：[状态管理概述](../state-management/arkts-state-management-overview.md)，从而对状态管理框架中AppStorage的定位有一个宏观了解。

AppStorage 是与应用进程绑定的全局UI状态存储中心，由UI框架在应用启动时创建，将UI状态数据存储在运行内存中，实现应用级别的全局状态共享。

作为应用的“中枢”，AppStorage是[持久化数据PersistentStorage](arkts-static-persiststorage.md)和[环境变量Environment](arkts-static-environment.md)与UI交互的中转桥梁。其核心价值在于为开发者提供跨ability的大范围UI状态数据共享能力。

AppStorage提供了API接口，允许开发者在自定义组件外手动触发AppStorage对应key的增、删、改、查操作。建议配合[AppStorage API文档](../../reference/apis-arkui/arkui-ts/ts-state-management-1.2.md#appstorage)阅读。

## 概述

AppStorage是在应用启动时创建的单例，用于提供应用状态数据的中心存储。这些状态数据在应用级别可访问。AppStorage在应用运行过程中保留其属性。

AppStorage中保存的属性通过唯一的字符串类型key值访问，该属性可以和UI组件同步，且可以在应用业务逻辑中被访问。

AppStorage支持应用的[主线程](../../application-models/thread-model-stage.md)内两个或更多[UIAbility](../../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md)实例间的UI状态数据共享。

AppStorage中的属性通过唯一的字符串类型key值访问，支持与UI组件同步，并可在应用业务逻辑中被访问，同时支持应用的[主线程](../../application-models/thread-model-stage.md)内多个[UIAbility](../../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md)实例间的UI状态数据共享。

AppStorage中的属性可以被双向同步，并具有不同的功能，比如数据持久化（详见[PersistentStorage](./arkts-static-persiststorage.md)）。这些UI状态是通过业务逻辑实现，与UI解耦，如果希望这些UI状态在UI中使用，需要用到[@StoragePropRef](#storagepropRef)和[@StorageLink](#storagelink)。

在静态上下文中使用时，需导入AppStorage：

```ts
import { AppStorage } from '@ohos.arkui.stateManagement';
```

## StoragePropRef

在上文中已经提到，如果要建立AppStorage和自定义组件的联系，需使用\@StoragePropRef和\@StorageLink装饰器。使用\@StoragePropRef(key)或\@StorageLink(key)装饰组件内的变量，key标识了AppStorage的属性。

当自定义组件初始化时，使用AppStorage中对应key的属性值初始化\@StoragePropRef(key)或\@StorageLink(key)装饰的变量。由于应用逻辑的差异，无法确认组件初始化前是否已向AppStorage实例中存入对应属性，因此对\@StoragePropRef(key)或\@StorageLink(key)装饰的变量进行本地初始化是必要的。

\@StoragePropRef(key)与AppStorage中key对应的属性建立单向数据同步：

1. 不同于动态Arkts的[@StorageProp](../state-management/arkts-appstorage.md#storageprop)，@StoragePropRef不会对数据做深拷贝，而是获得数据源的引用，本地修改时，该修改不会被写回AppStorage中。但对于复杂类型，修改属性会在AppStorage中体现。

2. AppStorage修改key对应的属性时，该修改会被同步到所有绑定AppStorage对应key的属性上，覆盖本地的修改。

> **说明：**
>
> 从API version 20开始，该装饰器支持在静态ArkTS中使用。

在静态上下文中使用时，需导入装饰器：

```ts
import { StoragePropRef } from '@ohos.arkui.stateManagement';
```

### 装饰器使用规则说明

| \@StoragePropRef变量装饰器 | 说明                                                         |
| ----------------------- | ------------------------------------------------------------ |
| 装饰器参数               | key：常量字符串，必填（字符串需要有引号）。                  |
| 允许装饰的变量类型        | Object、class、string、number、boolean、enum类型，以及这些类型的数组。<br/>支持Map、Set、Date、undefined和null类型。嵌套类型的场景请参考[观察变化和行为表现](#观察变化和行为表现)。<br/>类型必须被指定，建议和AppStorage中对应属性类型相同，否则会发生类型隐式转换，从而导致应用行为异常。<br/>不支持any。<br/>支持上述类型的联合类型，比如string \| number, string \| undefined 或者 ClassA \| null，示例见[AppStorage支持联合类型](#appstorage支持联合类型)。 <br/>**注意**<br/>当使用undefined和null的时候，必须显式指定类型，遵循静态ArkTS类型校验，比如：`@StoragePropRef('AA') a: number \| null = null`能通过编译，`@StoragePropRef('AA') a: number = null`无法通过编译。 |
| 同步类型                | 单向同步：从AppStorage的对应属性到组件的状态变量。<br/>组件本地的修改是允许的，但是AppStorage中给定的属性一旦发生变化，将覆盖本地的修改。 |
| 被装饰变量的初始值       | 必须指定，如果AppStorage实例中不存在属性，则用该初始值初始化该属性，并存入AppStorage中。 |

### 变量的传递/访问规则说明

| 传递/访问            | 说明                                                         |
| -------------------- | ------------------------------------------------------------ |
| 从父节点初始化和更新 | 禁止从父节点初始化和更新@StoragePropRef。仅支持使用AppStorage中对应key的属性进行初始化，如果不存在对应key，则使用本地默认值进行初始化。 |
| 初始化子节点        | 支持，可用于初始化\@State、\@Link、\@PropRef、\@Provide。    |
| 是否支持组件外访问   | 否。                                                         |

### 观察变化和行为表现

**观察变化**

- 当装饰的类型为boolean、string、number时，可以观察到数值的变化。

- 当装饰的对象是数组时，可以观察到数组添加、删除、更新数组单元的变化。

- 当装饰的对象是Date时，可以观察到Date整体的赋值，以及通过调用Date的接口`setFullYear`、`setMonth`、`setDate`、`setHours`、`setMinutes`、`setSeconds`、`setMilliseconds`、`setTime`、`setUTCFullYear`、`setUTCMonth`、`setUTCDate`、`setUTCHours`、`setUTCMinutes`、`setUTCSeconds`、`setUTCMilliseconds`更新Date的属性。详见[装饰Date类型变量](#装饰date类型变量)。

- 当装饰的变量是Map时，可以观察到Map整体的赋值，以及通过调用Map的接口`set`、`clear`、`delete`更新Map的值。详见[装饰Map类型变量](#装饰map类型变量)。

- 当装饰的变量是Set时，可以观察到Set整体的赋值，以及通过调用Set的接口`add`、`clear`、`delete`更新Set的值。详见[装饰Set类型变量](#装饰set类型变量)。

**框架行为**

1. \@StoragePropRef(key)装饰的数值发生变化，不会同步写回AppStorage对应的属性；变化会触发自定义组件重新渲染，并且该变动仅作用于当前组件的私有成员变量，其他绑定该key的数据不会同步改变;但对于复杂类型，由于\@StoragePropRef拿到的是数据源的引用，修改属性会在AppStorage中体现。

2. 当AppStorage中对应key的属性发生改变时，所有\@StoragePropRef(key)装饰的变量都会同步更新，本地的修改将被覆盖。

## \@StorageLink

> **说明：**
>
> 从API version 20开始，该装饰器支持在静态ArkTS中使用。

在静态上下文中使用时，需导入装饰器：

```ts
import { StorageLink } from '@ohos.arkui.stateManagement';
```

\@StorageLink(key)是和AppStorage中key对应的属性建立双向数据同步：

1. 本地修改发生时，该修改会被写回AppStorage中。

2. 当AppStorage中的修改发生后，该修改会被同步到所有绑定AppStorage对应key的属性上，包括单向（\@StorageProp和通过@Prop创建的单向绑定变量）、双向（\@StorageLink和通过link创建的双向绑定变量）变量和其他实例（如PersistentStorage）。

### 装饰器使用规则说明

| \@StorageLink变量装饰器 | 说明                                                         |
| ----------------------- | ------------------------------------------------------------ |
| 装饰器参数              | key：常量字符串，必填（字符串需要有引号）。                  |
| 允许装饰的变量类型      | Object、class、string、number、boolean、enum类型，以及这些类型的数组。<br/>支持Map、Set、Date、undefined和null类型。嵌套类型的场景请参考[观察变化和行为表现](#观察变化和行为表现)。<br/>类型必须被指定，建议和AppStorage中对应属性类型相同，否则会发生类型隐式转换，从而导致应用行为异常。<br/>不支持any。<br/>支持上述类型的联合类型，比如string \ |
| 同步类型                | 双向同步：从AppStorage的对应属性到自定义组件，从自定义组件到AppStorage对应属性。 |
| 被装饰变量的初始值      | 必须指定，如果AppStorage实例中不存在属性，则用该初始值初始化该属性，并存入AppStorage中。 |


### 变量的传递/访问规则说明

| 传递/访问            | 说明                                                         |
| -------------------- | ------------------------------------------------------------ |
| 从父节点初始化和更新 | 禁止。                                                       |
| 初始化子节点         | 支持，可用于初始化常规变量、\@State、\@Link、\@PropRef、\@Provide。 |
| 是否支持组件外访问   | 否。                                                         |

### 观察变化和行为表现

**观察变化**

- 装饰的数据类型为boolean、string、number时，可以观察到数值变化。

- 当装饰的对象是数组时，可以观察到数组添加、删除、更新数组单元的变化。

- 当装饰的对象是Date时，可以观察到Date整体的赋值，以及通过调用Date的接口`setFullYear`, `setMonth`, `setDate`, `setHours`, `setMinutes`, `setSeconds`, `setMilliseconds`, `setTime`, `setUTCFullYear`, `setUTCMonth`, `setUTCDate`, `setUTCHours`, `setUTCMinutes`, `setUTCSeconds`, `setUTCMilliseconds` 更新Date的属性。详见[装饰Date类型变量](#装饰date类型变量)。

- 当装饰的变量是Map时，可以观察到Map整体的赋值，以及通过调用Map的接口`set`、`clear`、`delete`更新Map的值。详见[装饰Map类型变量](#装饰map类型变量)。

- 当装饰的变量是Set时，可以观察到Set的整体赋值，以及通过调用Set的接口`add`、`clear`、`delete`更新Set的值。详见[装饰Set类型变量](#装饰set类型变量)。

**框架行为**

1. 当\@StorageLink(key)装饰的数值发生变化时，修改将被同步回AppStorage对应key的属性中。

2. AppStorage中key对应的数据一旦改变，其绑定的所有的数据（包括双向\@StorageLink和单向\@StoragePropRef）都将被同步修改。

3. `@StorageLink(key)`装饰的数据是状态变量，其变化不仅会同步到AppStorage，还会触发自定义组件的重新渲染。


## 限制条件

1. \@StoragePropRef、\@StorageLink的参数必须为string类型，否则编译期会报错。

    ```ts
    'use static'

    import { Entry, Column, Component, Text } from '@ohos.arkui.component';
    import { AppStorage, StoragePropRef, StorageLink } from '@ohos.arkui.stateManagement';

    @Entry
    @Component
    struct Index {
      // 错误写法，编译报错
      // @StoragePropRef() storageProp: int = 1;
      // @StorageLink() storageLink: int = 2;

      // 正确写法
      @StoragePropRef('PropA') storageProp: int = 1;
      @StorageLink('PropA') storageLink: int = 2;
      // 在ArkTS-Sta中，全局的逻辑代码不会默认执行。开发者可将需要执行的逻辑代码移至static代码块中，以达到与ArkTS-Dyn一样的效果。
      static {
        AppStorage.setOrCreate<int>('PropA', 47); 
      }

      build() {
        Column() {
          Text(`storageProp ${this.storageProp}`)
          Text(`storageLink ${this.storageLink}`)
        }
      }
    }
    ```

2.AppStorage与[PersistentStorage](arkts-static-persiststorage.md)和[Environment](arkts-static-environment.md)配合使用时，需要注意以下几点：：

- 在AppStorage中创建属性后，调用PersistentStorage.[persistProp](../../reference/apis-arkui/arkui-ts/ts-state-management-1.2.md#persistProp)接口时，会使用AppStorage中已存在的值，并覆盖PersistentStorage中的同名属性。因此，建议调用顺序相反。反例可见[在PersistentStorage之前访问AppStorage中的属性](arkts-static-persiststorage.md#在persistentstorage之前访问appstorage中的属性)。

- 如果在AppStorage中已创建属性，再调用Environment.[envProp](../../reference/apis-arkui/arkui-ts/ts-state-management-1.2.md#envprop)创建同名属性，会调用失败。因为AppStorage已有同名属性，Environment环境变量不会再写入AppStorage中，所以建议不要在AppStorage中使用Environment预置环境变量名。

- 状态装饰器装饰的变量，改变会引起UI的渲染更新。如果改变的变量仅用于消息传递，不用于UI更新，不要使用StorageLink以防出现预料之外的UI刷新。

- AppStorage同一进程内共享，UIAbility和<!--Del-->[<!--DelEnd-->UIExtensionAbility<!--Del-->](../../application-models/uiextensionability.md)<!--DelEnd-->是两个进程，所以在<!--Del-->[<!--DelEnd-->UIExtensionAbility<!--Del-->](../../application-models/uiextensionability.md)<!--DelEnd-->中不共享主进程的AppStorage。

## 使用场景

### 从应用逻辑使用AppStorage和LocalStorage

AppStorage是单例，其所有API均为静态方法，使用方法类似于[LocalStorage](arkts-static-localstorage.md)中对应的非静态方法。

```ts
import { LocalStorage, AppStorage, SubscribedAbstractProperty } from '@ohos.arkui.stateManagement';

AppStorage.setOrCreate<number>('PropA', 47);

let storage: LocalStorage = new LocalStorage();
storage.setOrCreate<number>('PropA',17);
let propA: number | undefined = AppStorage.get<number>('PropA'); // propA in AppStorage == 47, propA in LocalStorage == 17
let link1: SubscribedAbstractProperty<number> | undefined = AppStorage.link<number>('PropA'); // link1.get() == 47
let link2: SubscribedAbstractProperty<number> | undefined = AppStorage.link<number>('PropA'); // link2.get() == 47

link1!.set(48); // 双向同步: link1.get() == link2.get() == prop.get() == 48
link1!.set(49); // 双向同步: link1.get() == link2.get() == prop.get() == 49

storage.get<number>('PropA') // == 17
storage.set<number>('PropA', 101);
storage.get<number>('PropA') // == 101

AppStorage.get<number>('PropA') // == 49
link1!.get() // == 49
link2!.get() // == 49
```

### 从UI内部使用AppStorage和LocalStorage

@StorageLink与AppStorage配合使用，通过AppStorage中的属性创建双向数据同步。

```ts
'use static'

import { Entry, Text, Column, Component, Button, ClickEvent } from '@ohos.arkui.component';
import { LocalStorage, AppStorage, StorageLink, LocalStorageLink } from '@ohos.arkui.stateManagement';

class Data {
  code: number;

  constructor(code: number) {
    this.code = code;
  }
}

@Entry
@Component
struct Index {
  @StorageLink('PropA') storageLink: number = 1;
  @LocalStorageLink('LinkA') localStorageLink: number = 1;
  @StorageLink('PropB') storageLinkObject: Data = new Data(1);
  @LocalStorageLink('LinkB') localStorageLinkObject: Data = new Data(1);
  static {
    AppStorage.setOrCreate<Double>('PropA', 47);
    AppStorage.setOrCreate<Data>('PropB', new Data(50));
  }

  build() {
    Column() {
      Button(`From AppStorage ${this.storageLink}`)
        .onClick((e: ClickEvent) => {
          this.storageLink += 1;
        })

      Button(`From LocalStorage ${this.localStorageLink}`)
        .onClick((e: ClickEvent) => {
          this.localStorageLink += 1;
        })

      // class属性监听需要使用@Observed装饰才能观察变化
      Button(`From AppStorage ${this.storageLinkObject.code}`)
        .onClick((e: ClickEvent) => {
          this.storageLinkObject.code += 1;
        })

      // class属性监听需要使用@Observed装饰才能观察变化
      Button(`From LocalStorage ${this.localStorageLinkObject.code}`)
        .onClick((e: ClickEvent) => {
          this.localStorageLinkObject.code += 1;
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

### AppStorage支持联合类型

在下面的示例中，变量A的类型为number | null，变量B的类型为number | undefined。Text组件初始化分别显示为null和undefined，点击切换为数字，再次点击切换回null和undefined。

```ts
'use static'

import { Entry, Text, Row, Column, Component, Button, ClickEvent } from '@ohos.arkui.component';
import { AppStorage, StorageLink, StoragePropRef } from '@ohos.arkui.stateManagement';

@Component
struct StorageLinkComponent {
  @StorageLink('LinkA') LinkA: number | null = null;
  @StorageLink('LinkB') LinkB: number | undefined = undefined;

  build() {
    Column() {
      Text('@StorageLink接口初始化，@StorageLink取值')
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
  @StoragePropRef('PropA') PropA: number | null = null;
  @StoragePropRef('PropB') PropB: number | undefined = undefined;

  build() {
    Column() {
      Text('@StoragePropRef接口初始化，@StoragePropRef取值')
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

以下示例中，@StorageLink装饰的selectedDate类型为Date。点击Button改变selectedDate的值，视图会随之刷新。

```ts
'use static'

import { Entry, Text, Column, Component, Button, ClickEvent } from '@ohos.arkui.component';
import { AppStorage, StorageLink } from '@ohos.arkui.stateManagement';

@Entry
@Component
struct DateSample {
  @StorageLink('date') selectedDate: Date = new Date('2021-08-08');

  build() {
    Column() {
      Text(`${this.selectedDate}`)
      Button('set selectedDate to 2023-07-08')
        .margin(10)
        .onClick((e: ClickEvent) => {
          AppStorage.setOrCreate('date', new Date('2023-07-08'));
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

在下面的示例中，@StorageLink装饰的message类型为Map\<number, string\>，点击Button改变message的值，视图会随之刷新。

```ts
'use static'

import { Entry, Text, Row, Column, Component, Button, ClickEvent } from '@ohos.arkui.component';
import { AppStorage, StorageLink } from '@ohos.arkui.stateManagement';

@Entry
@Component
struct MapSample {
  @StorageLink('map') message: Map<number, string> = new Map<number, string>([[0, 'a'], [1, 'b'], [3, 'c']]);

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
          AppStorage.get<Map<number, string>>('map')?.delete(0);
        })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```


### 装饰Set类型变量

在下面的示例中，@StorageLink装饰的memberSet类型为Set\<number\>，点击Button改变memberSet的值，视图会随之刷新。

```ts
'use static'

import { Entry, Text, Row, Column, Component, Button, ClickEvent } from '@ohos.arkui.component';
import { AppStorage, StorageLink } from '@ohos.arkui.stateManagement';

@Entry
@Component
struct SetSample {
  @StorageLink('set') memberSet: Set<number> = new Set<number>([0, 1, 2, 3, 4]);

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
            AppStorage.get<Set<number>>('set')?.add(5);
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