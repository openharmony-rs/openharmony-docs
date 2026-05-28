# 视效设置
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

本模块提供接口设置组件视觉效果，包括滤镜效果（如：模糊，像素扩展等）和非滤镜效果（如：点光源等）。

>  **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块接口仅可在Stage模型下使用。
>
> - 从API version 12开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

## visualEffect

ArkTS-Dyn: visualEffect(effect: VisualEffect): T

ArkTS-Sta: visualEffect(effect: VisualEffect | undefined): this

设置非滤镜视觉效果。

>**说明：**
>
> 从API version 20开始，该接口支持在[attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier)中调用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                                                         | 必填 | 说明                                                 |
| ------ | ------------------------------------------------------------ | ---- | ---------------------------------------------------- |
| effect | ArkTS-Dyn: [VisualEffect](#visualeffect-1) <br/>  ArkTS-Sta: [VisualEffect](#visualeffect-1) \| undefined| 是   | 非滤镜视觉效果。<br/>当effect的值为undefined时，无非滤镜视觉效果。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn: T<br/>ArkTS-Sta: this | 返回当前组件。 |

## backgroundFilter

ArkTS-Dyn: backgroundFilter(filter: Filter): T

ArkTS-Sta: backgroundFilter(filter: Filter | undefined): this

设置背景滤镜视觉效果。

> **说明：**
>
> 从API version 20开始，该接口支持在[attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier)中调用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                                                         | 必填 | 说明                                                 |
| ------ | ------------------------------------------------------------ | ---- | ---------------------------------------------------- |
| filter | ArkTS-Dyn: [Filter](#filter)<br/>  ArkTS-Sta: [Filter](#filter) \| undefined| 是   | 背景滤镜视觉效果。<br/>当filter的值为undefined时，无背景滤镜视觉效果。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
|  ArkTS-Dyn: T<br/>ArkTS-Sta: this  | 返回当前组件。 |

## foregroundFilter

ArkTS-Dyn: foregroundFilter(filter: Filter): T

ArkTS-Sta: foregroundFilter(filter: Filter | undefined): this

设置前景滤镜（内容）视觉效果。

>**说明：**
>
> 从API version 20开始，该接口支持在[attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier)中调用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                                                         | 必填 | 说明                                                 |
| ------ | ------------------------------------------------------------ | ---- | ---------------------------------------------------- |
| filter | ArkTS-Dyn: [Filter](#filter)<br/>  ArkTS-Sta: [Filter](#filter) \| undefined | 是   | 前景滤镜（内容）视觉效果。<br/>当filter的值为undefined时，无前景滤镜（内容）视觉效果。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
|  ArkTS-Dyn: T<br/>ArkTS-Sta: this | 返回当前组件。 |

## compositingFilter

ArkTS-Dyn: compositingFilter(filter: Filter): T

ArkTS-Sta: compositingFilter(filter: Filter | undefined): this

设置合成滤镜视觉效果。

>**说明：**
>
> 从API version 20开始，该接口支持在[attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier)中调用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                                                         | 必填 | 说明                                                 |
| ------ | ------------------------------------------------------------ | ---- | ---------------------------------------------------- |
| filter | ArkTS-Dyn: [Filter](#filter)<br/>  ArkTS-Sta: [Filter](#filter) \| undefined | 是   | 合成滤镜视觉效果。<br/>当filter的值为undefined时，无合成滤镜视觉效果。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
|  ArkTS-Dyn: T<br/>ArkTS-Sta: this  | 返回当前组件。 |

## materialFilter<sup>23+</sup>

ArkTS-Dyn: materialFilter(filter: Filter | undefined): T

ArkTS-Sta: materialFilter(filter: Filter | undefined): this

设置系统材质滤镜效果，系统材质滤镜的绘制早于[backgroundFilter](#backgroundfilter)绘制，即位于backgroundFilter的更底层。

>**说明：**
>
> 该接口支持在[attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier)中调用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                                                         | 必填 | 说明                                                 |
| ------ | ------------------------------------------------------------ | ---- | ---------------------------------------------------- |
| filter | [Filter](#filter) &nbsp;\|&nbsp; undefined | 是   | 系统材质滤镜视觉效果。设置为undefined时恢复为无系统材质滤镜效果。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
|  ArkTS-Dyn: T<br/>ArkTS-Sta: this  | 返回当前组件。 |

## Filter

ArkTS-Dyn: type Filter = Filter

ArkTS-Sta: type Filter = uiEffect.Filter

导入Filter类型对象。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

| 类型   | 说明                     |
| ------ | ------------------------ |
| ArkTS-Dyn: [Filter](../../apis-arkgraphics2d/js-apis-uiEffect.md#filter)<br/>ArkTS-Sta: uiEffect.Filter | 用于将相应的效果添加到指定的组件上。 |

## VisualEffect

ArkTS-Dyn: type VisualEffect = VisualEffect

ArkTS-Sta: type VisualEffect = uiEffect.VisualEffect

导入VisualEffect类型对象。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

| 类型   | 说明                     |
| ------ | ------------------------ |
| ArkTS-Dyn: [VisualEffect](../../apis-arkgraphics2d/js-apis-uiEffect.md#visualeffect)<br/>ArkTS-Sta: uiEffect.[VisualEffect](../../apis-arkgraphics2d/js-apis-uiEffect.md#visualeffect) | 用于将相应的效果添加到指定的组件上。 |

## 示例

该示例主要演示前景滤镜、背景滤镜和合成滤镜的模糊效果。

```ts
// xxx.ets
import { uiEffect } from '@kit.ArkGraphics2D';

@Entry
@Component
struct FilterEffectExample {
  @State filterTest1: uiEffect.Filter = uiEffect.createFilter().blur(10);
  @State filterTest2: uiEffect.Filter = uiEffect.createFilter().blur(10);
  @State filterTest3: uiEffect.Filter = uiEffect.createFilter().blur(10);

  build() {
    Column({ space: 15 }) {

      Text('foregroundFilter').fontSize(20).width('75%').fontColor('#DCDCDC')
      Text('前景滤镜')
        .width(100)
        .height(100)
        .backgroundColor('#ADD8E6')
        // $r("app.media.app_icon")需替换为开发者所需的资源文件
        .backgroundImage($r("app.media.app_icon"))
        .backgroundImageSize({ width: 80, height: 80 })
        .foregroundFilter(this.filterTest1) // 通过 foregroundFilter 设置模糊效果

      Text('backgroundFilter').fontSize(20).width('75%').fontColor('#DCDCDC')
      Text('背景滤镜')
        .width(100)
        .height(100)
        .backgroundColor('#ADD8E6')
        // $r("app.media.app_icon")需替换为开发者所需的资源文件
        .backgroundImage($r("app.media.app_icon"))
        .backgroundImageSize({ width: 80, height: 80 })
        .backgroundFilter(this.filterTest2) // 通过 backgroundFilter 设置模糊效果

      Text('compositingFilter').fontSize(20).width('75%').fontColor('#DCDCDC')
      Text('合成滤镜')
        .width(100)
        .height(100)
        .backgroundColor('#ADD8E6')
        // $r("app.media.app_icon")需替换为开发者所需的资源文件
        .backgroundImage($r("app.media.app_icon"))
        .backgroundImageSize({ width: 80, height: 80 })
        .compositingFilter(this.filterTest3) // 通过 compositingFilter 设置模糊效果
    }
    .height('100%')
    .width('100%')
  }
}
```

![filterEffect](figures/filterEffectWithText.jpg)