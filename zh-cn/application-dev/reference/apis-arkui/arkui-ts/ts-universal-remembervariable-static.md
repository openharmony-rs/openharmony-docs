# rememberVariable：@Builder内部状态

开发者可以在[@Builder](../../../ui/state-management/arkts-builder.md)函数内声明新的状态变量并用于UI组件，当这些状态变量更新时，会触发@Builder内UI组件的更新。开发指南见[rememberVariable：@Builder内部状态](../../../ui/state-management-static/arkts-static-remembervariable.md)。

> **说明：**
>
> - 本模块适用于ArkTS-Sta。
>
> - 本模块首批接口从API version 23开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## rememberVariable\<T\>

rememberVariable\<T\>(initialValue: RememberInitialType\<T\>): MutableVariable\<T\>

创建状态变量。

**装饰器类型：** @Builder

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名         | 类型                                            | 必填 | 说明                                                         |
| -------------- | ---------------------------------------------- | ---- | ----  |
| initialValue   | [RememberInitialType\<T\>](#rememberinitialtypet) | 是   | 状态变量的初始值。 |

**返回值：**

| 类型                                   | 说明                       |
| -------------------------------------- | -------------------------- |
| [MutableVariable\<T\>](#mutablevariablet) | 返回状态变量。              |

**示例：**

```ts
'use static'
import { rememberVariable, MutableVariable, Entry, Component, Column, Text, Builder, Button } from '@kit.ArkUI';

@Builder
function MyBuilder() {
  let message: MutableVariable<string> = rememberVariable<string>('Hello world'); // 声明基础类型的状态变量，直接传入初始值。
  Text(`message: ${message.value}`) // 通过.value获取状态变量的值，绑定UI组件。
  Button('Change message in builder')
    .onClick(() => {
      message.value += '!'; // 通过.value修改状态变量，触发UI组件更新。
    })
}
@Entry
@Component
struct Index {
  build() {
    Column() {
      MyBuilder()
    }
  }
}
```

## RememberInitialType\<T\> 

type RememberInitialType\<T\> = (() => T) | T

状态变量初始值入参类型。基础类型使用类型T直接传入；复杂类型（interface、class和包含Array、Map、Set和Date的内置类型）使用回调（() => T）初始化能避免重复创建实例，性能更高。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
'use static'
import { rememberVariable, MutableVariable, Entry, Component, Column, Text,
         Builder, Observed, Button } from '@kit.ArkUI';

@Observed
class Person {
  name: string
  constructor(name: string) {
    this.name = name;
  }
}
@Builder
function MyBuilder() {
  let message: MutableVariable<string> = rememberVariable<string>('Hello world'); // 声明基础类型的状态变量，直接传入初始值。
  let person: MutableVariable<Person> = rememberVariable<Person>(() => new Person('ArkTS')); // 声明class类型状态变量，传入回调，避免重复创建实例。
  Text(`message: ${message.value}`) // 通过.value获取状态变量的值，绑定UI组件。
  Text(`My name is: ${person.value.name}`)
  Button('Change message in builder')
    .onClick(() => {
      message.value += '!'; // 通过.value修改状态变量，触发UI组件更新。
    })
  Button('Change name')
    .onClick(() => {
      person.value.name += '?';
    })
}
@Entry
@Component
struct Index {
  build() {
    Column() {
      MyBuilder()
    }
  }
}
```

## MutableVariable\<T\>

rememberVariable创建的状态变量类型。

### 属性

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称    | 类型                    | 只读 | 可选 | 说明      |
| ------- | ---------------------- | ---- | ---  | -------- |
| value   | T                      | 否   | 否   | 状态变量的值。 |