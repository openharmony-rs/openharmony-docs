# Stack
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fenglinbailu-->
<!--Designer: @lanshouren-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->

堆叠容器，子组件按照顺序依次入栈，后一个子组件覆盖前一个子组件。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 该组件从API version 7开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
> 
> - 通用属性[align](./ts-universal-attributes-location.md#align)在该组件上支持镜像能力。


## 子组件

可以包含子组件。

## 接口

### Stack

Stack(options?: StackOptions)

堆叠容器，子组件按照顺序依次入栈，后一个子组件覆盖前一个子组件。

> **说明：**
>
> 过多的组件嵌套会导致性能劣化。在部分场景中，直接使用组件属性或借助系统API的能力可以替代层叠容器的效果，减少了嵌套组件数进而优化性能。最佳实践请参考[组件嵌套优化-优先使用组件属性代替嵌套组件](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-component-nesting-optimization#section78181114123811)。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名       | 类型                                    | 必填 | 说明                                                    |
| ------------ | ------------------------------------------- | ---- | ----------------------------------------------------------- |
| options | [StackOptions](#stackoptions18对象说明) | 否   | 设置子组件在容器内的对齐方式。 |

## StackOptions<sup>18+</sup>对象说明

设置堆叠容器的子组件对齐方式。

> **说明：**
>
> 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**卡片能力：** 从API version 18开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 18

**ArkTS-Sta起始版本：** 23

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| alignContent<sup>7+</sup> | [Alignment](ts-appendix-enums.md#alignment) | 否 | 是   | 设置子组件在容器内的对齐方式。<br/>默认值：Alignment.Center <br />非法值：按默认值处理。<br/>**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 7<br/>**ArkTS-Sta起始版本：** 23 |

## 属性

除支持[通用属性](ts-component-general-attributes.md)外，还支持以下属性：

### alignContent

ArkTS-Dyn: alignContent(value: Alignment)

ArkTS-Sta: alignContent(value: Alignment | undefined)

设置子组件在容器内的对齐方式。该属性与[align](ts-universal-attributes-location.md#align)同时设置时，后设置的属性生效。该属性与接口的构造入参同时设置时，生效属性上的设置效果。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 23

**参数：** 

| 参数名 | 类型                                        | 必填 | 说明                                                        |
| ------ | ------------------------------------------- | ---- | ----------------------------------------------------------- |
| value  | ArkTS-Dyn: [Alignment](ts-appendix-enums.md#alignment)<br/>ArkTS-Sta: [Alignment](ts-appendix-enums.md#alignment) \| undefined | 是   | 所有子组件在容器内的对齐方式。<br/>默认值：Alignment.Center <br />非法值：按默认值处理。<br/>取值为undefined时，按默认值处理。 |

### attributeModifier<sup>12+</sup>

ArkTS-Dyn: attributeModifier(modifier: AttributeModifier\<StackAttribute>)

ArkTS-Sta: attributeModifier(modifier: AttributeModifier\<StackAttribute> | AttributeModifier\<CommonMethod> | undefined)

设置组件的动态属性。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：** 

| 参数名 | 类型                                                | 必填 | 说明                                                         |
| ------ | --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| modifier  | ArkTS-Dyn: [AttributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifiert)\<StackAttribute><br/>ArkTS-Sta: [AttributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifiert)\<StackAttribute> \| [AttributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifiert)\<CommonMethod> \| undefined | 是   | 动态设置Stack组件的属性。<br/>取值为undefined时，按当前组件的属性方法默认值处理。 |

### syncLoad

syncLoad(enable: boolean)

设置是否同步加载Stack区域内所有子组件。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**参数：** 

| 参数名 | 类型                                                         | 必填 | 说明                                                         |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| enable   | boolean | 是   | 是否同步加载Stack区域内所有子组件。<br/>true表示同步加载；false表示异步加载。<br/>默认值：true<br/>**说明：** <br/>设置为false时，在首次显示场景，若当前帧布局耗时超过50ms，会将Stack区域内尚未布局的子组件延后到下一帧进行布局。 |

## 事件

支持[通用事件](ts-component-general-events.md)。

## 示例

当Stack的[alignContent](#aligncontent)属性设为Alignment.Bottom，且[syncLoad](#syncload)为true时，其子组件的显示效果表现为在Stack组件底部横向居中并且所有子组件在同一帧内加载完成。

从API版本26.0.0开始，新增syncLoad属性。

**ArkTS-Dyn示例：**

```ts
// xxx.ets
@Entry
@Component
struct StackExample {
  build() {
    Stack({ alignContent: Alignment.Bottom }) {
      Text('First child, show in bottom').width('90%').height('100%').backgroundColor(0xd2cab3).align(Alignment.Top)
      Text('Second child, show in top').width('70%').height('60%').backgroundColor(0xc1cbac).align(Alignment.Top)
    }.width('100%').height(150).margin({ top: 5 })
    // 从API版本26.0.0开始，新增syncLoad属性。
    .syncLoad(true)
  }
}
```

**ArkTS-Sta示例：**

```ts
// xxx.ets
import { Entry, Component, Text, Stack, Alignment, Margin } from '@ohos.arkui.component';

@Entry
@Component
struct StackExample {
  build() {
    Stack({ alignContent: Alignment.Bottom }) {
      Text('First child, show in bottom').width('90%').height('100%').backgroundColor(0xd2cab3).align(Alignment.Top)
      Text('Second child, show in top').width('70%').height('60%').backgroundColor(0xc1cbac).align(Alignment.Top)
    }.width('100%').height(150).margin({ top: 5 } as Margin)
  }
}
```

![zh-cn_image_0000001219982699](figures/zh-cn_image_0000001219982699.PNG)
