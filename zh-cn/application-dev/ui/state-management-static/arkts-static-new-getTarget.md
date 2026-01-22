# getTarget接口：获取状态管理框架包装前的原始对象

开发者可以使用[getTarget](../../reference/apis-arkui/js-apis-stateManagement-static.md#gettarget)接口获取状态管理框架包装前的原始对象。

## 概述

状态管理框架会为Date、Map、Set、Array、interface字面量类型的原始对象添加包装类，用于观察其内部变化。这一层包装类使得变量类型发生改变，在涉及类型判断的场景，会导致无法达到预期效果。

- 在静态语言上下文中使用时，需要导入UIUtils工具。

  ```ts
  import { UIUtils } from '@kit.ArkUI';
  ```

- 状态管理V1和V2会给状态变量装饰器（如[@State](arkts-static-state.md)、[@Local](arkts-static-new-local.md)）装饰或[makeObserved接口](arkts-static-new-makeObserved.md)转换后的Date、Map、Set、Array、interface字面量添加一层包装类用于观察属性变化与API调用，使用getTarget接口可以获取这些包装对象的原始对象。

- 传入其他类型（如class类型）时，将不做处理。


## 限制条件

- getTarget传入参数必须是对象类型。传入非对象类型，如number、string、undefined、null，虽然在静态语言上下文中不会编译报错，但实际无作用，会直接返回传入内容。

  ```ts
  import { UIUtils } from '@kit.ArkUI';
  let res = UIUtils.getTarget(2); // 非对象类型入参，实际无作用，返回传入内容
  let res1 = UIUtils.getTarget(undefined); // 传入undefined，实际无作用，返回undefined
  let res2 = UIUtils.getTarget(null); // 传入null，实际无作用，返回null
  ```

- getTarget传入Date、Map、Set、Array以及interface字面量之外的class时，不做处理，直接返回传入内容。

  ```ts
  'use static'
  
  import { Entry, Component, Column, Text } from '@kit.ArkUI';
  import { State, Observed, UIUtils } from '@kit.ArkUI';
  @Observed
  class Info {
    name: string = 'Tom';
  }
  @Entry
  @Component
  struct Index {
    @State info: Info = new Info();
    build() {
      Column() {
        // 传入非Date、Map、Set、Array、interface字面量之外的对象时，不做处理，直接返回传入内容
        Text(`${UIUtils.getTarget(this.info) === this.info}`) // true
      }
    }
  }
  ```

- 更改getTarget获取的原始对象中的内容不会被观察，也不会触发UI刷新。

  ```ts
  'use static'
  
  import { Text, Column, Component, Entry, Button, ClickEvent } from '@kit.ArkUI';
  import { State, UIUtils } from '@kit.ArkUI';
  interface Info {
    name: string;
  }
  @Entry
  @Component
  struct Index {
    @State info: Info = { name: 'Tom' } as Info;
  
    build() {
      Column() {
        Text(`info.name: ${this.info.name}`)
        Button(`更改包装后对象的属性`)
          .onClick((e: ClickEvent) => {
            this.info.name = 'Alice'; // Text组件能够刷新
          })
        Button(`更改原始对象的属性`)
          .onClick((e: ClickEvent) => {
            let rawInfo: Info = UIUtils.getTarget(this.info);
            rawInfo.name = 'Bob'; // Text组件不能刷新
          })
      }
    }
  }
  ```

## 使用场景

状态管理V1与V2使用相同的数据包装机制，可以通过getTarget接口获取被包装前的原始对象。

Date、Map、Set、Array和interface字面量只有经过包装才具有观察内部变化的能力，即仅能通过包装类更改数据才能触发UI刷新。

使用下面的方法可以判断对象是否被状态管理包装。当表达式结果为false时，表示value是状态管理包装过的对象；否则，表示value不是状态管理包装过的对象。

```ts
UIUtils.getTarget(value) === value
```

以V1中的Array和interface字面量类型为例，完整示例如下。

```ts
'use static'

import { Text, Column, Component, Entry } from '@kit.ArkUI';
import { State, UIUtils } from '@kit.ArkUI';
interface Info {
  name: string;
}
@Entry
@Component
struct Index {
  rawArray: int[] = [1, 2, 3];
  rawInfo: Info = { name: 'Tom' } as Info;
  @State observedArray: int[] = this.rawArray; // 会添加包装类
  @State observedInfo: Info = this.rawInfo; // 会添加包装类
  build() {
    Column() {
      Text(`${UIUtils.getTarget(this.observedArray) === this.observedArray}`) // false，说明observedArray被包装
      Text(`${UIUtils.getTarget(this.observedArray) === this.rawArray}`) // true，getTarget获得原始对象
      Text(`${UIUtils.getTarget(this.observedInfo) === this.observedInfo}`) // false，说明observedArray被包装
      Text(`${UIUtils.getTarget(this.observedInfo) === this.rawInfo}`) // true，getTarget获得原始对象
    }
  }
}
```