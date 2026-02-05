# Video Playback (Video)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @sd-wu-->
<!--Designer: @sunbees-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->


The **Video** component is used to play a video and control its playback. It is usually used in video players and video list pages within applications. A video automatically plays once fully loaded. When the user clicks the video area, the video is paused and the playback progress bar is displayed. The user can drag the progress bar to the desired position. For details, see [Video](../reference/apis-arkui/arkui-ts/ts-media-components-video.md).


## Creating a Video Component

You can create a **Video** component by calling the following API:

`Video(value: VideoOptions)`

## Loading Video

The **Video** component supports both local and online videos. For details about data source configuration, see [VideoOptions](../reference/apis-arkui/arkui-ts/ts-media-components-video.md#videooptions).


### Loading a Local Video

- Common local video

  To load a local video, specify the corresponding video file in the local **rawfile** directory, as shown in the following figure.

  ![en-us_image_0000001562700409](figures/en-us_image_0000001562700409.png)

  Use **$rawfile()** to reference the video resource.

  <!-- @[local_video](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/VideoPlayer/entry/src/main/ets/pages/LocalVideo.ets) -->
  
  ``` TypeScript
  // xxx.ets
  // ···
  @Component
  export struct LocalVideo {
    private controller: VideoController = new VideoController();
    private previewUris: Resource = $r('app.media.preview');
    private innerResource: Resource = $rawfile('videoTest.mp4');
  
    build() {
      Column() {
        Video({
          src: this.innerResource,  // Set the video source.
          previewUri: this.previewUris, // Set the preview image.
          controller: this.controller // Set the video controller to control the video playback status.
        })
      }
    }
  }
  ```


- Video provided by a [DataAbility](../application-models/dataability-overview.md), whose path contains the **dataability://** prefix<br>Ensure that the corresponding video resource exists.

  <!-- @[data_ability](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/VideoPlayer/entry/src/main/ets/pages/DataAbility.ets) -->
  
  ``` TypeScript
  // xxx.ets
  // ···
  @Component
  export struct LocalVideoTwo {
    private controller: VideoController = new VideoController();
    private previewUris: Resource = $r('app.media.preview');
    private videoSrc: string = 'dataability://device_id/com.domainname.dataability.videodata/video/10';
  
    build() {
      Column() {
        Video({
          src: this.videoSrc,
          previewUri: this.previewUris,
          controller: this.controller
        })
      }
    }
  }
  ```

### Loading a Video in the Application Sandbox

To load a video in the application sandbox, use a string with the **file://** prefix. Ensure that there are files in the specified path and the application has the read permission to the files.

<!-- @[sandbox](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/VideoPlayer/entry/src/main/ets/pages/Sandbox.ets) -->

``` TypeScript
// xxx.ets
// ···
@Component
export struct Sandbox {
  private controller: VideoController = new VideoController();
  private videoSrc: string = 'file:///data/storage/el2/base/haps/entry/files/show.mp4';

  build() {
    Column() {
      Video({
        src: this.videoSrc,
        controller: this.controller
      })
    }
  }
}
```


### Loading an Online Video

To load online videos, you must apply for the ohos.permission.INTERNET permission. For details about how to apply for the permission, see [Declaring Permissions](../security/AccessToken/declare-permissions.md). In this scenario, the **src** attribute indicates the URL of the online video.


<!-- @[online_video](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/VideoPlayer/entry/src/main/ets/pages/OnlineVideo.ets) -->

``` TypeScript
// xxx.ets
// ···
@Component
export struct OnlineVideo {
  private controller: VideoController = new VideoController();
  private previewUris: Resource = $r('app.media.preview');
  private videoSrc: string = 'www.example.com/example.mp4'; // Replace the URL with that of the actual video to load.

  build() {
    Column() {
      Video({
        src: this.videoSrc,
        previewUri: this.previewUris,
        controller: this.controller
      })
    }
  }
}
```


## Adding Attributes

Use the [attributes](../reference/apis-arkui/arkui-ts/ts-media-components-video.md#attributes) of the **Video** component to control video playback. For example, you can set whether to mute the video and whether to display the video playback control bar.


<!-- @[attribute_video](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/VideoPlayer/entry/src/main/ets/pages/AttributeVideo.ets) -->

``` TypeScript
// xxx.ets
// ···
@Component
export struct AttributeVideo {
  private controller: VideoController = new VideoController();

  build() {
    Column() {
      Video({
        controller: this.controller
      })
        .muted(false) // Set whether to mute the video.
        .controls(false) // Set whether to display the video playback control bar.
        .autoPlay(false) // Set whether to enable auto play.
        .loop(false) // Set whether to repeat the video.
        .objectFit(ImageFit.Contain) // Set the video fill mode.
    }
  }
}
```


## Adding Events

The **Video** component supports various callback events in addition to the universal events. For details, see [Events](../reference/apis-arkui/arkui-ts/ts-media-components-video.md#events).

<!-- @[event_call](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/VideoPlayer/entry/src/main/ets/pages/EventCall.ets) -->

``` TypeScript
// xxx.ets
@Entry
@Component
struct EventCall {
  private controller: VideoController = new VideoController();
  private previewUris: Resource = $r('app.media.preview');
  private innerResource: Resource = $rawfile('videoTest.mp4');

  build() {
    Column() {
      Video({
        src: this.innerResource,
        previewUri: this.previewUris,
        controller: this.controller
      })
        .onUpdate((event) => { // Triggered when the playback progress changes.
        })
        .onPrepared((event) => { // Triggered when video preparation is complete.
        })
        .onError(() => { // Triggered when the video playback fails.
        })
        .onStop(() => { // Triggered when the video playback stops.
        })
    }
  }
}
```


## Using the Video Controller

The video controller is used to control video playback. For details, see [VideoController](../reference/apis-arkui/arkui-ts/ts-media-components-video.md#videocontroller).

- Default controller

  The default controller supports four basic features: start playback, pause playback, set the video playback position, and play the video in full screen.

  <!-- @[video_guide](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/VideoPlayer/entry/src/main/ets/pages/VideoControl.ets) -->
  
  ``` TypeScript
  // xxx.ets
  @Entry
  @Component
  struct VideoGuide {
    @State videoSrc: Resource = $rawfile('videoTest.mp4');
    @State previewUri: string = 'common/videoIcon.png';
    @State curRate: PlaybackSpeed = PlaybackSpeed.Speed_Forward_1_00_X;
  
    build() {
      Row() {
        Column() {
          Video({
            src: this.videoSrc,
            previewUri: this.previewUri,
            currentProgressRate: this.curRate // Set the playback speed.
          })
        }
        .width('100%')
      }
      .height('100%')
    }
  }
  ```

- Custom controller

  To implement a custom control bar, first disable the default controller. Then, use components such as [Button](../reference/apis-arkui/arkui-ts/ts-basic-components-button.md) and [Slider](../reference/apis-arkui/arkui-ts/ts-basic-components-slider.md) to build your own control and display elements. This approach is suitable for scenarios that require a highly customized UI.

  <!-- @[customize_control](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/VideoPlayer/entry/src/main/ets/pages/CustomizedControl.ets) -->

  ``` TypeScript
  // xxx.ets
  @Entry
  @Component
  struct CustomizedControl {
    @State videoSrc: Resource = $rawfile('videoTest.mp4');
    @State previewUri: string = 'common/videoIcon.png';
    @State curRate: PlaybackSpeed = PlaybackSpeed.Speed_Forward_1_00_X;
    // Initialize the current time to 0.
    @State currentTime: number = 0;
    // Initialize the current time to 0.
    @State durationTime: number = 0;
    controller: VideoController = new VideoController();

    build() {
      Row() {
        Column() {
          Video({
            src: this.videoSrc,
            previewUri: this.previewUri,
            currentProgressRate: this.curRate,
            controller: this.controller
          })
            .controls(false)
            .autoPlay(true)
            .onPrepared((event) => {
              if (event) {
                this.durationTime = event.duration
              }
            })
            .onUpdate((event) => {
              if (event) {
                this.currentTime = event.time
              }
            })
          Row() {
            Text(JSON.stringify(this.currentTime) + 's')
            Slider({
              value: this.currentTime,
              min: 0,
              max: this.durationTime
            })
              .onChange((value: number, mode: SliderChangeMode) => {
                this.controller.setCurrentTime(value); // Set the video playback position to the specified time.
              })
              .width('90%')
            Text(JSON.stringify(this.durationTime) + 's')
          }
          .opacity(0.8)
          .width('100%')
        }
        .width('100%')
      }
      .height('40%')
    }
  }
  ```


## Remarks

The **Video** component has encapsulated the basic capabilities of video playback. You do not need to create video instances or set and obtain video information. Simply set the data source and basic information to play videos. To customize video playback, you can use [AVPlayer](../media/media/media-kit-intro.md#avplayer). The following is a simple example of using AVPlayer to play a video. For more details or more complex features, see [Using AVPlayer to Play Videos (ArkTS)](../media/media/video-playback.md).
  <!-- @[xcomponent_av_player](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/VideoPlayer/entry/src/main/ets/pages/XComponentAVPlayer.ets) -->

  ``` TypeScript
  // xxx.ets
  import { window } from '@kit.ArkUI';
  import { AVPlayerController } from '../avplayertool/AVPlayerController';
  import { emitter } from '@kit.BasicServicesKit';
  import { CommonConstants, VideoDataType } from  '../common/constants/CommonConstants';
  import { VideoData } from '../model/VideoData'
  import { common } from '@kit.AbilityKit'

  class VideoXComponentController extends XComponentController {
    private avPlayerController: AVPlayerController;

    constructor(avPlayerController: AVPlayerController) {
      super();
      this.avPlayerController = avPlayerController;
    }

    onSurfaceCreated(surfaceId: string): void {
      let source: VideoData = {
        type: VideoDataType.RAW_FILE,
        videoSrc: 'videoTest.mp4'
      };
      // Pass the surface ID and video source to AVPlayer.
      this.avPlayerController.initAVPlayer(source, surfaceId);
    }
  }

  const MINUTE_UNIT = 60000;
  const SECOND_UNIT = 1000;
  const SECOND_TEN = 10;
  function timeCover(time: number): string {
    let min: number = Math.floor(time / MINUTE_UNIT);
    let second: string = ((time % MINUTE_UNIT) / SECOND_UNIT).toFixed(0);
    return `${min}:${(Number(second) < SECOND_TEN ? '0' : '') + second}`;
  }

  @Entry
  @Component
  struct XComponentAVPlayer {
    // Set the video controller to control the video playback status.
    @State avPlayerController: AVPlayerController = new AVPlayerController(this.getUIContext().getHostContext()!);
    // Total video duration.
    @State durationTime: number = 0;
    // Current progress of video playback.
    @State currentTime: number = 0;
    // Check whether the video is paused.
    @State isPause: boolean = true;
    // Check whether the video is played in full-screen mode.
    @State isLayoutFullScreen: boolean = false;
    // Set the XComponent controller.
    private videoXComponentController: XComponentController = new VideoXComponentController(this.avPlayerController);
    // Check whether the window is in landscape mode.
    @State isLandScape: boolean = false;
    // System navigation bar.
    private WINDOW_SYSTEM_BAR: Array<'status' | 'navigation'> = ['navigation', 'status'];
    // Window width.
    @State windowWidth:number = 0;
    // Window height.
    @State windowHeight: number = 0;
    // Window instance.
    private windowClass: window.Window | null = null;

    // Obtain the window instance.
    getWindow(): window.Window {
      const context = this.getUIContext().getHostContext() as common.UIAbilityContext;
      return context.windowStage!.getMainWindowSync();
    }

    aboutToAppear(): void {
      this.windowClass = this.getWindow();
      let properties = this.windowClass.getWindowProperties();
      let context = this.getUIContext();
      this.windowWidth = context.px2vp(properties.windowRect.width);
      this.windowHeight = context.px2vp(properties.windowRect.height);
      // Obtain the window orientation and size.
      this.windowClass.on('windowSizeChange', (size: window.Size) => {
        this.isLandScape = size.width > size.height;
        this.windowWidth = context.px2vp(size.width);
        this.windowHeight = context.px2vp(size.height);
      })
      emitter.on(CommonConstants.AVPLAYER_PREPARED, (res) => {
        if (res.data) {
          this.durationTime = this.avPlayerController.durationTime;
          // Update the video playback progress.
          setInterval(() => {
            this.currentTime = this.avPlayerController.currentTime;
          }, 1000);
        }
      });
    }

    // Set the full-screen mode.
    setFullScreen(isLayoutFullScreen: boolean) {
      window.getLastWindow(this.getUIContext().getHostContext()).then((win) => {
        if (isLayoutFullScreen) {
          // Set the visibility of the navigation bar and status bar when the window is in full-screen mode.
          win.setWindowSystemBarEnable([]);
        } else {
          // Set the visibility of the navigation bar and status bar when the window exits the full-screen mode.
          win.setWindowSystemBarEnable(this.WINDOW_SYSTEM_BAR);
        }
      }).catch((err: string) => {
        console.error(`setFullScreen failed, message is ${err}`);
      });
    }

    build() {
      Column() {
        Stack() {
          XComponent({ type: XComponentType.SURFACE, controller: this.videoXComponentController })
          Column() {
            Blank()
            Column() {
              Column() {
                Row() {
                  Row() {
                    // Set the video play or pause button.
                    SymbolGlyph(this.isPause ? $r('sys.symbol.pause') : $r('sys.symbol.play_fill'))
                      .fontSize(30)
                      .fontWeight(FontWeight.Bolder)
                      .fontColor([Color.White])
                      .onClick(() => {
                        if (this.isPause) {
                          this.avPlayerController.videoPause();
                        } else {
                          this.avPlayerController.videoPlay();
                        }
                        this.isPause = !this.isPause;
                      })
                    // Current progress of video playback.
                    Text(timeCover(this.currentTime))
                      .fontColor(Color.White)
                      .textAlign(TextAlign.End)
                      .fontWeight(FontWeight.Regular)
                      .margin({ left: 5 })
                  }
                  Row() {
                    // Video progress bar.
                    Slider({
                      value: this.currentTime,
                      min: 0,
                      max: this.durationTime,
                      style: SliderStyle.OutSet
                    })
                      .id('Slider')
                      .blockColor(Color.White)
                      .trackColor(Color.Gray)
                      .selectedColor('#317af7')
                      .showTips(false)
                      .onChange((value: number, mode: SliderChangeMode) => {
                        if (mode === SliderChangeMode.Begin) {
                          this.avPlayerController.videoPause();
                        }
                        this.avPlayerController.videoSeek(value);
                        this.currentTime = value;
                        if (mode === SliderChangeMode.End) {
                          this.isPause = true;
                          this.avPlayerController.videoPlay();
                        }
                      })
                  }
                  .layoutWeight(1)
                  Row() {
                    // Total video duration.
                    Text(timeCover(this.durationTime))
                      .fontColor(Color.White)
                      .fontWeight(FontWeight.Regular)
                      .margin({ right: 5 })
                  }
                  Row() {
                    // Set the button for full-screen playback.
                    SymbolGlyph(this.isLayoutFullScreen ? $r('sys.symbol.arrow_down_right_and_arrow_up_left') : $r('sys.symbol.arrow_up_left_and_arrow_down_right'))
                      .fontSize(30)
                      .fontWeight(FontWeight.Bolder)
                      .fontColor([Color.White])
                      .onClick(()=> {
                        this.isLayoutFullScreen = !this.isLayoutFullScreen;
                        this.setFullScreen(this.isLayoutFullScreen);
                      })
                  }
                }
                .justifyContent(FlexAlign.Center)
                .padding({ left: 12, right: 20, bottom: 28 })
                .width('100%')
              }
              .backgroundColor(Color.Black)
            }
            .justifyContent(FlexAlign.Center)
          }
          .width('100%')
          .height('100%')
        }
        .height(this.isLayoutFullScreen ? this.windowHeight : 300)
        .width(this.isLayoutFullScreen ? this.windowWidth : 300)
      }
      .width('100%')
      .height('100%')
      .justifyContent(FlexAlign.Center)
      .alignItems(HorizontalAlign.Center)
    }
  }
  ```

<!--RP1--><!--RP1End-->
