# @ohos.graphics.uiEffect (效果级联)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hanamaru-->
<!--Designer: @chensiyi_CE-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->

本模块提供组件效果的基础能力，包括模糊、提亮等。效果被分为Filter和VisualEffect大类，同类效果可以级联在一个效果大类的实例下。在实际开发中，模糊可用于背景虚化等场景，提亮可用于亮屏显示等场景。使用本模块可以提升应用的视觉效果，增强用户体验。

- [Filter](#filter)：用于添加指定Filter效果到组件上，支持模糊、HDR提亮等视觉效果。
- [VisualEffect](#visualeffect)：用于添加指定VisualEffect效果到组件上。

**Filter与VisualEffect的选择：** 两者分别属于不同的效果大类，支持的视觉效果类型不同，根据实际需求的效果类型选择对应的效果类。

> **说明：**
>
> 本模块首批接口从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 本模块的接口均依赖画布上已有的内容进行绘制，如果与具有离屏功能的接口（如[blendMode<sup>11+</sup>](../apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#blendmode11)的离屏模式）联合使用，可能会产生非预期效果。

## 导入模块

```ts
import { uiEffect } from '@kit.ArkGraphics2D';
```

## uiEffect.createFilter
createFilter(): Filter

创建Filter实例用于给组件添加多种filter效果。

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型              | 说明                 |
| ------------------| ------------------- |
| [Filter](#filter) | 返回Filter实例，支持添加多种filter效果。 |

**示例：**

```ts
// 创建Filter实例
let filter : uiEffect.Filter = uiEffect.createFilter();
```

## uiEffect.createEffect
createEffect(): VisualEffect

创建VisualEffect实例用于给组件添加多种effect效果。

**卡片能力：** 从API version 24开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型                          | 说明                       |
| ----------------------------- | ------------------------- |
| [VisualEffect](#visualeffect) | 返回VisualEffect实例，支持添加多种effect效果。 |

**示例：**

```ts
// 创建VisualEffect实例
let visualEffect : uiEffect.VisualEffect = uiEffect.createEffect();
```

## Filter
Filter效果类，用于将相应的效果添加到指定的组件上。在调用Filter的方法前，需要先通过[createFilter](#uieffectcreatefilter)创建一个Filter实例。

### blur
blur(blurRadius: number): Filter

将模糊效果添加至组件上。

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**
| 参数名       | 类型   | 必填 | 说明       |
| ----------- | -------| ---- | --------- |
| blurRadius  | number | 是   | 模糊半径，单位为px。<br>取值需大于等于0，模糊半径越大，模糊效果越强。<br>模糊半径为0时无模糊效果。<br>传入负数时自动修正为0。 |

**返回值：**

| 类型               | 说明                       |
| ----------------- | -------------------------- |
| [Filter](#filter) | 返回挂载了模糊效果的Filter，支持链式调用继续添加其他效果。 |

**示例：**

```ts
// xxx.ts
import { uiEffect } from '@kit.ArkGraphics2D';

// 创建Filter实例
let filter: uiEffect.Filter = uiEffect.createFilter();
// 设置模糊半径为10px
filter.blur(10);

@Entry
@Component
struct UIEffectFilterExample {
    build() {
        Column({ space: 15 }) {
            Text('UIEffectFilter').fontSize(20).width('75%').fontColor('#DCDCDC')
            Image($r('app.media.foreground'))
                .width(100)
                .height(100)
                .backgroundImage($r('app.media.background'))
                .backgroundImagePosition(Alignment.Center)
                .backgroundImageSize({ width: 90, height: 90 })
                // 将Filter效果应用到组件背景
                .backgroundFilter(filter)
        }
        .height('100%')
        .width('100%')
    }
}
```
![UIEffect-blur.png](figures/UIEffect-blur.png)

### hdrBrightnessRatio<sup>24+</sup>
hdrBrightnessRatio(ratio: number): Filter

为组件内容添加HDR（高动态范围成像）提亮效果。不建议嵌套使用，强行嵌套使用可能造成过曝现象。

提亮效果需要开启HDR渲染管线才能生效，某些场景下即使尝试触发HDR渲染管线也无法开启HDR，例如：设备硬件规格不支持HDR。

设备当前支持最大提亮倍数为设备当前的最大亮度除以设备SDR参考白亮度得到的值。

>  **说明：**
>
> 使用HDR提亮效果会带来一定的性能功耗开销，建议在已有HDR图片或视频的场景使用。

**需要权限：** ohos.permission.HDR_BRIGHTNESS
<!--Del-->系统应用无需申请此权限。<!--DelEnd-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**
| 参数名         | 类型                  | 必填 | 说明                       |
| ------------- | --------------------- | ---- | ------------------------- |
| ratio  | number         | 是   | 提亮倍数，取值范围为[1.0, 设备当前支持的最大提亮倍数]。小于1.0按1.0处理；等于1.0不做处理；大于1.0尝试触发HDR渲染管线；超过最大倍数按最大倍数处理。 |

**返回值：**

| 类型              | 说明                               |
| ----------------- | --------------------------------- |
| [Filter](#filter) | 返回挂载了HDR提亮效果的Filter，支持链式调用继续添加其他效果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 201 | Permission verification failed. The application does not have the permission required to call the API. |

**示例：**

```ts
// 创建Filter实例
let filter: uiEffect.Filter = uiEffect.createFilter();
// 设置HDR提亮倍数为2.0
filter.hdrBrightnessRatio(2.0);
```

## VisualEffect
VisualEffect效果类，用于将相应的效果添加到指定的组件上。在调用VisualEffect的方法前，需要先通过[createEffect](#uieffectcreateeffect)创建一个VisualEffect实例。