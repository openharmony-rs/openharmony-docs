# UI互操作声明文件规范
## 概述
在ArkTS-Dyn与ArkTS-Sta的互操作工程中，语言编译器在一次编译过程中只支持处理一种语法（ArkTS-Dyn或ArkTS-Sta）。

因此，当主模块使用某一种语法编译时，如需调用由另一种语法编写的模块（下文统称为“被调用模块”），则需要依赖编译阶段为被调用模块生成的声明文件和胶水代码来完成语法检查和调用对接。

- **声明文件**：采用主模块语法编写的`.d.ets`文件，用于向主模块提供被调用模块的类型、装饰器等信息。
- **胶水代码**：桥接层代码，用于将被调用模块转换为主模块可识别、可执行的调用形式，从而实现跨语法调用。

互操作工程在编译构建时会自动生成这两类代码文件，生成位置位于各模块的`build`目录下。考虑到互操作场景的复杂性，部分场景下自动生成的声明文件可能不完整，因此需要开发者在生成产物的基础上自行修改声明文件，并通过增量编译使修改生效。

UI互操作无需对胶水代码做额外处理，可直接使用自动生成结果。本文重点给出声明文件的修改规范。


## 声明文件转换规格
### ArkTS-Dyn调用ArkTS-Sta

当ArkTS-Dyn作为主模块，ArkTS-Sta作为被调用模块时，编译器仅接收ArkTS-Dyn语法。因此，在编译构建阶段会基于被调用的ArkTS-Sta模块源码生成符合ArkTS-Dyn语法的声明文件，并将这份声明文件与ArkTS-Dyn主模块源码一起参与编译。

声明文件路径如下：`build/default/intermediates/declgen/default/declgenV1/.../xxx.d.ets`。

