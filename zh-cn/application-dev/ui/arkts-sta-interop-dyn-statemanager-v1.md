# 状态管理V1互操作

## 介绍

ArkTS-Sta使用ArkTS-Dyn自定义组件时，涉及状态管理V1交互的场景主要包括：

1. ArkTS-Dyn子组件通过ArkTS-Sta父组件初始化状态数据并进行状态绑定。
2. ArkTS-Dyn子组件通过[@Consume](../ui/state-management/arkts-provide-and-consume.md)和ArkTS-Sta祖先节点进行交互。
3. ArkTS-Dyn子组件和ArkTS-Sta的[AppStorage](../ui/state-management/arkts-appstorage.md)进行交互。
4. ArkTS-Dyn子组件和ArkTS-Sta的[LocalStorage](../ui/state-management/arkts-localstorage.md)进行交互。

## 和ArkTS-Dyn的\@State交互

状态管理V1互操作支持在ArkTS-Sta上下文中初始化ArkTS-Dyn自定义组件的[\@State](../ui/state-management/arkts-state.md)装饰变量，相关初始化规则与非互操作场景下保持一致。


如下示例展示了相关用法。


- 创建ArkTS-Dyn子模块dynamic_module，并在动态模块中创建和导出自定义组件。如何创建子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

  ```
  @Component
  export struct Child {
    @State count: number = 0;
  
    build() {
      Column() {
        Button(`click times: ${this.count}`)
          .onClick(() => {
            this.count += 1;
          })
      }
    }
  }
    ```


- 在ArkTS-Sta模块中配置相关模块依赖后，导入动态模块的自定义组件。如何导入和使用子模块参考共享包（[HAR](har-package.md)）说明。

  ```
  'use static'
  import { Entry, Component, Column } from '@ohos.arkui.component';
  import { State } from '@ohos.arkui.stateManagement';
  import { Child } from 'dynamic_module';
  
  @Entry
  @Component
  struct Index {
    @State count: number = 0;
  
    build() {
      Column() {
        // 支持初始化子组件的@State变量；
        // 子组件@State变化不会导致父组件count变化。
        Child({count: this.count})
      }
    }
  }
  ```

## 和ArkTS-Dyn的\@Prop交互

状态管理V1互操作支持在ArkTS-Sta上下文中初始化ArkTS-Dyn自定义组件的[\@Prop](../ui/state-management/arkts-prop.md)装饰变量，并建立单向同步机制。


如下示例展示了相关用法。


- 创建ArkTS-Dyn子模块dynamic_module，在动态模块中创建并导出自定义组件。
  ```
  @Component
  export struct Child {
    @Prop count: number = 0;
  
    build() {
      Column() {
        Button(`click times: ${this.count}`)
          .onClick(() => {
            this.count += 1; // 子组件修改不会同步父组件。
          })
      }
    }
  }
  ```


- 在ArkTS-Sta模块中配置相关模块依赖后，导入动态模块的自定义组件。

  ```
  'use static'
  import { Entry, Component, Column, Button, ClickEvent } from '@ohos.arkui.component';
  import { State } from '@ohos.arkui.stateManagement';
  import { Child } from 'dynamic_module';
  
  @Entry
  @Component
  struct Index {
    @State count: number = 0;
  
    build() {
      Column() {
        Child({ count: this.count })
        Button('change value')
          .onClick((value: ClickEvent) => {
            // 父组件状态修改会同步给ArkTS-Dyn子组件并刷新UI。
            this.count += 2;
          })
      }
    }
  }
  ```


### 规格限制

ArkTS-Dyn自定义组件中的\@Prop装饰变量支持从ArkTS-Sta父组件中进行初始化，由于ArkTS-Sta静态类型对象深拷贝的限制，初始化规则和非互操作场景下存在差异和限制。

- ArkTS-Sta传递的数据类型为基础类型时，例如string、number、boolean，相关使用和传递规则和非互操作场景下保持一致。

