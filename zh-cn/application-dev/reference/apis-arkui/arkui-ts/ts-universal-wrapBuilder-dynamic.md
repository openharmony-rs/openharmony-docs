# wrapBuilder：封装全局@Builder 

当在一个struct内使用多个全局@Builder函数实现UI的不同效果时，代码维护将变得非常困难，且页面不够整洁。此时，可以使用wrapBuilder封装全局@Builder，帮助维护代码。开发指南见[wrapBuilder：封装全局@Builder](../../../ui/state-management/arkts-wrapBuilder.md)。

> **说明：**
>
> - 本装饰器仅适用于ArkTS-Dyn。
>
> - 本装饰器首批接口从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## wrapBuilder

wrapBuilder\<Args extend Object[]\>(builder: (...args: Args) => void): WrappedBuilder\<Args\>

wrapBuilder是一个模板函数，返回一个`WrappedBuilder`对象。模板参数`Args extends Object[]`是需要包装的builder函数的参数列表

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名         | 类型                                    | 必填 | 说明                                                         |
| -------------- | -------------------------------------- | ---- | ---- |
| builder        | (...args: Args) => void                | 是   | @Builder装饰的全局函数。 |

**返回值：**

| 类型                  | 说明                       |
| --------------------- | -------------------------- |
| [WrappedBuilder\<Args\>](#wrappedbuilder) | WrappedBuilder对象。 |

**示例：**

```ts
@Builder
function MyBuilder(value: string, size: number) {
  Text(value)
    .fontSize(size)
}

let globalBuilder: WrappedBuilder<[string, number]> = wrapBuilder(MyBuilder);
```
## WrappedBuilder

@Builder函数的包装类。模板参数`(...args: Args) => void`应传入@Builder函数类型。

### 属性

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称    | 类型                    | 只读 | 可选 | 说明      |
| ------- | ---------------------- | ---- | ---  | -------- |
| builder | (...args: Args) => void| 否   | 否   | @Builder修饰的全局函数。 |


### constructor

constructor(builder: (...args: Args) => void)

WrappedBuilder的构造函数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名    | 类型                                    | 必填 | 说明                                                              |
| --------- | --------------------------------------- | ---- | ----------------------------------------------------------------- |
| builder   | (...args: Args) => void                 | 是 | @Builder装饰的全局函数。 |

**示例：**

```ts
@Builder
function MyBuilder(value: string, size: number) {
  Text(value)
    .fontSize(size)
}

let globalBuilder: WrappedBuilder<[string, number]> = wrapBuilder(MyBuilder);

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    Row() {
      Column() {
        globalBuilder.builder(this.message, 50)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```