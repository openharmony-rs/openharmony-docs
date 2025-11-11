# mutableBuilder
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @zhangwenhan-->
<!--Adviser: @zhang_yixin13-->

使用mutableBuilder封装全局@Builder，实现全局@Builder的动态切换。开发指南见[mutableBuilder: 实现全局@Builder动态更新](../../../ui/state-management/arkts-mutableBuilder.md) 

> **说明：**
>
> 本模块首批接口从API version 22开始支持。
>
> 后续版本的新增接口，采用上角标单独标记接口的起始版本。

## mutableBuilder

mutableBuilder\<Args extends Object[]\>(builder: BuilderCallback): MutableBuilder\<Args\>

`mutableBuilder`是一个模板函数，它返回一个`MutableBuilder`对象，只接受一个全局的`@Builder`函数作为其参数。
该函数返回的[MutableBuilder](#mutablebuilder-1)对象中，`builder`属性方法只能在自定义组件内部使用。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名       | 类型   | 必填 | 说明                                                     |
| ------------ | ------ | ---- | ------------------------------------------------------------ |
| builder     | [BuilderCallback](#buildercallback) | 是   | `@Builder`装饰的全局函数。                                       |

**返回值：**

| 类型                      | 说明                                                         |
| ------------------------- | ------------------------------------------------------------ |
| [MutableBuilder&lt;Args&gt;](#mutablebuilder-1) | MutableBuilder&lt;Args&gt;的实例，用于[全局\@Builder](../../../ui/state-management/arkts-builder.md#全局自定义构建函数)进行赋值和传递的类，实现全局@Builder的动态更新。 |

**示例：**

```ts
class TextContent {
  text: string = '';
}

@Builder
function textBuilder(p: TextContent) {
  Text(p.text).margin(20)
}

@Builder
function buttonBuilder(p: TextContent) {
  Button(p.text).margin(20)
}

let counter: number = 1;
@Entry
@ComponentV2
struct MyApp {
  @Local message: string = 'init';
  @Local switchingBuilder: MutableBuilder<[TextContent]> = mutableBuilder(textBuilder);
  build() {
    Column() {
      this.switchingBuilder.builder({ text: this.message })
      Button('Click to change')
      .onClick(() => {
        counter++; // 每次点击按钮修改counter来动态改变全局@Builder
        if(counter % 2 === 0) {
          this.message += 'B';
          this.switchingBuilder = mutableBuilder(buttonBuilder); // textBuilder--->buttonBuilder
        } else {
          this.message += 'T';
          this.switchingBuilder = mutableBuilder(textBuilder); // buttonBuilder--->textBuilder
        }
      })
    }.position({x: 120, y: 60})
  }
}
```

## MutableBuilder

class MutableBuilder\<Args extends Object[]\> extends WrappedBuilder\<Args\> {
}

用于实现包装[全局\@Builder](../../../ui/state-management/arkts-builder.md#全局自定义构建函数)的动态切换的类，MutableBuilder继承自[WrappedBuilder](./ts-universal-wrapBuilder.md)，其模板参数`Args extends Object[]`应传入@Builder函数的参数类型列表。[mutableBuilder](../../../ui/state-management/arkts-mutableBuilder.md)函数返回MutableBuilder对象。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BuilderCallback

type BuilderCallback = (...args: Args) => void

mutableBuilder函数入参为全局`@Builder`函数。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名       | 类型   | 必填 | 说明                                                     |
| ------------ | ------ | ---- | ------------------------------------------------------------ |
| ...args     | Args | 否   | 全局`@Builder`函数的入参。Args用于表示一个参数可以接收任意数量的参数。 |          

**示例：**

```ts
@Builder
function MyBuilder(value: string, size: number) {
  Text(value)
    .fontSize(size)
}
let builderVar: MutableBuilder<[string, number]> = mutableBuilder(MyBuilder); // 声明builderVar的类型为MutableBuilder 
```