- ArkTS-Sta传递的数据类型为静态对象类型时，例如Array，Map，Class，Interface，enum，由于不支持对象类型深拷贝，从而不支持初始化\@Prop变量，否则运行时会产生异常。建议开发者使用[\@Link](../ui/state-management/arkts-link.md)或者[\@ObjectLink](../ui/state-management/arkts-observed-and-objectlink.md)替代。

- ArkTS-Sta传递的数据类型为语言互操作导入的动态对象类型，但内部使用了静态类型对象，由于深拷贝限制，不支持初始化\@Prop变量，运行时会产生异常，建议开发者使用\@Link或者\@ObjecLink替代。

- 当ArkTS-Sta传递的数据类型为语言互操作导入的纯动态对象类型时，由于动态类型对象支持深拷贝，其使用和传递规则与非互操作场景保持一致。

## 和ArkTS-Dyn的\@Link交互


状态管理V1互操作支持在ArkTS-Sta上下文中初始化ArkTS-Dyn自定义组件的[\@Link](../ui/state-management/arkts-link.md)装饰变量并建立双向同步机制，相关使用规则与非互操作场景下保持一致。


如下示例展示了相关用法。


- 创建ArkTS-Dyn子模块dynamic_module，在动态模块中创建并导出自定义组件。
  ```
  @Component
  export struct Child {
    @Link count: number;
  
    build() {
      Column() {
        Button(`click times: ${this.count}`)
          .onClick(() => {
            this.count += 1; // 子组件的修改将同步到父组件。
          })
      }
    }
  }
  ```


- 在ArkTS-Sta模块中配置相关模块依赖后，导入动态模块的自定义组件。

  ```
  'use static'
  import { Entry, Component, Column, Button, ClickEvent } from '@ohos.arkui.component';
  import { State } from '@ohos.arkui.stateManagement';
  import { Child } from 'dynamic_module';
  
  @Entry
  @Component
  struct Index {
    @State count: number = 0;
  
    build() {
      Column() {
        Child({ count: this.count })
        Button('change value')
          .onClick((value: ClickEvent) => {
            // 父组件状态的修改会同步到ArkTS-Dyn子组件，并刷新UI。
            this.count += 2;
          })
      }
    }
  }
  ```

## 和ArkTS-Dyn的\@Provide/\@Consume交互


状态管理V1互操作支持在ArkTS-Sta上下文中初始化ArkTS-Dyn自定义组件的[\@Provide](../ui/state-management/arkts-provide-and-consume.md)装饰变量，相关初始化规则与非互操作场景下保持一致。同时，ArkTS-Dyn自定义组件还支持通过[\@Consume](../ui/state-management/arkts-provide-and-consume.md)和ArkTS-Sta祖先组件建立双向数据同步，相关使用规则与非互操场场景下保持一致。


如下示例展示了相关用法。


- 创建ArkTS-Dyn子模块dynamic_module，在动态模块中创建并导出自定义组件。
  ```
  @Component
  export struct Child {
    @Provide message: string = '';
    @Consume count: number;
  
    build() {
      Column() {
        Text(this.message)
        Button(`click times: ${this.count}`)
          .onClick(() => {
            // 状态修改将同步到ArkTS-Sta祖先组件并刷新UI。
            this.count += 1;
          })
      }
    }
  }
  ```


- 在ArkTS-Sta模块中配置相关模块依赖后，导入动态模块的自定义组件。

  ```
  'use static'
  import { Entry, Component, Column, Button, ClickEvent } from '@ohos.arkui.component';
  import { State, Provide } from '@ohos.arkui.stateManagement';
  import { Child } from 'dynamic_module';
  
  @Entry
  @Component
  struct Index {
    @State message: string = 'Hello World';
    @Provide count: number = 0;
  
    build() {
      Column() {
        // 支持初始化子组件的@Provide成员。
        Child({ message: this.message })
        Button('change value')
          .onClick((value: ClickEvent) => {
            // 父组件状态的修改将同步到ArkTS-Dyn子组件并刷新UI。
            this.count += 2;
          })
      }
    }
  }
  ```

