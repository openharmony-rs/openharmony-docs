# wrapBuilder：封装全局@Builder (ArkTS-Sta)

使用wrapBuilder封装全局@Builder，可以帮助维护代码。开发指南见[wrapBuilder：封装全局@Builder（ArkTS-Sta）](../../../ui/state-management/arkts-v1.2-wrapBuilder.md)。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。
>
> - 本模块首批接口从API version 20开始支持。
>
> - 后续版本的新增接口，采用上角标单独标记接口的起始版本。

## wrapBuilder

wrapBuilder\<T\>(builder: T): WrappedBuilder\<T\>

wrapBuilder是一个模板函数，返回一个`WrappedBuilder`对象。模板参数`T`是@Builder的函数类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名         | 类型                                    | 必填 | 说明                                                         |
| -------------- | -------------------------------------- | ---- | ---- |
| builder        | T                                      | 是   | @Builder装饰的全局函数。 |

**返回值：**

| 类型                  | 说明                       |
| --------------------- | -------------------------- |
| [WrappedBuilder\<T\>](#wrappedbuilder) | WrappedBuilder对象。 |

**示例：**

```ts
'use static'
import { Builder, Text, WrappedBuilder, wrapBuilder } from '@ohos.arkui.component';

@Builder
function MyBuilder(value: string, size: number) {
  Text(value)
    .fontSize(size)
}
let builderVar: WrappedBuilder<@Builder (value: string, size: number) => void> = wrapBuilder(MyBuilder);
```
## WrappedBuilder

@Builder函数的包装类。模板参数`T`应传入@Builder函数类型。

### 属性

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称    | 类型                    | 只读 | 可选 | 说明      |
| ------- | ---------------------- | ---- | ---  | -------- |
| builder | T                      | 否   | 否   | @Builder修饰的全局函数。 |


### constructor

constructor(builder: T)

WrappedBuilder的构造函数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名    | 类型                                    | 必填 | 说明                                                              |
| --------- | --------------------------------------- | ---- | ----------------------------------------------------------------- |
| builder   | T                                       | 是 | @Builder装饰的全局函数。 |

**示例：**

```ts
'use static'
import { Builder, Text, WrappedBuilder, wrapBuilder, Entry, Component } from '@ohos.arkui.component';

@Builder
function MyBuilder(value: string, size: number) {
  Text(value)
    .fontSize(size)
}
type MyBuilderType = @Builder (value: string, size: number) => void;
let builderVar: WrappedBuilder<MyBuilderType> = new WrappedBuilder<MyBuilderType>(MyBuilder);

@Entry
@Component
struct Index {
  build() {
    builderVar.builder('Hello world', 20)
  }
}
```