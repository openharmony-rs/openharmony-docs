# ImageAnimator

提供帧动画组件来实现逐帧播放图片的能力，可以配置需要播放的图片列表，每张图片可以配置时长。
> **说明：** > > - 该组件从API版本26.0.0开始支持WithTheme。

## 子组件

无

## ImageAnimator

```TypeScript
ImageAnimator()
```

返回ImageAnimator。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [ImageFrameInfo](arkts-arkui-imageframeinfo-i.md) | 图片帧信息集合。 |

## 示例

通过ImageAnimator组件播放Resource动画。

```TypeScript
// xxx.ets
@Entry
@Component
struct ImageAnimatorExample {
  @State state: AnimationStatus = AnimationStatus.Initial;
  @State reverse: boolean = false;
  @State iterations: number = 1;

  build() {
    Column({ space: 10 }) {
      ImageAnimator()
        .images([
          {
            // $r('app.media.img1')需要替换为开发者所需的图像资源文件。
            src: $r('app.media.img1')
          },
          {
            // $r('app.media.img2')需要替换为开发者所需的图像资源文件。
            src: $r('app.media.img2')
          },
          {
            // $r('app.media.img3')需要替换为开发者所需的图像资源文件。
            src: $r('app.media.img3')
          },
          {
            // $r('app.media.img4')需要替换为开发者所需的图像资源文件。
            src: $r('app.media.img4')
          }
        ])
        .duration(4000)
        .state(this.state)
        .reverse(this.reverse)
        .fillMode(FillMode.None)
        .iterations(this.iterations)
        .width(340)
        .height(240)
        .margin({ top: 100 })
        .onStart(() => {
          console.info('Start')
        })
        .onPause(() => {
          console.info('Pause')
        })
        .onRepeat(() => {
          console.info('Repeat')
        })
        .onCancel(() => {
          console.info('Cancel')
        })
        .onFinish(() => {
          console.info('Finish')
          this.state = AnimationStatus.Stopped
        })
      Row() {
        Button('start').width(100).padding(5).onClick(() => {
          this.state = AnimationStatus.Running
        }).margin(5)
        Button('pause').width(100).padding(5).onClick(() => {
          this.state = AnimationStatus.Paused // 显示当前帧图片
        }).margin(5)
        Button('stop').width(100).padding(5).onClick(() => {
          this.state = AnimationStatus.Stopped // 显示动画的起始帧图片
        }).margin(5)
      }

      Row() {
        Button('reverse').width(100).padding(5).onClick(() => {
          this.reverse = !this.reverse
        }).margin(5)
        Button('once').width(100).padding(5).onClick(() => {
          this.iterations = 1
        }).margin(5)
        Button('infinite').width(100).padding(5).onClick(() => {
          this.iterations = -1 // 无限循环播放
        }).margin(5)
      }
    }.width('100%').height('100%')
  }
}
```

通过ImageAnimator组件播放PixelMap动画。

```TypeScript
// xxx.ets
import { image } from '@kit.ImageKit';

@Entry
@Component
struct ImageAnimatorExample {
  imagePixelMap: Array<PixelMap> = [];
  @State state: AnimationStatus = AnimationStatus.Initial;
  @State reverse: boolean = false;
  @State iterations: number = 1;
  @State images: Array<ImageFrameInfo> = [];

  async aboutToAppear() {
    // $r('app.media.1')需要替换为开发者所需的图像资源文件。
    this.imagePixelMap.push(await this.getPixmapFromMedia($r('app.media.1')));
    // $r('app.media.2')需要替换为开发者所需的图像资源文件。
    this.imagePixelMap.push(await this.getPixmapFromMedia($r('app.media.2')));
    // $r('app.media.3')需要替换为开发者所需的图像资源文件。
    this.imagePixelMap.push(await this.getPixmapFromMedia($r('app.media.3')));
    // $r('app.media.4')需要替换为开发者所需的图像资源文件。
    this.imagePixelMap.push(await this.getPixmapFromMedia($r('app.media.4')));
    this.images.push({ src: this.imagePixelMap[0] });
    this.images.push({ src: this.imagePixelMap[1] });
    this.images.push({ src: this.imagePixelMap[2] });
    this.images.push({ src: this.imagePixelMap[3] });
  }

  build() {
    Column({ space: 10 }) {
      ImageAnimator()
        .images(this.images)
        .duration(2000)
        .state(this.state)
        .reverse(this.reverse)
        .fillMode(FillMode.None)
        .iterations(this.iterations)
        .width(340)
        .height(240)
        .margin({ top: 100 })
        .onStart(() => {
          console.info('Start');
        })
        .onPause(() => {
          console.info('Pause');
        })
        .onRepeat(() => {
          console.info('Repeat');
        })
        .onCancel(() => {
          console.info('Cancel');
        })
        .onFinish(() => {
          console.info('Finish');
          this.state = AnimationStatus.Stopped;
        })
      Row() {
        Button('start').width(100).padding(5).onClick(() => {
          this.state = AnimationStatus.Running;
        }).margin(5)
        Button('pause').width(100).padding(5).onClick(() => {
          this.state = AnimationStatus.Paused; // 显示当前帧图片
        }).margin(5)
        Button('stop').width(100).padding(5).onClick(() => {
          this.state = AnimationStatus.Stopped; // 显示动画的起始帧图片
        }).margin(5)
      }

      Row() {
        Button('reverse').width(100).padding(5).onClick(() => {
          this.reverse = !this.reverse;
        }).margin(5)
        Button('once').width(100).padding(5).onClick(() => {
          this.iterations = 1;
        }).margin(5)
        Button('infinite').width(100).padding(5).onClick(() => {
          this.iterations = -1; // 无限循环播放
        }).margin(5)
      }
    }.width('100%').height('100%')
  }

  private async getPixmapFromMedia(resource: Resource) {
    // 获取资源文件的内容数据
    let uint8Array = await this.getUIContext().getHostContext()?.resourceManager?.getMediaContent(resource.id);
    // 根据二进制数据创建图像源
    let imageSource = image.createImageSource(uint8Array?.buffer.slice(0, uint8Array.buffer.byteLength));
    try {
      // 从图像源创建PixelMap对象，指定像素格式为RGBA_8888
      let createPixelMap: image.PixelMap = await imageSource.createPixelMap({
        desiredPixelFormat: image.PixelMapFormat.RGBA_8888
      });
      return createPixelMap;
    } finally {
      // 释放图像源资源
      await imageSource.release();
    }
  }
}
```