## 与ArkTS-Dyn的LocalStorage交互


### 使用\@LocalStorageProp进行交互

状态管理V1互操作支持ArkTS-Dyn自定义组件通过[\@LocalStorageProp](../ui/state-management/arkts-localstorage.md)与ArkTS-Sta的LocalStorage数据进行单向数据同步，如下示例展示了相关用法。

- 创建ArkTS-Dyn子模块dynamic_module，在动态模块中创建并导出自定义组件。
  ```
  @Component
  export struct Child {
    @LocalStorageProp('PropA') storageProp: number = 1;
  
    build() {
      Column() {
        Button(`click times: ${this.storageProp}`)
          .onClick(() => {
            // 状态修改不会同步给ArkTS-Sta的LocalStorage
            this.storageProp += 1;
          })
      }
    }
  }
  ```

- 在ArkTS-Sta模块中配置相关模块依赖后，导入动态模块的自定义组件。

  ```
  'use static'
  import { Entry, Component, Column, Button, ClickEvent } from '@ohos.arkui.component';
  import { LocalStorageLink } from '@ohos.arkui.stateManagement';
  import { Child } from 'dynamic_module';
  
  @Entry
  @Component
  struct Index {
    // 初始化1.2中的LocalStorage数据
    @LocalStorageLink('PropA') storageLink: number = 1;
  
    build() {
      Column() {
        Child()
        Button('update value')
          .onClick((value: ClickEvent) => {
            // 更新LocalStorage中的数据并同步更新ArkTS-Dyn组件
            this.storageLink += 1;
          })
      }
    }
  }
  ```

#### 规格限制

针对ArkTS-Dyn自定义组件通过\@LocalStorageProp使用ArkTS-Sta数据的场景，由于ArkTS-Sta静态类型对象深拷贝限制，相关规则与非互操作场景存在差异和限制。

- 存储在ArkTS-StaLocalStorage中的数据，其类型为基础类型时，例如string、number、boolean，相关使用和传递规则和非互操作场景下保持一致；

- 存储在ArkTS-StaLocalStorage中的数据，其类型为静态对象类型时，例如Array，Map，Class，Interface，enum，由于不支持对象类型深拷贝，不支持通过\@LocalStorageProp获取数据，否则将产生运行时异常，建议开发者使用[\@LocalStorageLink](../ui/state-management/arkts-localstorage.md)替代；

- 存储在ArkTS-StaLocalStorage中的数据，其类型为语言互操作导入的动态对象类型，但内部使用了静态类型对象，由于深拷贝限制，不支持通过\@LocalStorageProp获取数据，否则将产生运行时异常，建议开发者使用\@LocalStorageLink替代；

- 存储在ArkTS-StaLocalStorage中的数据，其类型为语言互操作导入的纯动态对象类型时，由于动态类型对象支持深拷贝，使用规则与非互操作场景一致。


### 使用\@LocalStorageLink进行交互

状态管理V1互操作支持ArkTS-Dyn自定义组件通过[\@LocalStorageLink](../ui/state-management/arkts-localstorage.md)与ArkTS-Sta的LocalStorage数据进行双向数据同步，使用规则与非互操作场景一致。

如下示例展示了相关用法。

- 创建ArkTS-Dyn子模块dynamic_module，在动态模块中创建并导出自定义组件。
  ```
  @Component
  export struct Child {
    @LocalStorageLink('PropA') storageLink: number = 1;
  
    build() {
      Column() {
        Button(`click times: ${this.storageLink}`)
          .onClick(() => {
            // 状态修改同步给ArkTS-Sta的LocalStorage并同步更新ArkTS-Sta组件
            this.storageLink += 1;
          })
      }
    }
  }
  ```

