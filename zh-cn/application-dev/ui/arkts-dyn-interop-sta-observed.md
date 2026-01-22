# 在ArkTS-Dyn中使用ArkTS-Sta的@Observed和@ObjectLink（嵌套类对象属性变化）

## 概述

ArkUI的组件间数据交互能力是支持父子组件、兄弟组件、跨层级组件之间传递、同步数据的机制。从API version 23开始，支持在ArkTS-Dyn的UI组件中渲染和响应ArkTS-Sta的静态数据和[@Observed](../ui/state-management-static/arkts-static-observed-and-objectlink.md)装饰的数据的变化。


## 使用限制

- 遵循ArkTS-Dyn @Observed和@ObjectLink的[使用限制](../ui/state-management/arkts-observed-and-objectlink.md#限制条件)；

- 遵循ArkTS-Dyn @Track的[使用限制](../ui/state-management/arkts-track.md#限制条件)；

- 遵循ArkTS-Sta @Observed和@ObjectLink的[使用限制](../ui/state-management-static/arkts-static-observed-and-objectlink.md#限制条件)；

- 遵循ArkTS-Sta @Track的[使用限制](../ui/state-management-static/arkts-static-track.md#限制条件)；

- 不能在非UI线程中直接修改ArkTS-Dyn组件中使用的ArkTS-Sta @Observed装饰的数据成员的值，否则会运行异常；

- 遵循[ArkTS-Sta互操作](../quick-start/arkts-interop-overview.md)规范，如不支持ArkTS-Sta对象继承ArkTS-Dyn对象。


## 使用场景

基于以下示例结构，说明在ArkTS-Dyn组件中使用静态数据和@Observed装饰数据的场景。

```text
project/
├── entry/                           # ArkTS-Dyn主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets     # 使用静态@Observed装饰的数据
│
└── static_module/                    # ArkTS-Sta子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets   # 导出静态@Observed装饰的数据

```

示例如下：

- 创建ArkTS-Sta子模块`static_module`，在`src/main/ets/components`目录创建并导出静态@Observed装饰的数据。如何创建子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```TypeScript
'use static'

// static_module/src/main/ets/components/MainPage.ets
import { Observed, Track } from '@ohos.arkui.stateManagement';

@Observed
export class MyClassA { // 定义静态@Observed装饰的类并导出
  @Track name: string = 'text: x';
  message: string = 'text: x';
}
```

- 在ArkTS-Sta子模块`static_module`的`Index.ets`文件中导出静态@Observed装饰的数据。

```TypeScript
'use static'

// static_module/Index.ets
export { MyClassA } from './src/main/ets/components/MainPage'; // 导出静态@Observed装饰的类
```

- 在主模块`entry`的`oh-package.json5`文件的`dependencies`字段中添加子模块依赖。如何导入和使用子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```json
// entry/oh-package.json5

"dependencies": {
  "static_module": "file:../static_module"
}
```

- 在ArkTS-Dyn主模块中使用import语句导入ArkTS-Sta组件。

```TypeScript
// entry/src/main/ets/pages/Index.ets

// 引用ArkTS-Dyn动态@Observed装饰的数据
import { MyClassA } from 'static_module';

@Entry
@Component
export struct Index {
  @State state: MyClassA = new MyClassA();

  build() {
    Scroll() {
      Row() {
        Column() {
          // 在ArkTS-Dyn中使用动态@Observed装饰的数据
          Text(this.state.name)
            .height('10%')

          Row() {
            // 单独为静态@Observed装饰的类中的某一个成员赋值
            Button('Member Assignment')
              .layoutWeight(1)
              .onClick(() => {
                this.state.name = 'state: x';
              })

            // 创建新对象整体为静态@Observed装饰的类中的成员赋值
            Button('Overall Assignment')
              .layoutWeight(1)
              .onClick(() => {
                let data = new MyClassA();
                data.name = 'state: Hello';
                this.state = data;
              })
          }
          .width('80%')
        }
        .width('100%')
      }
    }
    .height('100%')
  }
}
```


## 常见问题

### 声明文件编译报错

由于ArkTS-Sta上下文中会将@Track装饰的属性自动转换出getter和setter方法，需要删除。详见[互操作声明文件规范](./arkts-ui-interop-declaration-spec.md)。

`entry/src/main/ets/components/MainPage.ets`文件中@Track的示例如下：

```TypeScript
'use static'

// static_module/src/main/ets/components/MainPage.ets
import { Observed, Track } from '@ohos.arkui.stateManagement';

@Observed
export class MyClassA { // 定义静态@Observed装饰的类并导出
  @Track name: string = 'text: x';
  message: string = 'text: x';
}
```

位于`static_module/build/default/intermediates/declgen/default/declgenV1/static_module/src/main/ets/components/MainPage.d.ets`的声明文件，修改前如下：

```TypeScript
import type { Record } from '../../../../../static.Record';

@Observed
export declare class MyClassA {
  @Track
  public get name(): string;
  @Track
  public set name(value: string);
  public get message(): string;
  public set message(value: string);
  constructor(); 
}
```

应按如下格式修改：

```TypeScript
import type { Record } from '../../../../../static.Record';

@Observed
export declare class MyClassA {
  @Track
  name: string;
  message: string;
}
```