下文依次给出声明文件全局修改原则，状态管理V1装饰器转换规格，状态管理V2装饰器转换规格，以及[\@Builder](./state-management/arkts-builder.md)，[WrappedBuilder](./state-management/arkts-v1.2-wrapBuilder.md)，[\@BuilderParam](./state-management/arkts-builderparam.md)转换规格。开发者需要参照这些规则，检视自动生成的声明文件是否符合要求。对于不完整或不符合规格的部分，参照对应规则进行手动调整。若声明文件不符合本节规则，会导致编译声明文件时报错。建议结合[使用场景](#arkts-dyn调用arkts-sta-1)章节，通过完整示例了解这些规则在互操作工程中的用法。

**声明文件全局修改原则**
- ArkTS-Dyn声明文件无需import装饰器及组件。
- ArkTS-Dyn与ArkTS-Sta状态管理接口不一致时，需要修改成ArkTS-Dyn可识别的语法。
- 修复语言自动转换的缺失及错误，如装饰器缺失、类型缺失等。


**状态管理V1装饰器转换规格**

| V1装饰器 | ArkTS-Sta源码示例 | ArkTS-Dyn声明文件示例 |
|---|---|---|
| [\@State](./state-management-static/arkts-static-state.md) | `@State stateVar: string = 'stateVar';` | `@State stateVar: string;` |
| [\@PropRef](./state-management-static/arkts-static-propref.md) | `@PropRef propVar: string = 'propVar';` | `@Prop propVar: string;` |
| [\@Link](./state-management-static/arkts-static-link.md) | `@Link linkVar: string;` | `@Link linkVar: string;` |
| [\@Provide](./state-management-static/arkts-static-provide-and-consume.md) | `@Provide provideVar: string = 'provideVar';` | `@Provide provideVar: string;` |
| [\@Consume](./state-management-static/arkts-static-provide-and-consume.md) | `@Consume consumeVar: string;` | `@Consume consumeVar: string;` |
| [\@LocalStorageLink](./state-management-static/arkts-static-localstorage.md) | `@LocalStorageLink('link1') localStorageLinkVar: number = 11;` | `@LocalStorageLink('link1') localStorageLinkVar: number;` |
| [\@LocalStoragePropRef](./state-management-static/arkts-static-localstorage.md) | `@LocalStoragePropRef('prop1') localStoragePropVar: number = 22;` | `@LocalStorageProp('prop1') localStoragePropVar: number;` |
| [\@StorageLink](./state-management-static/arkts-static-appstorage.md) | `@StorageLink('link2') storageLinkVar: number = 33;` | `@StorageLink('link2') storageLinkVar: number;` |
| [\@StoragePropRef](./state-management-static/arkts-static-appstorage.md) | `@StoragePropRef('prop2') storagePropVar: number = 44;` | `@StorageProp('prop2') storagePropVar: number;` |
| [\@Watch](./state-management-static/arkts-static-watch.md) | `@State @Watch('stateOnChange') watchVar: string = 'Hello';` | `@State @Watch('stateOnChange') watchVar: string;` |
| [\@ObjectLink](./state-management-static/arkts-static-observed-and-objectlink.md) | `@ObjectLink person: Person;` | `@ObjectLink person: Person;` |
| [\@Observed](./state-management-static/arkts-static-observed-and-objectlink.md)/[\@Track](./state-management-static/arkts-static-track.md) | `@Observed export class Person { @Track age: number = 20; }` | `@Observed export declare class Person { @Track age: number; }` |

**状态管理V2装饰器转换规格**
| V2装饰器 | ArkTS-Sta源码示例 | ArkTS-Dyn声明文件示例 |
|---|---|---|
| [\@Local](./state-management-static/arkts-static-new-local.md) | `@Local localVar: string = 'localVar';` | `@Local localVar: string;` |
| [\@Param](./state-management-static/arkts-static-new-param.md) | `@Param paramVar: string = 'paramVar';` | `@Param paramVar: string;` |
| [\@Once](./state-management-static/arkts-static-new-once.md) | `@Param @Once onceParam: string = 'onceParam';` | `@Param @Once onceParam: string;` |
| [\@Event](./state-management-static/arkts-static-new-event.md) | `@Event eventVar: (val: number) => void;` | `@Event eventVar: (val: number) => void;` |
| [\@Provider](./state-management-static/arkts-static-new-provider-and-consumer.md) | `@Provider providerVar: string = 'providerVar';` | `@Provider() providerVar: string;` |
| [\@Consumer](./state-management-static/arkts-static-new-provider-and-consumer.md) | `@Consumer consumerVar: string = 'consumerVar';` | `@Consumer() consumerVar: string;` |
| [\@Monitor](./state-management-static/arkts-static-new-monitor.md) | `@Monitor(['localVar', 'paramVar']) onStrChange(monitor: IMonitor) {}` | `public onStrChange(monitor: IMonitor): void;` |
| [\@Computed](./state-management-static/arkts-static-new-computed.md) | `@Computed get computeVar(): string {}` | `public get computeVar(): string;` |
| [\@ObservedV2/\@Trace](./state-management-static/arkts-static-new-observedV2-and-trace.md) | `@ObservedV2 export class PersonV2 { @Trace age: number = 20; }` | `@ObservedV2 export declare class PersonV2 { @Trace age: number; }` |

**\@Builder，WrappedBuilder，\@BuilderParam转换规格**
| \@Builder相关语法 | ArkTS-Sta源码示例 | ArkTS-Dyn声明文件示例 |
|---|---|---|
| [\@Builder](./state-management/arkts-builder.md) | `@Builder export function myBuilder(value: string) { Text(value) }` | `@Builder export declare function myBuilder(value: string): void;` |
| [WrappedBuilder](./state-management/arkts-v1.2-wrapBuilder.md) | `export const myWrappedBuilder: WrappedBuilder<@Builder (value: string) => void> = wrapBuilder(myBuilder);` | `export declare const myWrappedBuilder: WrappedBuilder<[string]>;` |
| [\@BuilderParam](./state-management/arkts-builderparam.md) | `@BuilderParam myBuilderParam: (value: string) => void = this.myText;` | `@BuilderParam myBuilderParam: (value: string) => void;` |


### ArkTS-Sta调用ArkTS-Dyn
当ArkTS-Sta作为主模块，ArkTS-Dyn作为被调用模块时，编译器仅接收ArkTS-Sta语法。因此，在编译构建阶段会基于被调用的ArkTS-Dyn模块源码生成符合ArkTS-Sta语法的声明文件，并将这份声明文件与ArkTS-Sta主模块源码一起参与编译。

声明文件路径如下：`build/default/intermediates/declgen/default/declgenV2/.../xxx.d.ets`。

下文依次给出声明文件全局修改原则，状态管理V1装饰器转换规格，状态管理V2装饰器转换规格，以及[\@Builder](./state-management/arkts-builder.md)，[WrappedBuilder](./state-management/arkts-v1.2-wrapBuilder.md)，[\@BuilderParam](./state-management/arkts-builderparam.md)转换规格。开发者需要参照这些规则，检视自动生成的声明文件是否符合要求。对于不完整或不符合规格的部分，参照对应规则进行手动调整。若声明文件不符合本节规则，会导致编译声明文件时报错。建议结合[使用场景](#arkts-sta调用arkts-dyn-1)章节，通过完整示例了解这些规则在互操作工程中的用法。

**声明文件全局修改原则**
- ArkTS-Sta声明文件需要import装饰器及组件。
- ArkTS-Sta与ArkTS-Dyn状态管理接口不一致时，需要修改成符合ArkTS-Sta的语法。
- 修复语言自动转换的缺失及错误，如装饰器缺失、类型缺失等。

**状态管理V1装饰器转换规格**
| V1装饰器 | ArkTS-Dyn源码示例 | ArkTS-Sta声明文件示例 |
|---|---|---|
| [\@State](./state-management/arkts-state.md) | `@State stateVar: string = 'stateVar';` | `@State stateVar: string;` |
| [\@Prop](./state-management/arkts-prop.md) | `@Prop propVar: string = 'propVar';` | `@Prop propVar: string;` |
| [\@Link](./state-management/arkts-link.md) | `@Link linkVar: string;` | `@Link linkVar: string;` |
| [\@Provide](./state-management/arkts-provide-and-consume.md) | `@Provide provideVar: string = 'provideVar';` | `@Provide provideVar: string;` |
| [\@Consume](./state-management/arkts-provide-and-consume.md) | `@Consume consumeVar: string;` | `@Consume consumeVar: string;` |
| [\@LocalStorageLink](./state-management/arkts-localstorage.md) | `@LocalStorageLink('link1') localStorageLinkVar: number = 11;` | `@LocalStorageLink('link1') localStorageLinkVar: number;` |
| [\@LocalStorageProp](./state-management/arkts-localstorage.md) | `@LocalStorageProp('prop1') localStoragePropVar: number = 22;` | `@LocalStorageProp('prop1') localStoragePropVar: number;` |
| [\@StorageLink](./state-management/arkts-appstorage.md) | `@StorageLink('link2') storageLinkVar: number = 33;` | `@StorageLink('link2') storageLinkVar: number;` |
| [\@StorageProp](./state-management/arkts-appstorage.md)  | `@StorageProp('prop2') storagePropVar: number = 44;` | `@StorageProp('prop2') storagePropVar: number;` |
| [\@Watch](./state-management/arkts-watch.md) | `@State @Watch('stateOnChange') watchVar: string = 'Hello';` | `@State @Watch('stateOnChange') watchVar: string;` |
| [\@ObjectLink](./state-management/arkts-observed-and-objectlink.md) | `@ObjectLink person: Person;` | `@ObjectLink person: Person;` |
| [\@Observed](./state-management/arkts-observed-and-objectlink.md)/[\@Track](./state-management/arkts-track.md) | `@Observed export class Person { @Track age: number = 20; }` | `@Observed export declare class Person { @Track age: number; }` |

**状态管理V2装饰器转换规格**
| V2装饰器 | ArkTS-Dyn源码示例 | ArkTS-Sta声明文件示例 |
|---|---|---|
| [\@Local](./state-management/arkts-new-local.md) | `@Local localVar: string = 'localVar';` | `@Local localVar: string;` |
| [\@Param](./state-management/arkts-new-param.md) | `@Param paramVar: string = 'paramVar';` | `@Param paramVar: string;` |
| [\@Once](./state-management/arkts-new-once.md) | `@Param @Once onceParam: string = 'onceParam';` | `@Param @Once onceParam: string;` |
| [\@Event](./state-management/arkts-new-event.md) | `@Event eventVar: (val: number) => void;` | `@Event eventVar: (val: number) => void;` |
| [\@Provider](./state-management/arkts-new-provider-and-consumer.md) | `@Provider() providerVar: string = 'providerVar';` | `@Provider providerVar: string;` |
| [\@Consumer](./state-management/arkts-new-provider-and-consumer.md) | `@Consumer() consumerVar: string = 'consumerVar';` | `@Consumer consumerVar: string;` |
| [\@Monitor](./state-management/arkts-new-monitor.md) | `@Monitor('localVar', 'paramVar') onStrChange(monitor: IMonitor) {}` | `@Monitor(['localVar', 'paramVar']) onStrChange(monitor: IMonitor): void;` |
| [\@Computed](./state-management/arkts-new-computed.md) | `@Computed get computeVar(): string {}` | `@Computed get computeVar(): string;` |
| [\@ObservedV2/\@Trace](./state-management/arkts-new-observedV2-and-trace.md) | `@ObservedV2 export class PersonV2 { @Trace age: number = 20; }` | `@ObservedV2 export declare class PersonV2 { @Trace age: number; }` |

**\@Builder，WrappedBuilder，\@BuilderParam转换规格**
| \@Builder相关语法 | ArkTS-Dyn源码示例 | ArkTS-Sta声明文件示例 |
|---|---|---|
| [\@Builder](./state-management/arkts-builder.md) | `@Builder export function myBuilder(value: string) { Text(value) }` | `@Builder export declare function myBuilder(value: string): void;` |
| [WrappedBuilder](./state-management/arkts-wrapBuilder.md) | `export const myWrappedBuilder: WrappedBuilder<[string]> = wrapBuilder(myBuilder);` | `export declare const myWrappedBuilder: WrappedBuilder<Array<Any>>;` |
| [\@BuilderParam](./state-management/arkts-builderparam.md) | `@BuilderParam myBuilderParam: (value: string) => void = this.myText;` | `@BuilderParam myBuilderParam: (value: string) => void;` |

## 使用场景
### ArkTS-Dyn调用ArkTS-Sta
结合[声明文件转换规格](#arkts-dyn调用arkts-sta)，下文依次给出状态管理V1装饰器，状态管理V2装饰器，以及[\@Builder](./state-management/arkts-builder.md)，[WrappedBuilder](./state-management/arkts-v1.2-wrapBuilder.md)，[\@BuilderParam](./state-management/arkts-builderparam.md)的使用场景。

**状态管理V1装饰器**

完整示例结构如下所示：
```txt
project/
├── entry/                            # ArkTS-Dyn主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets     # 调用ArkTS-Sta V1自定义组件
│
└── static_library/                   # ArkTS-Sta子模块
    ├── build/
    │   └── default/
    │        └── intermediates/    
    │           └── declgen/
    │               └── default/
    │                   └── declgenV1/
    │                       └── static_library/
    │                           └── src/
    │                               └── main/
    │                                   └── ets/
    │                                       └── components/
    │                                           └── MainPage.d.ets # ArkTS-Sta自定义组件对应的声明文件
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets  # ArkTS-Sta V1自定义组件
            
```

下面的代码示例展示了在ArkTS-Dyn中调用ArkTS-Sta自定义组件并使用状态管理V1装饰器的场景下，修改声明文件的规格。

- 创建ArkTS-Sta子模块`static_library`，在`static_library/src/main/ets/components`目录创建并导出自定义组件。如何创建子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```TypeScript
'use static';

// static_library/src/main/ets/components/MainPage.ets
import { Text, Column, Component } from '@ohos.arkui.component';
import { Observed, Track, State, PropRef, Link, Provide, Consume, LocalStorageLink, LocalStoragePropRef, StorageLink, StoragePropRef, Watch, ObjectLink } from '@ohos.arkui.stateManagement';

@Observed
export class Person{
  name: string = 'person';
  @Track age: number = 20;
}

@Component
export struct Child {
  @State stateVar: string = 'stateVar';
  @PropRef propVar: string = 'propVar';
  @Link linkVar: string;
  @Provide provideVar: string = 'provideVar';
  @Consume consumeVar: string;
  @LocalStorageLink('link1') localStorageLinkVar: number = 11;
  @LocalStoragePropRef('prop1') localStoragePropVar: number = 22;
  @StorageLink('link2') storageLinkVar: number = 33;
  @StoragePropRef('prop2') storagePropVar: number = 44;
  @State @Watch('stateOnChange') watchVar: string = 'Hello World';
  @ObjectLink person: Person;
  stateOnChange(propName: string) {}

  build() {
    Column() {
      Text(`${this.stateVar}`)
      Text(`${this.propVar}`)
      Text(`${this.linkVar}`)
      Text(`${this.provideVar}`)
      Text(`${this.consumeVar}`)
      Text(`${this.localStorageLinkVar}`)
      Text(`${this.localStoragePropVar}`)
      Text(`${this.storageLinkVar}`)
      Text(`${this.storagePropVar}`)
      Text(`${this.watchVar}`)
      Text(`${this.person.age}`)
    }
  }
}
```

```TypeScript
'use static'

// static_library/index.ets
export { Child, Person } from './src/main/ets/components/MainPage';
```

- 手动修改`static_library/src/main/ets/components/MainPage.ets`对应的声明文件，路径为`static_library/build/default/intermediates/declgen/default/declgenV1/static_library/src/main/ets/components/MainPage.d.ets`。

```TypeScript
// static_library/build/default/intermediates/declgen/default/declgenV1/static_library/src/main/ets/components/MainPage.d.ets

// 删除多余的import语句
@Observed
export declare class Person {
    public get name(): string;
    public set name(value: string);
    // @Track装饰的属性语言自动转换出getter，setter，需要删除
    @Track age: number;
    constructor();
}
@Component
export declare struct Child {
    @State
    stateVar: string;
    // 需要将@PropRef转换成@Prop
    @Prop
    propVar: string;
    @Link
    linkVar: string;
    // @Provide ArkTS-Dyn与ArkTS-Sta接口不一致，此处参考ArkTS-Dyn语法
    @Provide
    provideVar: string;
    // @Consume ArkTS-Dyn与ArkTS-Sta接口不一致，此处参考ArkTS-Dyn语法
    @Consume
    consumeVar: string;
    @LocalStorageLink('link1')
    localStorageLinkVar: number;
    // 需要将@LocalStoragePropRef转换成@LocalStorageProp
    @LocalStorageProp('prop1')
    localStoragePropVar: number;
    @StorageLink('link2')
    storageLinkVar: number;
    // 需要将@StoragePropRef转换成@StorageProp
    @StorageProp('prop2')
    storagePropVar: number;
    @State
    @Watch('stateOnChange')
    watchVar: string;
    @ObjectLink
    person: Person;
    public stateOnChange(propName: string): void;
    public build(): void;
}
```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。
```json
// entry/oh-package.json5

"dependencies": {
  "static_library": "file:../static_library"
}
```

- 在ArkTS-Dyn主模块`entry`中引入ArkTS-Sta组件。
```TypeScript
// entry/src/main/ets/pages/Index.ets

import { Child, Person } from 'static_library';

@Entry
@Component
struct Parent {
  @State stateVar: string = 'Parent';
  @Provide consumeVar: string = 'consumeVar';
  @State person: Person = new Person();

  build() {
    Column() {
      Child({
        linkVar: this.stateVar,
        person: this.person
      })
    }
  }
}
```

**状态管理V2装饰器**

完整示例结构如下所示：
```txt
project/
├── entry/                            # ArkTS-Dyn主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets     # 调用ArkTS-Sta V2自定义组件
│
└── static_library/                   # ArkTS-Sta子模块
    ├── build/
    │   └── default/
    │        └── intermediates/    
    │           └── declgen/
    │               └── default/
    │                   └── declgenV1/
    │                       └── static_library/
    │                           └── src/
    │                               └── main/
    │                                   └── ets/
    │                                       └── components/
    │                                           └── MainPage.d.ets # ArkTS-Sta自定义组件对应的声明文件
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets  # ArkTS-Sta V2自定义组件
            
```

下面的代码示例展示了在ArkTS-Dyn中调用ArkTS-Sta自定义组件并使用状态管理V2装饰器的场景下，修改声明文件的规格。

- 创建ArkTS-Sta子模块`static_library`，在`static_library/src/main/ets/components`目录创建并导出自定义组件。如何创建子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```TypeScript
'use static'

// static_library/src/main/ets/components/MainPage.ets
import { ComponentV2, Text, Column } from '@ohos.arkui.component';
import { Local, Param, Once, Event, Provider, Consumer, Monitor, IMonitor, Computed, ObservedV2, Trace } from '@ohos.arkui.stateManagement';

@ObservedV2
export class Person{
  name: string = 'person';
  @Trace age: number = 20;
}

@ComponentV2
export struct ChildV2 {
  @Local localVar: string = 'localVar';
  @Param paramVar: string = 'paramVar';
  @Param @Once onceParam: string = 'onceParam';
  @Event eventVar: (val: number) => void;
  @Provider providerVar: string = 'providerVar';
  @Consumer consumerVar: string = 'consumerVar';
  @Monitor(['localVar', 'paramVar'])
  onStrChange(monitor: IMonitor) {
    monitor.dirty.forEach((path: string) => {
      console.info(`${path} changed from ${monitor.value<string>(path)?.before} to ${monitor.value<string>(path)?.now}`);
    });
  }
  @Computed
  get computeVar(): string {
    return this.localVar + this.paramVar;
  }
  person: Person = new Person();

  build() {
    Column() {
      Text(`${this.localVar}`)
      Text(`${this.paramVar}`)
      Text(`${this.onceParam}`)
      Text(`${this.providerVar}`)
      Text(`${this.consumerVar}`)
      Text(`${this.person.age}`)
    }
  }
}
```

```TypeScript
'use static'

// static_library/index.ets
export { ChildV2 } from './src/main/ets/components/MainPage';
```

- 手动修改`static_library/src/main/ets/components/MainPage.ets`对应的声明文件，路径为`static_library/build/default/intermediates/declgen/default/declgenV1/static_library/src/main/ets/components/MainPage.d.ets`。

```TypeScript
//static_library/build/default/intermediates/declgen/default/declgenV1/static_library/src/main/ets/components/MainPage.d.ets

// 删除多余的import语句
@ObservedV2
export declare class Person {
    public get name(): string;
    public set name(value: string);
    // @Trace装饰的属性语言自动转换出getter，setter，需要删除
    @Trace age: number;
    constructor();
}
@ComponentV2
export declare struct ChildV2 {
    @Local
    localVar: string;
    @Param
    paramVar: string;
    @Param
    @Once
    onceParam: string;
    @Event
    eventVar: (val: number) => void;
    // @Provider ArkTS-Dyn与ArkTS-Sta接口不一致，此处参考ArkTS-Dyn语法
    @Provider()
    providerVar: string;
    // @Consumer ArkTS-Dyn与ArkTS-Sta接口不一致，此处参考ArkTS-Dyn语法
    @Consumer()
    consumerVar: string;
    // 需要删除@Monitor装饰器
    public onStrChange(monitor: IMonitor): void;
    // 需要删除@Computed装饰器
    public get computeVar(): string;
    person: Person;
    public build(): void;
}
```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

```json
// entry/oh-package.json5

"dependencies": {
  "static_library": "file:../static_library"
}
```

- 在ArkTS-Dyn主模块`entry`中引入ArkTS-Sta组件。

```TypeScript
// entry/src/main/ets/pages/Index.ets

import { ChildV2 } from 'static_library';
@Entry
@ComponentV2
struct Index {
  @Provider() consumerVar: string = 'consumerVar';
  build() {
    Column() {
      ChildV2()
    }
  }
}
```

**\@Builder，WrappedBuilder，\@BuilderParam**

完整示例结构如下所示：
```txt
project/
├── entry/                            # ArkTS-Dyn主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets     # 调用ArkTS-Sta @Builder等
│
└── static_library/                   # ArkTS-Sta子模块
    ├── build/
    │   └── default/
    │        └── intermediates/    
    │           └── declgen/
    │               └── default/
    │                   └── declgenV1/
    │                       └── static_library/
    │                           └── src/
    │                               └── main/
    │                                   └── ets/
    │                                       └── components/
    │                                           └── MainPage.d.ets # ArkTS-Sta @Builder对应的声明文件
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets  # ArkTS-Sta @Builder等
            
```

下面的代码示例展示了在ArkTS-Dyn中调用ArkTS-Sta自定义组件并使用\@Builder，WrappedBuilder，\@BuilderParam，修改声明文件的规格。

- 创建ArkTS-Sta子模块`static_library`，在`static_library/src/main/ets/components`目录创建并导出自定义组件。如何创建子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```TypeScript
'use static';

// static_library/src/main/ets/components/MainPage.ets
import { Text, Column, Component, Builder, BuilderParam, WrappedBuilder, wrapBuilder } from '@ohos.arkui.component';

@Component
export struct Child {
  @Builder
  myText(content: string, num: number) {
    Text('myText')
  }
  @BuilderParam customBuilderParam: (content: string, num: number) => void = this.myText;

  build() {
    Column() {
      this.customBuilderParam('hello world', 30)
    }
  }
}

@Builder
export function staticBuilder(value: string, size: number) {
  Text(value).fontSize(size)
}

export const staticWrappedBuilder: WrappedBuilder<@Builder (value: string, size: number) => void> = wrapBuilder(staticBuilder);
```

```TypeScript
'use static'

// static_library/index.ets
export { Child, staticBuilder, staticWrappedBuilder } from './src/main/ets/components/MainPage';
```

- 手动修改`static_library/src/main/ets/components/MainPage.ets`对应的声明文件，路径为`static_library/build/default/intermediates/declgen/default/declgenV1/static_library/src/main/ets/components/MainPage.d.ets`。

```TypeScript
// static_library/build/default/intermediates/declgen/default/declgenV1/static_library/src/main/ets/components/MainPage.d.ets

// 删除多余的import语句
@Builder
export declare function staticBuilder(value: string, size: number): void;
// WrappedBuilder ArkTS-Dyn与ArkTS-Sta接口不一致，此处参考ArkTS-Dyn语法
export declare const staticWrappedBuilder: WrappedBuilder<[string , number]>;
@Component
export declare struct Child {
    @Builder
    public myText(content: string, num: number): void;
    @BuilderParam
    customBuilderParam: (content: string, num: number) => void;
    public build(): void;
}
```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。
```json
// entry/oh-package.json5

"dependencies": {
  "static_library": "file:../static_library"
}
```

- 在ArkTS-Dyn主模块`entry`中调用ArkTS-Sta \@Builder，WrappedBuilder，以及传递\@BuilderParam。

```TypeScript
// entry/src/main/ets/pages/Index.ets

import { Child, staticBuilder, staticWrappedBuilder } from 'static_library';

@Entry
@Component
struct Parent {
    @Builder
    parentText(content: string, num: number) {
      Text(content)
        .fontSize(num)
    }

  build() {
    Column() {
      Child({ customBuilderParam: this.parentText })
      staticBuilder('dynamicBuilder', 20)
      staticWrappedBuilder.builder('dynamicWrappedBuilder', 20)
    }
  }
}
```

### ArkTS-Sta调用ArkTS-Dyn
结合[声明文件转换规格](#arkts-sta调用arkts-dyn)，下文依次给出状态管理V1装饰器，状态管理V2装饰器，以及[\@Builder](./state-management/arkts-builder.md)，[WrappedBuilder](./state-management/arkts-v1.2-wrapBuilder.md)，[\@BuilderParam](./state-management/arkts-builderparam.md)的使用场景。

**状态管理V1装饰器**

完整示例结构如下所示：
```txt
project/
├── entry/                            # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets     # 调用ArkTS-Dyn V1自定义组件
│
└── dynamic_library/                   # ArkTS-Dyn子模块
    ├── build/
    │   └── default/
    │        └── intermediates/    
    │           └── declgen/
    │               └── default/
    │                   └── declgenV1/
    │                       └── dynamic_library/
    │                           └── src/
    │                               └── main/
    │                                   └── ets/
    │                                       └── components/
    │                                           └── MainPage.d.ets # ArkTS-Dyn自定义组件对应的声明文件
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets  # ArkTS-Dyn V1自定义组件
            
```

下面的代码示例展示了在ArkTS-Sta中调用ArkTS-Dyn自定义组件并使用状态管理V1装饰器的场景下，修改声明文件的规格。

- 创建ArkTS-Dyn子模块`dynamic_library`，在`dynamic_library/src/main/ets/components`目录创建并导出自定义组件。如何创建子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```TypeScript
// dynamic_library/src/main/ets/components/MainPage.ets

@Observed
export class Person{
  name: string = 'person';
  @Track age: number = 20;
}

@Component
export struct Child {
  @State stateVar: string = 'stateVar';
  @Prop propVar: string = 'propVar';
  @Link linkVar: string;
  @Provide provideVar: string = 'provideVar';
  @Consume consumeVar: string;
  @LocalStorageLink('link1') localStorageLinkVar: number = 11;
  @LocalStorageProp('Prop1') localStoragePropVar: number = 22;
  @StorageLink('link2') storageLinkVar: number = 33;
  @StorageProp('Prop2') storagePropVar: number = 44;
  @State @Watch('stateOnChange') watchVar: string = 'Hello World';
  @ObjectLink person: Person;
  stateOnChange(propName: string) {}

  build() {
    Column() {
      Text(`${this.stateVar}`)
      Text(`${this.propVar}`)
      Text(`${this.linkVar}`)
      Text(`${this.provideVar}`)
      Text(`${this.consumeVar}`)
      Text(`${this.localStorageLinkVar}`)
      Text(`${this.localStoragePropVar}`)
      Text(`${this.storageLinkVar}`)
      Text(`${this.storagePropVar}`)
      Text(`${this.watchVar}`)
      Text(`${this.person.age}`)
    }
  }
}
```

```TypeScript
// dynamic_library/index.ets

export { Child, Person } from './src/main/ets/components/MainPage';
```

- 手动修改`dynamic_library/src/main/ets/components/MainPage.ets`对应的声明文件，路径为`dynamic_library/build/default/intermediates/declgen/default/declgenV2/dynamic_library/src/main/ets/components/MainPage.d.ets`。

```TypeScript
'use static';
// dynamic_library/build/default/intermediates/declgen/default/declgenV2/dynamic_library/src/main/ets/components/MainPage.d.ets

// 添加对应import语句
import { compatibleComponent, getCompatibleState, transferCompatibleBuilder, transferCompatibleUpdatableBuilder } from 'arkui.component.interop';
import { State, Prop, Link, Provide, Consume, LocalStorageLink, LocalStorageProp, StorageLink, StorageProp, ObjectLink, Observed, Track, Watch } from '@ohos.arkui.stateManagement';
import { Component } from '@ohos.arkui.component';
@Component
export declare struct Child {
    @State
    stateVar: string;
    @Prop
    propVar: string;
    @Link
    linkVar: string;
    // @Provide ArkTS-Sta与ArkTS-Dyn接口不一致，此处参考ArkTS-Sta语法
    @Provide
    provideVar: string;
    // @Consume ArkTS-Sta与ArkTS-Dyn接口不一致，此处参考ArkTS-Sta语法
    @Consume
    consumeVar: string;
    @LocalStorageLink('link1')
    localStorageLinkVar: number;
    @LocalStorageProp('Prop1')
    localStoragePropVar: number;
    @StorageLink('link2')
    storageLinkVar: number;
    @StorageProp('Prop2')
    storagePropVar: number;
    @State
    @Watch('stateOnChange')
    watchVar: string;
    @ObjectLink
    person: Person;
    stateOnChange(propName: string): void;
    build(): void;
}
@Observed
export declare class Person {
    name: string;
    @Track age: number;
}
```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。
```json
// entry/oh-package.json5

"dependencies": {
  "dynamic_library": "file:../dynamic_library"
}
```

- 在ArkTS-Sta主模块`entry`中引入ArkTS-Dyn组件。

```TypeScript
'use static';

// entry/src/main/ets/pages/Index.ets
import { Entry, Column, Component } from '@ohos.arkui.component';
import { State, Provide } from '@ohos.arkui.stateManagement';
import { Child, Person } from 'dynamic_library';

@Entry
@Component
struct Parent {
  @State stateVar: string = 'Parent';
  @Provide consumeVar: string = 'consumeVar';
  @State person: Person = new Person();

  build() {
    Column() {
      Child({
        linkVar: this.stateVar,
        person: this.person
      })
    }
  }
}
```

**状态管理V2装饰器**

完整示例结构如下所示：
```txt
project/
├── entry/                            # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets     # 调用ArkTS-Dyn V2自定义组件
│
└── dynamic_library/                   # ArkTS-Dyn子模块
    ├── build/
    │   └── default/
    │        └── intermediates/    
    │           └── declgen/
    │               └── default/
    │                   └── declgenV1/
    │                       └── dynamic_library/
    │                           └── src/
    │                               └── main/
    │                                   └── ets/
    │                                       └── components/
    │                                           └── MainPage.d.ets # ArkTS-Dyn自定义组件对应的声明文件
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets  # ArkTS-Dyn V2自定义组件
            
```

下面的代码示例展示了在ArkTS-Sta中调用ArkTS-Dyn自定义组件并使用状态管理V2装饰器的场景下，修改声明文件的规格。

- 创建ArkTS-Dyn子模块`dynamic_library`，在`dynamic_library/src/main/ets/components`目录创建并导出自定义组件。如何创建子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```TypeScript
// dynamic_library/src/main/ets/components/MainPage.ets

@ObservedV2
export class Person{
  name: string = 'person';
  @Trace age: number = 20;
}

@ComponentV2
export struct ChildV2 {
  @Local localVar: string = 'localVar';
  @Param paramVar: string = 'paramVar';
  @Param @Once onceParam: string = 'onceParam';
  @Event eventVar: (val: number) => void;
  @Provider() providerVar: string = 'providerVar';
  @Consumer() consumerVar: string = 'consumerVar';
  @Monitor('localVar', 'paramVar')
  onStrChange(monitor: IMonitor) {
    monitor.dirty.forEach((path: string) => {
      console.info(`${path} changed from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`);
    });
  }
  @Computed
  get computeVar(): string {
    return this.localVar + this.paramVar;
  }
  person: Person = new Person();

  build() {
    Column() {
      Text(`${this.localVar}`)
      Text(`${this.paramVar}`)
      Text(`${this.onceParam}`)
      Text(`${this.providerVar}`)
      Text(`${this.consumerVar}`)
      Text(`${this.person.age}`)
    }
  }
}
```

```TypeScript
// dynamic_library/index.ets

export { ChildV2 } from './src/main/ets/components/MainPage';
```

- 手动修改`dynamic_library/src/main/ets/components/MainPage.ets`对应的声明文件，路径为`dynamic_library/build/default/intermediates/declgen/default/declgenV2/dynamic_library/src/main/ets/components/MainPage.d.ets`。

```TypeScript
'use static';
// dynamic_library/build/default/intermediates/declgen/default/declgenV2/dynamic_library/src/main/ets/components/MainPage.d.ets

// 添加对应import语句
import { compatibleComponent, getCompatibleState, transferCompatibleBuilder, transferCompatibleUpdatableBuilder } from 'arkui.component.interop';
import { Local, Param, Once, Event, Provider, Consumer, Monitor, ObservedV2, IMonitor, Trace, Computed} from '@ohos.arkui.stateManagement';
import { ComponentV2 } from '@ohos.arkui.component';
@ComponentV2
export declare struct ChildV2 {
    @Local
    localVar: string;
    @Param
    readonly paramVar: string;
    @Param
    @Once
    onceParam: string;
    @Event
    eventVar: (val: number) => void;
    // @Provider ArkTS-Sta与ArkTS-Dyn接口不一致，此处参考ArkTS-Sta语法
    @Provider
    providerVar: string;
    // @Consumer ArkTS-Sta与ArkTS-Dyn接口不一致，此处参考ArkTS-Sta语法
    @Consumer
    consumerVar: string;
    // @Monitor ArkTS-Sta与ArkTS-Dyn接口不一致，此处参考ArkTS-Sta语法
    @Monitor(['localVar', 'paramVar'])
    onStrChange(monitor: IMonitor): void;
    @Computed
    get computeVar(): string;
    person: Person;
    build(): void;
}
@ObservedV2
export declare class Person {
    name: string;
    @Trace age: number;
}
```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。
```json
// entry/oh-package.json5

"dependencies": {
  "dynamic_library": "file:../dynamic_library"
}
```

- 在ArkTS-Sta主模块`entry`中引入ArkTS-Dyn组件。

```TypeScript
'use static';

// entry/src/main/ets/pages/Index.ets
import { Entry, Column, ComponentV2 } from '@ohos.arkui.component';
import { Provider } from '@ohos.arkui.stateManagement';
import { ChildV2 } from 'dynamic_library';

@Entry
@ComponentV2
struct Index {
  @Provider consumerVar: string = 'consumerVar';
  build() {
    Column() {
      ChildV2()
    }
  }
}
```

**\@Builder，WrappedBuilder，\@BuilderParam**
完整示例结构如下所示：
```txt
project/
├── entry/                            # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets     # 调用ArkTS-Dyn @Builder等
│
└── dynamic_library/                   # ArkTS-Dyn子模块
    ├── build/
    │   └── default/
    │        └── intermediates/    
    │           └── declgen/
    │               └── default/
    │                   └── declgenV1/
    │                       └── dynamic_library/
    │                           └── src/
    │                               └── main/
    │                                   └── ets/
    │                                       └── components/
    │                                           └── MainPage.d.ets # ArkTS-Dyn @Builder对应的声明文件
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets  # ArkTS-Dyn @Builder等
            
```

下面的代码示例展示了在ArkTS-Sta中调用ArkTS-Dyn自定义组件并使用\@Builder，WrappedBuilder，\@BuilderParam的场景下，修改声明文件的规格。

- 创建ArkTS-Dyn子模块`dynamic_library`，在`dynamic_library/src/main/ets/components`目录创建并导出自定义组件。如何创建子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```TypeScript
// dynamic_library/src/main/ets/components/MainPage.ets

@Component
export struct Child {
  @Builder
  myText(content: string, num: number) {
    Text('myText')
  }
  @BuilderParam customBuilderParam: (content: string, num: number) => void = this.myText;

  build() {
    Column() {
      this.customBuilderParam('hello world', 30)
    }
  }
}

@Builder
export function staticBuilder(value: string, size: number) {
  Text(value).fontSize(size)
}

export const staticWrappedBuilder: WrappedBuilder<[string, number]> = wrapBuilder(staticBuilder);
```

```TypeScript
// dynamic_library/index.ets

export { Child, staticBuilder, staticWrappedBuilder } from './src/main/ets/components/MainPage';
```

- 手动修改`dynamic_library/src/main/ets/components/MainPage.ets`对应的声明文件，路径为`dynamic_library/build/default/intermediates/declgen/default/declgenV2/dynamic_library/src/main/ets/components/MainPage.d.ets`。

```TypeScript
'use static';
// dynamic_library/build/default/intermediates/declgen/default/declgenV2/dynamic_library/src/main/ets/components/MainPage.d.ets

// 添加对应import语句
import { compatibleComponent, getCompatibleState, transferCompatibleBuilder, transferCompatibleUpdatableBuilder } from 'arkui.component.interop';
import { Component, Builder, BuilderParam, WrappedBuilder } from '@ohos.arkui.component';
@Component
export declare struct Child {
    @Builder
    myText(content: string, num: number): void;
    @BuilderParam
    customBuilderParam: (content: string, num: number) => void;
    build(): void;
}
@Builder
export declare function staticBuilder(value: string, size: number): void;
// WrappedBuilder ArkTS-Sta与ArkTS-Dyn接口不一致，此处参考ArkTS-Sta语法
export declare const staticWrappedBuilder: WrappedBuilder<Array<Any>>;
```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。
```json
// entry/oh-package.json5

"dependencies": {
  "dynamic_library": "file:../dynamic_library"
}
```

- 在ArkTS-Sta主模块`entry`中调用ArkTS-Dyn \@Builder，WrappedBuilder，以及传递\@BuilderParam。

```TypeScript
'use static';

// entry/src/main/ets/pages/Index.ets
import { Entry, Column, Component, Text, Builder, compatibleWrappedBuilder } from '@ohos.arkui.component';
import { Provider } from '@ohos.arkui.stateManagement';
import { Child, staticBuilder, staticWrappedBuilder } from 'dynamic_library';

@Entry
@Component
struct Parent {
  @Builder
  parentText(content: string, num: number) {
    Text(content)
      .fontSize(num)
  }

  build() {
    Column() {
      Child({ customBuilderParam: this.parentText })
      staticBuilder('dynamicBuilder', 20)
      compatibleWrappedBuilder(staticWrappedBuilder, ESValue.wrap('dynamicWrappedBuilder'), ESValue.wrap(20))
    }
  }
}
```