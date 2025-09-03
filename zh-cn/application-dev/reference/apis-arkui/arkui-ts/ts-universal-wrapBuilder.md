# wrapBuilder
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

使用wrapBuilder封装全局@Builder，可以帮助维护代码。开发指南见[wrapBuilder：封装全局@Builder](../../../ui/state-management/arkts-wrapBuilder.md)。

> **说明：**
>
> 本模块首批接口从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## wrapBuilder

wrapBuilder\<Args extends Object[]>(builder: (...args: Args) => void): WrappedBuilder\<Args>

wrapBuilder是一个模板函数，返回一个`WrappedBuilder`对象。模板参数`Args extends Object[]`是需要包装的builder函数的参数列表。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名         | 类型                                   | 必填 | 说明                                                         |
| -------------- | -------------------------------------- | ---- | ---- |
| builder        | (...args: Args) => void                | 是   | @Builder装饰的全局函数。 |

**示例：**

```ts
@Builder
function MyBuilder(value: string, size: number) {
  Text(value)
    .fontSize(size)
}
let builderVar: WrappedBuilder<[string, number]> = wrapBuilder(MyBuilder);
```
## WrappedBuilder

@Builder函数的包装类。模板参数`Args extends Object[]`应传入@Builder函数的参数类型列表。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### 属性

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称    | 类型                    | 只读 | 可选 | 说明      |
| ------- | ---------------------- | ---- | ---  | -------- |
| builder | (...args: Args) => void | 否  | 否   | @Builder修饰的全局函数。 |


### constructor

constructor(builder: (...args: Args) => void)

WrappedBuilder的构造函数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名    | 类型                                    | 必填 | 说明                                                              |
| --------- | --------------------------------------- | ---- | ----------------------------------------------------------------- |
| builder   | (...args: Args) => void)               | 是 | @Builder装饰的全局函数。 |

**示例：**

```ts
@Builder
function MyBuilder(value: string, size: number) {
  Text(value)
    .fontSize(size)
}
let builderVar: WrappedBuilder<[string, number]> = new WrappedBuilder<[string, number]>(MyBuilder);
```