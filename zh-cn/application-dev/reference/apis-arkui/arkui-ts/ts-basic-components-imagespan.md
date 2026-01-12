# ImageSpan

[Text](ts-basic-components-text.md)、[ContainerSpan](ts-basic-components-containerspan.md)组件的子组件，用于显示行内图片。

>  **说明：**
>
>  - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
>  - 该组件从API version 10开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。


## 子组件

无


## 接口

ImageSpan(value: ResourceStr | PixelMap)

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | [ResourceStr](ts-types.md#resourcestr) \|&nbsp;[PixelMap](../../apis-image-kit/arkts-apis-image-PixelMap.md)&nbsp; | 是 | 图片的数据源，支持本地图片和网络图片。<br/>当使用相对路径引用图片资源时，例如`ImageSpan("common/test.jpg")`，不支持跨包/跨模块调用该ImageSpan组件，建议使用`$r`方式来管理需全局使用的图片资源。<br/>\- 支持的图片格式包括png、jpg、bmp、svg、gif和heif。<br/>\- 支持`Base64`字符串。格式`data:image/[png\|jpeg\|bmp\|webp\|heif];base64,[base64 data]`，其中`[base64 data]`为`Base64`字符串数据。<br/>\- 支持file://data/storage路径前缀的字符串，用于读取本应用安装目录下file文件夹下的图片资源。需要保证目录包路径下的文件有可读权限。 |


## 属性

属性继承自[BaseSpan](ts-basic-components-span.md#basespan)，通用属性方法支持[尺寸设置](ts-universal-attributes-size.md)、[背景设置](ts-universal-attributes-background.md#背景设置)、[边框设置](ts-universal-attributes-border.md#边框设置)。

### verticalAlign

ArkTS-Dyn: verticalAlign(value: ImageSpanAlignment)

ArkTS-Sta: verticalAlign(value: ImageSpanAlignment | undefined)

设置图片基于行高的对齐方式。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 22

**参数：** 

| 参数名 | 类型                                      | 必填 | 说明                                                         |
| ------ | ----------------------------------------- | ---- | ------------------------------------------------------------ |
| value  | ArkTS-Dyn: [ImageSpanAlignment](ts-appendix-enums.md#imagespanalignment10)<br/>ArkTS-Sta: [ImageSpanAlignment](ts-appendix-enums.md#imagespanalignment10) \| undefined | 是   | 图片基于行高的对齐方式。<br />默认值：ImageSpanAlignment.BOTTOM |

### objectFit

ArkTS-Dyn: objectFit(value: ImageFit)

ArkTS-Sta: objectFit(value: ImageFit | undefined)

设置图片的缩放类型。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 22

**参数：** 

| 参数名 | 类型                                      | 必填 | 说明                                        |
| ------ | ----------------------------------------- | ---- | ------------------------------------------- |
| value  | ArkTS-Dyn: [ImageFit](ts-appendix-enums.md#imagefit)<br/>ArkTS-Sta: [ImageFit](ts-appendix-enums.md#imagefit) \| undefined | 是   | 图片的缩放类型。<br/>默认值：ImageFit.Cover |

### alt<sup>12+</sup>

ArkTS-Dyn: alt(value:&nbsp;PixelMap)

ArkTS-Sta: alt(value:&nbsp;PixelMap | undefined)

设置图片加载时显示的占位图。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 22

**参数：** 

| 参数名 | 类型                                                     | 必填 | 说明                                                         |
| ------ | -------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| value  | ArkTS-Dyn: [PixelMap](../../apis-image-kit/arkts-apis-image-PixelMap.md)<br/>ArkTS-Sta: [PixelMap](../../apis-image-kit/arkts-apis-image-PixelMap.md) \| undefined | 是   | 加载时显示的占位图，支持[PixelMap](../../apis-image-kit/arkts-apis-image-PixelMap.md)类型。<br/>默认值：null<br/>由有效值（可正常解析并加载的图片资源）切换为无效值（无法解析或加载的图片路径）时，组件保持显示此前成功加载的图片内容，不进行清除或重置操作。 |

### colorFilter<sup>14+</sup>

ArkTS-Dyn: colorFilter(filter: ColorFilter | DrawingColorFilter)

ArkTS-Sta: colorFilter(filter: ColorFilter | DrawingColorFilter | undefined)

为图像设置颜色滤镜效果。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 14

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型                                    | 必填 | 说明                                                         |
| ------ | --------------------------------------- | ---- | ------------------------------------------------------------ |
| filter  | ArkTS-Dyn: [ColorFilter](ts-types.md#colorfilter9) \| [DrawingColorFilter](ts-basic-components-image.md#drawingcolorfilter12)<br/>ArkTS-Sta: [ColorFilter](ts-types.md#colorfilter9) \| [DrawingColorFilter](ts-basic-components-image.md#drawingcolorfilter12) \| undefined | 是   | 1. 给图像设置颜色滤镜效果，入参为一个的4x5的RGBA转换矩阵。<br/>矩阵第一行表示R（红色）的向量值，第二行表示G（绿色）的向量值，第三行表示B（蓝色）的向量值，第四行表示A（透明度）的向量值，4行分别代表不同的RGBA的向量值。<br/>当矩阵对角线值为1，其余值为0时，保持图片原有色彩。<br/> **计算规则：**<br/>如果输入的滤镜矩阵为：<br/>![image-matrix-1](figures/image_matrix_1.png)<br/>像素点为[R, G, B, A]，色值的范围[0, 255]<br/>则过滤后的颜色为 [R’, G’, B’, A’]<br/>![image-matrix-2](figures/image_matrix_2.png)<br/>2. 支持@ohos.graphics.drawing的ColorFilter类型作为入参。<br/>**说明：** <br/>该接口中的DrawingColorfilter类型支持在原子化服务中使用。其中，svg类型的图源只对stroke属性生效。|

### supportSvg2<sup>22+</sup>

ArkTS-Dyn: supportSvg2(enable: Optional\<boolean>)

ArkTS-Sta: supportSvg2(enable: boolean | undefined)

开启或关闭[SVG标签解析能力增强功能](ts-image-svg2-capabilities.md)，开启后相关SVG图片显示效果会有变化。未通过该接口设置时，默认保持原有SVG解析能力。

ImageSpan组件创建后，不支持动态修改该属性的值。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 23

**参数：** 

| 参数名 | 类型                                                     | 必填 | 说明                                                         |
| ------ | -------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| enable  | ArkTS-Dyn: [Optional](ts-universal-attributes-custom-property.md#optional12)\<boolean><br/>ArkTS-Sta: boolean \| undefined | 是   | 控制是否开启[SVG标签解析能力增强功能](ts-image-svg2-capabilities.md)。<br>true：支持SVG解析新能力；false：保持原有SVG解析能力。<br>值为undefined时，保持原有SVG解析能力。|

## 事件

通用事件仅支持[点击事件](ts-universal-attributes-click.md)。还支持以下事件：

### onComplete<sup>12+</sup>

ArkTS-Dyn: onComplete(callback: ImageCompleteCallback)

ArkTS-Sta: onComplete(callback: ImageCompleteCallback | undefined)

图片数据加载成功和解码成功时均触发该回调，返回成功加载的图片尺寸。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                                       | 必填 | 说明                       |
| -------- | ------------------------------------------ | ---- | -------------------------- |
| callback | ArkTS-Dyn: [ImageCompleteCallback](#imagecompletecallback12)<br/>ArkTS-Sta: [ImageCompleteCallback](#imagecompletecallback12) \| undefined | 是   | 图片数据加载成功和解码成功时触发的回调。 |

### onError<sup>12+</sup>

ArkTS-Dyn: onError(callback: ImageErrorCallback)

ArkTS-Sta: onError(callback: ImageErrorCallback | undefined)

图片加载异常时触发该回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                                       | 必填 | 说明                       |
| -------- | ------------------------------------------ | ---- | -------------------------- |
| callback | ArkTS-Dyn: [ImageErrorCallback](ts-basic-components-image.md#imageerrorcallback9)<br/>ArkTS-Sta: [ImageErrorCallback](ts-basic-components-image.md#imageerrorcallback9) \| undefined | 是   | 图片加载异常时触发的回调。 |

## ImageCompleteCallback<sup>12+</sup>

type ImageCompleteCallback = (result: ImageLoadResult) => void

图片加载成功和解码成功时触发的回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 参数名 | 类型                       | 必填 | 说明                               |
| ------ | -------------------------- | ---- | ---------------------------------- |
| result  | [ImageLoadResult](#imageloadresult12对象说明) | 是   | 图片数据加载成功和解码成功触发回调时返回的对象。 |

## ImageLoadResult<sup>12+</sup>对象说明

图片数据加载成功和解码成功触发回调时返回的对象。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称                       | 类型   | 必填 | 说明                                                         |
| ---------------------------- | ------ | ---- | ------------------------------------------------------------ |
| width                        | number | 是   | 图片的宽。<br/>单位：[px](ts-pixel-units.md)                                    |
| height                       | number | 是   | 图片的高。<br/>单位：[px](ts-pixel-units.md)                                    |
| componentWidth               | number | 是   | 组件的宽。<br/>单位：[px](ts-pixel-units.md)                                    |
| componentHeight              | number | 是   | 组件的高。<br/>单位：[px](ts-pixel-units.md)                                    |
| loadingStatus                | number | 是   | 图片加载成功的状态值。<br/>**说明：**<br/>返回的状态值为0时，表示图片数据加载成功。返回的状态值为1时，表示图片解码成功。 |
| contentWidth   | number | 是   | 图片实际绘制的宽度。<br/>单位：[px](ts-pixel-units.md)<br>**说明：**<br/>仅在loadingStatus返回1时有效。 |
| contentHeight  | number | 是   | 图片实际绘制的高度。<br/>单位：[px](ts-pixel-units.md)<br/>**说明：**<br/>仅在loadingStatus返回1时有效。 |
| contentOffsetX | number | 是   | 实际绘制内容相对于组件自身的x轴偏移。<br/>单位：[px](ts-pixel-units.md)<br/>**说明：**<br/>仅在loadingStatus返回1时有效。 |
| contentOffsetY | number | 是   | 实际绘制内容相对于组件自身的y轴偏移。<br/>单位：[px](ts-pixel-units.md)<br/>**说明：**<br/>仅在loadingStatus返回1时有效。 |



## 示例

### 示例1（设置对齐方式）

该示例通过verticalAlign、objectFit属性展示了ImageSpan的对齐方式以及缩放效果。

```ts
// xxx.ets
@Entry
@Component
struct SpanExample {
  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Text() {
        Span('This is the Span and ImageSpan component').fontSize(25).textCase(TextCase.Normal)
          .decoration({ type: TextDecorationType.None, color: Color.Pink })
      }.width('100%').textAlign(TextAlign.Center)

      Text() {
        ImageSpan($r('app.media.app_icon'))
          .width('200px')
          .height('200px')
          .objectFit(ImageFit.Fill)
          .verticalAlign(ImageSpanAlignment.CENTER)
        Span('I am LineThrough-span')
          .decoration({ type: TextDecorationType.LineThrough, color: Color.Red }).fontSize(25)
        ImageSpan($r('app.media.app_icon'))
          .width('50px')
          .height('50px')
          .verticalAlign(ImageSpanAlignment.TOP)
        Span('I am Underline-span')
          .decoration({ type: TextDecorationType.Underline, color: Color.Red }).fontSize(25)
        ImageSpan($r('app.media.app_icon'))
          .size({ width: '100px', height: '100px' })
          .verticalAlign(ImageSpanAlignment.BASELINE)
        Span('I am Underline-span')
          .decoration({ type: TextDecorationType.Underline, color: Color.Red }).fontSize(25)
        ImageSpan($r('app.media.app_icon'))
          .width('70px')
          .height('70px')
          .verticalAlign(ImageSpanAlignment.BOTTOM)
        Span('I am Underline-span')
          .decoration({ type: TextDecorationType.Underline, color: Color.Red }).fontSize(50)
      }
      .width('100%')
      .textIndent(50)
    }.width('100%').height('100%').padding({ left: 0, right: 0, top: 0 })
  }
}
```

![imagespan](figures/imagespan.png)

### 示例2（设置背景样式）

该示例通过textBackgroundStyle属性展示了文本设置背景样式的效果。

```ts
// xxx.ets
@Component
@Entry
struct Index {
  build() {
    Row() {
      Column() {
        Text() {
          ImageSpan($r('app.media.sky'))//建议使用自定义的本地图片
            .width('60vp')
            .height('60vp')
            .verticalAlign(ImageSpanAlignment.CENTER)
            .borderRadius(20)
            .textBackgroundStyle({ color: '#7F007DFF', radius: "5vp" })
        }
      }.width('100%')
    }.height('100%')
  }
}
```
![imagespan](figures/image_span_textbackgroundstyle.png)

### 示例3（为图片添加事件）

该示例通过onComplete、onError为图片添加加载成功和加载异常的事件。

```ts
// xxx.ets
@Entry
@Component
struct Index {
  @State src: ResourceStr = $r('app.media.app_icon');

  build() {
    Column() {
      Text() {
        ImageSpan(this.src)
          .width(100).height(100)
          .onError((err) => {
            console.log("onError: " + err.message);
          })
          .onComplete((event) => {
            console.log("onComplete: " + event.loadingStatus);
          })
      }
    }.width('100%').height('100%')
  }
}
```
### 示例4（设置颜色滤镜）

该示例通过colorFilter属性展示了给ImageSpan图像设置颜色滤镜的效果。

```ts
// xxx.ets
import { drawing } from '@kit.ArkGraphics2D';

@Entry
@Component
struct SpanExample {
  private ColorFilterMatrix: number[] = [0.239, 0, 0, 0, 0, 0, 0.616, 0, 0, 0, 0, 0, 0.706, 0, 0, 0, 0, 0, 1, 0];
  @State DrawingColorFilterFirst: ColorFilter | undefined = new ColorFilter(this.ColorFilterMatrix);

  build() {
    Row() {
      Column({ space: 10 }) {
        //创建ColorFilter对象的方式为图片设置颜色滤镜
        Text() {
          ImageSpan($r('app.media.sky'))//建议使用自定义的本地图片
            .width('60vp')
            .height('60vp')
            .colorFilter(this.DrawingColorFilterFirst)
        }

        //通过drawing.ColorFilter的方式为图片设置颜色滤镜
        Text() {
          ImageSpan($r('app.media.sky'))//建议使用自定义的本地图片
            .width('60vp')
            .height('60vp')
            .colorFilter(drawing.ColorFilter.createBlendModeColorFilter({
              alpha: 255,
              red: 112,
              green: 112,
              blue: 112
            }, drawing.BlendMode.SRC))
        }
      }.width('100%')
    }.height('100%')
  }
}
```
![imagespan](figures/image_span_colorfilter.png)

### 示例5（设置加载占位图）

该示例alt属性展示了ImageSpan设置加载网络图片时占位图的效果。

```ts
// xxx.ets
import { http } from '@kit.NetworkKit';
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct SpanExample {
  @State imageAlt: PixelMap | undefined = undefined;

  httpRequest() {
    // 直接加载网络地址，请填写一个具体的网络图片地址
    http.createHttp().request("https://www.example.com/xxx.png", (error: BusinessError, data: http.HttpResponse) => {
      if (error) {
        console.error(`http request failed with. Code: ${error.code}, message: ${error.message}`);
      } else {
        console.log(`http request success.`);
        let imageData: ArrayBuffer = data.result as ArrayBuffer;
        let imageSource: image.ImageSource = image.createImageSource(imageData);

        class tmp {
          height: number = 100;
          width: number = 100;
        }

        let option: Record<string, number | boolean | tmp> = {
          'alphaType': 0, // 透明度
          'editable': false, // 是否可编辑
          'pixelFormat': 3, // 像素格式
          'scaleMode': 1, // 缩略值
          'size': { height: 100, width: 100 }
        };
        //创建图片大小
        imageSource.createPixelMap(option).then((pixelMap: PixelMap) => {
          this.imageAlt = pixelMap;
        })
      }
    })
  }

  build() {
    Column() {
      Button("获取网络图片")
        .onClick(() => {
          this.httpRequest();
        })

      Text() {
        // 直接加载网络地址，请填写一个具体的网络图片地址
        ImageSpan('https://www.example.com/xxx.png')
          .alt(this.imageAlt)
          .width(300)
          .height(300)
      }

    }.width('100%').height(250).padding({ left: 35, right: 35, top: 35 })
  }
}
```

![imagespan](figures/image_span_alt.gif)

### 示例6（开启或关闭SVG标签解析能力增强功能）

该示例通过设置[supportSvg2](#supportsvg222)接口，使[SVG标签解析能力增强功能](ts-image-svg2-capabilities.md#svg易用性提升)的SVG易用性提升能力生效，从而提升SVG的易用性。

从API version 22开始，新增[supportSvg2](#supportsvg222)接口。

ArkTS-Dyn示例：

```ts
import { drawing } from '@kit.ArkGraphics2D';
@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Text('属性字符串不支持SVG2')
        // $r("app.media.ice")需要替换为开发者所需的图像资源文件。
        Text() {
          ImageSpan($r("app.media.ice"))
            .width(50)
            .height(50)
            .colorFilter(drawing.ColorFilter.createBlendModeColorFilter(
              drawing.Tool.makeColorFromResourceColor(Color.Blue), drawing.BlendMode.SRC_IN))
        }
        Text('属性字符串支持SVG2')
        // $r("app.media.ice")需要替换为开发者所需的图像资源文件。
        Text() {
          ImageSpan($r("app.media.ice"))
            .width(50)
            .height(50)
            .supportSvg2(true)
            .colorFilter(drawing.ColorFilter.createBlendModeColorFilter(
              drawing.Tool.makeColorFromResourceColor(Color.Blue), drawing.BlendMode.SRC_IN))
        }
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

ArkTS-Sta示例:

```ts
import { Entry, Column, Row, Component, Text, Button, ImageSpan, $r, Color } from '@kit.ArkUI';
import { drawing, common2D } from '@kit.ArkGraphics2D';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Text('属性字符串不支持SVG2')
        // $r("app.media.ice")需要替换为开发者所需的图像资源文件。
        Text() {
          ImageSpan($r("app.media.ice"))
            .width(50)
            .height(50)
            .colorFilter(drawing.ColorFilter.createBlendModeColorFilter(
              drawing.Tool.makeColorFromResourceColor(Color.Blue) as common2D.Color, drawing.BlendMode.SRC_IN))
        }
        Text('属性字符串支持SVG2')
        // $r("app.media.ice")需要替换为开发者所需的图像资源文件。
        Text() {
          ImageSpan($r("app.media.ice"))
            .width(50)
            .height(50)
            .supportSvg2(true)
            .colorFilter(drawing.ColorFilter.createBlendModeColorFilter(
              drawing.Tool.makeColorFromResourceColor(Color.Blue) as common2D.Color, drawing.BlendMode.SRC_IN))
        }
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

![styledString_17](figures/styledString_17.png)

