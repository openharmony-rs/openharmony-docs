# 挂载卸载事件

挂载卸载事件指组件从组件树上挂载、卸载时触发的事件。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 从API version 7开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

## onAttach<sup>12+</sup>

ArkTS-Dyn: onAttach(callback: Callback\<void>): T

ArkTS-Sta: onAttach(callback: VoidCallback | undefined): this

组件挂载至组件树时触发此回调。

> **说明：**
>
> 回调在组件布局渲染之前调用。
>
> 不允许在回调中对组件树进行变更，例如启动动画或使用if-else变更组件树结构。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型  | 必填 | 说明                       |
| ------ | ------ | ---- | -------------------------- |
| callback  | ArkTS-Dyn: [Callback](./ts-types.md#callback12)\<void><br/>ArkTS-Sta: [VoidCallback](./ts-types.md#VoidCallback12) | 是   | onAttach事件的回调函数，表示组件已经挂载至组件树。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTs-Dyn: T<br/>ArkTs-Sta: this | 返回当前组件。 |

## onDetach<sup>12+</sup>

ArkTS-Dyn: onDetach(callback: Callback\<void>): T

ArkTS-Sta: onDetach(callback: VoidCallback | undefined): this

组件从组件树卸载时触发此回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型  | 必填 | 说明                       |
| ------ | ------ | ---- | -------------------------- |
| callback  | ArkTS-Dyn: [Callback](./ts-types.md#callback12)\<void><br/>ArkTS-Sta: [VoidCallback](./ts-types.md#voidcallback12) \| undefined| 是   | onDetach事件的回调函数，表示组件已经从组件树卸载。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTs-Dyn: T<br/>ArkTs-Sta: this | 返回当前组件。 |

## onAppear

ArkTS-Dyn: onAppear(event: () => void): T

ArkTS-Sta: onAppear(event: (() => void) | undefined): this

组件挂载显示后触发此回调。

> **说明：**
>
> 回调的调用时机有可能发生在组件布局渲染后。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型  | 必填 | 说明                       |
| ------ | ------ | ---- | -------------------------- |
| event  | ArkTS-Dyn: () => void  <br/>ArkTS-Sta: () => void | undefined| 是   | onAppear事件的回调函数，表示组件已挂载显示。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTs-Dyn: T<br/>ArkTs-Sta: this | 返回当前组件。 |


## onDisAppear

ArkTS-Dyn: onDisAppear(event: () => void): T

ArkTS-Sta: onDisAppear(event: (() => void) | undefined): this

组件卸载消失时触发此回调。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 22


**参数：**

| 参数名 | 类型  | 必填 | 说明                       |
| ------ | ------ | ---- | -------------------------- |
| event  | ArkTS-Dyn: () => void  <br/>ArkTS-Sta: () => void | undefined| 是   | onDisAppear事件的回调函数，表示组件已卸载消失。 |


**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTs-Dyn: T<br/>ArkTs-Sta: this | 返回当前组件。 |


## 示例

该示例通过按钮控制组件的挂载和卸载，触发onAttach和onDetach事件。

```ts
// xxx.ets
import { promptAction } from '@kit.ArkUI';

@Entry
@Component
struct AppearExample {
  @State isShow: boolean = true;
  @State changeAppear: string = '点我卸载挂载组件';
  private myText: string = 'Text for onAppear';

  build() {
    Column() {
      Button(this.changeAppear)
        .onClick(() => {
          this.isShow = !this.isShow
        }).margin(15)
      if (this.isShow) {
        Text(this.myText).fontSize(26).fontWeight(FontWeight.Bold)
          .onAttach(() => {
            this.getUIContext().getPromptAction().showToast({
              message: 'The text is shown',
              duration: 2000,
              bottom: 500
            })
          })
          .onDetach(() => {
            this.getUIContext().getPromptAction().showToast({
              message: 'The text is hidden',
              duration: 2000,
              bottom: 500
            })
          })
      }
    }.padding(30).width('100%')
  }
}
```

![zh-cn_image_0000001219864151](figures/zh-cn_image_0000001219864151.gif)
