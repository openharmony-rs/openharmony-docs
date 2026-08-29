# Video

Video组件用于播放视频文件并控制其播放状态，支持播放、暂停、进度控制、倍速播放、全屏切换等功能。
> **说明：** > > 该组件从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。 > 
 > > Video组件只提供简单的视频播放功能，无法支撑复杂的视频播控场景。复杂开发场景推荐使用[AVPlayer](../../apis-media-kit/arkts-apis/arkts-media-media-avplayer-i.md)播控API和 > XComponent组件开发。 > 
 > > Video组件在使用[expandSafeArea](arkts-arkui-commonmethod-c.md#expandsafearea)扩展安全区域时，组件视频显示内容区域不支持扩展。

## 权限列表

使用网络视频时，需要申请权限ohos.permission.INTERNET。具体申请方式请参考[声明权限](../../../security/AccessToken/declare-permissions.md)。

## 子组件

不支持子组件。

## Video

```TypeScript
Video(value: VideoOptions)
```

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [VideoOptions](arkts-arkui-videooptions-i.md) | 是 | 视频信息。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [FullscreenInfo](arkts-arkui-fullscreeninfo-i.md) | 用于描述当前视频是否进入全屏播放状态。 |
| [PlaybackInfo](arkts-arkui-playbackinfo-i.md) | 用于描述当前视频播放的进度。 |
| [PosterOptions](arkts-arkui-posteroptions-i.md) | 用于描述当前视频是否配置首帧送显。 |
| [PreparedInfo](arkts-arkui-preparedinfo-i.md) | 用于描述当前视频的时长。 |
| [VideoOptions](arkts-arkui-videooptions-i.md) | 定义Video的具体配置参数。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [PlaybackSpeed](arkts-arkui-playbackspeed-e.md) | 视频播放倍速选项。 |
| [SeekMode](arkts-arkui-seekmode-e.md) | 视频跳转模式选项。 
| 名称 |值| 说明 | | ---------------- |--| ---------------------------- | | PreviousKeyframe |0| 跳转到当前播放位置之前最近的关键帧。 | | NextKeyframe |1| 跳转到当前播放位置之后最近的关键帧。 | | ClosestKeyframe |2| 跳转到距离当前播放位置最近的关键帧。 | | Accurate |3| 精准跳转到指定时间点，不论是否为关键帧。精度高但可能需要解码更多帧。 | |

## 示例

基础用法包括：控制栏、预览图、自动播放、播放速度、响应快捷键（从API version 15开始，支持通过[enableShortcutKey](arkts-arkui-video-attribute.md#enableshortcutkey)设置组件开启快捷键响应）、控制器（开始播放、暂停播放、停止播放、重置视频播放器、跳转等）、首帧送显（从API version 18开始，支持通过posterOptions设置视频播放的首帧送显选项。从API version 21开始，posterOptions支持通过PosterOptions的contentTransitionEffect参数来设置当前视频的预览图内容变化时的转场动效。）以及一些状态回调方法。

```TypeScript
// xxx.ets
@Entry
@Component
struct VideoCreateComponent {
  // $rawfile('video1.mp4')、$r('app.media.poster1')需要分别替换为开发者所需的视频、图片资源文件。
  @State videoSrc: Resource = $rawfile('video1.mp4');
  @State previewUri: Resource = $r('app.media.poster1');
  @State curRate: PlaybackSpeed = PlaybackSpeed.Speed_Forward_1_00_X;
  @State isAutoPlay: boolean = false;
  @State showControls: boolean = true;
  @State isShortcutKeyEnabled: boolean = false;
  @State showFirstFrame: boolean = false;
  controller: VideoController = new VideoController();

  build() {
    Column() {
      Video({
        src: this.videoSrc,
        previewUri: this.previewUri, // 设置预览图。
        currentProgressRate: this.curRate, // 设置播放速度。
        controller: this.controller,
        posterOptions: {
          showFirstFrame: this.showFirstFrame,
          contentTransitionEffect: ContentTransitionEffect.OPACITY
        } // 关闭首帧送显, 设置预览图淡入淡出动效。
      })
        .width('100%')
        .height(600)
        .autoPlay(this.isAutoPlay)
        .controls(this.showControls)
        .enableShortcutKey(this.isShortcutKeyEnabled)
        .onStart(() => {
          console.info('onStart');
        })
        .onPause(() => {
          console.info('onPause');
        })
        .onFinish(() => {
          console.info('onFinish');
        })
        .onError(() => {
          console.error('onError');
        })
        .onStop(() => {
          console.info('onStop');
        })
        .onPrepared((e?: DurationObject) => {
          if (e != undefined) {
            console.info(`onPrepared is ${e.duration}`);
          }
        })
        .onSeeking((e?: TimeObject) => {
          if (e != undefined) {
            console.info(`onSeeking is ${e.time}`);
          }
        })
        .onSeeked((e?: TimeObject) => {
          if (e != undefined) {
            console.info(`onSeeked is ${e.time}`);
          }
        })
        .onUpdate((e?: TimeObject) => {
          if (e != undefined) {
            console.info(`onUpdate is ${e.time}`);
          }
        })
        .onFullscreenChange((e?: FullscreenObject) => {
          if (e != undefined) {
            console.info(`onFullscreenChange is ${e.fullscreen}`);
          }
        })

      Row() {
        // $rawfile('video2.mp4')、$r('app.media.poster2')需要分别替换为开发者所需的视频、图片资源文件。
        Button('src').onClick(() => {
          this.videoSrc = $rawfile('video2.mp4'); // 切换视频源。
        }).margin(5)
        Button('previewUri').onClick(() => {
          this.previewUri = $r('app.media.poster2'); // 切换视频预览海报。
        }).margin(5)
        Button('controls').onClick(() => {
          this.showControls = !this.showControls; // 切换是否显示视频控制栏。
        }).margin(5)
      }

      Row() {
        Button('start').onClick(() => {
          this.controller.start(); // 开始播放。
        }).margin(2)
        Button('pause').onClick(() => {
          this.controller.pause(); // 暂停播放。
        }).margin(2)
        Button('stop').onClick(() => {
          this.controller.stop(); // 结束播放。
        }).margin(2)
        Button('reset').onClick(() => {
          this.controller.reset(); // 重置视频播放器。
        }).margin(2)
        Button('setTime').onClick(() => {
          this.controller.setCurrentTime(10, SeekMode.Accurate); // 精准跳转到视频的10s位置。
        }).margin(2)
      }

      Row() {
        Button('rate 0.75').onClick(() => {
          this.curRate = PlaybackSpeed.Speed_Forward_0_75_X; // 0.75倍速播放。
        }).margin(5)
        Button('rate 1').onClick(() => {
          this.curRate = PlaybackSpeed.Speed_Forward_1_00_X; // 原倍速播放。
        }).margin(5)
        Button('rate 2').onClick(() => {
          this.curRate = PlaybackSpeed.Speed_Forward_2_00_X; // 2倍速播放。
        }).margin(5)
      }
    }
  }
}

interface DurationObject {
  duration: number;
}

interface TimeObject {
  time: number;
}

interface FullscreenObject {
  fullscreen: boolean;
}
```

通过enableAnalyzer属性开启图像AI分析。

```TypeScript
// xxx.ets
@Entry
@Component
struct ImageAnalyzerExample {
  // $rawfile('video1.mp4')、$r('app.media.poster1')需要分别替换为开发者所需的视频、图片资源文件
  @State videoSrc: Resource = $rawfile('video1.mp4');
  @State previewUri: Resource = $r('app.media.poster1');
  controller: VideoController = new VideoController();
  config: ImageAnalyzerConfig = {
    types: [ImageAnalyzerType.SUBJECT, ImageAnalyzerType.TEXT]
  }
  private aiController: ImageAnalyzerController = new ImageAnalyzerController();
  private options: ImageAIOptions = {
    types: [ImageAnalyzerType.SUBJECT, ImageAnalyzerType.TEXT],
    aiController: this.aiController
  }

  build() {
    Column() {
      Video({
        src: this.videoSrc,
        previewUri: this.previewUri,
        controller: this.controller,
        imageAIOptions: this.options // 设置图像AI分析选项
      })
        .width('100%')
        .height(600)
        .controls(false)
        .enableAnalyzer(true)
        .analyzerConfig(this.config)
        .onStart(() => {
          console.info('onStart');
        })
        .onPause(() => {
          console.info('onPause');
        })

      Row() {
        Button('start').onClick(() => {
          this.controller.start(); // 开始播放
        }).margin(5)
        Button('pause').onClick(() => {
          this.controller.pause(); // 暂停播放
        }).margin(5)
        Button('getTypes').onClick(() => {
          this.aiController.getImageAnalyzerSupportTypes();
        }).margin(5)
      }
    }
  }
}
```

以下示例展示了如何使Video组件能够播放拖入的视频。

```TypeScript
// xxx.ets
import { unifiedDataChannel, uniformTypeDescriptor } from '@kit.ArkData';

@Entry
@Component
struct Index {
  // $rawfile('video1.mp4')需要替换为开发者所需的视频资源文件
  @State videoSrc: Resource | string = $rawfile('video1.mp4');
  private controller: VideoController = new VideoController();

  build() {
    Column() {
      Video({
        src: this.videoSrc,
        controller: this.controller
      })
        .width('100%')
        .height(600)
        .onPrepared(() => {
          // 在onPrepared回调中执行controller的start方法，确保视频源更换后直接开始播放。
          this.controller.start();
        })
        .onDrop((e: DragEvent) => {
          // 外部视频拖入应用Video组件范围，松手后触发通过onDrop注册的回调。
          // 在DragEvent中会包含拖入的视频源信息，取出后赋值给状态变量videoSrc即可改变Video的视频源。
          let record = e.getData().getRecords()[0];
          if (record.getType() == uniformTypeDescriptor.UniformDataType.VIDEO) {
            let videoInfo = record as unifiedDataChannel.Video;
            this.videoSrc = videoInfo.videoUri;
          }
        })
    }
  }
}
```

通过objectFit属性设置视频填充模式。

```TypeScript
// xxx.ets
@Entry
@Component
struct VideoObject {
  // $rawfile('rabbit.mp4')、$r('app.media.tree')需要分别替换为开发者所需的视频、图片资源文件
  @State videoSrc: Resource = $rawfile('rabbit.mp4');
  @State previewUri: Resource = $r('app.media.tree');
  @State showControls: boolean = true;
  controller: VideoController = new VideoController();

  build() {
    Column() {
      Text('ImageFit.Contain').fontSize(12)
      Video({
        src: this.videoSrc,
        previewUri: this.previewUri,
        controller: this.controller
      })
        .width(350)
        .height(230)
        .controls(this.showControls)
        .objectFit(ImageFit.Contain) // 设置视频填充模式为ImageFit.Contain
        .margin(5)

      Text('ImageFit.Fill').fontSize(12)
      Video({
        src: this.videoSrc,
        previewUri: this.previewUri,
        controller: this.controller
      })
        .width(350)
        .height(230)
        .controls(this.showControls)
        .objectFit(ImageFit.Fill) // 设置视频填充模式为ImageFit.Fill
        .margin(5)

      Text('ImageFit.START').fontSize(12)
      Video({
        src: this.videoSrc,
        previewUri: this.previewUri,
        controller: this.controller
      })
        .width(350)
        .height(230)
        .controls(this.showControls)
        .objectFit(ImageFit.START) // 设置视频填充模式为ImageFit.START
        .margin(5)
    }.width('100%').alignItems(HorizontalAlign.Center)
  }
}
```

从API version 20开始，支持通过onError获取错误信息，该示例以传入不存在的视频资源路径为例。

```TypeScript
// xxx.ets
@Entry
@Component
struct VideoErrorComponent {
  @State videoSrc: string = 'video.mp4'; // 传入不存在的视频资源路径。
  @State isAutoPlay: boolean = false;
  @State showControls: boolean = true;
  controller: VideoController = new VideoController();
  @State errorMessage: string = '';

  build() {
    Column() {
      Video({
        src: this.videoSrc,
        controller: this.controller,
      })
        .width(200)
        .height(120)
        .margin(5)
        .autoPlay(this.isAutoPlay)
        .controls(this.showControls)
        .onError((err) => {
          // 通过onError事件获取错误码，code为错误码，message为错误信息。
          console.error(`code is ${err.code}, message is ${err.message}`);
          this.errorMessage = `code is ${err.code}, message is ${err.message}`;
        })
      // 传入不存在的视频资源路径，预期："code is 103602, message is Not a valid source"。
      Text(this.errorMessage)
    }
    .width('100%')
    .height('100%')
    .backgroundColor('rgb(213,213,213)')
  }
}
```

以下示例展示了如何使用attributeModifier动态设置Video组件的enableAnalyzer、analyzerConfig属性和onStart、onPause、onFinish、onError、onStop、onPrepared、onSeeking、onSeeked、onUpdate、onFullscreenChange方法。

```TypeScript
// xxx.ets
class MyVideoModifier implements AttributeModifier<VideoAttribute> {
  applyNormalAttribute(instance: VideoAttribute): void {
    // 设置开启组件AI分析功能，长按触发AI识别功能
    instance.enableAnalyzer(true);
    let config: ImageAnalyzerConfig = {
      types: [ImageAnalyzerType.SUBJECT, ImageAnalyzerType.TEXT]
    }
    instance.analyzerConfig(config);
    instance.onStart(() => {
      console.info('video: onStart');
    })
    instance.onPause(() => {
      console.info('video: onPause');
    })
    instance.onFinish(() => {
      console.info('video: onFinish');
    })
    instance.onError((err) => {
      console.error(`video: onError is code = ${err.code}, message = ${err.message}`);
    })
    instance.onStop(() => {
      console.info('video: onStop');
    })
    instance.onPrepared((e?: DurationObject) => {
      if (e != undefined) {
        console.info(`video: onPrepared is ${e.duration}`);
      }
    })
    instance.onSeeking((e?: TimeObject) => {
      if (e != undefined) {
        console.info(`video: onSeeking is ${e.time}`);
      }
    })
    instance.onSeeked((e?: TimeObject) => {
      if (e != undefined) {
        console.info(`video: onSeeked is ${e.time}`);
      }
    })
    instance.onUpdate((e?: TimeObject) => {
      if (e != undefined) {
        console.info(`video: onUpdate is ${e.time}`);
      }
    })
    instance.onFullscreenChange((e?: FullscreenObject) => {
      if (e != undefined) {
        console.info(`video: onFullscreenChange is ${e.fullscreen}`);
      }
    })
  }
}

@Entry
@Component
struct VideoModifierDemo {
  // $rawfile('video.mp4')需要替换为开发者所需的视频资源文件
  @State videoSrc: Resource = $rawfile('video.mp4');
  @State curRate: PlaybackSpeed = PlaybackSpeed.Speed_Forward_1_00_X;
  @State isAutoPlay: boolean = false;
  @State showControls: boolean = false;
  controller: VideoController = new VideoController();
  @State modifier: MyVideoModifier = new MyVideoModifier();

  build() {
    Column() {
      Video({
        src: this.videoSrc,
        currentProgressRate: this.curRate, // 设置播放速度
        controller: this.controller
      })
        .width(300)
        .height(180)
        .autoPlay(this.isAutoPlay)
        .controls(this.showControls)
        .attributeModifier(this.modifier)
      Row() {
        Button('start').onClick(() => {
          this.controller.start(); // 开始播放
        }).margin(2)
        Button('pause').onClick(() => {
          this.controller.pause(); // 暂停播放
        }).margin(2)
        Button('stop').onClick(() => {
          this.controller.stop(); // 结束播放
        }).margin(2)
        Button('reset').onClick(() => {
          this.controller.reset(); // 重置视频播放器
        }).margin(2)
      }

      Row() {
        Button('Fullscreen').onClick(() => {
          this.controller.requestFullscreen(true); // 全屏
        }).margin(2)
        Button('showControls').onClick(() => {
          this.showControls = !this.showControls; // 显示控制栏
        }).margin(2)
      }
    }
  }
}

interface DurationObject {
  duration: number;
}

interface TimeObject {
  time: number;
}

interface FullscreenObject {
  fullscreen: boolean;
}
```

从API版本26.0.0开始，新增VideoControllerAsync控制器及start、pause、stop、reset接口。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct VideoControllerAsyncExample {
  @State videoSrc: Resource = $rawfile('video1.mp4');// 替换为开发者所需的视频资源文件。
  controller: VideoControllerAsync = new VideoControllerAsync();

  build() {
    Column() {
      Video({
        src: this.videoSrc,
        controllerAsync: this.controller,
      })
        .width('100%')
        .height(600)
        .onStart(() => {
          console.info('onStart');
        })
        .onPause(() => {
          console.info('onPause');
        })
        .onFinish(() => {
          console.info('onFinish');
        })
        .onError(() => {
          console.error('onError');
        })
        .onStop(() => {
          console.info('onStop');
        })
        .onPrepared((e?: PreparedInfo) => {
          if (e != undefined) {
            console.info(`onPrepared is ${e.duration}`);
          }
        })
        .onSeeking((e?: PlaybackInfo) => {
          if (e != undefined) {
            console.info(`onSeeking is ${e.time}`);
          }
        })
        .onSeeked((e?: PlaybackInfo) => {
          if (e != undefined) {
            console.info(`onSeeked is ${e.time}`);
          }
        })
        .onUpdate((e?: PlaybackInfo) => {
          if (e != undefined) {
            console.info(`onUpdate is ${e.time}`);
          }
        })
        .onFullscreenChange((e?: FullscreenInfo) => {
          if (e != undefined) {
            console.info(`onFullscreenChange is ${e.fullscreen}`);
          }
        })

      Row() {
        Button('start').onClick(() => {
          this.controller.start() // 开始播放，返回Promise<void>。
            .then(() => { // 可以通过then等待执行成功。
              console.info('start success')
            })
            .catch((err: BusinessError) => { // catch处理执行失败的场景。
              console.info(`start failed: ${err.message}`)
            })
        }).margin(2)
        Button('pause').onClick(() => {
          this.controller.pause() // 暂停播放。
            .then(() => {
              console.info('pause success')
            })
            .catch((err: BusinessError) => {
              console.info(`pause failed: ${err.message}`)
            })
        }).margin(2)
        Button('stop').onClick(() => {
          this.controller.stop() // 结束播放。
            .then(() => {
              console.info('stop success')
            })
            .catch((err: BusinessError) => {
              console.info(`stop failed: ${err.message}`)
            })
        }).margin(2)
        Button('reset').onClick(() => {
          this.controller.reset() // 重置视频播放器。
            .then(() => {
              console.info('reset success')
            })
            .catch((err: BusinessError) => {
              console.info(`reset failed: ${err.message}`)
            })
        }).margin(2)
      }
    }
  }
}
```
