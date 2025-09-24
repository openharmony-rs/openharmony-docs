# @ohos.arkui.stateManagement (状态管理)

状态管理模块提供了应用程序动态刷新、UI数据存储、使能数据观察等能力。

>**说明：**
>
>本模块首批接口从API version 20开始支持，后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
>本模块仅适用于ArkTS静态上下文中使用。

## 导入模块

```ts
import { UIUtils } from '@ohos.arkui.stateManagement';
```

## UIUtils

UIUtils是状态管理提供的工具，用于处理可观察数据。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### makeObserved

static makeObserved\<T extends object\>(source: T): T

将不可观察数据转化为可观察数据。支持built-in类型（Array、Map、Set、Date）以及interface字面量。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明         |
| ------ | ---- | ---- | ------------ |
| source | T    | 是   | 数据源对象。 |

**返回值：**

| 类型 | 说明               |
| ---- | ------------------ |
| T    | 可观察的数据对象。 |

**示例：**

```ts
'use static'

import { Entry, Component, Column, Text, ClickEvent } from '@ohos.arkui.component';
import { UIUtils } from '@ohos.arkui.stateManagement';
interface Info {
  name: string,
  age: number
}
@Entry
@Component
struct Index {
  info: Info = UIUtils.makeObserved({ name: 'Jack', age: 25} as Info) as Info;
  build() {
    Column() {
      Text(`info.name: ${this.info.name}`)
        .onClick((e: ClickEvent) => {
          this.info.name = 'Tom';
        })
    }
  }
}
```

### getTarget

static getTarget\<T extends object\>(source: T): T

获取状态管理框架包装前的原始对象。支持built-in类型（Array、Map、Set、Date）以及interface字面量。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明                   |
| ------ | ---- | ---- | ---------------------- |
| source | T    | 是   | 状态管理框架包装的对象。 |

**返回值：**

| 类型 | 说明                         |
| ---- | ---------------------------- |
| T    | 状态管理框架包装前的原始对象。 |

**示例：**

```ts
'use static'

import { Entry, Component, Column, Text, ClickEvent } from '@ohos.arkui.component';
import { State, UIUtils } from '@ohos.arkui.stateManagement';
interface Info {
  name: string,
  age: number
}
@Entry
@Component
struct Index {
  rawInfo: Info = { name: 'Jack', age: 25} as Info;
  // 装饰字面量
  @State info: Info = this.rawInfo;
  build() {
    Column() {
      Text(`rawInfo === info: ${this.rawInfo === this.info}`) // false
      Text(`rawInfo === UIUtils.getTarget(info): ${this.rawInfo === UIUtils.getTarget(this.info)}`) // true
    }
  }
}
```

### makeBindingReadonly\<T\>

static makeBindingReadonly\<T\>(getter: GetterCallback\<T\>): Binding\<T\>

