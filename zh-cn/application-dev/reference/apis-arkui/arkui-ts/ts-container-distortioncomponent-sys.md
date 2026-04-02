# DistortionComponent (系统接口)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @CCFFWW-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

空间扭曲组件，提供空间扭曲感的形变视效能力。

>  **说明：**
>
> - 本模块为系统接口。
> 
> - 空间扭曲感的形变视效支持动画，如在[animateTo](../../apis-arkui/arkts-apis-uicontext-uicontext.md#animateto)动画接口闭包中改变该视效参数，可以产生空间扭曲感的形变动画。

**起始版本：** 26.0.0

## 子组件

可以包含单个子组件，需要通过[ComponentContent](../js-apis-arkui-ComponentContent.md)传入。

## 接口

### DistortionComponent

DistortionComponent(content: ComponentContent, options?: DistortionComponentOptions)

创建提供空间扭曲形变视效的组件。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型                                             | 必填 | 说明                                                         |
| ------- | ------------------------------------------------- | ---- | ------------------------------------------------------------ |
| content | [ComponentContent](../js-apis-arkui-ComponentContent.md#componentcontent-1)  | 是   | 内容构建函数。                                               |
| options | [DistortionComponentOptions](#distortioncomponentoptions)  | 否  | 空间扭曲形变选项。                                           |

## DistortionComponentOptions

空间扭曲形变选项。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称        | 类型                                              | 只读  | 可选 | 说明                                                         |
| ----------- | ------------------------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| distortion  | [DistortionParam](#distortionparam) | 否  | 是  | 空间扭曲形变参数。通过指定四个角的位置关系和四条边的桶形变程度产生空间扭曲效果。                                        |

## DistortionParam

空间扭曲形变参数。

> **说明：**
> - 四个角的坐标可以按照如下坐标系设置。一个组件，左上角位置为[0, 0]，右上角位置为[1, 0]，左下角位置为[0, 1]，右下角位置为[1, 1]。
> - 如bottomLeft属性设置为[0.5, 0.5]，则表示左下角形变到组件中心点的位置，产生对应的形变效果。
> - 设置四个角坐标位置时请符合空间感逻辑。如topLeft = [0.7, 0]，bottomLeft = [0.2, 0]，左上角的位置低于左下角的位置，违背空间感的逻辑，可能导致渲染异常。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称           | 类型    | 只读  | 可选 | 说明                                                                                                                                  |
| --------------- | --------- | ---- | ---- | ------------------------------------------------------------------------------------------------------------------------------------- |
| topLeft        | [Vector2](#vector2) | 否  | 否   | 左上角的坐标。<br/>默认值：[0, 0]                                                                                      |
| topRight       | [Vector2](#vector2) | 否  | 否   | 右上角的坐标。<br/>默认值：[1, 0]                                                                                     |
| bottomLeft     | [Vector2](#vector2) | 否  | 否   | 左下角的坐标。<br/>默认值：[0, 1]                                                                                     |
| bottomRight    | [Vector2](#vector2) | 否  | 否   | 右下角的坐标。<br/>默认值：[1, 1]                                                                                   |
| barrelDistortion | [Vector4](#vector4) | 否   | 否   | 四条边的桶形扭曲程度参数。<br/>Vector4中四个值分别控制：x是左边，y是右边，z是上边，w是下边。<br/>默认值：[0, 0, 0, 0] <br/>正数表示边向外凸出的扭曲，负数表示边向内凹陷的扭曲。扭曲参数绝对值达到1时，扭曲程度为极端扭曲。<br/> x、y、z、w 各值建议设置范围：[-1, 1]|


## Vector2

type Vector2 = Vector2

二维向量类型，包含x和y坐标，表示位置坐标关系。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型   | 说明     |
| ------ | -------- |
| [Vector2](../../apis-arkui/js-apis-arkui-graphics.md#vector2)   | 包含x和y两个值的向量。<br/>x和y表示坐标值。<br/>取值范围：(-∞, +∞) |


## Vector4

type Vector4 = Vector4

四维向量类型，包含x、y、z、w，各数值表示桶形形变程度。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型   | 说明     |
| ------ | -------- |
| [Vector4](../../apis-arkui/js-apis-arkui-graphics.md#vector4)   | 包含x、y、z、w四个值的向量。<br/>x、y、z、w的值分别表示组件左边、右边、上边、下边的桶形形变程度。<br/>取值范围：(-∞, +∞) |


## 属性

支持[通用属性](ts-component-general-attributes.md)，支持宽高设置（[width](ts-universal-attributes-size.md#width)、[height](ts-universal-attributes-size.md#height)），支持系统材质属性[systemMaterial](ts-universal-attributes-image-effect-sys.md#systemmaterial23)。

## 示例

### 示例1（动态改变扭曲形变视效）

该示例主要演示如何使用[DistortionComponent](#distortioncomponent)组件，通过改变distortion参数的空间扭曲形变值，产生不同的扭曲形变效果。

从API版本26.0.0开始，新增系统组件DistortionComponent。

```ts
// 示例：动态更新扭曲效果
import { FrameNode, ComponentContent } from '@kit.ArkUI';

class Params {
  text: string = '';

  constructor(text:string) {
    this.text = text;
  }
}

let contentNode: ComponentContent<Params>;

// 形变的前景内容（自定义组件）
@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
    Text('content2')
  }
}

@Entry
@Component
struct DistortionExample {
  @State distortionParam: DistortionParam = {
    topLeft: {x:0.8, y:0.8},
    topRight: {x:1, y:0.8},
    bottomLeft: {x:0.8, y:1},
    bottomRight: {x:1, y:1},
    barrelDistortion: {x:0, y:0, z:0, w:0},
  }

  aboutAppear() {
    contentNode = new ComponentContent(this.getUIContext(), wrapBuilder(buildText), new Params('Hello World'));
  }

  build() {
    Column() {
      DistortionComponent(contentNode, {
        distortion: this.distortionParam
      })
      .width(200)
      .height(200)
      .backgroundColor(Color.Pink)
      
      Button('Change Distortion')
        .onClick(() => {
          this.distortionParam = {
              topLeft: {x:0, y:0},
              topRight: {x:1, y:0},
              bottomLeft: {x:0.8, y:1},
              bottomRight: {x:1, y:1},
              barrelDistortion: {x:0, y:0, z:0, w:0},
          }
        })
    }
  }
}
```