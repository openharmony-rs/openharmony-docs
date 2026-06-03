# UI集合类型互操作(Array/Map/Set)

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
│                   └── Index.ets   # 父组件定义
│
└── dynamic_library/                # ArkTS-Dyn子模块
    ├── config.json                 # 配置文件（新增）
    ├── build-profile.json5         # 需添加arkOptions配置
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets  # 子组件定义
```

步骤：

1. 创建ArkTS-Dyn子模块`dynamic_library`，定义接收`st.Array`类型的组件。

   ```TypeScript
   // dynamic_library/src/main/ets/components/MainPage.ets
   import st, { STValue } from 'static.@ohos.lang.interop';

   @Component
   export struct Child {
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

   ```TypeScript
   // dynamic_library/Index.ets
   export { Child } from './src/main/ets/components/MainPage';
   ```

2. 在子模块`dynamic_library`根目录下创建`config.json`文件，用于配置`st`和`STValue`的导入别名。

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
   // dynamic_library/build-profile.json5
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
       "dynamic_library": "file:../dynamic_library"
     }
   }
   ```

5. 在ArkTS-Sta主模块中引入ArkTS-Dyn组件。

   ```TypeScript
   'use static';
   // entry/src/main/ets/pages/Index.ets

   import { ClickEvent, Entry, Column, Button, Component, Text, State } from '@kit.ArkUI';
   import { Child } from 'dynamic_library';

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
         Child({ data: this.data })
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
│                   └── Index.ets   # 父组件定义
│
└── dynamic_library/                # ArkTS-Dyn子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets  # 子组件定义
```

步骤：

1. 创建ArkTS-Dyn子模块`dynamic_library`，定义接收`Array`类型的组件。

   ```TypeScript
   // dynamic_library/src/main/ets/components/MainPage.ets

   @Component
   export struct Child {
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

   ```TypeScript
   // dynamic_library/Index.ets
   export { Child, dynCreateArray } from './src/main/ets/components/MainPage';
   ```

2. 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

   ```json5
   // entry/oh-package.json5
   {
     "dependencies": {
       "dynamic_library": "file:../dynamic_library"
     }
   }
   ```

3. 在ArkTS-Sta主模块中引入ArkTS-Dyn组件。

   ```TypeScript
   'use static';
   // entry/src/main/ets/pages/Index.ets

   import { ClickEvent, Entry, Column, Button, Component, Text, State } from '@kit.ArkUI';
   import es from '@ohos.lang.interop';
   import { Child, dynCreateArray } from 'dynamic_library';

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
         Child({ data: this.data })
       }
     }
   }
   ```

### ArkTS-Dyn使用Array传给ArkTS-Sta es.Array

完整示例结构如下：

```text
project/
├── entry/                          # ArkTS-Dyn主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets   # 父组件定义
│
├── dynamic_library/                # ArkTS-Dyn子模块（提供创建Array的方法）
│   └── src/
│       └── main/
│           └── ets/
│               └── components/
│                   └── MainPage.ets  # 导出创建Array方法
│
└── static_library/                 # ArkTS-Sta子模块
    ├── oh-package.json5            # 需依赖dynamic_library
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets  # 子组件定义
```

步骤：

1. 创建ArkTS-Dyn子模块`dynamic_library`，导出创建`Array`的方法。

   ```TypeScript
   // dynamic_library/src/main/ets/components/MainPage.ets
   export function dynCreateArray(): Array<string> {
     return ['apple', 'banana'];
   }
   ```

   ```TypeScript
   // dynamic_library/Index.ets
   export { dynCreateArray } from './src/main/ets/components/MainPage';
   ```

2. 创建ArkTS-Sta子模块`static_library`，定义接收`es.Array`类型的组件。

   ```TypeScript
   'use static';
   // static_library/src/main/ets/components/MainPage.ets

   import { Component, Column, Button, Text, ClickEvent, Link } from '@kit.ArkUI';
   import es from '@ohos.lang.interop';
   import { dynCreateArray } from 'dynamic_library';

   @Component
   export struct Child {
     @Link data: es.Array<string>;

     build() {
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

   ```TypeScript
   'use static';
   // static_library/Index.ets

   export { Child } from './src/main/ets/components/MainPage';
   ```

3. 在`static_library`的`oh-package.json5`中配置对`dynamic_library`的依赖。

   ```json5
   // static_library/oh-package.json5
   {
     "name": "static_library",
     "version": "1.0.0",
     "main": "Index.ets",
     "dependencies": {
       "dynamic_library": "file:../dynamic_library"
     }
   }
   ```

4. 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

   ```json5
   // entry/oh-package.json5
   {
     "dependencies": {
       "static_library": "file:../static_library"
     }
   }
   ```

5. 在ArkTS-Dyn主模块中引入ArkTS-Sta组件。

   ```TypeScript
   // entry/src/main/ets/pages/Index.ets
   import { Child } from 'static_library';

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
         Child({ data: this.data })
       }
     }
   }
   ```


### ArkTS-Dyn使用st.Array传给ArkTS-Sta Array

完整示例结构如下：

```text
project/
├── entry/                          # ArkTS-Dyn主模块
│   ├── config.json                 # 配置文件（新增）
│   ├── build-profile.json5         # 需添加arkOptions配置
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets   # 父组件定义
│
└── static_library/                 # ArkTS-Sta子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets  # 子组件定义
```

步骤：

1. 创建ArkTS-Sta子模块`static_library`，定义接收`Array`类型的组件。

   ```TypeScript
   'use static';
   // static_library/src/main/ets/components/MainPage.ets

   import { Component, Column, Button, Text, ClickEvent, Link } from '@kit.ArkUI';

   @Component
   export struct Child {
     @Link data: Array<string>;

     build() {
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

   ```TypeScript
   'use static';
   // static_library/Index.ets

   export { Child } from './src/main/ets/components/MainPage';
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
       "static_library": "file:../static_library"
     }
   }
   ```

5. 在ArkTS-Dyn主模块中引入ArkTS-Sta组件。

   ```TypeScript
   // entry/src/main/ets/pages/Index.ets
   import st, { STValue } from 'static.@ohos.lang.interop';
   import { Child } from 'static_library';

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
         Child({ data: this.data })
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
│                   └── Index.ets   # 父组件定义
│
└── dynamic_library/                # ArkTS-Dyn子模块
    ├── config.json                 # 配置文件（新增）
    ├── build-profile.json5         # 需添加arkOptions配置
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets  # 子组件定义
```

步骤：

1. 创建ArkTS-Dyn子模块`dynamic_library`，定义接收`st.Map`类型的组件。

   ```TypeScript
   // dynamic_library/src/main/ets/components/MainPage.ets
   import st, { STValue } from 'static.@ohos.lang.interop';

   @Component
   export struct Child {
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

   ```TypeScript
   // dynamic_library/Index.ets
   export { Child } from './src/main/ets/components/MainPage';
   ```

2. 在子模块`dynamic_library`根目录下创建`config.json`文件，用于配置`st`和`STValue`的导入别名。

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
   // dynamic_library/build-profile.json5
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
       "dynamic_library": "file:../dynamic_library"
     }
   }
   ```

5. 在ArkTS-Sta主模块中引入ArkTS-Dyn组件。

   ```TypeScript
   'use static';
   // entry/src/main/ets/pages/Index.ets

   import { ClickEvent, Entry, Column, Button, Component, Text, State } from '@kit.ArkUI';
   import { Child } from 'dynamic_library';

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
         Child({ data: this.data })
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
│                   └── Index.ets   # 父组件定义
│
└── dynamic_library/                # ArkTS-Dyn子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets  # 子组件定义
```

步骤：

1. 创建ArkTS-Dyn子模块`dynamic_library`，定义接收`Map`类型的组件。

   ```TypeScript
   // dynamic_library/src/main/ets/components/MainPage.ets

   @Component
   export struct Child {
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

   ```TypeScript
   // dynamic_library/Index.ets
   export { Child, dynCreateMap } from './src/main/ets/components/MainPage';
   ```

2. 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

   ```json5
   // entry/oh-package.json5
   {
     "dependencies": {
       "dynamic_library": "file:../dynamic_library"
     }
   }
   ```

3. 在ArkTS-Sta主模块中引入ArkTS-Dyn组件。

   ```TypeScript
   'use static';
   // entry/src/main/ets/pages/Index.ets

   import { ClickEvent, Entry, Column, Button, Component, Text, ForEach, State } from '@kit.ArkUI';
   import es from '@ohos.lang.interop';
   import { Child, dynCreateMap } from 'dynamic_library';

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
         Child({ data: this.data })
       }
     }
   }
   ```

### ArkTS-Dyn使用Map传给ArkTS-Sta es.Map

完整示例结构如下：

```text
project/
├── entry/                          # ArkTS-Dyn主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets   # 父组件定义
│
├── dynamic_library/                # ArkTS-Dyn子模块（提供创建Map的方法）
│   └── src/
│       └── main/
│           └── ets/
│               └── components/
│                   └── MainPage.ets  # 导出创建Map方法
│
└── static_library/                 # ArkTS-Sta子模块
    ├── oh-package.json5            # 需依赖dynamic_library
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets  # 子组件定义
```

步骤：

1. 创建ArkTS-Dyn子模块`dynamic_library`，导出创建`Map`的方法。

   ```TypeScript
   // dynamic_library/src/main/ets/components/MainPage.ets
   export function dynCreateMap(): Map<string, number> {
     return new Map<string, number>([['apple', 1], ['banana', 2]]);
   }
   ```

   ```TypeScript
   // dynamic_library/Index.ets
   export { dynCreateMap } from './src/main/ets/components/MainPage';
   ```

2. 创建ArkTS-Sta子模块`static_library`，定义接收`es.Map`类型的组件。

   ```TypeScript
   'use static';
   // static_library/src/main/ets/components/MainPage.ets

   import { Component, Column, Button, Text, ClickEvent, Link } from '@kit.ArkUI';
   import es from '@ohos.lang.interop';
   import { dynCreateMap } from 'dynamic_library';

   @Component
   export struct Child {
     @Link data: es.Map<string, number>;

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

   ```TypeScript
   'use static';
   // static_library/Index.ets

   export { Child } from './src/main/ets/components/MainPage';
   ```

3. 在`static_library`的`oh-package.json5`中配置对`dynamic_library`的依赖。

   ```json5
   // static_library/oh-package.json5
   {
     "name": "static_library",
     "version": "1.0.0",
     "main": "Index.ets",
     "dependencies": {
       "dynamic_library": "file:../dynamic_library"
     }
   }
   ```

4. 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

   ```json5
   // entry/oh-package.json5
   {
     "dependencies": {
       "static_library": "file:../static_library"
     }
   }
   ```

5. 在ArkTS-Dyn主模块中引入ArkTS-Sta组件。

   ```TypeScript
   // entry/src/main/ets/pages/Index.ets
   import { Child } from 'static_library';

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
         Child({ data: this.data })
       }
     }
   }
   ```


### ArkTS-Dyn使用st.Map传给ArkTS-Sta Map

完整示例结构如下：

```text
project/
├── entry/                          # ArkTS-Dyn主模块
│   ├── config.json                 # 配置文件（新增）
│   ├── build-profile.json5         # 需添加arkOptions配置
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets   # 父组件定义
│
└── static_library/                 # ArkTS-Sta子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets  # 子组件定义
```

步骤：

1. 创建ArkTS-Sta子模块`static_library`，定义接收`Map`类型的组件。

   ```TypeScript
   'use static';
   // static_library/src/main/ets/components/MainPage.ets

   import { Component, Column, Button, Text, ClickEvent, Link } from '@kit.ArkUI';

   @Component
   export struct Child {
     @Link data: Map<string, number>;

     build() {
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

   ```TypeScript
   'use static';
   // static_library/Index.ets

   export { Child } from './src/main/ets/components/MainPage';
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
       "static_library": "file:../static_library"
     }
   }
   ```

5. 在ArkTS-Dyn主模块中引入ArkTS-Sta组件。

   ```TypeScript
   // entry/src/main/ets/pages/Index.ets
   import st, { STValue } from 'static.@ohos.lang.interop';
   import { Child } from 'static_library';

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
         Child({ data: this.data })
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
│                   └── Index.ets   # 父组件定义
│
└── dynamic_library/                # ArkTS-Dyn子模块
    ├── config.json                 # 配置文件（新增）
    ├── build-profile.json5         # 需添加arkOptions配置
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets  # 子组件定义
```

步骤：

1. 创建ArkTS-Dyn子模块`dynamic_library`，定义接收`st.Set`类型的组件。

   ```TypeScript
   // dynamic_library/src/main/ets/components/MainPage.ets
   import st, { STValue } from 'static.@ohos.lang.interop';

   @Component
   export struct Child {
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

   ```TypeScript
   // dynamic_library/Index.ets
   export { Child } from './src/main/ets/components/MainPage';
   ```

2. 在子模块`dynamic_library`根目录下创建`config.json`文件，用于配置`st`和`STValue`的导入别名。

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
   // dynamic_library/build-profile.json5
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
       "dynamic_library": "file:../dynamic_library"
     }
   }
   ```

5. 在ArkTS-Sta主模块中引入ArkTS-Dyn组件。

   ```TypeScript
   'use static';
   // entry/src/main/ets/pages/Index.ets

   import { ClickEvent, Entry, Column, Button, Component, Text, State } from '@kit.ArkUI';
   import { Child } from 'dynamic_library';

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
         Child({ data: this.data })
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
│                   └── Index.ets   # 父组件定义
│
└── dynamic_library/                # ArkTS-Dyn子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets  # 子组件定义
```

步骤：

1. 创建ArkTS-Dyn子模块`dynamic_library`，定义接收`Set`类型的组件。

   ```TypeScript
   // dynamic_library/src/main/ets/components/MainPage.ets

   @Component
   export struct Child {
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

   ```TypeScript
   // dynamic_library/Index.ets
   export { Child, dynCreateSet } from './src/main/ets/components/MainPage';
   ```

2. 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

   ```json5
   // entry/oh-package.json5
   {
     "dependencies": {
       "dynamic_library": "file:../dynamic_library"
     }
   }
   ```

3. 在ArkTS-Sta主模块中引入ArkTS-Dyn组件。

   ```TypeScript
   'use static';
   // entry/src/main/ets/pages/Index.ets

   import { ClickEvent, Entry, Column, Button, Component, Text, State } from '@kit.ArkUI';
   import es from '@ohos.lang.interop';
   import { Child, dynCreateSet } from 'dynamic_library';

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
         Child({ data: this.data })
       }
     }
   }
   ```

### ArkTS-Dyn使用Set传给ArkTS-Sta es.Set

完整示例结构如下：

```text
project/
├── entry/                          # ArkTS-Dyn主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets   # 父组件定义
│
├── dynamic_library/                # ArkTS-Dyn子模块（提供创建Set的方法）
│   └── src/
│       └── main/
│           └── ets/
│               └── components/
│                   └── MainPage.ets  # 导出创建Set方法
│
└── static_library/                 # ArkTS-Sta子模块
    ├── oh-package.json5            # 需依赖dynamic_library
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets  # 子组件定义
```

步骤：

1. 创建ArkTS-Dyn子模块`dynamic_library`，导出创建`Set`的方法。

   ```TypeScript
   // dynamic_library/src/main/ets/components/MainPage.ets
   export function dynCreateSet(): Set<string> {
     return new Set<string>(['apple', 'banana']);
   }
   ```

   ```TypeScript
   // dynamic_library/Index.ets
   export { dynCreateSet } from './src/main/ets/components/MainPage';
   ```

2. 创建ArkTS-Sta子模块`static_library`，定义接收`es.Set`类型的组件。

   ```TypeScript
   'use static';
   // static_library/src/main/ets/components/MainPage.ets

   import { Component, Column, Button, Text, ClickEvent, Link } from '@kit.ArkUI';
   import es from '@ohos.lang.interop';
   import { dynCreateSet } from 'dynamic_library';

   @Component
   export struct Child {
     @Link data: es.Set<string>;

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

   ```TypeScript
   'use static';
   // static_library/Index.ets

   export { Child } from './src/main/ets/components/MainPage';
   ```

3. 在`static_library`的`oh-package.json5`中配置对`dynamic_library`的依赖。

   ```json5
   // static_library/oh-package.json5
   {
     "name": "static_library",
     "version": "1.0.0",
     "main": "Index.ets",
     "dependencies": {
       "dynamic_library": "file:../dynamic_library"
     }
   }
   ```

4. 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

   ```json5
   // entry/oh-package.json5
   {
     "dependencies": {
       "static_library": "file:../static_library"
     }
   }
   ```

5. 在ArkTS-Dyn主模块中引入ArkTS-Sta组件。

   ```TypeScript
   // entry/src/main/ets/pages/Index.ets
   import { Child } from 'static_library';

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
         Child({ data: this.data })
       }
     }
   }
   ```


### ArkTS-Dyn使用st.Set传给ArkTS-Sta Set

完整示例结构如下：

```text
project/
├── entry/                          # ArkTS-Dyn主模块
│   ├── config.json                 # 配置文件（新增）
│   ├── build-profile.json5         # 需添加arkOptions配置
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets   # 父组件定义
│
└── static_library/                 # ArkTS-Sta子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets  # 子组件定义
```

步骤：

1. 创建ArkTS-Sta子模块`static_library`，定义接收`Set`类型的组件。

   ```TypeScript
   'use static';
   // static_library/src/main/ets/components/MainPage.ets

   import { Component, Column, Button, Text, ClickEvent, Link } from '@kit.ArkUI';

   @Component
   export struct Child {
     @Link data: Set<string>;

     build() {
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

   ```TypeScript
   'use static';
   // static_library/Index.ets

   export { Child } from './src/main/ets/components/MainPage';
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
       "static_library": "file:../static_library"
     }
   }
   ```

5. 在ArkTS-Dyn主模块中引入ArkTS-Sta组件。

   ```TypeScript
   // entry/src/main/ets/pages/Index.ets
   import st, { STValue } from 'static.@ohos.lang.interop';
   import { Child } from 'static_library';

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
         Child({ data: this.data })
       }
     }
   }
   ```

## 常见问题

### 声明文件编译报错

跨语言传递集合类型时，编译时生成的声明文件可能转换错误，需要开发者手动修改声明文件报错位置后增量编译，以符合语法规格。详见[互操作声明文件规范](./arkts-ui-interop-declaration-spec.md)。

**ArkTS-Sta生成声明文件修改示例**

源码

```TypeScript
'use static';

// static_library/src/main/ets/components/MainPage.ets
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

```TypeScript
// static_library/build/default/intermediates/declgen/default/declgenV1/static_library/src/main/ets/components/MainPage.d.ets

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
