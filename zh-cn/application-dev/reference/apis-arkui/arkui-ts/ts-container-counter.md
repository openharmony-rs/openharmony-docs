# Counter
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Zhang-Dong-hui-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

计数器组件，提供相应的增加或者减少的计数操作。

>  **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 该组件从API version 7开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
> 
> - 该组件从API版本26.0.0开始支持[WithTheme](./ts-container-with-theme.md)。
> 

## 子组件

可以包含子组件。


## 接口

Counter()

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 23

## 属性

除支持[通用属性](ts-component-general-attributes.md)外，还支持以下属性。 

### enableInc<sup>10+</sup>

ArkTS-Dyn: enableInc(value: boolean)

ArkTS-Sta: enableInc(value: boolean | undefined)

设置“增加”按钮的禁用或使能。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：** 

| 参数名 | 类型    | 必填 | 说明                                  |
| ------ | ------- | ---- | ------------------------------------- |
| value  | ArkTS-Dyn: boolean <br/>ArkTS-Sta: boolean  \| undefined | 是   | “增加”按钮禁用或使能。<br/>默认值：true，true表示使能“增加”按钮，false表示禁用“增加”按钮。<br/>设置undefined时恢复默认值。 |

### enableDec<sup>10+</sup>

ArkTS-Dyn: enableDec(value: boolean)

ArkTS-Sta: enableDec(value: boolean | undefined)

设置“减少”按钮的禁用或使能。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：** 

| 参数名 | 类型    | 必填 | 说明                                  |
| ------ | ------- | ---- | ------------------------------------- |
| value  | ArkTS-Dyn: boolean <br/>ArkTS-Sta: boolean  \| undefined | 是   | “减少”按钮禁用或使能。<br/>默认值：true，true表示使能“减少”按钮，false表示禁用“减少”按钮。<br/>设置undefined时恢复默认值。 |

## 事件

除支持[通用事件](ts-component-general-events.md)外，还支持以下事件：

### onInc

ArkTS-Dyn: onInc(event:&nbsp;VoidCallback)

ArkTS-Sta: onInc(event:&nbsp;VoidCallback | undefined)

监听数值增加事件。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 23

**参数：** 

| 参数名 | 类型                                           | 必填 | 说明                                 |
| ------ | --------------------------------------------- | ---- | ----------------------------------- |
| event  | ArkTS-Dyn: [VoidCallback](ts-types.md#voidcallback12) <br/>ArkTS-Sta: [VoidCallback](ts-types.md#voidcallback12)  \| undefined    | 是   | Counter数值增加的回调函数。 |

### onDec

ArkTS-Dyn: onDec(event:&nbsp;VoidCallback)

ArkTS-Sta: onDec(event:&nbsp;VoidCallback | undefined)

监听数值减少事件。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                                           | 必填 | 说明                                 |
| ------ | --------------------------------------------- | ---- | ----------------------------------- |
| event  | ArkTS-Dyn: [VoidCallback](ts-types.md#voidcallback12) <br/>ArkTS-Sta: [VoidCallback](ts-types.md#voidcallback12)  \| undefined | 是   | Counter数值减少的回调函数。<br/>设置为undefined时不会执行回调。|


## 示例

该示例展示了Counter组件的基本使用方法。点击+、-按钮可以修改value值。

```ts
// xxx.ets
@Entry
@Component
struct CounterExample {
  @State value1: number = 0;
  @State value2: number = 0;

  build() {
    Column({ space: 50 }) {
      Counter() {
        Text(this.value1.toString())
      }
      .onInc(() => {
        this.value1++;
      })
      .onDec(() => {
        this.value1--;
      })

      Counter() {
        Text(this.value2.toString())
      }
      .onInc(() => {
        this.value2++;
      })
      .onDec(() => {
        this.value2--;
      })
      .enableInc(true)
      .enableDec(false)
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }
}
```

![zh-cn_image_0000001219982711](figures/zh-cn_image_0000001219982711.gif)