通过[monitorInvisibleArea](arkts-arkui-imageanimator-attribute.md#monitorinvisiblearea)属性实现了当ImageAnimator的state属性为AnimationStatus.Running时，控制组件在不可见时停止播放，在可见时恢复播放。

```TypeScript
@Entry
@Component
struct ImageAnimatorAutoPauseTest {
  scroller: Scroller = new Scroller();
  @State state: AnimationStatus = AnimationStatus.Running;
  @State reverse: boolean = false;
  @State iterations: number = 100;
  @State preCallBack: string = 'Null';
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];

  build() {
    Stack({ alignContent: Alignment.TopStart }) {
      Scroll(this.scroller) {
        Column() {
          ImageAnimator()
            .images([
              {
                // $r('app.media.Clouds')需要替换为开发者所需的图像资源文件。
                src: $r('app.media.Clouds')
              },
              {
                // $r('app.media.landscape')需要替换为开发者所需的图像资源文件。
                src: $r('app.media.landscape')
              },
              {
                // $r('app.media.sky')需要替换为开发者所需的图像资源文件。
                src: $r('app.media.sky')
              },
              {
                // $r('app.media.mountain')需要替换为开发者所需的图像资源文件。
                src: $r('app.media.mountain')
              }
            ])
            .borderRadius(10)
            .monitorInvisibleArea(true)
            .clip(true)
            .duration(4000)
            .state(this.state)
            .reverse(this.reverse)
            .fillMode(FillMode.Forwards)
            .iterations(this.iterations)
            .width(340)
            .height(240)
            .margin({ top: 100 })
            .onStart(() => {
              this.preCallBack = 'Start';
              console.info('ImageAnimator Start');
            })
            .onPause(() => {
              this.preCallBack = 'Pause';
              console.info('ImageAnimator Pause');
            })
            .onRepeat(() => {
              console.info('ImageAnimator Repeat');
            })
            .onCancel(() => {
              console.info('ImageAnimator Cancel');
            })
            .onFinish(() => {
              console.info('ImageAnimator Finish');
            })
          ForEach(this.arr, (item: number) => {
            Text(item.toString())
              .width('90%')
              .height(150)
              .backgroundColor(0xFFFFFF)
              .borderRadius(15)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .margin({ top: 10 })
          }, (item: number) => item.toString())
        }.width('100%')
      }
      .scrollable(ScrollDirection.Vertical) // 滚动方向纵向
      .scrollBar(BarState.On) // 滚动条常驻显示
      .scrollBarColor(Color.Gray) // 滚动条颜色
      .scrollBarWidth(10) // 滚动条宽度
      .friction(0.6)
      .edgeEffect(EdgeEffect.None)
      .onWillScroll((xOffset: number, yOffset: number, scrollState: ScrollState) => {
        console.info(xOffset + ' ' + yOffset);
      })
      .onScrollEdge((side: Edge) => {
        console.info('To the edge');
      })
      .onScrollStop(() => {
        console.info('Scroll Stop');
      })

      Text('上次触发的回调（Pause/Start）：' + this.preCallBack)
        .margin({ top: 60, left: 20 })
    }.width('100%').height('100%').backgroundColor(0xDCDCDC)
  }
}
```
