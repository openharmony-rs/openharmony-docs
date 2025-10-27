# 在ArkTS-Sta中使用ArkTS-Dyn动态数据

从API version 20开始，UI自定义组件互操作适用于[ArkTS-Sta互操作](../quick-start/arkts-interop-overview.md)中使用UI的场景。

完整示例结构如下：

```text
project/
├── entry/          # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── MainPage.ets
│
└── library/         # ArkTS-Dyn子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── DynData.ets
```

ArkUI互操作能力支持静态上下文调用动态模块的动态数据。

以下示例展示了如何在静态上下文中使用动态模块的动态数据。

- 创建ArkTS-Dyn子模块`library`，在`library/src/main/ets/components`目录创建并导出动态数据。

  ```TypeScript
  // library/src/main/ets/components/DynData.ets
  // ArkTS-Dyn定义动态数据
  export let testNumber: number = 123;
  export let testString: string = 'test string';
  export let testBoolean: boolean = true;
  export let testNull: number | null = 1;
  export let testUndefined: number | undefined = 2;
  ```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

  ```json
  // entry/oh-package.json5

  "dependencies": {
    "library": "file:../library",
  }
  ```

- 在ArkTS-Sta主模块中引入ArkTS-Dyn动态数据并使用。

  ```TypeScript
  // entry/src/main/ets/pages/MainPage.ets
  'use static'
  import { Entry, Text, Column, Component, Button, Margin, TextAlign, Scroll } from '@ohos.arkui.component';
  import { State } from '@ohos.arkui.stateManagement';
  import {
    testNumber, testString, testBoolean, testNull, testUndefined
  } from 'library';

  @Entry
  @Component
  struct TypeTestPage {
    @State NumberVal: number = testNumber;
    @State StringVal: string = testString;
    @State BooleanVal: boolean = testBoolean;
    @State NullVal: number | null = testNull;
    @State UndefinedVal: number | undefined = testUndefined;

    // 转为输出字符串
    toStringValue(value: number | string | boolean | null | undefined): string {
      if (value === null) return 'null';
      if (value === undefined) return 'undefined';
      return value.toString();
    }

    build() {
      Scroll() {
        Column() {
          // 更新ArkTS-Dyn动态数据
          Button('update')
            .height('30%')
            .width('40%')
            .onClick(() => {
              this.NumberVal = this.NumberVal + 1;
              this.StringVal = this.StringVal + 'str';
              this.BooleanVal = !this.BooleanVal;
              this.NullVal = (null ? 111 : null) as number | null;
              this.UndefinedVal = (undefined ? 222 : undefined) as number | undefined;
            })
          // 观察ArkTS-Dyn数据变化
          Text('Number:' + this.NumberVal)
          Text('String:' + this.StringVal)
          Text('Boolean:' + this.BooleanVal)
          Text('Null:' + this.toStringValue(this.NullVal))
          Text('Undefined:' + this.toStringValue(this.UndefinedVal))
        }
        .width('100%')
        .padding(10)
      }
    }
  }
  ```