- 在ArkTS-Sta模块中配置相关模块依赖后，导入动态模块的自定义组件。

  ```
  'use static'
  import { Entry, Component, Column, Button, ClickEvent } from '@ohos.arkui.component';
  import { LocalStorageLink } from '@ohos.arkui.stateManagement';
  import { Child } from 'dynamic_module';
  
  @Entry
  @Component
  struct Index {
    // 初始化1.2中的LocalStorage数据
    @LocalStorageLink('PropA') storageLink: number = 1;
  
    build() {
      Column() {
        Child()
        Button('update value')
          .onClick((value: ClickEvent) => {
            // 更新LocalStorage中的数据并同步更新ArkTS-Dyn组件
            this.storageLink += 1;
          })
      }
    }
  }
  ```

### 其他规格限制

- 由于动静态LocalStorage数据对象存在差异，不支持通过ArkTS-Dyn自定义组件构造参数来传递ArkTS-Sta的LocalStorage实例。

## 和ArkTS-Dyn的AppStorage交互


### 和\@StorageProp进行交互

状态管理V1互操作支持ArkTS-Dyn自定义组件通过[\@StorageProp](../ui/state-management/arkts-appstorage.md)和ArkTS-Sta的AppStorage数据进行单向数据同步，如下示例展示了具体用法。

- 创建ArkTS-Dyn子模块dynamic_module，在动态模块中创建并导出自定义组件。
  ```
  @Component
  export struct Child {
    @StorageProp('PropA') storageProp: number = 1;
  
    build() {
      Column() {
        Button(`click times: ${this.storageProp}`)
          .onClick(() => {
            // 状态修改不会同步给ArkTS-Sta的AppStorage
            this.storageProp += 1;
          })
      }
    }
  }
  ```

- 在ArkTS-Sta模块中配置相关模块依赖后，导入动态模块的自定义组件。

  ```
  'use static'
  import { Entry, Component, Column, Button, ClickEvent } from '@ohos.arkui.component';
  import { StorageLink } from '@ohos.arkui.stateManagement';
  import { Child } from 'dynamic_module';
  
  @Entry
  @Component
  struct Index {
    // 初始化1.2中的AppStorage数据
    @StorageLink('PropA') storageLink: number = 1;
  
    build() {
      Column() {
        Child()
        Button('update value')
          .onClick((value: ClickEvent) => {
            // 更新AppStorage中的数据并同步更新ArkTS-Dyn组件
            this.storageLink += 1;
          })
      }
    }
  }
  ```

#### 规格限制

针对ArkTS-Dyn自定义组件通过\@StorageProp访问ArkTS-Sta数据的场景，由于ArkTS-Sta静态类型对象深拷贝限制，相关规则和非互操作场景下存在差异和限制。

- 存储在ArkTS-Sta中的AppStorage中的数据，其类型为基础类型时，例如string、number、boolean，相关使用和传递规则与非互操作场景下保持一致。

- 存储在ArkTS-Sta中的AppStorage中的数据，其类型为静态对象类型时，例如Array，Map，Class，Interface，enum，由于不支持对象类型深拷贝，不支持通过\@StorageProp获取数据，否则将产生运行时异常，建议开发者使用[\@StorageLink](../ui/state-management/arkts-appstorage.md)替代。

- 存储在ArkTS-Sta中的AppStorage中的数据，其类型为语言互操作导入的动态对象类型，但内部使用了静态类型对象，同样由于深拷贝限制，不支持通过\@StorageProp获取数据，否则将产生运行时异常，建议开发者使用\@StorageLink替代。

- 存储在ArkTS-Sta中的AppStorage中的数据，其类型为语言互操作导入的纯动态对象类型时，由于动态类型对象支持深拷贝，相关使用规则与非互操作场景下一致。


### 和\@StorageLink进行交互

状态管理V1互操作支持ArkTS-Dyn自定义组件通过[\@StorageLink](../ui/state-management/arkts-appstorage.md)和ArkTS-Sta的AppStorage数据进行双向数据同步，使用规则与非互操作场景一致。

如下示例展示了相关用法。

- 创建ArkTS-Dyn子模块dynamic_module，在动态模块中创建并导出自定义组件。
  ```
  @Component
  export struct Child {
    @StorageLink('PropA') storageLink: number = 1;
  
    build() {
      Column() {
        Button(`click times: ${this.storageLink}`)
          .onClick(() => {
            // 状态修改同步给ArkTS-Sta的AppStorage并同步更新ArkTS-Sta组件
            this.storageLink += 1;
          })
      }
    }
  }
  ```

