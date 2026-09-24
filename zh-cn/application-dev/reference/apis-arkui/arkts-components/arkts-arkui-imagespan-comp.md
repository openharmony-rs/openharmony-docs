# ImageSpan

ImageSpan是[Text](arkts-arkui-text-comp.md#text)、[ContainerSpan](arkts-arkui-containerspan-comp-attribute.md)组件的子组件，用于在文本中显示行内图片，支持设置图片对齐方式、缩放类型、加载占位图和颜色滤镜等，适用于需要在文本段落中嵌入图片实现图文混排的场景。

> **说明：** 
> 
> - 该组件从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 子组件

无

## ImageSpan

```TypeScript
ImageSpan(value: ResourceStr | PixelMap)
```

定义ImageSpan组件构造函数。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**测试接口：** 此接口仅在自动化测试脚本中使用。

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [PixelMap](arkts-arkui-common-comp-pixelmap-t.md) | 是 | 图片的数据源，支持本地图片和网络图片。<br>使用网络图片时，需要申请权限ohos.permission.INTERNET。具体申请方式请参考[声明权限](../../../security/AccessToken/declare-permissions.md)。<br>当使用相对路径引用图片资源时，例如`ImageSpan("common/test.jpg")`，不支持跨包/跨模块调用该ImageSpan组件，建议使用`$r`方式来管理需全局使用的图片资源。<br>- 支持的图片格式包括png、jpg、bmp、svg、gif、webp和heif。<br>- 支持`Base64`字符串。格式`data:image/[png&#124;jpeg&#124;bmp&#124;webp&#124;heif];base64,[base64 data]`，其中`[base64 data]`为`Base64`字符串数据。<br>- 支持file://data/storage路径前缀的字符串，用于读取本应用安装目录下file文件夹下的图片资源。需要保证应用安装目录路径下的文件有可读权限。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [ImageLoadResult](arkts-arkui-imagespan-comp-imageloadresult-i.md) | 图片数据加载成功和解码成功触发回调时返回的对象。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ImageCompleteCallback](arkts-arkui-imagespan-comp-imagecompletecallback-t.md) | 图片加载成功和解码成功时均触发的回调。 |

## 示例

### 示例1（设置对齐方式）

从API version 10开始，该示例通过[verticalAlign](#verticalalign)、[objectFit](#objectfit)属性展示了ImageSpan组件的对齐方式以及缩放效果。



```TypeScript
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
        // $r('app.media.app_icon')需要替换为实际的图像资源文件。
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

### 示例2（设置背景样式）

从API version 11开始，该示例通过[textBackgroundStyle](ts-basic-components-span.md#textbackgroundstyle11)属性展示了文本设置背景样式的效果。



```TypeScript
// xxx.ets
@Component
@Entry
struct Index {
  build() {
    Row() {
      Column() {
        Text() {
          // $r('app.media.sky')需要替换为实际的图像资源文件。
          ImageSpan($r('app.media.sky'))
            .width('60vp')
            .height('60vp')
            .verticalAlign(ImageSpanAlignment.CENTER)
            .borderRadius(20)
            .textBackgroundStyle({ color: '#7F007DFF', radius: '5vp' })
        }
      }.width('100%')
    }.height('100%')
  }
}
```

### 示例3（为图片添加事件）

从API version 12开始，该示例通过[onComplete](#oncomplete12)、[onError](#onerror12)为图片添加加载成功和加载异常的事件。

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  // $r('app.media.app_icon')需要替换为实际的图像资源文件。
  @State src: ResourceStr = $r('app.media.app_icon');

  build() {
    Column() {
      Text() {
        ImageSpan(this.src)
          .width(100).height(100)
          .onError((err) => {
            console.error(`Failed to load image. Code: ${err.error?.code}, message: ${err.message}`);
          })
          .onComplete((event) => {
            console.info('onComplete: ' + event.loadingStatus);
          })
      }
    }.width('100%').height('100%')
  }
}
```

### 示例4（设置颜色滤镜）

从API version 14开始，该示例通过[colorFilter](#colorfilter14)属性展示了给ImageSpan图像设置颜色滤镜的效果。



```TypeScript
// xxx.ets
import { drawing } from '@kit.ArkGraphics2D';

@Entry
@Component
struct SpanExample {
  private colorFilterMatrix: number[] = [0.239, 0, 0, 0, 0, 0, 0.616, 0, 0, 0, 0, 0, 0.706, 0, 0, 0, 0, 0, 1, 0];
  @State drawingColorFilterFirst: ColorFilter | undefined = new ColorFilter(this.colorFilterMatrix);

  build() {
    Row() {
      Column({ space: 10 }) {
        // 创建ColorFilter对象的方式为图片设置颜色滤镜。
        Text() {
          // $r('app.media.sky')需要替换为实际的图像资源文件。
          ImageSpan($r('app.media.sky'))
            .width('60vp')
            .height('60vp')
            .colorFilter(this.drawingColorFilterFirst)
        }

        // 通过drawing.ColorFilter的方式为图片设置颜色滤镜。
        Text() {
          // $r('app.media.sky')需要替换为实际的图像资源文件。
          ImageSpan($r('app.media.sky'))
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

### 示例5（设置加载占位图）

从API version 12开始，该示例通过[alt](#alt12)属性展示了ImageSpan设置加载网络图片时占位图的效果。

使用网络图片时，需要申请权限ohos.permission.INTERNET。具体申请方式请参考[声明权限](../../../security/AccessToken/declare-permissions.md)。



```TypeScript
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
    http.createHttp().request('https://www.example.com/xxx.png', (error: BusinessError, data: http.HttpResponse) => {
      if (error) {
        console.error(`http request failed with. Code: ${error.code}, message: ${error.message}`);
      } else {
        console.info('http request success');
        let imageData: ArrayBuffer = data.result as ArrayBuffer;
        let imageSource: image.ImageSource = image.createImageSource(imageData);

        class ImageSize {
          height: number = 100;
          width: number = 100;
        }

        let option: Record<string, number | boolean | ImageSize> = {
          'alphaType': 0, // 透明度
          'editable': false, // 是否可编辑
          'pixelFormat': 3, // 像素格式
          'scaleMode': 1, // 缩略值
          'size': { height: 100, width: 100 }
        };
        // 通过ImageSource创建PixelMap
        imageSource.createPixelMap(option).then((pixelMap: PixelMap) => {
          console.info('image createPixelMap success');
          this.imageAlt = pixelMap;
          imageSource.release();
        }).catch(() => {
          imageSource.release();
        })
      }
    })
  }

  build() {
    Column() {
      Button('获取网络图片')
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

### 示例6（使用supportSvg2属性时，SVG图片的显示效果）

从API version 22开始，该示例通过设置[supportSvg2](#supportsvg222)属性，使[SVG标签解析能力增强功能](ts-image-svg2-capabilities.md)的[SVG易用性提升](ts-image-svg2-capabilities.md#svg易用性提升)能力生效。



```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Text('属性字符串不支持svg2')
        // $r('app.media.ice')需要替换为实际的图像资源文件。
        Text() {
          ImageSpan($r('app.media.ice'))
            .width(50)
            .height(50)
            .colorFilter(drawing.ColorFilter.createBlendModeColorFilter(
              drawing.Tool.makeColorFromResourceColor(Color.Blue), drawing.BlendMode.SRC_IN))
        }
        Text('属性字符串支持svg2')
        // $r('app.media.ice')需要替换为实际的图像资源文件。
        Text() {
          ImageSpan($r('app.media.ice'))
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

### 示例7（设置图片拉伸）

该示例通过[resizable](#resizable)属性的slice选项，对ImageSpan图片不同方向进行拉伸。

从API版本26.1.0开始，新增resizable属性。

```TypeScript
@Entry
@Component
struct ImageSpanResizablePage {
  build() {
    Column({ space: 20 }) {
      Text('ImageSpan resizable Demo')
        .fontSize(28)
        .fontWeight(FontWeight.Bold)

      Text('使用 Text + ImageSpan，设置 resizable 的 slice 属性实现九宫格拉伸：')
        .fontSize(28)
        .fontColor('#666666')
        .width('90%')

      Text() {
        Span('原图\n')
          .fontSize(28)
        ImageSpan($r('app.media.landscape'))
          .width(200)
          .height(200)
        Span('\n设置Resizable后\n')
          .fontSize(28)
        ImageSpan($r('app.media.landscape'))
          .width(260)
          .height(260)
          .resizable({
            slice: {
              left: '200px',
              top: '200px',
              right: '20px',
              bottom: '20px'
            }
          })
      }
      .width('90%')
      .textAlign(TextAlign.Center)
      .margin({ top: 10 })
    }
    .width('100%')
    .height('100%')
    .padding(20)
    .alignItems(HorizontalAlign.Center)
  }
}
```
