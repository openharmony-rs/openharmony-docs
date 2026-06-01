# 组件双向绑定 (ArkTS-Sta)

\$$函数为系统组件提供ArkTS变量的双向绑定能力，使得ArkTS变量和系统组件的内部状态保持同步。

双向绑定语法详见[\$$()双向绑定函数](../../ui/state-management/arkts-two-way-sync-static.md)。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。
>
> - 本模块首批接口从API version 20开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { $$ } from '@kit.ArkUI';
```

##  \$$()<sup>23+</sup>

 \$$\<T\>(value: T): Bindable\<T\>

将支持双向绑定的组件属性转换成Bindable的绑定对象。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型   | 必填 | 说明               |
| -------- | ------ | ---- | ---------------------- |
| value | T | 是   | 支持双向绑定的属性。 |

**返回值：**

| 类型                                   | 说明                                                         |
| -------------------------------------- | ------------------------------------------------------------ |
| [Bindable\<T\>](#bindablet23)  | 将支持双向绑定的属性转成绑定对象。 |

**示例：**

```ts
'use static'

import { Text, Entry, Column, Component, $$, TextInput, State } from '@kit.ArkUI';

@Entry
@Component
struct MyStateSample {
  @State stateVar: string = "";

  build() {
    Column() {
      Text('展示$$()双向绑定')
      Text(this.stateVar)
      TextInput({ text: $$(this.stateVar), placeholder: 'input your word...' })
    }.width(`100%`).height(`100%`)
  }
}
```
##  Bindable\<T\><sup>23+</sup>

\$$()双向绑定函数的返回值类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

|名称   |类型    |只读   |可选    |说明      |
|--------|------------|------------|-----------|--------------|
|value        | T   |是   |否   |支持双向绑定的值。         |
|onChange         | [Callback\<T\>](../apis-basic-services-kit/js-apis-base.md#callback)   |是   |否   |定义可绑定属性的回调，该属性将在属性更改时调用。             |