- 在ArkTS-Sta模块中配置相关模块依赖后，导入动态模块的自定义组件。
  ```
  'use static'
  import { Entry, Component, Column, Button, ClickEvent } from '@ohos.arkui.component';
  import { StorageLink } from '@ohos.arkui.stateManagement';
  import { Child } from 'dynamic_module';
  
  @Entry
  @Component
  struct Index {
    // 初始化1.2中的AppStorage数据
    @StorageLink('PropA') storageLink: number = 1;
  
    build() {
      Column() {
        Child()
        Button('update value')
          .onClick((value: ClickEvent) => {
            // 更新AppStorage中的数据并同步更新ArkTS-Dyn组件
            this.storageLink += 1;
          })
      }
    }
  }
  ```

### 通过AppStorage接口进行交互

状态管理V1互操作支持通过ArkTS-Dyn的[AppStorage接口](../reference/apis-arkui/arkui-ts/ts-state-management.md)操作ArkTS-Sta的AppStorage数据，如下示例展示了具体用法。

- 创建ArkTS-Dyn子模块dynamic_module，在动态模块中创建并导出自定义组件。
  ```
  @Component
  export struct Child {
    build() {
      Column() {
        Button('change AppStorage')
          .onClick(() => {
            // 通过接口修改ArkTS-Sta的AppStorage并同步更新ArkTS-Sta组件
            AppStorage.setOrCreate('PropA', 4);
          })
      }
    }
  }
  ```

- 在ArkTS-Sta模块中配置相关模块依赖后，导入动态模块的自定义组件。
  ```
  'use static'
  import { Entry, Component, Column, Text } from '@ohos.arkui.component';
  import { StorageLink } from '@ohos.arkui.stateManagement';
  import { Child } from 'dynamic_module';
  
  @Entry
  @Component
  struct Index {
    // 初始化1.2中的AppStorage数据
    @StorageLink('PropA') storageLink: number = 1;
  
    build() {
      Column() {
        Child()
        Text(`current value: ${this.storageLink}`)
      }
    }
  }
  ```


#### 规格限制

在通过ArkTS-Dyn的AppStorage接口操作ArkTS-Sta的AppStorage数据时，除prop和setAndProp接口外的其他接口使用规则与非互操作场景一致。

针对prop和setAndProp接口，由于静态类型数据深拷贝的限制，存在规格差异和约束。

- 当存储在ArkTS-Sta中的AppStorage中的数据，其类型为基础类型时，例如string、number、boolean，prop和setAndProp接口规则与非互操作场景一致。

- 当存储在ArkTS-Sta中的AppStorage中的数据，其类型为静态对象类型时，例如Array，Map，Class，Interface，enum，由于不支持对象类型深拷贝，不支持通过prop和setAndProp接口获取数据，否则将产生运行时异常。建议开发者使用ref和setAndRef接口替代。

- 当存储在ArkTS-Sta中的AppStorage中的数据，其类型为语言互操作导入的动态对象类型，但内部使用了静态类型对象时，由于深拷贝限制，不支持通过prop和setAndProp接口获取数据，否则将产生运行时异常。建议开发者使用ref和setAndRef接口替代。

- 当存储在ArkTS-Sta中的AppStorage中的数据，其类型为语言互操作导入的纯动态对象类型时，由于动态类型对象支持深拷贝，prop和setAndProp接口规则与非互操作场景一致。


### 其他限制

由于动静态类型数据序列化差异，ArkTS-Dyn的[PersistentStorage](../ui/state-management/arkts-persiststorage.md)接口不支持对ArkTS-Sta的AppStorage数据进行持久化存储，否则将产生运行时异常。建议使用ArkTS-Sta的[PersistentStorage](../ui/state-management-static/arkts-static-persiststorage.md)接口进行操作。
