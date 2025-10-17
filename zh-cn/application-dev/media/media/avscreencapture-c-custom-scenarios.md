# AVScreenCapture录屏自定义场景

<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zzs_911-->
<!--Designer: @stupig001-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->

AVScreenCapture支持应用完成场景化的自定义配置，具体配置可参考下述指导。

## 设置录屏策略

### 蜂窝通话设置

从API 20开始支持蜂窝通话设置。

使用[OH_AVScreenCapture_StrategyForKeepCaptureDuringCall](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_strategyforkeepcaptureduringcall)设置蜂窝通话时是否保持录屏。

```c++
OH_AVScreenCapture_CaptureStrategy* strategy = OH_AVScreenCapture_CreateCaptureStrategy();
OH_AVScreenCapture_StrategyForKeepCaptureDuringCall(strategy, true);
OH_AVScreenCapture_SetCaptureStrategy(capture, strategy);
```

### 设置B帧编码

从API 20开始支持设置B帧编码。

使用[OH_AVScreenCapture_StrategyForBFramesEncoding](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_strategyforbframesencoding)设置是否使用B帧编码，用于减小录制文件的大小。

```c++
OH_AVScreenCapture_CaptureStrategy* strategy = OH_AVScreenCapture_CreateCaptureStrategy();
OH_AVScreenCapture_StrategyForBFramesEncoding(strategy, true);
OH_AVScreenCapture_SetCaptureStrategy(capture, strategy);
```

### 设置屏幕捕获Picker

从API 20开始支持设置屏幕捕获Picker。

使用[OH_AVScreenCapture_StrategyForPickerPopUp](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_strategyforpickerpopup)设置是否弹出屏幕捕获Picker。

```c++
OH_AVScreenCapture_CaptureStrategy* strategy = OH_AVScreenCapture_CreateCaptureStrategy();
OH_AVScreenCapture_StrategyForPickerPopUp(strategy, true);
OH_AVScreenCapture_SetCaptureStrategy(capture, strategy);
```

## 设置旋转适配

从API 20开始支持设置旋转适配。

使用[OH_AVScreenCapture_StrategyForCanvasFollowRotation](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_strategyforcanvasfollowrotation)，可设置录屏时是否自动跟随屏幕旋转。

调用此接口完成设置后，无需再调用[OH_AVScreenCapture_ResizeCanvas](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_resizecanvas)手动修改分辨率。

```c++
OH_AVScreenCapture_CaptureStrategy* strategy = OH_AVScreenCapture_CreateCaptureStrategy();
// 设为true，表示跟随屏幕旋转，并在横竖屏旋转后，自动调换虚拟屏尺寸，确保输出画面及时跟随旋转。
OH_AVScreenCapture_StrategyForCanvasFollowRotation(strategy, true);
OH_AVScreenCapture_SetCaptureStrategy(capture, strategy);
```

## 设置麦克风开关

使用[OH_AVScreenCapture_SetMicrophoneEnabled](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_setmicrophoneenabled)，可设置在录屏过程中是否开启麦克风，默认麦克风开关为开启状态。

> **说明：**
> 使用麦克风录制，需要：
>
> - 配置麦克风权限ohos.permission.MICROPHONE，配置方式请参见[向用户申请权限](../../security/AccessToken/request-user-authorization.md)。
> - 申请长时任务，申请方式请参见[申请长时任务](../../task-management/continuous-task.md)。

```c++
bool isMic = true;
OH_AVScreenCapture_SetMicrophoneEnabled(capture, isMic);
```

## 隐私设置

从API 20开始，支持使用[OH_AVScreenCapture_StrategyForPrivacyMaskMode](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_strategyforprivacymaskmode)设置屏幕录制隐私窗口屏蔽模式。


```c++
//  value值设为0，表示全屏屏蔽模式。value值设为1，表示窗口屏蔽模式。默认为全屏屏蔽模式。
int value = 0;
OH_AVScreenCapture_CaptureStrategy* strategy = OH_AVScreenCapture_CreateCaptureStrategy();
OH_AVScreenCapture_StrategyForPrivacyMaskMode(strategy, value);
OH_AVScreenCapture_SetCaptureStrategy(capture, strategy);
```

在API 12时，支持使用[OH_AVScreenCapture_SkipPrivacyMode](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_skipprivacymode)设置录屏时的豁免隐私窗口。目前设置豁免隐私窗口需要传入所有隐私子窗口和主窗口ID，传空数组取消豁免隐私窗口。

```c++
std::vector<int> windowIdsSkipPrivacy = {};
OH_AVScreenCapture_SkipPrivacyMode(capture, &windowIdsSkipPrivacy[0],
    static_cast<int32_t>(windowIdsSkipPrivacy.size()));
```

## 设置捕获区域

从API 20开始支持设置捕获区域。

可以根据需要设置区域坐标和大小，使用[OH_AVScreenCapture_SetCaptureArea](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_setcapturearea)设置想要捕获的区域，如下方创建了一个从（0，0）为起点的长100px，宽100px的矩形区域。此接口在录屏开始前后都可以设置。

```c++
OH_Rect* region = new OH_Rect;
    region->x = 0;
    region->y = 0;
    region->width = 100;
    region->height = 100;
uint64_t regionDisplayId = 0; // 传入矩形区域所在的屏幕Id。
OH_AVScreenCapture_SetCaptureArea(capture, regionDisplayId, region);
```

## 设置捕获光标

从API 15开始支持设置捕获光标。

使用[OH_AVScreenCapture_ShowCursor](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_showcursor)设置光标显示开关，开始录屏前后均可调用。

```c++
OH_AVScreenCapture_ShowCursor(capture, false);
```

## 设置最大帧率

从API 14开始支持设置最大帧率。

使用[OH_AVScreenCapture_SetMaxVideoFrameRate](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_setmaxvideoframerate)设置录屏时的最大帧率，需在录屏启动后被调用。

```c++
OH_AVScreenCapture_SetMaxVideoFrameRate(capture, 20);
```

## 设置屏幕分辨率

使用[OH_AVScreenCapture_ResizeCanvas](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_resizecanvas)调整录屏分辨率，需在启动后调用，分辨率有范围限制。

```c++
OH_AVScreenCapture_ResizeCanvas(capture, 768, 1280);
```

## 设置内容过滤

选择录屏时要过滤的声音和窗口。

使用[OH_AVScreenCapture_ContentFilter_AddAudioContent](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_contentfilter_addaudiocontent)设置可过滤的声音，包含系统音和应用自身声音。

使用[OH_AVScreenCapture_ContentFilter_AddWindowContent](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_contentfilter_addwindowcontent)设置可过滤的窗口，通过窗口ID来指定。

```c++
OH_AVScreenCapture_ContentFilter *contentFilter= OH_AVScreenCapture_CreateContentFilter();
// 添加过滤通知音。
OH_AVScreenCapture_ContentFilter_AddAudioContent(contentFilter, OH_SCREEN_CAPTURE_NOTIFICATION_AUDIO);
// 排除指定窗口id。
std::vector<int> windowIdsExclude = {};
OH_AVScreenCapture_ContentFilter_AddWindowContent(contentFilter, &windowIdsExclude[0],
    static_cast<int32_t>(windowIdsExclude.size()));

OH_AVScreenCapture_ExcludeContent(capture, contentFilter);
```

## 更多资源

- API参考：详细的API描述请见[native_avscreen_capture.h](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md)。

- 示例工程：该示例调用了媒体AVScreenCapture组件提供的接口能力，提供屏幕捕获的功能，详情见[录屏示例工程](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/ScreenCapture/ScreenCaptureSample)。