创建只读的单向数据绑定实例，用于在@Builder函数中为参数类型为Binding的参数提供实参。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明     |
| ------ | ---- | ---- | ------------ |
| getter | [GetterCallback\<T\>](#gettercallbackt)    | 是   | 获取值的回调函数，每次访问值时重新执行以获取最新值。 |

**返回值：**

| 类型 | 说明                                             |
| ---- | ------------------------------------------------ |
| [Binding\<T\>](#bindingt)    | 包含一个value属性，用于获取当前绑定的值，且只能读取，不能修改。 |

**示例：**

```ts
import { UIUtils, Binding, State } from '@ohos.arkui.stateManagement';
import { Entry, Column, Row, Component, Button, ButtonAttribute, ClickEvent, Builder } from '@ohos.arkui.component';

@Builder
function CustomButton(readOnlyParam: Binding<number>) {
  Row() {
    Button(`Custom btn: ${readOnlyParam.value}`)
  }
}

@Entry
@Component
struct MyApp {
  @State num1: number = 1;
  build() {
    Column() {
      Button(`Entry btn ${this.num1}`)
        .onClick((e) => {
          this.num1 += 1;
        });
      CustomButton(
        /**
         * 创建只读绑定实例
         * @param getter - 返回this.number1的函数
         * @returns 只读的Binding<number>对象
         *
         * 特点：
         * 1. 每次访问.value时重新计算
         * 2. 不能直接修改值
         */
        UIUtils.makeBindingReadonly(() => this.num1),
      );
    }
  }
}
```

### makeBindingMutable\<T\>

static makeBindingMutable\<T\>(getter: GetterCallback\<T\>, setter: SetterCallback\<T\>): MutableBinding\<T\>

创建双向数据绑定实例，用于构建@Builder函数中类型为MutableBinding的参数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明     |
| ------ | ---- | ---- | ------------ |
| getter | [GetterCallback\<T\>](#gettercallbackt)    | 是   | 获取值的回调函数，每次访问值时重新执行。 |
| setter | [SetterCallback\<T\>](#settercallbackt)    | 是   | 定义如何更新值，当.value被修改时调用。 |

**返回值：**

| 类型 | 说明                                             |
| ---- | ------------------------------------------------ |
| [MutableBinding\<T\>](#mutablebindingt)    | 包含一个value属性，支持读取和修改数据，设置值时检查类型是否匹配泛型`T`。 |

**示例：**

```ts
import { UIUtils, MutableBinding, State } from '@ohos.arkui.stateManagement';
import { Entry, Column, Row, Component, Button, ButtonAttribute, ClickEvent, Builder } from '@ohos.arkui.component';

@Builder
function CustomButton(mutableParam1: MutableBinding<number>, mutableParam2: MutableBinding<number>) {
  Row() {
    Button(`Custom btn: ${mutableParam1.value} -- ${mutableParam2.value}`)
      .onClick((e) => {
        mutableParam1.value += 1;
        mutableParam2.value += 1;
      });
  }
}

@Entry
@Component
struct MyApp {
  @State num2: number = 10;
  @State num3: number = 100;

  build() {
    Column() {
      Button(`Entry btn ${this.num2} -- ${this.num3}`)
        .onClick((e) => {
          this.num2 += 1;
          this.num3 += 1;
        });
      CustomButton(
        /**
         * 创建绑定
         * @param getter - 返回this.number2的函数
         * @param setter - 绑定值修改时调用的回调
         * @returns 可变的MutableBinding<number>对象
         *
         * 特点：
         * 1. 支持读写操作
         * 2. 修改.value时会自动调用setter回调
         */
        UIUtils.makeBindingMutable(() => this.num2, (v) => {
          this.num2 = v;
        }),
        UIUtils.makeBindingMutable(() => this.num3, (v) => {
          this.num3 = v;
        })
      );
    }
  }
}
```

### makeBinding

static overload makeBinding { makeBindingReadonly, makeBindingMutable }

根据入参，自动匹配makeBindingReadonly和makeBindingMutable。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
import { UIUtils, Binding, MutableBinding, State } from '@ohos.arkui.stateManagement';
import { Entry, Column, Row, Component, Button, ButtonAttribute, ClickEvent, Builder } from '@ohos.arkui.component';

@Builder
function CustomButton(readOnlyParam: Binding<number>, mutableParam: MutableBinding<number>) {
  Row() {
    Button(`Custom btn: ${readOnlyParam.value} -- ${mutableParam.value}`)
      .onClick((e) => {
        mutableParam.value += 1;
      });
  }
}

@Entry
@Component
struct MyApp {
  @State num2: number = 10;
  @State num3: number = 100;

  build() {
    Column() {
      Button(`Entry btn ${this.num2} -- ${this.num3}`)
        .onClick((e) => {
          this.num2 += 1;
          this.num3 += 1;
        });
      CustomButton(
        UIUtils.makeBinding(() => this.num2),
        UIUtils.makeBinding(() => this.num3, (v) => {
          this.num3 = v;
        })
      );
    }
  }
}
```

## GetterCallback\<T\>

type GetterCallback\<T\> = () => T

获取绑定值的回调方法。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明                                             |
| ---- | ------------------------------------------------ |
| T    | 返回当前组件。 |

**示例：**

```ts
import { UIUtils, Binding, State } from '@ohos.arkui.stateManagement';
import { Entry, Column, Row, Component, Button, ButtonAttribute, ClickEvent, Builder } from '@ohos.arkui.component';

@Builder
function CustomButton(readOnlyParam: Binding<number>) {
  Row() {
    Button(`Custom btn: ${readOnlyParam.value}`)
  }
}

@Entry
@Component
struct MyApp {
  @State num1: number = 1;
  build() {
    Column() {
      Button(`Entry btn ${this.num1}`)
        .onClick((e) => {
          this.num1 += 1;
        });
      CustomButton(
        // UIUtils.makeBinding函数的第一个参数是GetterCallback
        UIUtils.makeBinding(() => this.num1),
      );
    }
  }
}
```

## SetterCallback\<T\>

type SetterCallback\<T\> = (newValue: T) => void

设置绑定值的回调方法。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明     |
| ------ | ---- | ---- | ------------ |
| newValue | T    | 是   | 类型为T的参数。   |

**示例：**

```ts
import { UIUtils,MutableBinding, State } from '@ohos.arkui.stateManagement';
import { Entry, Column, Row, Component, Button, ButtonAttribute, ClickEvent, Builder } from '@ohos.arkui.component';

@Builder
function CustomButton(mutableParam1: MutableBinding<number>, mutableParam2: MutableBinding<number>) {
  Row() {
    Button(`Custom btn: ${mutableParam1.value} -- ${mutableParam2.value}`)
      .onClick((e) => {
        mutableParam1.value += 1;
        mutableParam2.value += 1;
      });
  }
}

@Entry
@Component
struct MyApp {
  @State num2: number = 10;
  @State num3: number = 100;

  build() {
    Column() {
      Button(`Entry btn ${this.num2} -- ${this.num3}`)
        .onClick((e) => {
          this.num2 += 1;
          this.num3 += 1;
        });
      CustomButton(
        // UIUtils.makeBinding函数的第二个参数应为SetterCallback
        UIUtils.makeBinding(() => this.num2, (v) => {
          this.num2 = v;
        }),
        UIUtils.makeBinding(() => this.num3, (v) => {
          this.num3 = v;
        })
      );
    }
  }
}
```

## Binding\<T\>

只读数据绑定的泛型类可以绑定任意类型的数据（需要与@builder参数列表同时使用）。当调用函数时，需要使用makeBinding来进行值的传递。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### value
get value(): T

提供get访问器以获取当前绑定值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型             | 说明                                                         |
| -------------------- | ------------------------------------------------------------ |
| T |返回值类型为泛型参数T，与Binding\<T\>定义的类型一致。|

**示例：**

```ts
import { Binding } from '@ohos.arkui.stateManagement';
import { Row, Button, Builder } from '@ohos.arkui.component';

@Builder
function CustomButton(readOnlyParam: Binding<number>) {
  // CustomButton的第一个参数为Binding，一个只读数据绑定的泛型类
  Row() {
    // num1.value Binding类可以使用绑定的值
    Button(`Custom btn: ${readOnlyParam.value}`)
  }
}
```

## MutableBinding\<T\>

可变数据绑定的泛型类，允许对绑定值进行读写操作，提供完整的get和set访问器（需要与@builder参数列表同时使用）。当调用函数时，需要使用makeBinding来进行值的传递。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### value
set value(newValue: T)

提供set访问器，用于设置当前绑定值。构造MutableBinding类实例时必须提供set访问器，否则会触发运行时错误。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| newValue  | T | 是   | 参数类型为泛型参数T，与MutableBinding\<T\>定义的类型一致。 |

### value
get value(): T

提供get访问器，用于获取当前绑定值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型             | 描述                                                         |
| -------------------- | ------------------------------------------------------------ |
| T |返回值类型为泛型参数T，与Binding\<T\>定义的类型一致。|

**示例：**

```ts
import { MutableBinding } from '@ohos.arkui.stateManagement';
import { Row, Button, ClickEvent, Builder } from '@ohos.arkui.component';

@Builder
function CustomButton(mutableParam1: MutableBinding<number>, mutableParam2: MutableBinding<number>) {
  // CustomButton的第二个参数为MutableBinding，即一个可变数据绑定的泛型类
  Row() {
    Button(`Custom btn: ${mutableParam1.value} -- ${mutableParam2.value}`)
      .onClick((e) => {
        // 可变数据绑定的泛型类可以修改绑定的值
        mutableParam1.value += 1;
        mutableParam2.value += 1;
      });
  }
}
```

