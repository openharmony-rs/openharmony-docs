# UI集合类型互操作(Array/Map/Set)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lixingchi1; @katabanga-->
<!--Designer: @lixingchi1; @katabanga-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->


## 概述
在ArkTS-Sta与ArkTS-Dyn互操作场景中，由于两种语言的Array/Map/Set底层实现不同，跨语言传递时类型对应规则如下：

- ArkTS-Sta的`Array`/`Map`/`Set`传入ArkTS-Dyn后，需使用`st.Array`/`st.Map`/`st.Set`接收。
- ArkTS-Dyn的`Array`/`Map`/`Set`传入ArkTS-Sta后，需使用`es.Array`/`es.Map`/`es.Set`接收。

**Array互操作规格**

| 父组件 | 子组件 | 父组件类型 | 子组件类型 | 示例 |
|-------|-------|----------|----------|-----|
| ArkTS-Sta | ArkTS-Dyn | Array | st.Array | [ArkTS-Sta使用Array传给ArkTS-Dyn st.Array](#arkts-sta使用array传给arkts-dyn-starray) |
| ArkTS-Sta | ArkTS-Dyn | es.Array | Array | [ArkTS-Sta使用es.Array传给ArkTS-Dyn Array](#arkts-sta使用esarray传给arkts-dyn-array) |
| ArkTS-Dyn | ArkTS-Sta | Array | es.Array | [ArkTS-Dyn使用Array传给ArkTS-Sta es.Array](#arkts-dyn使用array传给arkts-sta-esarray) |
| ArkTS-Dyn | ArkTS-Sta | st.Array | Array | [ArkTS-Dyn使用st.Array传给ArkTS-Sta Array](#arkts-dyn使用starray传给arkts-sta-array) |

**Map互操作规格**

| 父组件 | 子组件 | 父组件类型 | 子组件类型 | 示例 |
|-------|-------|----------|----------|-----|
| ArkTS-Sta | ArkTS-Dyn | Map | st.Map | [ArkTS-Sta使用Map传给ArkTS-Dyn st.Map](#arkts-sta使用map传给arkts-dyn-stmap) |
| ArkTS-Sta | ArkTS-Dyn | es.Map | Map | [ArkTS-Sta使用es.Map传给ArkTS-Dyn Map](#arkts-sta使用esmap传给arkts-dyn-map) |
| ArkTS-Dyn | ArkTS-Sta | Map | es.Map | [ArkTS-Dyn使用Map传给ArkTS-Sta es.Map](#arkts-dyn使用map传给arkts-sta-esmap) |
| ArkTS-Dyn | ArkTS-Sta | st.Map | Map | [ArkTS-Dyn使用st.Map传给ArkTS-Sta Map](#arkts-dyn使用stmap传给arkts-sta-map) |

**Set互操作规格**

| 父组件 | 子组件 | 父组件类型 | 子组件类型 | 示例 |
|-------|-------|----------|----------|-----|
| ArkTS-Sta | ArkTS-Dyn | Set | st.Set | [ArkTS-Sta使用Set传给ArkTS-Dyn st.Set](#arkts-sta使用set传给arkts-dyn-stset) |
| ArkTS-Sta | ArkTS-Dyn | es.Set | Set | [ArkTS-Sta使用es.Set传给ArkTS-Dyn Set](#arkts-sta使用esset传给arkts-dyn-set) |
| ArkTS-Dyn | ArkTS-Sta | Set | es.Set | [ArkTS-Dyn使用Set传给ArkTS-Sta es.Set](#arkts-dyn使用set传给arkts-sta-esset) |
| ArkTS-Dyn | ArkTS-Sta | st.Set | Set | [ArkTS-Dyn使用st.Set传给ArkTS-Sta Set](#arkts-dyn使用stset传给arkts-sta-set) |

下文将结合用例介绍Array、Map、Set在互操作场景下的具体使用场景。

## 使用限制
- es.Array、es.Map、es.Set不支持通过`new`创建。可通过ArkTS-Dyn方法创建后导入。
- st.Array、st.Map、st.Set不支持通过`new`创建。可通过`STValue.newSTArray()`，`STValue.newSTSet()`，`STValue.newSTMap()`创建，或ArkTS-Sta方法创建后导入。
- es.Array、es.Map、es.Set不支持迭代器及相关方法。
- st.Array、st.Map、st.Set不支持迭代器及相关方法。

## Array互操作

### ArkTS-Sta使用Array传给ArkTS-Dyn st.Array

完整示例结构如下：

```text
project/
├── entry/                          # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── StaDynBuiltinArraySt.ets   # 父组件定义
│
└── dynamic_module/                # ArkTS-Dyn子模块
    ├── config.json                 # 配置文件（新增）
    ├── build-profile.json5         # 需添加arkOptions配置
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── ArrayStPage.ets  # 子组件定义
```

步骤：

1. 创建ArkTS-Dyn子模块`dynamic_module`，定义接收`st.Array`类型的组件。

   <!-- @[StaDynBuiltinArrayStMainPage](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaInteropDynBuiltinCollection/dynamic_module/src/main/ets/components/ArrayStPage.ets) -->
   
   ``` TypeScript
   // dynamic_module/src/main/ets/components/ArrayStPage.ets
   import st, { STValue } from 'static.@ohos.lang.interop';
   
   @Component
   export struct ArrayStChild {
     @Link data: st.Array<string>;
   
     build() {
       Column() {
         Text(`Child data: ${this.data}`)
         Button('Push element')
           .onClick(() => {
             this.data.push('orange');
           })
         Button('Reset Array')
           .onClick(() => {
             this.data = STValue.newSTArray(); // 当前st.Array不支持new创建，通过STValue.newSTArray()创建空的st.Array
           })
       }
     }
   }
   ```

   <!-- @[StaDynBuiltinArrayStDynIndex](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaInteropDynBuiltinCollection/dynamic_module/Index.ets) -->
   
   ``` TypeScript
   // dynamic_module/Index.ets
   export { ArrayStChild } from './src/main/ets/components/ArrayStPage';
   ```

2. 在子模块`dynamic_module`根目录下创建`config.json`文件，用于配置`st`和`STValue`的导入别名。

   ```json5
   {
     "static.@ohos.lang.interop": {
       "originalAPIName": "@ohos.lang.interop",
       "isStatic": true
     },
     "dynamic.@ohos.lang.interop": {
       "originalAPIName": "@ohos.lang.interop",
       "isStatic": false
     }
   }
   ```

3. 在子模块的`build-profile.json5`的`buildOption`字段中添加`arkOptions`配置，引用`config.json`。

   ```json5
   // dynamic_module/build-profile.json5
   {
     // ...,
     "buildOption": {
       "arkOptions": {
         "sdkAliasConfigPath": "./config.json"
       },
       // ...
     },
     // ...
   }
   ```

4. 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

   ```json5
   // entry/oh-package.json5
   {
     "dependencies": {
       "dynamic_module": "file:../dynamic_module"
     }
   }
   ```

5. 在ArkTS-Sta主模块中引入ArkTS-Dyn组件。

   <!-- @[StaDynBuiltinArraySt](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaInteropDynBuiltinCollection/entry/src/main/ets/pages/StaDynBuiltinArraySt.ets) -->
   
   ``` TypeScript
   // entry/src/main/ets/pages/StaDynBuiltinArraySt.ets
   
   import { ClickEvent, Entry, Column, Button, Component, Text, State } from '@kit.ArkUI';
   import { ArrayStChild } from 'dynamic_module';
   
   @Entry
   @Component
   struct Parent {
     @State data: Array<string> = ['apple', 'banana'];
   
     build() {
       Column() {
         Text(`Parent data: ${this.data}`)
         Button('Push element')
           .onClick((event: ClickEvent) => {
             this.data.push('orange');
           })
         Button('Reset Array')
           .onClick((event: ClickEvent) => {
             this.data = ['strawberry', 'blueberry'];
           })
         ArrayStChild({ data: this.data })
       }
     }
   }
   ```

### ArkTS-Sta使用es.Array传给ArkTS-Dyn Array

完整示例结构如下：

```text
project/
├── entry/                          # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── StaDynBuiltinArrayEs.ets   # 父组件定义
│
└── dynamic_module/                # ArkTS-Dyn子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── EsPage.ets  # 子组件定义
```

步骤：

1. 创建ArkTS-Dyn子模块`dynamic_module`，定义接收`Array`类型的组件。

   <!-- @[StaDynBuiltinArrayEsMainPage](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaInteropDynBuiltinCollection/dynamic_module/src/main/ets/components/EsPage.ets) -->
   
   ``` TypeScript
   // dynamic_module/src/main/ets/components/EsPage.ets
   
   @Component
   export struct ArrayEsChild {
     @Link data: Array<string>;
   
     build() {
       Column() {
         Text(`Child data: ${this.data}`)
         Button('Push element')
           .onClick(() => {
             this.data.push('orange');
           })
         Button('Reset Array')
           .onClick(() => {
             this.data = ['strawberry', 'blueberry'];
           })
       }
     }
   }
   
   // 导出创建Array的方法，供ArkTS-Sta使用
   export function dynCreateArray(): Array<string> {
     return ['apple', 'banana'];
   }
   ```

   <!-- @[StaDynBuiltinArrayEsDynIndex](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaInteropDynBuiltinCollection/dynamic_module/Index.ets) -->
   
   ``` TypeScript
   // dynamic_module/Index.ets
   export { ArrayEsChild, dynCreateArray } from './src/main/ets/components/EsPage';
   ```

2. 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

   ```json5
   // entry/oh-package.json5
   {
     "dependencies": {
       "dynamic_module": "file:../dynamic_module"
     }
   }
   ```

3. 在ArkTS-Sta主模块中引入ArkTS-Dyn组件。

   <!-- @[StaDynBuiltinArrayEs](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaInteropDynBuiltinCollection/entry/src/main/ets/pages/StaDynBuiltinArrayEs.ets) -->
   
   ``` TypeScript
   // entry/src/main/ets/pages/StaDynBuiltinArrayEs.ets
   
   import { ClickEvent, Entry, Column, Button, Component, Text, State } from '@kit.ArkUI';
   import es from '@ohos.lang.interop';
   import { ArrayEsChild, dynCreateArray } from 'dynamic_module';
   
   @Entry
   @Component
   struct Parent {
     @State data: es.Array<string> = dynCreateArray(); // 当前es.Array不支持new创建，需通过ArkTS-Dyn方法创建
   
     build() {
       Column() {
         Text(`Parent data: ${this.data}`)
         Button('Push element')
           .onClick((event: ClickEvent) => {
             this.data.push('orange');
           })
         Button('Reset Array')
           .onClick((event: ClickEvent) => {
             this.data = dynCreateArray();
           })
         ArrayEsChild({ data: this.data })
       }
     }
   }
   ```

### ArkTS-Dyn使用Array传给ArkTS-Sta es.Array

完整示例结构如下：

```text
project/
├── entry/                              # ArkTS-Dyn主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── ESArray.ets     # 父组件定义
│
├── dynamic_module/                     # ArkTS-Dyn子模块（提供创建Array的方法）
│   └── src/
│       └── main/
│           └── ets/
│               └── components/
│                   └── DynESArray.ets  # 导出创建Array方法
│
└── static_module/                      # ArkTS-Sta子模块
    ├── oh-package.json5                # 需依赖dynamic_module
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── StaESArray.ets  # 子组件定义
```

步骤：

1. 创建ArkTS-Dyn子模块`dynamic_module`，导出创建`Array`的方法。

   <!-- @[DynInteropStaArrayDynCreateArray](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/DynInteropStaUI/dynamic_module/src/main/ets/components/DynCreateArray.ets) -->
   
   ``` TypeScript
   // dynamic_module/src/main/ets/components/DynCreateArray.ets
   export function dynCreateArray(): Array<string> {
     return ['apple', 'banana'];
   }
   ```

   <!-- @[StaDynCreateArrayIndex](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/DynInteropStaUI/dynamic_module/Index.ets) -->
   
   ``` TypeScript
   // dynamic_module/index.ets
   export { dynCreateArray } from './src/main/ets/components/DynCreateArray';
   ```

2. 创建ArkTS-Sta子模块`static_module`，定义接收`es.Array`类型的组件。

   <!-- @[DynInteropStaESArray](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/DynInteropStaUI/static_module/src/main/ets/components/StaESArray.ets) -->
   
   ``` TypeScript
   // static_module/src/main/ets/components/StaESArray.ets
   import { Component, Column, Button, Text, ClickEvent, Link } from '@kit.ArkUI';
   import es from '@ohos.lang.interop';
   import { dynCreateArray } from 'dynamic_module';
   
   @Component
   export struct ESArrayChild {
     @Link data: es.Array<string>;
   
     build(): void {
       Column() {
         Text(`Child data: ${this.data}`)
         Button('Push element')
           .onClick((event: ClickEvent) => {
             this.data.push('orange');
           })
         Button('Reset Array')
           .onClick((event: ClickEvent) => {
             this.data = dynCreateArray(); // 当前es.Array不支持new创建，需通过ArkTS-Dyn方法创建
           })
       }
     }
   }
   ```

   <!-- @[DynInteropStaESArrayIndex](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/DynInteropStaUI/static_module/Index.ets) -->
   
   ``` TypeScript
   // static_module/Index.ets
   export { ESArrayChild } from './src/main/ets/components/StaESArray';
   ```

3. 在`static_module`的`oh-package.json5`中配置对`dynamic_module`的依赖。

   ```json5
   // static_module/oh-package.json5
   {
     "name": "static_module",
     "version": "1.0.0",
     "main": "Index.ets",
     "dependencies": {
       "dynamic_module": "file:../dynamic_module"
     }
   }
   ```

4. 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

   ```json5
   // entry/oh-package.json5
   {
     "dependencies": {
       "static_module": "file:../static_module"
     }
   }
   ```

5. 在ArkTS-Dyn主模块中引入ArkTS-Sta组件。

   <!-- @[DynInteropStaESArray](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/DynInteropStaUI/entry/src/main/ets/pages/ESArray.ets) -->
   
   ``` TypeScript
   // entry/src/main/ets/pages/ESArray.ets
   import { ESArrayChild } from 'static_module';
   
   @Entry
   @Component
   struct Parent {
     @State data: Array<string> = ['apple', 'banana'];
   
     build() {
       Column() {
         Text(`Parent data: ${this.data}`)
         Button('Push element')
           .onClick((event: ClickEvent) => {
             this.data.push('orange');
           })
         Button('Reset Array')
           .onClick((event: ClickEvent) => {
             this.data = ['strawberry', 'blueberry'];
           })
         ESArrayChild({ data: this.data })
       }
     }
   }
   ```


### ArkTS-Dyn使用st.Array传给ArkTS-Sta Array

完整示例结构如下：

```text
project/
├── entry/                              # ArkTS-Dyn主模块
│   ├── config.json                     # 配置文件（新增）
│   ├── build-profile.json5             # 需添加arkOptions配置
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── STArray.ets     # 父组件定义
│
└── static_module/                      # ArkTS-Sta子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── StaSTArray.ets  # 子组件定义
```

步骤：

1. 创建ArkTS-Sta子模块`static_module`，定义接收`Array`类型的组件。

   <!-- @[DynInteropStaStaSTArray](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/DynInteropStaUI/static_module/src/main/ets/components/StaSTArray.ets) -->
   
   ``` TypeScript
   // static_module/src/main/ets/components/StaSTArray.ets
   import { Component, Column, Button, Text, ClickEvent, Link } from '@kit.ArkUI';
   
   @Component
   export struct STArrayChild {
     @Link data: Array<string>;
   
     build(): void {
       Column() {
         Text(`Child data: ${this.data}`)
         Button('Push element')
           .onClick((event: ClickEvent) => {
             this.data.push('orange');
           })
         Button('Reset Array')
           .onClick((event: ClickEvent) => {
             this.data = ['strawberry', 'blueberry'];
           })
       }
     }
   }
   ```
   
   <!-- @[DynInteropStaSTArrayIndex](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/DynInteropStaUI/static_module/Index.ets) -->
   
   ``` TypeScript
   // static_module/Index.ets
   export { STArrayChild } from './src/main/ets/components/StaSTArray';
   ```

2. 在主模块`entry`根目录下创建`config.json`文件，用于配置`st`和`STValue`的导入别名。

   ```json5
   {
     "static.@ohos.lang.interop": {
       "originalAPIName": "@ohos.lang.interop",
       "isStatic": true
     },
     "dynamic.@ohos.lang.interop": {
       "originalAPIName": "@ohos.lang.interop",
       "isStatic": false
     }
   }
   ```

3. 在主模块的`build-profile.json5`中添加`arkOptions`配置。

   ```json5
   // entry/build-profile.json5
   {
     // ...,
     "buildOption": {
       "arkOptions": {
         "sdkAliasConfigPath": "./config.json"
       },
       // ...
     },
     // ...
   }
   ```

4. 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

   ```json5
   // entry/oh-package.json5
   {
     "dependencies": {
       "static_module": "file:../static_module"
     }
   }
   ```

5. 在ArkTS-Dyn主模块中引入ArkTS-Sta组件。

   <!-- @[DynInteropStaSTArray](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/DynInteropStaUI/entry/src/main/ets/pages/STArray.ets) -->
   
   ``` TypeScript
   // entry/src/main/ets/pages/STArray.ets
   import st, { STValue } from 'static.@ohos.lang.interop';
   import { STArrayChild } from 'static_module';
   
   @Entry
   @Component
   struct Parent {
     @State data: st.Array<string> = STValue.newSTArray(); // 当前st.Array不支持new创建，通过STValue.newSTArray()创建空的st.Array
   
     build() {
       Column() {
         Text(`Parent data: ${this.data}`)
         Button('Push element')
           .onClick((event: ClickEvent) => {
             this.data.push('orange');
           })
         Button('Reset Array')
           .onClick((event: ClickEvent) => {
             this.data = STValue.newSTArray();
           })
         STArrayChild({ data: this.data })
       }
     }
   }
   ```

## Map互操作

### ArkTS-Sta使用Map传给ArkTS-Dyn st.Map

完整示例结构如下：

```text
project/
├── entry/                          # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── StaDynBuiltinMapSt.ets   # 父组件定义
│
└── dynamic_module/                # ArkTS-Dyn子模块
    ├── config.json                 # 配置文件（新增）
    ├── build-profile.json5         # 需添加arkOptions配置
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MapStPage.ets  # 子组件定义
```

步骤：

1. 创建ArkTS-Dyn子模块`dynamic_module`，定义接收`st.Map`类型的组件。

   <!-- @[StaDynBuiltinMapStMainPage](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaInteropDynBuiltinCollection/dynamic_module/src/main/ets/components/MapStPage.ets) -->
   
   ``` TypeScript
   // dynamic_module/src/main/ets/components/MapStPage.ets
   import st, { STValue } from 'static.@ohos.lang.interop';
   
   @Component
   export struct MapStChild {
     @Link data: st.Map<string, number>;
   
     build() {
       Column() {
         Text(`Child data: ${this.data}`)
         Button('Set element')
           .onClick(() => {
             this.data.set('orange', 3);
           })
         Button('Reset Map')
           .onClick(() => {
             this.data = STValue.newSTMap(); // 当前st.Map不支持new创建，通过STValue.newSTMap()创建空的st.Map
           })
       }
     }
   }
   ```

   <!-- @[StaDynBuiltinMapStDynIndex](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaInteropDynBuiltinCollection/dynamic_module/Index.ets) -->
   
   ``` TypeScript
   // dynamic_module/Index.ets
   export { MapStChild } from './src/main/ets/components/MapStPage';
   ```

2. 在子模块`dynamic_module`根目录下创建`config.json`文件，用于配置`st`和`STValue`的导入别名。

   ```json5
   {
     "static.@ohos.lang.interop": {
       "originalAPIName": "@ohos.lang.interop",
       "isStatic": true
     },
     "dynamic.@ohos.lang.interop": {
       "originalAPIName": "@ohos.lang.interop",
       "isStatic": false
     }
   }
   ```

3. 在子模块的`build-profile.json5`的`buildOption`字段中添加`arkOptions`配置，引用`config.json`。

   ```json5
   // dynamic_module/build-profile.json5
   {
     // ...,
     "buildOption": {
       "arkOptions": {
         "sdkAliasConfigPath": "./config.json"
       },
       // ...
     },
     // ...
   }
   ```

4. 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

   ```json5
   // entry/oh-package.json5
   {
     "dependencies": {
       "dynamic_module": "file:../dynamic_module"
     }
   }
   ```

5. 在ArkTS-Sta主模块中引入ArkTS-Dyn组件。

   <!-- @[StaDynBuiltinMapSt](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaInteropDynBuiltinCollection/entry/src/main/ets/pages/StaDynBuiltinMapSt.ets) -->
   
   ``` TypeScript
   // entry/src/main/ets/pages/StaDynBuiltinMapSt.ets
   
   import { ClickEvent, Entry, Column, Button, Component, Text, State } from '@kit.ArkUI';
   import { MapStChild } from 'dynamic_module';
   
   @Entry
   @Component
   struct Parent {
     @State data: Map<string, number> = new Map<string, number>([['apple', 1], ['banana', 2]]);
   
     build() {
       Column() {
         Text(`Parent data: ${this.data}`)
         Button('Set element')
           .onClick((event: ClickEvent) => {
             this.data.set('orange', 3);
           })
         Button('Reset Map')
           .onClick((event: ClickEvent) => {
             this.data = new Map<string, number>([['strawberry', 4], ['blueberry', 5]]);
           })
         MapStChild({ data: this.data })
       }
     }
   }
   ```

### ArkTS-Sta使用es.Map传给ArkTS-Dyn Map

完整示例结构如下：

```text
project/
├── entry/                          # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── StaDynBuiltinMapEs.ets   # 父组件定义
│
└── dynamic_module/                # ArkTS-Dyn子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── EsPage.ets  # 子组件定义
```

步骤：

1. 创建ArkTS-Dyn子模块`dynamic_module`，定义接收`Map`类型的组件。

   <!-- @[StaDynBuiltinMapEsMainPage](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaInteropDynBuiltinCollection/dynamic_module/src/main/ets/components/EsPage.ets) -->
   
   ``` TypeScript
   // dynamic_module/src/main/ets/components/EsPage.ets
   
   @Component
   export struct MapEsChild {
     @Link data: Map<string, number>;
   
     build() {
       Column() {
         ForEach(Array.from(this.data.entries()), (item: [string, number]) => {
           Text(`${item[0]}: ${item[1]}`)
         })
         Button('Set element')
           .onClick(() => {
             this.data.set('orange', 3);
           })
         Button('Reset Map')
           .onClick(() => {
             this.data = new Map<string, number>([['strawberry', 4], ['blueberry', 5]]);
           })
       }
     }
   }
   
   // 导出创建Map的方法，供ArkTS-Sta使用
   export function dynCreateMap(): Map<string, number> {
     return new Map<string, number>([['apple', 1], ['banana', 2]]);
   }
   ```

   <!-- @[StaDynBuiltinMapEsDynIndex](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaInteropDynBuiltinCollection/dynamic_module/Index.ets) -->
   
   ``` TypeScript
   // dynamic_module/Index.ets
   export { MapEsChild, dynCreateMap } from './src/main/ets/components/EsPage';
   ```

2. 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

   ```json5
   // entry/oh-package.json5
   {
     "dependencies": {
       "dynamic_module": "file:../dynamic_module"
     }
   }
   ```

3. 在ArkTS-Sta主模块中引入ArkTS-Dyn组件。

   <!-- @[StaDynBuiltinMapEs](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaInteropDynBuiltinCollection/entry/src/main/ets/pages/StaDynBuiltinMapEs.ets) -->
   
   ``` TypeScript
   // entry/src/main/ets/pages/StaDynBuiltinMapEs.ets
   
   import { ClickEvent, Entry, Column, Button, Component, Text, ForEach, State } from '@kit.ArkUI';
   import es from '@ohos.lang.interop';
   import { MapEsChild, dynCreateMap } from 'dynamic_module';
   
   @Entry
   @Component
   struct Parent {
     @State data: es.Map<string, number> = dynCreateMap(); // 当前es.Map不支持new创建，需通过ArkTS-Dyn方法创建
   
     // 辅助函数：将es.Map转为字符串展示
     mapToString(): string {
       let result = '';
       this.data.forEach((value: number, key: string) => { // 当前es.Map不支持iterator，通过forEach遍历
         result += `${key}:${value}, `;
       });
       return result;
     }
   
     build() {
       Column() {
         Text(`Parent data: ${this.mapToString()}`)
         Button('Set element')
           .onClick((event: ClickEvent) => {
             this.data.set('orange', 3);
           })
         Button('Reset Map')
           .onClick((event: ClickEvent) => {
             this.data = dynCreateMap();
           })
         MapEsChild({ data: this.data })
       }
     }
   }
   ```

### ArkTS-Dyn使用Map传给ArkTS-Sta es.Map

完整示例结构如下：

```text
project/
├── entry/                           # ArkTS-Dyn主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── ESMap.ets    # 父组件定义
│
├── dynamic_module/                  # ArkTS-Dyn子模块（提供创建Map的方法）
│   └── src/
│       └── main/
│           └── ets/
│               └── components/
│                   └── DynESMap.ets  # 导出创建Map方法
│
└── static_module/                    # ArkTS-Sta子模块
    ├── oh-package.json5              # 需依赖dynamic_module
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── StaESMap.ets  # 子组件定义
```

步骤：

1. 创建ArkTS-Dyn子模块`dynamic_module`，导出创建`Map`的方法。

   <!-- @[DynInteropStaMapDynCreateMap](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/DynInteropStaUI/dynamic_module/src/main/ets/components/DynCreateMap.ets) -->
   
   ``` TypeScript
   // dynamic_module/src/main/ets/components/DynCreateMap.ets
   export function dynCreateMap(): Map<string, number> {
     return new Map<string, number>([['apple', 1], ['banana', 2]]);
   }
   ```
   
   <!-- @[StaDynCreateMapIndex](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/DynInteropStaUI/dynamic_module/Index.ets) -->
   
   ``` TypeScript
   // dynamic_module/index.ets
   export { dynCreateMap } from './src/main/ets/components/DynCreateMap';
   ```

2. 创建ArkTS-Sta子模块`static_module`，定义接收`es.Map`类型的组件。

   <!-- @[DynInteropStaESMap](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/DynInteropStaUI/static_module/src/main/ets/components/StaESMap.ets) -->
   
   ``` TypeScript
   // static_module/src/main/ets/components/StaESMap.ets
   
   import { Component, Column, Button, Text, ClickEvent, Link } from '@kit.ArkUI';
   import es from '@ohos.lang.interop';
   import { dynCreateMap } from 'dynamic_module';
   
   @Component
   export struct ESMapChild {
     @Link data: es.Map<string, number>;
   
     // 辅助函数：将es.Map转为字符串展示
     mapToString(): string {
       let result = '';
       this.data.forEach((value: number, key: string) => { // 当前es.Map不支持iterator，通过forEach遍历
         result += `${key}:${value}, `;
       });
       return result;
     }
   
     build(): void {
       Column() {
         Text(`Child data: ${this.mapToString()}`)
         Button('Set element')
           .onClick((event: ClickEvent) => {
             this.data.set('orange', 3);
           })
         Button('Reset Map')
           .onClick((event: ClickEvent) => {
             this.data = dynCreateMap(); // 当前es.Map不支持new创建，需通过ArkTS-Dyn方法创建
           })
       }
     }
   }
   ```
   
   <!-- @[DynInteropStaESMapIndex](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/DynInteropStaUI/static_module/Index.ets) -->
   
   ``` TypeScript
   // static_module/Index.ets
   export { ESMapChild } from './src/main/ets/components/StaESMap';
   ```

3. 在`static_module`的`oh-package.json5`中配置对`dynamic_module`的依赖。

   ```json5
   // static_module/oh-package.json5
   {
     "name": "static_module",
     "version": "1.0.0",
     "main": "Index.ets",
     "dependencies": {
       "dynamic_module": "file:../dynamic_module"
     }
   }
   ```

4. 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

   ```json5
   // entry/oh-package.json5
   {
     "dependencies": {
       "static_module": "file:../static_module"
     }
   }
   ```

5. 在ArkTS-Dyn主模块中引入ArkTS-Sta组件。

   <!-- @[DynInteropStaESMap](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/DynInteropStaUI/entry/src/main/ets/pages/ESMap.ets) -->
   
   ``` TypeScript
   // entry/src/main/ets/pages/ESMap.ets
   import { ESMapChild } from 'static_module';
   
   @Entry
   @Component
   struct Parent {
     @State data: Map<string, number> = new Map<string, number>([['apple', 1], ['banana', 2]]);
   
     build() {
       Column() {
         ForEach(Array.from(this.data.entries()), (item: [string, number]) => {
           Text(`${item[0]}: ${item[1]}`)
         })
         Button('Set element')
           .onClick((event: ClickEvent) => {
             this.data.set('orange', 3);
           })
         Button('Reset Map')
           .onClick((event: ClickEvent) => {
             this.data = new Map<string, number>([['strawberry', 4], ['blueberry', 5]]);
           })
         ESMapChild({ data: this.data })
       }
     }
   }
   ```


### ArkTS-Dyn使用st.Map传给ArkTS-Sta Map

完整示例结构如下：

```text
project/
├── entry/                            # ArkTS-Dyn主模块
│   ├── config.json                   # 配置文件（新增）
│   ├── build-profile.json5           # 需添加arkOptions配置
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── STMap.ets     # 父组件定义
│
└── static_module/                    # ArkTS-Sta子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── StaSTMap.ets  # 子组件定义
```

步骤：

1. 创建ArkTS-Sta子模块`static_module`，定义接收`Map`类型的组件。

   <!-- @[DynInteropStaStaSTMap](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/DynInteropStaUI/static_module/src/main/ets/components/StaSTMap.ets) -->
   
   ``` TypeScript
   // static_module/src/main/ets/components/StaSTMap.ets
   import { Component, Column, Button, Text, ClickEvent, Link } from '@kit.ArkUI';
   
   @Component
   export struct STMapChild {
     @Link data: Map<string, number>;
   
     build(): void {
       Column() {
         Text(`Child data: ${this.data}`)
         Button('Set element')
           .onClick((event: ClickEvent) => {
             this.data.set('orange', 3);
           })
         Button('Reset Map')
           .onClick((event: ClickEvent) => {
             this.data = new Map<string, number>([['strawberry', 4], ['blueberry', 5]]);
           })
       }
     }
   }
   ```
   
   <!-- @[DynInteropStaSTMapIndex](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/DynInteropStaUI/static_module/Index.ets) -->
   
   ``` TypeScript
   // static_module/Index.ets
   export { STMapChild } from './src/main/ets/components/StaSTMap';
   ```

2. 在主模块`entry`根目录下创建`config.json`文件，用于配置`st`和`STValue`的导入别名。

   ```json5
   {
     "static.@ohos.lang.interop": {
       "originalAPIName": "@ohos.lang.interop",
       "isStatic": true
     },
     "dynamic.@ohos.lang.interop": {
       "originalAPIName": "@ohos.lang.interop",
       "isStatic": false
     }
   }
   ```

3. 在主模块的`build-profile.json5`中添加`arkOptions`配置。

   ```json5
   // entry/build-profile.json5
   {
     // ...,
     "buildOption": {
       "arkOptions": {
         "sdkAliasConfigPath": "./config.json"
       },
       // ...
     },
     // ...
   }
   ```

4. 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

   ```json5
   // entry/oh-package.json5
   {
     "dependencies": {
       "static_module": "file:../static_module"
     }
   }
   ```

5. 在ArkTS-Dyn主模块中引入ArkTS-Sta组件。

   <!-- @[DynInteropStaSTMap](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/DynInteropStaUI/entry/src/main/ets/pages/STMap.ets) -->
   
   ``` TypeScript
   // entry/src/main/ets/pages/STMap.ets
   import st, { STValue } from 'static.@ohos.lang.interop';
   import { STMapChild } from 'static_module';
   
   @Entry
   @Component
   struct Parent {
     @State data: st.Map<string, number> = STValue.newSTMap(); // 当前st.Map不支持new创建，通过STValue.newSTMap()创建空的st.Map
   
     build() {
       Column() {
         Text(`Parent data: ${this.data}`)
         Button('Set element')
           .onClick((event: ClickEvent) => {
             this.data.set('orange', 3);
           })
         Button('Reset Map')
           .onClick((event: ClickEvent) => {
             this.data = STValue.newSTMap();
           })
         STMapChild({ data: this.data })
       }
     }
   }
   ```

## Set互操作

### ArkTS-Sta使用Set传给ArkTS-Dyn st.Set

完整示例结构如下：

```text
project/
├── entry/                          # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── StaDynBuiltinSetSt.ets   # 父组件定义
│
└── dynamic_module/                # ArkTS-Dyn子模块
    ├── config.json                 # 配置文件（新增）
    ├── build-profile.json5         # 需添加arkOptions配置
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── SetStPage.ets  # 子组件定义
```

步骤：

1. 创建ArkTS-Dyn子模块`dynamic_module`，定义接收`st.Set`类型的组件。

   <!-- @[StaDynBuiltinSetStMainPage](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaInteropDynBuiltinCollection/dynamic_module/src/main/ets/components/SetStPage.ets) -->
   
   ``` TypeScript
   // dynamic_module/src/main/ets/components/SetStPage.ets
   import st, { STValue } from 'static.@ohos.lang.interop';
   
   @Component
   export struct SetStChild {
     @Link data: st.Set<string>;
   
     build() {
       Column() {
         Text(`Child data: ${this.data}`)
         Button('Add element')
           .onClick(() => {
             this.data.add('orange');
           })
         Button('Reset Set')
           .onClick(() => {
             this.data = STValue.newSTSet(); // 当前st.Set不支持new创建，通过STValue.newSTSet()创建空的st.Set
           })
       }
     }
   }
   ```

   <!-- @[StaDynBuiltinSetStDynIndex](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaInteropDynBuiltinCollection/dynamic_module/Index.ets) -->
   
   ``` TypeScript
   // dynamic_module/Index.ets
   export { SetStChild } from './src/main/ets/components/SetStPage';
   ```

2. 在子模块`dynamic_module`根目录下创建`config.json`文件，用于配置`st`和`STValue`的导入别名。

   ```json5
   {
     "static.@ohos.lang.interop": {
       "originalAPIName": "@ohos.lang.interop",
       "isStatic": true
     },
     "dynamic.@ohos.lang.interop": {
       "originalAPIName": "@ohos.lang.interop",
       "isStatic": false
     }
   }
   ```

3. 在子模块的`build-profile.json5`的`buildOption`字段中添加`arkOptions`配置，引用`config.json`。

   ```json5
   // dynamic_module/build-profile.json5
   {
     // ...,
     "buildOption": {
       "arkOptions": {
         "sdkAliasConfigPath": "./config.json"
       },
       // ...
     },
     // ...
   }
   ```

4. 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

   ```json5
   // entry/oh-package.json5
   {
     "dependencies": {
       "dynamic_module": "file:../dynamic_module"
     }
   }
   ```

5. 在ArkTS-Sta主模块中引入ArkTS-Dyn组件。

   <!-- @[StaDynBuiltinSetSt](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaInteropDynBuiltinCollection/entry/src/main/ets/pages/StaDynBuiltinSetSt.ets) -->
   
   ``` TypeScript
   // entry/src/main/ets/pages/StaDynBuiltinSetSt.ets
   
   import { ClickEvent, Entry, Column, Button, Component, Text, State } from '@kit.ArkUI';
   import { SetStChild } from 'dynamic_module';
   
   @Entry
   @Component
   struct Parent {
     @State data: Set<string> = new Set<string>(['apple', 'banana']);
   
     build() {
       Column() {
         Text(`Parent data: ${this.data}`)
         Button('Add element')
           .onClick((event: ClickEvent) => {
             this.data.add('orange');
           })
         Button('Reset Set')
           .onClick((event: ClickEvent) => {
             this.data = new Set<string>(['strawberry', 'blueberry']);
           })
         SetStChild({ data: this.data })
       }
     }
   }
   ```


### ArkTS-Sta使用es.Set传给ArkTS-Dyn Set

完整示例结构如下：

```text
project/
├── entry/                          # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── StaDynBuiltinSetEs.ets   # 父组件定义
│
└── dynamic_module/                # ArkTS-Dyn子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── EsPage.ets  # 子组件定义
```

步骤：

1. 创建ArkTS-Dyn子模块`dynamic_module`，定义接收`Set`类型的组件。

   <!-- @[StaDynBuiltinSetEsMainPage](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaInteropDynBuiltinCollection/dynamic_module/src/main/ets/components/EsPage.ets) -->
   
   ``` TypeScript
   // dynamic_module/src/main/ets/components/EsPage.ets
   
   @Component
   export struct SetEsChild {
     @Link data: Set<string>;
   
     build() {
       Column() {
         ForEach(Array.from(this.data.values()), (item: string) => {
           Text(item)
         })
         Button('Add element')
           .onClick(() => {
             this.data.add('orange');
           })
         Button('Reset Set')
           .onClick(() => {
             this.data = new Set<string>(['strawberry', 'blueberry']);
           })
       }
     }
   }
   
   // 导出创建Set的方法，供ArkTS-Sta使用
   export function dynCreateSet(): Set<string> {
     return new Set<string>(['apple', 'banana']);
   }
   ```

   <!-- @[StaDynBuiltinSetEsDynIndex](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaInteropDynBuiltinCollection/dynamic_module/Index.ets) -->
   
   ``` TypeScript
   // dynamic_module/Index.ets
   export { SetEsChild, dynCreateSet } from './src/main/ets/components/EsPage';
   ```

2. 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

   ```json5
   // entry/oh-package.json5
   {
     "dependencies": {
       "dynamic_module": "file:../dynamic_module"
     }
   }
   ```

3. 在ArkTS-Sta主模块中引入ArkTS-Dyn组件。

   <!-- @[StaDynBuiltinSetEs](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaInteropDynBuiltinCollection/entry/src/main/ets/pages/StaDynBuiltinSetEs.ets) -->
   
   ``` TypeScript
   // entry/src/main/ets/pages/StaDynBuiltinSetEs.ets
   
   import { ClickEvent, Entry, Column, Button, Component, Text, State } from '@kit.ArkUI';
   import es from '@ohos.lang.interop';
   import { SetEsChild, dynCreateSet } from 'dynamic_module';
   
   @Entry
   @Component
   struct Parent {
     @State data: es.Set<string> = dynCreateSet(); // 当前es.Set不支持new创建，需通过ArkTS-Dyn方法创建
   
     // 辅助函数：将es.Set转为字符串展示
     setToString(): string {
       let result = '';
       this.data.forEach((value: string) => { // 当前es.Set不支持iterator，通过forEach遍历
         result += `${value}, `;
       });
       return result;
     }
   
     build() {
       Column() {
         Text(`Parent data: ${this.setToString()}`)
         Button('Add element')
           .onClick((event: ClickEvent) => {
             this.data.add('orange');
           })
         Button('Reset Set')
           .onClick((event: ClickEvent) => {
             this.data = dynCreateSet();
           })
         SetEsChild({ data: this.data })
       }
     }
   }
   ```

### ArkTS-Dyn使用Set传给ArkTS-Sta es.Set

完整示例结构如下：

```text
project/
├── entry/                            # ArkTS-Dyn主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── ESSet.ets     # 父组件定义
│
├── dynamic_module/                   # ArkTS-Dyn子模块（提供创建Set的方法）
│   └── src/
│       └── main/
│           └── ets/
│               └── components/
│                   └── DynESSet.ets  # 导出创建Set方法
│
└── static_module/                    # ArkTS-Sta子模块
    ├── oh-package.json5              # 需依赖dynamic_module
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── StaESSet.ets  # 子组件定义
```

步骤：

1. 创建ArkTS-Dyn子模块`dynamic_module`，导出创建`Set`的方法。

   <!-- @[DynInteropStaMapDynCreateSet](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/DynInteropStaUI/dynamic_module/src/main/ets/components/DynCreateSet.ets) -->
   
   ``` TypeScript
   // dynamic_module/src/main/ets/components/DynCreateSet.ets
   export function dynCreateSet(): Set<string> {
     return new Set<string>(['apple', 'banana']);
   }
   ```
   
   <!-- @[StaDynCreateSetIndex](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/DynInteropStaUI/dynamic_module/Index.ets) -->
   
   ``` TypeScript
   // dynamic_module/index.ets
   export { dynCreateSet } from './src/main/ets/components/DynCreateSet';
   ```

2. 创建ArkTS-Sta子模块`static_module`，定义接收`es.Set`类型的组件。

   <!-- @[DynInteropStaESSet](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/DynInteropStaUI/static_module/src/main/ets/components/StaESSet.ets) -->
   
   ``` TypeScript
   // static_module/src/main/ets/components/StaESSet.ets
   import { Component, Column, Button, Text, ClickEvent, Link } from '@kit.ArkUI';
   import es from '@ohos.lang.interop';
   import { dynCreateSet } from 'dynamic_module';
   
   @Component
   export struct ESSetChild {
     @Link data: es.Set<string>;
   
     // 辅助函数：将es.Set转为字符串展示
     setToString(): string {
       let result = '';
       this.data.forEach((value: string) => { // 当前es.Set不支持iterator，通过forEach遍历
         result += `${value}, `;
       });
       return result;
     }
   
     build(): void {
       Column() {
         Text(`Child data: ${this.setToString()}`)
         Button('Add element')
           .onClick((event: ClickEvent) => {
             this.data.add('orange');
           })
         Button('Reset Set')
           .onClick((event: ClickEvent) => {
             this.data = dynCreateSet(); // 当前es.Set不支持new创建，需通过ArkTS-Dyn方法创建
           })
       }
     }
   }
   ```
   
   <!-- @[DynInteropStaESSetIndex](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/DynInteropStaUI/static_module/Index.ets) -->
   
   ``` TypeScript
   // static_module/Index.ets
   export { ESSetChild } from './src/main/ets/components/StaESSet';
   ```

3. 在`static_module`的`oh-package.json5`中配置对`dynamic_module`的依赖。

   ```json5
   // static_module/oh-package.json5
   {
     "name": "static_module",
     "version": "1.0.0",
     "main": "Index.ets",
     "dependencies": {
       "dynamic_module": "file:../dynamic_module"
     }
   }
   ```

4. 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

   ```json5
   // entry/oh-package.json5
   {
     "dependencies": {
       "static_module": "file:../static_module"
     }
   }
   ```

5. 在ArkTS-Dyn主模块中引入ArkTS-Sta组件。

   <!-- @[DynInteropStaESSet](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/DynInteropStaUI/entry/src/main/ets/pages/ESSet.ets) -->
   
   ``` TypeScript
   // entry/src/main/ets/pages/ESSet.ets
   import { ESSetChild } from 'static_module';
   
   @Entry
   @Component
   struct Parent {
     @State data: Set<string> = new Set<string>(['apple', 'banana']);
   
     build() {
       Column() {
         ForEach(Array.from(this.data.values()), (item: string) => {
           Text(item)
         })
         Button('Add element')
           .onClick((event: ClickEvent) => {
             this.data.add('orange');
           })
         Button('Reset Set')
           .onClick((event: ClickEvent) => {
             this.data = new Set<string>(['strawberry', 'blueberry']);
           })
         ESSetChild({ data: this.data })
       }
     }
   }
   ```


### ArkTS-Dyn使用st.Set传给ArkTS-Sta Set

完整示例结构如下：

```text
project/
├── entry/                           # ArkTS-Dyn主模块
│   ├── config.json                  # 配置文件（新增）
│   ├── build-profile.json5          # 需添加arkOptions配置
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── STSet.ets    # 父组件定义
│
└── static_module/                   # ArkTS-Sta子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── StaSTSet.ets  # 子组件定义
```

步骤：

1. 创建ArkTS-Sta子模块`static_module`，定义接收`Set`类型的组件。

   <!-- @[DynInteropStaStaSTSet](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/DynInteropStaUI/static_module/src/main/ets/components/StaSTSet.ets) -->
   
   ``` TypeScript
   // static_module/src/main/ets/components/StaSTSet.ets
   import { Component, Column, Button, Text, ClickEvent, Link } from '@kit.ArkUI';
   
   @Component
   export struct STSetChild {
     @Link data: Set<string>;
   
     build(): void {
       Column() {
         Text(`Child data: ${this.data}`)
         Button('Add element')
           .onClick((event: ClickEvent) => {
             this.data.add('orange');
           })
         Button('Reset Set')
           .onClick((event: ClickEvent) => {
             this.data = new Set<string>(['strawberry', 'blueberry']);
           })
       }
     }
   }
   ```

   <!-- @[DynInteropStaSTSetIndex](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/DynInteropStaUI/static_module/Index.ets) -->
   
   ``` TypeScript
   // static_module/Index.ets
   export { STSetChild } from './src/main/ets/components/StaSTSet';
   ```

2. 在主模块`entry`根目录下创建`config.json`文件，用于配置`st`和`STValue`的导入别名。

   ```json5
   {
     "static.@ohos.lang.interop": {
       "originalAPIName": "@ohos.lang.interop",
       "isStatic": true
     },
     "dynamic.@ohos.lang.interop": {
       "originalAPIName": "@ohos.lang.interop",
       "isStatic": false
     }
   }
   ```

3. 在主模块的`build-profile.json5`中添加`arkOptions`配置。

   ```json5
   // entry/build-profile.json5
   {
     // ...,
     "buildOption": {
       "arkOptions": {
         "sdkAliasConfigPath": "./config.json"
       },
       // ...
     },
     // ...
   }
   ```

4. 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

   ```json5
   // entry/oh-package.json5
   {
     "dependencies": {
       "static_module": "file:../static_module"
     }
   }
   ```

5. 在ArkTS-Dyn主模块中引入ArkTS-Sta组件。

   <!-- @[DynInteropStaSTSet](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/DynInteropStaUI/entry/src/main/ets/pages/STSet.ets) -->
   
   ``` TypeScript
   // entry/src/main/ets/pages/STSet.ets
   import st, { STValue } from 'static.@ohos.lang.interop';
   import { STSetChild } from 'static_module';
   
   @Entry
   @Component
   struct Parent {
     @State data: st.Set<string> = STValue.newSTSet(); // 当前st.Set不支持new创建，通过STValue.newSTSet()创建空的st.Set
   
     build() {
       Column() {
         Text(`Parent data: ${this.data}`)
         Button('Add element')
           .onClick((event: ClickEvent) => {
             this.data.add('orange');
           })
         Button('Reset Set')
           .onClick((event: ClickEvent) => {
             this.data = STValue.newSTSet();
           })
         STSetChild({ data: this.data })
       }
     }
   }
   ```

## 常见问题

### 声明文件编译报错

跨语言传递集合类型时，编译时生成的声明文件可能转换错误，需要开发者手动修改声明文件报错位置后增量编译，以符合语法规格。详见[互操作声明文件规范](./arkts-ui-interop-declaration-spec.md)。

**ArkTS-Sta生成声明文件修改示例**

源码

``` TypeScript
'use static';

// static_module/src/main/ets/components/MainPage.ets
import { Component, Link } from '@kit.ArkUI';
import es from '@ohos.lang.interop';

@Component
export struct Child {
  @Link dynArr: es.Array<string>;
  @Link dynMap: es.Map<string, number>;
  @Link dynSet: es.Set<string>;
  @Link staArr: Array<string>;
  @Link staMap: Map<string, number>;
  @Link staSet: Set<string>;

  build() {}
}
```

修改声明文件为

``` TypeScript
// static_module/build/default/intermediates/declgen/default/declgenV1/static_module/src/main/ets/components/MainPage.d.ets

import st from "@ohos.lang.interop"
@Component
export struct Child {
  @Link dynArr: Array<string>;
  @Link dynMap: Map<string, number>;
  @Link dynSet: Set<string>;
  @Link staArr: st.Array<string>;
  @Link staMap: st.Map<string, number>;
  @Link staSet: st.Set<string>;

  public build(): void;
}
```

**ArkTS-Dyn生成声明文件修改示例**

源码

```TypeScript
// dyn_library/src/main/ets/components/MainPage.ets
import st from '@ohos.lang.interop';

@Component
export struct Child {
  @Link dynArr: Array<string>;
  @Link dynMap: Map<string, number>;
  @Link dynSet: Set<string>;
  @Link staArr: st.Array<string>;
  @Link staMap: st.Map<string, number>;
  @Link staSet: st.Set<string>;

  build() {}
}
```

修改声明文件为

```TypeScript
'use static';

// dynamic_library/build/default/intermediates/declgen/default/declgenV2/src/main/ets/components/MainPage.d.ets
import { LocalStorage } from '@ohos.arkui.stateManagement';
import { Component, Link } from 'dynamic/@ohos.arkui.GlobalAnnotation';
import es from "@ohos.lang.interop"
@Component
export struct Child {
  @Link dynArr: es.Array<string>;
  @Link dynMap: es.Map<string, number>;
  @Link dynSet: es.Set<string>;
  @Link staArr: Array<string>;
  @Link staMap: Map<string, number>;
  @Link staSet: Set<string>;

  public build(): void;
}
```
