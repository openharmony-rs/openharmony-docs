# native_avscreen_capture.h

## 概述

声明用于构造屏幕录制对象的API。

**库：** libnative_avscreen_capture.so

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**起始版本：** 10

**相关模块：** [AVScreenCapture](capi-avscreencapture.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture *OH_AVScreenCapture_Create(void)](#oh_avscreencapture_create) | 实例化对象，创建OH_AVScreenCapture。可以通过调用[OH_AVScreenCapture_Release](capi-native-avscreen-capture-h.md#oh_avscreencapture_release)释放实例。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_Init(struct OH_AVScreenCapture *capture, OH_AVScreenCaptureConfig config)](#oh_avscreencapture_init) | 初始化[OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md)相关参数，包括下发的音频麦克风采样相关参数（可选）、音频内录采样相关参数、视频分辨率相关参数。录屏存文件场景，应用需要保证视频编码参数、视频采样参数、音频编码参数、音频内录采样参数均合法，音频麦克风采样参数合法（可选）。录屏出码流场景，应用需要保证音频内录采样参数、视频采样参数至少一个合法，音频麦克风采样参数合法（可选）。由于结构体变量在初始化时不会对成员进行初始化，应用必须根据使用场景正确设置各项参数。建议应用先将OH_AVScreenCaptureConfig结构体变量的所有内存字节均设置为0，然后再根据录屏场景设置合法参数。音频采样参数结构体[OH_AudioCaptureInfo](capi-avscreencapture-oh-audiocaptureinfo.md)，若audioSampleRate和audioChannels同时为0，则录屏实例OH_AVScreenCapture将忽略该类型的音频参数，且不采集该类型的音频数据。视频采样参数结构体[OH_VideoCaptureInfo](capi-avscreencapture-oh-videocaptureinfo.md)，若videoFrameWidth和videoFrameHeight同时为0，则录屏实例OH_AVScreenCapture将忽略对应视频参数，且不采集屏幕数据。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StartScreenCapture(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_startscreencapture) | 开始录屏，采集原始码流。调用后可以通过回调的监听（[OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable)）来监听当前是否有码流的产生,通过回调的监听（[OH_AVScreenCapture_OnStateChange](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onstatechange)）来监听启动状态。通过调用获取音频buffer（[OH_AVScreenCapture_AcquireAudioBuffer](capi-native-avscreen-capture-h.md#oh_avscreencapture_acquireaudiobuffer)）和视频buffer（[OH_AVScreenCapture_AcquireVideoBuffer](capi-native-avscreen-capture-h.md#oh_avscreencapture_acquirevideobuffer)）的接口来获取录屏的原始码流。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StopScreenCapture(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_stopscreencapture) | 结束录屏，与[OH_AVScreenCapture_StartScreenCapture](capi-native-avscreen-capture-h.md#oh_avscreencapture_startscreencapture)配合使用。调用后针对调用该接口的应用会停止录屏或屏幕共享，释放麦克风。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StartScreenRecording(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_startscreenrecording) | 启动录屏，调用此接口，可保存录屏文件。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StopScreenRecording(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_stopscreenrecording) | 停止录屏，与[OH_AVScreenCapture_StartScreenRecording](capi-native-avscreen-capture-h.md#oh_avscreencapture_startscreenrecording)配合使用。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_AcquireAudioBuffer(struct OH_AVScreenCapture *capture, OH_AudioBuffer **audiobuffer, OH_AudioCaptureSourceType type)](#oh_avscreencapture_acquireaudiobuffer) | 获取音频buffer。应用调用时需分配audiobuffer对应结构体大小的内存，否则影响音频buffer的获取。从API version 12开始，推荐使用接口[OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable)替代。 |
| [OH_NativeBuffer* OH_AVScreenCapture_AcquireVideoBuffer(struct OH_AVScreenCapture *capture, int32_t *fence, int64_t *timestamp, struct OH_Rect *region)](#oh_avscreencapture_acquirevideobuffer) | 获取视频buffer。应用通过此接口获取视频缓存区及时间戳等信息。buffer使用完成后，调用OH_AVScreenCapture_ReleaseVideoBuffer接口进行视频buffer的释放。从API version 12开始，推荐使用接口[OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable)替代。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseAudioBuffer(struct OH_AVScreenCapture *capture, OH_AudioCaptureSourceType type)](#oh_avscreencapture_releaseaudiobuffer) | 根据音频类型释放buffer。当某一帧音频buffer使用完成后，调用此接口进行释放对应的音频buffer。从API version 12开始，推荐使用接口[OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable)替代。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseVideoBuffer(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_releasevideobuffer) | 根据视频类型释放buffer。当某一帧视频buffer使用完成后，调用此接口释放对应的视频buffer。从API version 12开始，推荐使用接口[OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable)替代。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCallback(struct OH_AVScreenCapture *capture, struct OH_AVScreenCaptureCallback callback)](#oh_avscreencapture_setcallback) | 设置监听接口，通过设置监听，可以监听到调用过程中的错误信息，以及是否有可用的视频buffer和音频buffer。从API version 12开始，推荐使用接口[OH_AVScreenCapture_SetErrorCallback](capi-native-avscreen-capture-h.md#oh_avscreencapture_seterrorcallback)、[OH_AVScreenCapture_SetDataCallback](capi-native-avscreen-capture-h.md#oh_avscreencapture_setdatacallback)替代。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_Release(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_release) | 释放创建的OH_AVScreenCapture实例，对应[OH_AVScreenCapture_Create](capi-native-avscreen-capture-h.md#oh_avscreencapture_create)。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetMicrophoneEnabled(struct OH_AVScreenCapture *capture, bool isMicrophone)](#oh_avscreencapture_setmicrophoneenabled) | 设置麦克风开关。当isMicrophone为true时，则打开麦克风，通过调用[OH_AVScreenCapture_StartScreenCapture](capi-native-avscreen-capture-h.md#oh_avscreencapture_startscreencapture)和[OH_AVScreenCapture_AcquireAudioBuffer](capi-native-avscreen-capture-h.md#oh_avscreencapture_acquireaudiobuffer)可以正常获取到音频的麦克风原始PCM数据；isMicrophone为false时，获取到的音频数据为无声数据。默认麦克风开关为开启。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetStateCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnStateChange callback, void *userData)](#oh_avscreencapture_setstatecallback) | 设置状态变更处理回调方法，在开始录制前调用。调用该方法设置状态变更处理回调方法，当OH_AVScreenCapture实例发生状态变更时，该状态变更处理回调方法将会被调用。调用该设置方法成功后，在启动录屏时将通过隐私弹窗方式征求用户同意：1. 如果用户同意则开始启动录屏流程，在启动录屏成功后，通过该状态处理回调方法上报[OH_AVScreenCaptureStateCode](capi-native-avscreen-capture-base-h.md#oh_avscreencapturestatecode).OH_SCREEN_CAPTURE_STATE_STARTED状态，告知应用启动录屏成功，并在屏幕显示录屏通知。如果启动录屏失败，则通过该状态处理回调方法上报失败状态信息（如，若麦克风不可用则上报[OH_AVScreenCaptureStateCode](capi-native-avscreen-capture-base-h.md#oh_avscreencapturestatecode).OH_SCREEN_CAPTURE_STATE_MIC_UNAVAILABLE状态），或通过错误处理回调方法[OH_AVScreenCapture_OnError](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onerror)上报错误信息。2. 如果用户拒绝，则终止启动录屏，通过该状态处理回调方法上报[OH_AVScreenCaptureStateCode](capi-native-avscreen-capture-base-h.md#oh_avscreencapturestatecode).OH_SCREEN_CAPTURE_STATE_CANCELED状态，告知应用用户拒绝启动录屏，启动录屏失败。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetDataCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnBufferAvailable callback, void *userData)](#oh_avscreencapture_setdatacallback) | 设置数据处理回调方法，在开始录制前调用。调用该方法设置数据处理回调方法，当OH_AVScreenCapture操作期间有音频或视频数据缓存区可用时，将调用该数据处理回调方法。应用需要在该数据处理回调方法中根据数据类型完成处理麦克风音频、内录音频、视频数据，当该数据处理回调方法返回后数据缓存区将不再有效。调用该方法成功后：1. 当OH_AVScreenCapture操作期间有音视频缓存区可用时，将不再调用通过[OH_AVScreenCapture_SetCallback](capi-native-avscreen-capture-h.md#oh_avscreencapture_setcallback)设置的数据回调方法[OH_AVScreenCaptureOnAudioBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencaptureonaudiobufferavailable)和[OH_AVScreenCaptureOnVideoBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencaptureonvideobufferavailable)。2. 不允许应用调用如下4个方法[OH_AVScreenCapture_AcquireAudioBuffer](capi-native-avscreen-capture-h.md#oh_avscreencapture_acquireaudiobuffer)、[OH_AVScreenCapture_ReleaseAudioBuffer](capi-native-avscreen-capture-h.md#oh_avscreencapture_releaseaudiobuffer)、[OH_AVScreenCapture_AcquireVideoBuffer](capi-native-avscreen-capture-h.md#oh_avscreencapture_acquirevideobuffer)和[OH_AVScreenCapture_ReleaseVideoBuffer](capi-native-avscreen-capture-h.md#oh_avscreencapture_releasevideobuffer)，直接返回失败。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetErrorCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnError callback, void *userData)](#oh_avscreencapture_seterrorcallback) | 设置错误处理回调方法，在开始录制前调用。调用该方法设置错误处理回调方法，当OH_AVScreenCapture实例发生错误时，该错误处理回调方法将会被调用。调用该设置方法成功后，当OH_AVScreenCapture实例发生错误时，将不再调用通过[OH_AVScreenCapture_SetCallback](capi-native-avscreen-capture-h.md#oh_avscreencapture_setcallback)设置的错误处理回调方法[OH_AVScreenCaptureOnError](capi-native-avscreen-capture-base-h.md#oh_avscreencaptureonerror)。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureContentChangedCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnCaptureContentChanged callback, void *userData)](#oh_avscreencapture_setcapturecontentchangedcallback) | 设置录屏内容变更回调事件，需在录屏启动前被调用。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StartScreenCaptureWithSurface(struct OH_AVScreenCapture *capture, OHNativeWindow *window)](#oh_avscreencapture_startscreencapturewithsurface) | 使用Surface模式录屏。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCanvasRotation(struct OH_AVScreenCapture *capture, bool canvasRotation)](#oh_avscreencapture_setcanvasrotation) | 设置录屏屏幕数据旋转。调用该方法可以设置录屏屏幕数据是否旋转，当canvasRotation为true时，打开录屏屏幕数据旋转功能，录制的屏幕数据保持正向。默认为false。 |
| [struct OH_AVScreenCapture_ContentFilter *OH_AVScreenCapture_CreateContentFilter(void)](#oh_avscreencapture_createcontentfilter) | 创建ContentFilter。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseContentFilter(struct OH_AVScreenCapture_ContentFilter *filter)](#oh_avscreencapture_releasecontentfilter) | 释放ContentFilter。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ContentFilter_AddAudioContent(struct OH_AVScreenCapture_ContentFilter *filter, OH_AVScreenCaptureFilterableAudioContent content)](#oh_avscreencapture_contentfilter_addaudiocontent) | 向ContentFilter实例添加可过滤的声音类型。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ExcludeContent(struct OH_AVScreenCapture *capture, struct OH_AVScreenCapture_ContentFilter *filter)](#oh_avscreencapture_excludecontent) | 设置OH_AVScreenCapture实例的内容过滤器ContentFilter。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ContentFilter_AddWindowContent(struct OH_AVScreenCapture_ContentFilter *filter, int32_t *windowIDs, int32_t windowCount)](#oh_avscreencapture_contentfilter_addwindowcontent) | 向ContentFilter实例添加可被过滤的窗口ID列表。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ResizeCanvas(struct OH_AVScreenCapture *capture, int32_t width, int32_t height)](#oh_avscreencapture_resizecanvas) | 调整屏幕的分辨率。调用该方法可以设置录屏屏幕数据的分辨率，width为屏幕的宽度，height为屏幕的高度。该接口目前仅支持录屏取码流的场景，不支持录屏存文件的场景。并且调用该接口的调用者以及视频数据的消费者需要确保自身能够支持收到的视频数据分辨率发生变化。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SkipPrivacyMode(struct OH_AVScreenCapture *capture, int32_t *windowIDs, int32_t windowCount)](#oh_avscreencapture_skipprivacymode) | 录屏时豁免隐私窗口。调用该方法可以豁免隐私窗口，windowIDs为需要豁免的隐私窗口ID指针，windowCount 为隐私窗口ID列表的长度，目前豁免需要传入所有隐私子窗口和主窗口ID。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetMaxVideoFrameRate(struct OH_AVScreenCapture *capture, int32_t frameRate)](#oh_avscreencapture_setmaxvideoframerate) | 设置录屏时的最大帧率。该接口应在录屏启动之后被调用。调用该方法可以设置录屏时的最大帧率，frameRate为想要设置的最大帧率。该接口设置最大帧率时，实际设置的帧率受限设备的能力，由底层的系统能力决定。调用该接口设置录屏最大帧率时，实际帧率将受限于设备能力。目前接口入参的最大值不设限制，但当前支持的最高帧率为60FPS，当入参设置超过60FPS，将以60FPS处理。不超过上限时，则按照实际入参值处理。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ShowCursor(struct OH_AVScreenCapture *capture, bool showCursor)](#oh_avscreencapture_showcursor) | 设置光标显示开关。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureArea(struct OH_AVScreenCapture *capture, uint64_t displayId, OH_Rect* area)](#oh_avscreencapture_setcapturearea) | 设置或更新捕获区域。接口在开始录屏前后都可以设置，设置的坐标和宽高不能为负数，捕获区域不能跨屏幕，区域位置设置失败后仍按照上一次的区域进行捕获。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureAreaHighlight(struct OH_AVScreenCapture *capture, OH_AVScreenCaptureHighlightConfig config)](#oh_avscreencapture_setcaptureareahighlight) | 设置屏幕捕获区域高亮模式。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetSelectionCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnUserSelected callback, void *userData)](#oh_avscreencapture_setselectioncallback) | 注册手工确认界面用户选择结果的回调，需在录屏启动前被调用。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetCaptureTypeSelected(OH_AVScreenCapture_UserSelectionInfo *selection, int32_t* type)](#oh_avscreencapture_getcapturetypeselected) | 获取用户在确认界面选择的屏幕捕获对象类型。在[OH_AVScreenCapture_OnUserSelected](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onuserselected)回调中使用，selection指针在回调结束后销毁。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetDisplayIdSelected(OH_AVScreenCapture_UserSelectionInfo *selection, uint64_t* displayId)](#oh_avscreencapture_getdisplayidselected) | 获取确认页面，用户选择录制的屏幕ID。在[OH_AVScreenCapture_OnUserSelected](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onuserselected)回调中使用，selection指针在回调结束后销毁。 |
| [OH_AVScreenCapture_CaptureStrategy* OH_AVScreenCapture_CreateCaptureStrategy(void)](#oh_avscreencapture_createcapturestrategy) | 创建录屏策略对象。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseCaptureStrategy(OH_AVScreenCapture_CaptureStrategy* strategy)](#oh_avscreencapture_releasecapturestrategy) | 释放录屏策略对象。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureStrategy( 
	struct OH_AVScreenCapture *capture, OH_AVScreenCapture_CaptureStrategy *strategy)](#oh_avscreencapture_setcapturestrategy) | 给指定的OH_AVScreenCapture实例设置捕获策略。该接口应在录屏启动之前被调用。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForKeepCaptureDuringCall( OH_AVScreenCapture_CaptureStrategy *strategy, bool value)](#oh_avscreencapture_strategyforkeepcaptureduringcall) | 向CaptureStrategy实例设置蜂窝通话时是否保持录屏。value设置为true时并且录屏时接听蜂窝通话的过程中，出于隐私要求，双方通话的声音（本地麦克风和对方说话声音）不会被录制，其他系统音录制正常。电话挂断之后，录屏框架恢复麦克风录制。注意，如果挂断电话时录屏应用在后台运行，麦克风录制会启动失败，原因是音频模块不允许后台应用启动麦克风录制。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForPrivacyMaskMode( OH_AVScreenCapture_CaptureStrategy *strategy, int32_t value)](#oh_avscreencapture_strategyforprivacymaskmode) | Set the fill mode for screen capture when a privacy window exists |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForBFramesEncoding( OH_AVScreenCapture_CaptureStrategy *strategy, bool value )](#oh_avscreencapture_strategyforbframesencoding) | 向CaptureStrategy实例设置是否使能B帧编码，用于减小录制文件的大小。B帧视频编码相关的约束和限制可以参考文档{@link B帧视频编码约束和限制}。如果当前不符合B帧视频编码的约束和限制，则正常录制不含B帧的视频，不会返回错误。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForCanvasFollowRotation( OH_AVScreenCapture_CaptureStrategy *strategy, bool value)](#oh_avscreencapture_strategyforcanvasfollowrotation) | 设置屏幕录屏自动跟随旋转配置。设为true，表示跟随屏幕旋转，并在横竖屏旋转后，自动调换虚拟屏尺寸，确保输出画面及时跟随旋转。设置是否自动跟随旋转配置后，在旋转通知后，无需再手动调用[OH_AVScreenCapture_ResizeCanvas](capi-native-avscreen-capture-h.md#oh_avscreencapture_resizecanvas)接口。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForPickerPopUp( OH_AVScreenCapture_CaptureStrategy *strategy, bool value)](#oh_avscreencapture_strategyforpickerpopup) | 设置是否弹出屏幕捕获Picker。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForFillMode( OH_AVScreenCapture_CaptureStrategy *strategy, OH_AVScreenCapture_FillMode mode)](#oh_avscreencapture_strategyforfillmode) | 设置捕获图像在目标区域的填充模式。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetDisplayCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnDisplaySelected callback, void *userData)](#oh_avscreencapture_setdisplaycallback) | 设置获取录屏屏幕Id的回调。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ExcludePickerWindows(struct OH_AVScreenCapture *capture, const int32_t *excludedWindowIDs, uint32_t windowCount)](#oh_avscreencapture_excludepickerwindows) | 在Picker界面中隐藏指定的窗口。在picker界面显示前调用本接口，可对指定窗口进行过滤和隐藏。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetPickerMode(struct OH_AVScreenCapture *capture, OH_CapturePickerMode pickerMode)](#oh_avscreencapture_setpickermode) | 设置Picker显示模式。定义picker中显示的内容类型，模式更改会在下一次调用[OH_AVScreenCapture_PresentPicker](capi-native-avscreen-capture-h.md#oh_avscreencapture_presentpicker) 函数时生效。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_PresentPicker(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_presentpicker) | 录屏开始后，调用该接口再次弹出picker，可动态更新录制源（窗口、屏幕）。更新录制源过程中，原录制流程不中断。通过picker动态更新录制源后，可以按照新的录制源进行录制。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetMultiDisplayCaptureCapability(struct OH_AVScreenCapture *capture, uint64_t *displayIds, size_t count, OH_MultiDisplayCapability *capability)](#oh_avscreencapture_getmultidisplaycapturecapability) | 获取多屏幕录制能力信息，判断用户选择的多个屏幕是否支持联合录制。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetMultiDisplayIdsSelected(OH_AVScreenCapture_UserSelectionInfo *selection, uint64_t **displayIds, size_t *count)](#oh_avscreencapture_getmultidisplayidsselected) | 获取picker页面上用户选择录制的DisplayID列表。在[OH_AVScreenCapture_OnUserSelected](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onuserselected)回调中使用，selection指针在回调结束后销毁。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetPrivacyProtectCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnPrivacyProtect callback, void *userData)](#oh_avscreencapture_setprivacyprotectcallback) | 设置隐私保护回调函数，以便应用程序响应屏幕捕获产生的隐私保护事件。该接口必须在调用开始录屏之前调用。 |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForPause(OH_AVScreenCapture_CaptureStrategy *strategy, bool value)](#oh_avscreencapture_strategyforpause) | Allow to pause screen capture |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_PauseScreenCapture(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_pausescreencapture) | Pause screen capture |
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ResumeScreenCapture(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_resumescreencapture) | Resume screen capture |

## 函数说明

### OH_AVScreenCapture_Create()

```c
struct OH_AVScreenCapture *OH_AVScreenCapture_Create(void)
```

**描述**

实例化对象，创建OH_AVScreenCapture。可以通过调用[OH_AVScreenCapture_Release](capi-native-avscreen-capture-h.md#oh_avscreencapture_release)释放实例。

**起始版本：** 10

**返回：**

| 类型 | 说明 |
| -- | -- |
| [struct OH_AVScreenCapture *](capi-avscreencapture-oh-avscreencapture.md) | 返回一个指向OH_AVScreenCapture实例的指针。 |

### OH_AVScreenCapture_Init()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_Init(struct OH_AVScreenCapture *capture, OH_AVScreenCaptureConfig config)
```

**描述**

初始化[OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md)相关参数，包括下发的音频麦克风采样相关参数（可选）、音频内录采样相关参数、视频分辨率相关参数。录屏存文件场景，应用需要保证视频编码参数、视频采样参数、音频编码参数、音频内录采样参数均合法，音频麦克风采样参数合法（可选）。录屏出码流场景，应用需要保证音频内录采样参数、视频采样参数至少一个合法，音频麦克风采样参数合法（可选）。由于结构体变量在初始化时不会对成员进行初始化，应用必须根据使用场景正确设置各项参数。建议应用先将OH_AVScreenCaptureConfig结构体变量的所有内存字节均设置为0，然后再根据录屏场景设置合法参数。音频采样参数结构体[OH_AudioCaptureInfo](capi-avscreencapture-oh-audiocaptureinfo.md)，若audioSampleRate和audioChannels同时为0，则录屏实例OH_AVScreenCapture将忽略该类型的音频参数，且不采集该类型的音频数据。视频采样参数结构体[OH_VideoCaptureInfo](capi-avscreencapture-oh-videocaptureinfo.md)，若videoFrameWidth和videoFrameHeight同时为0，则录屏实例OH_AVScreenCapture将忽略对应视频参数，且不采集屏幕数据。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | 指向OH_AVScreenCapture实例的指针。 |
| [OH_AVScreenCaptureConfig](capi-avscreencapture-oh-avscreencaptureconfig.md) config | 录屏初始化相关参数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数capture为空指针。<br> AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT：不允许操作，初始化配置失败。 |

### OH_AVScreenCapture_StartScreenCapture()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StartScreenCapture(struct OH_AVScreenCapture *capture)
```

**描述**

开始录屏，采集原始码流。调用后可以通过回调的监听（[OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable)）来监听当前是否有码流的产生,通过回调的监听（[OH_AVScreenCapture_OnStateChange](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onstatechange)）来监听启动状态。通过调用获取音频buffer（[OH_AVScreenCapture_AcquireAudioBuffer](capi-native-avscreen-capture-h.md#oh_avscreencapture_acquireaudiobuffer)）和视频buffer（[OH_AVScreenCapture_AcquireVideoBuffer](capi-native-avscreen-capture-h.md#oh_avscreencapture_acquirevideobuffer)）的接口来获取录屏的原始码流。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to an OH_AVScreenCapture instance |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数capture为空指针。<br> AV_SCREEN_CAPTURE_ERR_UNSUPPORT（API version 20新增）：设备不支持该操作。<br> AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT：不允许操作，设置隐私权限启用失败或启动录屏失败。 |

### OH_AVScreenCapture_StopScreenCapture()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StopScreenCapture(struct OH_AVScreenCapture *capture)
```

**描述**

结束录屏，与[OH_AVScreenCapture_StartScreenCapture](capi-native-avscreen-capture-h.md#oh_avscreencapture_startscreencapture)配合使用。调用后针对调用该接口的应用会停止录屏或屏幕共享，释放麦克风。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | 指向OH_AVScreenCapture实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数capture为空指针。<br> AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT：不允许操作，结束录屏失败。 |

### OH_AVScreenCapture_StartScreenRecording()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StartScreenRecording(struct OH_AVScreenCapture *capture)
```

**描述**

启动录屏，调用此接口，可保存录屏文件。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to an OH_AVScreenCapture instance |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数capture为空指针。<br> AV_SCREEN_CAPTURE_ERR_UNSUPPORT（API version 20新增）：设备不支持该操作。<br> AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT：不允许操作，设置隐私权限启用失败或启用屏幕录制失败。 |

### OH_AVScreenCapture_StopScreenRecording()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StopScreenRecording(struct OH_AVScreenCapture *capture)
```

**描述**

停止录屏，与[OH_AVScreenCapture_StartScreenRecording](capi-native-avscreen-capture-h.md#oh_avscreencapture_startscreenrecording)配合使用。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | 指向OH_AVScreenCapture实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数capture为空指针。<br> AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT：不允许操作，停止屏幕录制失败。 |

### OH_AVScreenCapture_AcquireAudioBuffer()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_AcquireAudioBuffer(struct OH_AVScreenCapture *capture, OH_AudioBuffer **audiobuffer, OH_AudioCaptureSourceType type)
```

**描述**

获取音频buffer。应用调用时需分配audiobuffer对应结构体大小的内存，否则影响音频buffer的获取。从API version 12开始，推荐使用接口[OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable)替代。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | 指向OH_AVScreenCapture实例的指针。 |
| [OH_AudioBuffer](capi-avscreencapture-oh-audiobuffer.md) **audiobuffer | 保存音频buffer的结构体，通过该结构体获取到音频buffer以及buffer的时间戳等信息。 |
| [OH_AudioCaptureSourceType](capi-native-avscreen-capture-base-h.md#oh_audiocapturesourcetype) type | 音频buffer的类型，区分是麦克风录制的外部流还是系统内部播放音频的内录流。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数capture为空指针或输入参数audiobuffer为空指针。<br> AV_SCREEN_CAPTURE_ERR_NO_MEMORY：内存不足，audiobuffer分配失败。<br> AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT：不允许操作，设置隐私权限启用失败或获取音频buffer失败。 |

### OH_AVScreenCapture_AcquireVideoBuffer()

```c
OH_NativeBuffer* OH_AVScreenCapture_AcquireVideoBuffer(struct OH_AVScreenCapture *capture, int32_t *fence, int64_t *timestamp, struct OH_Rect *region)
```

**描述**

获取视频buffer。应用通过此接口获取视频缓存区及时间戳等信息。buffer使用完成后，调用OH_AVScreenCapture_ReleaseVideoBuffer接口进行视频buffer的释放。从API version 12开始，推荐使用接口[OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable)替代。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | 指向OH_AVScreenCapture实例的指针。 |
| int32_t *fence | 用于同步的显示相关参数信息。 |
| int64_t *timestamp | 视频帧的时间戳。 |
| [struct OH_Rect](capi-avscreencapture-oh-rect.md) *region | 视频显示相关的坐标信息。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_NativeBuffer*](capi-avscreencapture-oh-nativebuffer.md) | 执行成功返回OH_NativeBuffer对象，通过OH_NativeBuffer对象相关接口可以获取到视频buffer和分辨率等信息参数。 |

### OH_AVScreenCapture_ReleaseAudioBuffer()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseAudioBuffer(struct OH_AVScreenCapture *capture, OH_AudioCaptureSourceType type)
```

**描述**

根据音频类型释放buffer。当某一帧音频buffer使用完成后，调用此接口进行释放对应的音频buffer。从API version 12开始，推荐使用接口[OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable)替代。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | 指向OH_AVScreenCapture实例的指针。 |
| [OH_AudioCaptureSourceType](capi-native-avscreen-capture-base-h.md#oh_audiocapturesourcetype) type | 音频buffer的类型，区分麦克风录制的外部流还是系统内部播放音频的内录流。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数capture为空指针。<br> AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT：不允许操作，不允许用于已设置过DataCallback或释放音频buffer失败。 |

### OH_AVScreenCapture_ReleaseVideoBuffer()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseVideoBuffer(struct OH_AVScreenCapture *capture)
```

**描述**

根据视频类型释放buffer。当某一帧视频buffer使用完成后，调用此接口释放对应的视频buffer。从API version 12开始，推荐使用接口[OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable)替代。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | 指向OH_AVScreenCapture实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数capture为空指针。<br> AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT：不允许操作，不允许用于已设置过DataCallback或释放视频buffer失败。 |

### OH_AVScreenCapture_SetCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCallback(struct OH_AVScreenCapture *capture, struct OH_AVScreenCaptureCallback callback)
```

**描述**

设置监听接口，通过设置监听，可以监听到调用过程中的错误信息，以及是否有可用的视频buffer和音频buffer。从API version 12开始，推荐使用接口[OH_AVScreenCapture_SetErrorCallback](capi-native-avscreen-capture-h.md#oh_avscreencapture_seterrorcallback)、[OH_AVScreenCapture_SetDataCallback](capi-native-avscreen-capture-h.md#oh_avscreencapture_setdatacallback)替代。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | 指向OH_AVScreenCapture实例的指针。 |
| [struct OH_AVScreenCaptureCallback](capi-avscreencapture-oh-avscreencapturecallback.md) callback | OH_AVScreenCaptureCallback的结构体，保存相关回调函数指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数capture为空指针或输入参数callback为空指针。<br> AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT：不允许操作，设置监听接口失败。 |

### OH_AVScreenCapture_Release()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_Release(struct OH_AVScreenCapture *capture)
```

**描述**

释放创建的OH_AVScreenCapture实例，对应[OH_AVScreenCapture_Create](capi-native-avscreen-capture-h.md#oh_avscreencapture_create)。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | 指向OH_AVScreenCapture实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数capture为空指针。<br> AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT：不允许操作，OH_AVScreenCapture实例释放失败。 |

### OH_AVScreenCapture_SetMicrophoneEnabled()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetMicrophoneEnabled(struct OH_AVScreenCapture *capture, bool isMicrophone)
```

**描述**

设置麦克风开关。当isMicrophone为true时，则打开麦克风，通过调用[OH_AVScreenCapture_StartScreenCapture](capi-native-avscreen-capture-h.md#oh_avscreencapture_startscreencapture)和[OH_AVScreenCapture_AcquireAudioBuffer](capi-native-avscreen-capture-h.md#oh_avscreencapture_acquireaudiobuffer)可以正常获取到音频的麦克风原始PCM数据；isMicrophone为false时，获取到的音频数据为无声数据。默认麦克风开关为开启。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | 指向OH_AVScreenCapture实例的指针。 |
| bool isMicrophone | 麦克风开关参数。true表示打开麦克风，false表示关闭麦克风。默认是true。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数capture为空指针。<br> AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT：不允许操作，设置麦克风开关失败。 |

### OH_AVScreenCapture_SetStateCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetStateCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnStateChange callback, void *userData)
```

**描述**

设置状态变更处理回调方法，在开始录制前调用。调用该方法设置状态变更处理回调方法，当OH_AVScreenCapture实例发生状态变更时，该状态变更处理回调方法将会被调用。调用该设置方法成功后，在启动录屏时将通过隐私弹窗方式征求用户同意：1. 如果用户同意则开始启动录屏流程，在启动录屏成功后，通过该状态处理回调方法上报[OH_AVScreenCaptureStateCode](capi-native-avscreen-capture-base-h.md#oh_avscreencapturestatecode).OH_SCREEN_CAPTURE_STATE_STARTED状态，告知应用启动录屏成功，并在屏幕显示录屏通知。如果启动录屏失败，则通过该状态处理回调方法上报失败状态信息（如，若麦克风不可用则上报[OH_AVScreenCaptureStateCode](capi-native-avscreen-capture-base-h.md#oh_avscreencapturestatecode).OH_SCREEN_CAPTURE_STATE_MIC_UNAVAILABLE状态），或通过错误处理回调方法[OH_AVScreenCapture_OnError](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onerror)上报错误信息。2. 如果用户拒绝，则终止启动录屏，通过该状态处理回调方法上报[OH_AVScreenCaptureStateCode](capi-native-avscreen-capture-base-h.md#oh_avscreencapturestatecode).OH_SCREEN_CAPTURE_STATE_CANCELED状态，告知应用用户拒绝启动录屏，启动录屏失败。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | 指向OH_AVScreenCapture实例的指针。 |
| [OH_AVScreenCapture_OnStateChange](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onstatechange) callback | 指向状态处理回调方法实例的指针。 |
| void *userData | 指向应用提供的自定义数据的指针，在状态处理回调方法被调用时作为入参回传。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数capture为空指针或输入参数callback为空指针。<br> AV_SCREEN_CAPTURE_ERR_NO_MEMORY：内存不足，内存分配失败。<br> AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT：不允许操作，设置StateCallback失败。 |

### OH_AVScreenCapture_SetDataCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetDataCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnBufferAvailable callback, void *userData)
```

**描述**

设置数据处理回调方法，在开始录制前调用。调用该方法设置数据处理回调方法，当OH_AVScreenCapture操作期间有音频或视频数据缓存区可用时，将调用该数据处理回调方法。应用需要在该数据处理回调方法中根据数据类型完成处理麦克风音频、内录音频、视频数据，当该数据处理回调方法返回后数据缓存区将不再有效。调用该方法成功后：1. 当OH_AVScreenCapture操作期间有音视频缓存区可用时，将不再调用通过[OH_AVScreenCapture_SetCallback](capi-native-avscreen-capture-h.md#oh_avscreencapture_setcallback)设置的数据回调方法[OH_AVScreenCaptureOnAudioBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencaptureonaudiobufferavailable)和[OH_AVScreenCaptureOnVideoBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencaptureonvideobufferavailable)。2. 不允许应用调用如下4个方法[OH_AVScreenCapture_AcquireAudioBuffer](capi-native-avscreen-capture-h.md#oh_avscreencapture_acquireaudiobuffer)、[OH_AVScreenCapture_ReleaseAudioBuffer](capi-native-avscreen-capture-h.md#oh_avscreencapture_releaseaudiobuffer)、[OH_AVScreenCapture_AcquireVideoBuffer](capi-native-avscreen-capture-h.md#oh_avscreencapture_acquirevideobuffer)和[OH_AVScreenCapture_ReleaseVideoBuffer](capi-native-avscreen-capture-h.md#oh_avscreencapture_releasevideobuffer)，直接返回失败。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | 指向OH_AVScreenCapture实例的指针。 |
| [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) callback | 指向数据处理回调方法实例的指针。 |
| void *userData | 指向应用提供的自定义数据的指针，在数据处理回调方法被调用时作为入参回传。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数capture为空指针或输入参数callback为空指针。<br> AV_SCREEN_CAPTURE_ERR_NO_MEMORY：内存不足，内存分配失败。<br> AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT：不允许操作，设置DataCallback失败。 |

### OH_AVScreenCapture_SetErrorCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetErrorCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnError callback, void *userData)
```

**描述**

设置错误处理回调方法，在开始录制前调用。调用该方法设置错误处理回调方法，当OH_AVScreenCapture实例发生错误时，该错误处理回调方法将会被调用。调用该设置方法成功后，当OH_AVScreenCapture实例发生错误时，将不再调用通过[OH_AVScreenCapture_SetCallback](capi-native-avscreen-capture-h.md#oh_avscreencapture_setcallback)设置的错误处理回调方法[OH_AVScreenCaptureOnError](capi-native-avscreen-capture-base-h.md#oh_avscreencaptureonerror)。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | 指向OH_AVScreenCapture实例的指针。 |
| [OH_AVScreenCapture_OnError](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onerror) callback | 指向错误处理回调方法实例的指针。 |
| void *userData | 指向应用提供的自定义数据的指针，在错误处理回调方法被调用时作为入参回传。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数capture为空指针或输入参数callback为空指针。<br> AV_SCREEN_CAPTURE_ERR_NO_MEMORY：内存不足，内存分配失败。<br> AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT：不允许操作，设置ErrorCallback失败。 |

### OH_AVScreenCapture_SetCaptureContentChangedCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureContentChangedCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnCaptureContentChanged callback, void *userData)
```

**描述**

设置录屏内容变更回调事件，需在录屏启动前被调用。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | 指向OH_AVScreenCapture实例的指针。 |
| [OH_AVScreenCapture_OnCaptureContentChanged](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_oncapturecontentchanged) callback | 指向录屏内容变更回调方法实例的指针。 |
| void *userData | 指向应用提供的自定义数据的指针，在错误处理回调方法被调用时作为入参回传。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：操作成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：参数无效，输入参数capture或callback为空指针。<br> AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT：不允许操作，设置录屏内容回调失败。 |

### OH_AVScreenCapture_StartScreenCaptureWithSurface()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StartScreenCaptureWithSurface(struct OH_AVScreenCapture *capture, OHNativeWindow *window)
```

**描述**

使用Surface模式录屏。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to an OH_AVScreenCapture instance. |
| OHNativeWindow *window | Pointer to an OHNativeWindow instance. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数capture为空指针或输入参数window为空指针或window指向的windowSurface为空指针。<br> AV_SCREEN_CAPTURE_ERR_UNSUPPORT（API version 20新增）：设备不支持该操作。<br> AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT：不允许操作，设置隐私权限启用失败或启动ScreenCaptureWithSurface失败。 |

### OH_AVScreenCapture_SetCanvasRotation()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCanvasRotation(struct OH_AVScreenCapture *capture, bool canvasRotation)
```

**描述**

设置录屏屏幕数据旋转。调用该方法可以设置录屏屏幕数据是否旋转，当canvasRotation为true时，打开录屏屏幕数据旋转功能，录制的屏幕数据保持正向。默认为false。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to an OH_AVScreenCapture instance |
| bool canvasRotation | whether to rotate the canvas |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数capture为空指针。<br> AV_SCREEN_CAPTURE_ERR_UNSUPPORT（API version 20新增）：设备不支持该操作。<br> AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT：不允许操作，设置录屏屏幕数据旋转失败。 |

### OH_AVScreenCapture_CreateContentFilter()

```c
struct OH_AVScreenCapture_ContentFilter *OH_AVScreenCapture_CreateContentFilter(void)
```

**描述**

创建ContentFilter。

**起始版本：** 12

**返回：**

| 类型 | 说明 |
| -- | -- |
| [struct OH_AVScreenCapture_ContentFilter *](capi-avscreencapture-oh-avscreencapture-contentfilter.md) | 执行成功返回OH_AVScreenCapture_ContentFilter实例，否则返回空指针。 |

### OH_AVScreenCapture_ReleaseContentFilter()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseContentFilter(struct OH_AVScreenCapture_ContentFilter *filter)
```

**描述**

释放ContentFilter。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture_ContentFilter](capi-avscreencapture-oh-avscreencapture-contentfilter.md) *filter | 指向OH_AVScreenCapture_ContentFilter实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数filter为空指针。 |

### OH_AVScreenCapture_ContentFilter_AddAudioContent()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ContentFilter_AddAudioContent(struct OH_AVScreenCapture_ContentFilter *filter, OH_AVScreenCaptureFilterableAudioContent content)
```

**描述**

向ContentFilter实例添加可过滤的声音类型。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture_ContentFilter](capi-avscreencapture-oh-avscreencapture-contentfilter.md) *filter | 指向OH_AVScreenCapture_ContentFilter实例的指针。 |
| [OH_AVScreenCaptureFilterableAudioContent](capi-native-avscreen-capture-base-h.md#oh_avscreencapturefilterableaudiocontent) content | OH_AVScreenCaptureFilterableAudioContent实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数filter为空指针或输入参数content无效。 |

### OH_AVScreenCapture_ExcludeContent()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ExcludeContent(struct OH_AVScreenCapture *capture, struct OH_AVScreenCapture_ContentFilter *filter)
```

**描述**

设置OH_AVScreenCapture实例的内容过滤器ContentFilter。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | 指向OH_AVScreenCapture实例的指针。 |
| [struct OH_AVScreenCapture_ContentFilter](capi-avscreencapture-oh-avscreencapture-contentfilter.md) *filter | 指向OH_AVScreenCapture_ContentFilter实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数capture为空指针或输入参数filter为空指针。<br> AV_SCREEN_CAPTURE_ERR_UNSUPPORT：操作不支持。对于流，启动时应该调用AudioCapturer接口。<br> 对于capture文件，启动时调用Recorder接口。 |

### OH_AVScreenCapture_ContentFilter_AddWindowContent()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ContentFilter_AddWindowContent(struct OH_AVScreenCapture_ContentFilter *filter, int32_t *windowIDs, int32_t windowCount)
```

**描述**

向ContentFilter实例添加可被过滤的窗口ID列表。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture_ContentFilter](capi-avscreencapture-oh-avscreencapture-contentfilter.md) *filter | 指向OH_AVScreenCapture_ContentFilter实例的指针。 |
| int32_t *windowIDs | 指向窗口ID的指针。 |
| int32_t windowCount | 窗口ID列表的长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | 执行成功返回AV_SCREEN_CAPTURE_ERR_OK，否则返回具体错误码。 |

### OH_AVScreenCapture_ResizeCanvas()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ResizeCanvas(struct OH_AVScreenCapture *capture, int32_t width, int32_t height)
```

**描述**

调整屏幕的分辨率。调用该方法可以设置录屏屏幕数据的分辨率，width为屏幕的宽度，height为屏幕的高度。该接口目前仅支持录屏取码流的场景，不支持录屏存文件的场景。并且调用该接口的调用者以及视频数据的消费者需要确保自身能够支持收到的视频数据分辨率发生变化。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to an OH_AVScreenCapture instance |
| int32_t width | Video frame width of avscreeencapture, in px. |
| int32_t height | Video frame height of avscreeencapture, in px. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数capture为空指针。<br> AV_SCREEN_CAPTURE_ERR_UNSUPPORT（API version 20新增）：设备不支持该操作。<br> AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT：不允许操作。 |

### OH_AVScreenCapture_SkipPrivacyMode()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SkipPrivacyMode(struct OH_AVScreenCapture *capture, int32_t *windowIDs, int32_t windowCount)
```

**描述**

录屏时豁免隐私窗口。调用该方法可以豁免隐私窗口，windowIDs为需要豁免的隐私窗口ID指针，windowCount 为隐私窗口ID列表的长度，目前豁免需要传入所有隐私子窗口和主窗口ID。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to an OH_AVScreenCapture instance |
| int32_t *windowIDs | Pointer of windowID list |
| int32_t windowCount | length of windowID list |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数capture为空指针。<br> AV_SCREEN_CAPTURE_ERR_UNSUPPORT（API version 20新增）：设备不支持该操作。<br> AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT：不允许操作。 |

### OH_AVScreenCapture_SetMaxVideoFrameRate()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetMaxVideoFrameRate(struct OH_AVScreenCapture *capture, int32_t frameRate)
```

**描述**

设置录屏时的最大帧率。该接口应在录屏启动之后被调用。调用该方法可以设置录屏时的最大帧率，frameRate为想要设置的最大帧率。该接口设置最大帧率时，实际设置的帧率受限设备的能力，由底层的系统能力决定。调用该接口设置录屏最大帧率时，实际帧率将受限于设备能力。目前接口入参的最大值不设限制，但当前支持的最高帧率为60FPS，当入参设置超过60FPS，将以60FPS处理。不超过上限时，则按照实际入参值处理。

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to an OH_AVScreenCapture instance |
| int32_t frameRate | max frame rate of video, in fps. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数capture为空指针或者输入参数frameRate不支持。<br> AV_SCREEN_CAPTURE_ERR_UNSUPPORT（API version 20新增）：设备不支持该操作。<br> AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT：不允许操作。 |

### OH_AVScreenCapture_ShowCursor()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ShowCursor(struct OH_AVScreenCapture *capture, bool showCursor)
```

**描述**

设置光标显示开关。

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to an OH_AVScreenCapture instance |
| bool showCursor | The switch of the cursor |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数capture为空指针。<br> AV_SCREEN_CAPTURE_ERR_UNSUPPORT（API version 20新增）：设备不支持该操作。<br> AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT：不允许操作，设置光标失败。 |

### OH_AVScreenCapture_SetCaptureArea()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureArea(struct OH_AVScreenCapture *capture, uint64_t displayId, OH_Rect* area)
```

**描述**

设置或更新捕获区域。接口在开始录屏前后都可以设置，设置的坐标和宽高不能为负数，捕获区域不能跨屏幕，区域位置设置失败后仍按照上一次的区域进行捕获。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | capture Pointer to an OH_AVScreenCapture instance |
| uint64_t displayId | Indicates the screen index for setting area recording |
| [OH_Rect](capi-avscreencapture-oh-rect.md)* area | Pointer to an object describing the location and size of the region |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数capture为空指针、输入displayId不存在或输入的捕获区域异常。 |

### OH_AVScreenCapture_SetCaptureAreaHighlight()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureAreaHighlight(struct OH_AVScreenCapture *capture, OH_AVScreenCaptureHighlightConfig config)
```

**描述**

设置屏幕捕获区域高亮模式。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to OH_AVScreenCapture which want to set highlight style. |
| [OH_AVScreenCaptureHighlightConfig](capi-avscreencapture-oh-avscreencapturehighlightconfig.md) config | the highlight parameters are to be set for this screen capture. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数capture为空指针或者config参数值无效。 |

### OH_AVScreenCapture_SetSelectionCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetSelectionCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnUserSelected callback, void *userData)
```

**描述**

注册手工确认界面用户选择结果的回调，需在录屏启动前被调用。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to OH_AVScreenCapture which want to handle user selection info |
| [OH_AVScreenCapture_OnUserSelected](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onuserselected) callback | user selection callback function, see [OH_AVScreenCapture_OnUserSelected](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onuserselected) |
| void *userData | The control block pointer passed by the application is carried to the application when it isreturned |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数capture为空指针。 |

### OH_AVScreenCapture_GetCaptureTypeSelected()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetCaptureTypeSelected(OH_AVScreenCapture_UserSelectionInfo *selection, int32_t* type)
```

**描述**

获取用户在确认界面选择的屏幕捕获对象类型。在[OH_AVScreenCapture_OnUserSelected](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onuserselected)回调中使用，selection指针在回调结束后销毁。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVScreenCapture_UserSelectionInfo](capi-avscreencapture-oh-avscreencapture-userselectioninfo.md) *selection | Pointer to an OH_AVScreenCapture_UserSelectionInfo instance |
| int32_t* type | The capture object type selected by the user,0: represents the screen, 1: represents the window, 2: represents the app. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数selection为空指针。 |

### OH_AVScreenCapture_GetDisplayIdSelected()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetDisplayIdSelected(OH_AVScreenCapture_UserSelectionInfo *selection, uint64_t* displayId)
```

**描述**

获取确认页面，用户选择录制的屏幕ID。在[OH_AVScreenCapture_OnUserSelected](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onuserselected)回调中使用，selection指针在回调结束后销毁。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVScreenCapture_UserSelectionInfo](capi-avscreencapture-oh-avscreencapture-userselectioninfo.md) *selection | Pointer to an OH_AVScreenCapture_UserSelectionInfo instance |
| uint64_t* displayId | Returns the screen ID value selected by the user |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数selection为空指针。 |

### OH_AVScreenCapture_CreateCaptureStrategy()

```c
OH_AVScreenCapture_CaptureStrategy* OH_AVScreenCapture_CreateCaptureStrategy(void)
```

**描述**

创建录屏策略对象。

**起始版本：** 20

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVScreenCapture_CaptureStrategy*](capi-avscreencapture-oh-avscreencapture-capturestrategy.md) | 执行成功返回OH_AVScreenCapture_CaptureStrategy实例，否则返回空指针。 |

### OH_AVScreenCapture_ReleaseCaptureStrategy()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseCaptureStrategy(OH_AVScreenCapture_CaptureStrategy* strategy)
```

**描述**

释放录屏策略对象。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md)* strategy | Pointer to an OH_AVScreenCapture_CaptureStrategy instance |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数strategy为空指针。 |

### OH_AVScreenCapture_SetCaptureStrategy()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureStrategy( 
	struct OH_AVScreenCapture *capture, OH_AVScreenCapture_CaptureStrategy *strategy)
```

**描述**

给指定的OH_AVScreenCapture实例设置捕获策略。该接口应在录屏启动之前被调用。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to an OH_AVScreenCapture which need to be setted. |
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md) *strategy | Pointer to an OH_AVScreenCapture_CaptureStrategy which want toset. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数capture或strategy为空指针。<br> AV_SCREEN_CAPTURE_ERR_INVALID_STATE：在录屏启动之后调用该接口。 |

### OH_AVScreenCapture_StrategyForKeepCaptureDuringCall()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForKeepCaptureDuringCall( OH_AVScreenCapture_CaptureStrategy *strategy, bool value)
```

**描述**

向CaptureStrategy实例设置蜂窝通话时是否保持录屏。value设置为true时并且录屏时接听蜂窝通话的过程中，出于隐私要求，双方通话的声音（本地麦克风和对方说话声音）不会被录制，其他系统音录制正常。电话挂断之后，录屏框架恢复麦克风录制。注意，如果挂断电话时录屏应用在后台运行，麦克风录制会启动失败，原因是音频模块不允许后台应用启动麦克风录制。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md) *strategy | Pointer to an OH_AVScreenCapture_CaptureStrategy instance |
| bool value | The default value is false, which means that screen recording is not allowed during cellularcalls. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数strategy为空指针。 |

### OH_AVScreenCapture_StrategyForPrivacyMaskMode()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForPrivacyMaskMode( OH_AVScreenCapture_CaptureStrategy *strategy, int32_t value)
```

**描述**

Set the fill mode for screen capture when a privacy window exists

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md) *strategy | Pointer to an OH_AVScreenCapture_CaptureStrategy instance |
| int32_t value | If set to 0, it means that when there is a privacy window interface, the output screen image is completely black. If set to 1, it means that when there is a privacy window interface, only the privacy window area of 鈥嬧�媡he output screen becomes black, and other values returns an error. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | Function result code.<br>         {@link AV_SCREEN_CAPTURE_ERR_OK} if the execution is successful.<br>         {@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL} strategy is nullptr or  value is invalid. |

### OH_AVScreenCapture_StrategyForBFramesEncoding()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForBFramesEncoding( OH_AVScreenCapture_CaptureStrategy *strategy, bool value )
```

**描述**

向CaptureStrategy实例设置是否使能B帧编码，用于减小录制文件的大小。B帧视频编码相关的约束和限制可以参考文档{@link B帧视频编码约束和限制}。如果当前不符合B帧视频编码的约束和限制，则正常录制不含B帧的视频，不会返回错误。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md) *strategy | Pointer to an OH_AVScreenCapture_CaptureStrategy instance |
| value | The default value is false, which means B frames  encoding are disabled. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数strategy为空指针。 |

### OH_AVScreenCapture_StrategyForCanvasFollowRotation()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForCanvasFollowRotation( OH_AVScreenCapture_CaptureStrategy *strategy, bool value)
```

**描述**

设置屏幕录屏自动跟随旋转配置。设为true，表示跟随屏幕旋转，并在横竖屏旋转后，自动调换虚拟屏尺寸，确保输出画面及时跟随旋转。设置是否自动跟随旋转配置后，在旋转通知后，无需再手动调用[OH_AVScreenCapture_ResizeCanvas](capi-native-avscreen-capture-h.md#oh_avscreencapture_resizecanvas)接口。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md) *strategy | Pointer to an OH_AVScreenCapture_CaptureStrategy instance |
| bool value | The default value is False, which means that the width and height of the VirtualDisplayremain the initial settings. If set to True, it means that the width and height of the VirtualDisplay rotateswith the rotation of the screen.. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数strategy为空指针。 |

### OH_AVScreenCapture_StrategyForPickerPopUp()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForPickerPopUp( OH_AVScreenCapture_CaptureStrategy *strategy, bool value)
```

**描述**

设置是否弹出屏幕捕获Picker。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md) *strategy | Pointer to an OH_AVScreenCapture_CaptureStrategy instance |
| valueIf | set to false, it means that the APP don't need to pop up the Picker after screen capture starts;If set to True, the Picker will pop up uniformly after screen capture starts;If not set, it means using the system recommended behavior. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数strategy为空指针或输入value为无效值。 |

### OH_AVScreenCapture_StrategyForFillMode()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForFillMode( OH_AVScreenCapture_CaptureStrategy *strategy, OH_AVScreenCapture_FillMode mode)
```

**描述**

设置捕获图像在目标区域的填充模式。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md) *strategy | Pointer to an OH_AVScreenCapture_CaptureStrategy instance |
| [OH_AVScreenCapture_FillMode](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_fillmode) mode | Value of the captured image fill mode |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数strategy为空指针。 |

### OH_AVScreenCapture_SetDisplayCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetDisplayCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnDisplaySelected callback, void *userData)
```

**描述**

设置获取录屏屏幕Id的回调。

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | 指向OH_AVScreenCapture实例的指针。 |
| OH_AVScreenCapture_OnDisplaySelected callback | 指向录屏屏幕Id回调方法实例的指针。 |
| void *userData | 指向应用提供的自定义数据的指针，在状态处理回调方法被调用时作为入参回传。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数capture为空指针或输入参数callback为空指针。<br> AV_SCREEN_CAPTURE_ERR_NO_MEMORY：内存不足，内存分配失败。<br> AV_SCREEN_CAPTURE_ERR_INVALID_STATE：回调必须在start方法前调用。 |

### OH_AVScreenCapture_ExcludePickerWindows()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ExcludePickerWindows(struct OH_AVScreenCapture *capture, const int32_t *excludedWindowIDs, uint32_t windowCount)
```

**描述**

在Picker界面中隐藏指定的窗口。在picker界面显示前调用本接口，可对指定窗口进行过滤和隐藏。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | 指向OH_AVScreenCapture实例的指针。 |
| const int32_t *excludedWindowIDs | 需要隐藏的窗口ID数组（已存在的窗口）。 |
| uint32_t windowCount | 需要隐藏的窗口ID数组长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数capture为空指针或者窗口ID参数值无效。<br> AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT：不允许操作。 |

### OH_AVScreenCapture_SetPickerMode()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetPickerMode(struct OH_AVScreenCapture *capture, OH_CapturePickerMode pickerMode)
```

**描述**

设置Picker显示模式。定义picker中显示的内容类型，模式更改会在下一次调用[OH_AVScreenCapture_PresentPicker](capi-native-avscreen-capture-h.md#oh_avscreencapture_presentpicker) 函数时生效。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | 指向OH_AVScreenCapture实例的指针。 |
| [OH_CapturePickerMode](capi-native-avscreen-capture-base-h.md#oh_capturepickermode) pickerMode | Picker显示模式（请参阅OH_CapturePickerMode枚举）。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数capture为空指针或者pickerMode参数值无效。<br> AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT：不允许操作。 |

### OH_AVScreenCapture_PresentPicker()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_PresentPicker(struct OH_AVScreenCapture *capture)
```

**描述**

录屏开始后，调用该接口再次弹出picker，可动态更新录制源（窗口、屏幕）。更新录制源过程中，原录制流程不中断。通过picker动态更新录制源后，可以按照新的录制源进行录制。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | 指向OH_AVScreenCapture实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入参数capture为空指针。<br> AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT：不允许操作。 |

### OH_AVScreenCapture_GetMultiDisplayCaptureCapability()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetMultiDisplayCaptureCapability(struct OH_AVScreenCapture *capture, uint64_t *displayIds, size_t count, OH_MultiDisplayCapability *capability)
```

**描述**

获取多屏幕录制能力信息，判断用户选择的多个屏幕是否支持联合录制。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | 指向OH_AVScreenCapture实例的指针。 |
| uint64_t *displayIds | 返回用户选择的DisplayID数组。 |
| size_t count | 返回用户选择的DisplayID的数量。 |
| [OH_MultiDisplayCapability](capi-avscreencapture-oh-multidisplaycapability.md) *capability | 指向OH_MultiDisplayCapability实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：操作执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入的录屏实例参数capture为空指针。<br> AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT：不允许操作，获取数据失败。 |

### OH_AVScreenCapture_GetMultiDisplayIdsSelected()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetMultiDisplayIdsSelected(OH_AVScreenCapture_UserSelectionInfo *selection, uint64_t **displayIds, size_t *count)
```

**描述**

获取picker页面上用户选择录制的DisplayID列表。在[OH_AVScreenCapture_OnUserSelected](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onuserselected)回调中使用，selection指针在回调结束后销毁。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVScreenCapture_UserSelectionInfo](capi-avscreencapture-oh-avscreencapture-userselectioninfo.md) *selection | 指向OH_AVScreenCapture_UserSelectionInfo实例的指针。 |
| uint64_t **displayIds | 返回用户选择的DisplayID数组。参数displayIds的内存由OH_AVScreenCapture_UserSelectionInfo管理，无需手动释放。 |
| size_t *count | 返回用户选择的DisplayID的数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：操作执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入包含用户选择信息的参数selection为空指针。 |

### OH_AVScreenCapture_SetPrivacyProtectCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetPrivacyProtectCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnPrivacyProtect callback, void *userData)
```

**描述**

设置隐私保护回调函数，以便应用程序响应屏幕捕获产生的隐私保护事件。该接口必须在调用开始录屏之前调用。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | 指向OH_AVScreenCapture实例的指针。 |
| [OH_AVScreenCapture_OnPrivacyProtect](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onprivacyprotect) callback | 隐私保护回调函数。 |
| void *userData | 指向应用提供的自定义数据的指针，在状态处理回调方法被调用时作为入参回传。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | AV_SCREEN_CAPTURE_ERR_OK：执行成功。<br> AV_SCREEN_CAPTURE_ERR_INVALID_VAL：输入录屏实例为空指针或输入回调为空指针。 |

### OH_AVScreenCapture_StrategyForPause()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForPause(OH_AVScreenCapture_CaptureStrategy *strategy, bool value)
```

**描述**

Allow to pause screen capture

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md) *strategy | Pointer to an OH_AVScreenCapture_CaptureStrategy instance. |
| bool value | The default value is false, which means that screen recording is not allowed to pause |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | Function result code.<br>         {@link AV_SCREEN_CAPTURE_ERR_OK} if the execution is successful.<br>         {@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL} strategy value is nullptr. |

### OH_AVScreenCapture_PauseScreenCapture()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_PauseScreenCapture(struct OH_AVScreenCapture *capture)
```

**描述**

Pause screen capture

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Initialized screen capture instance. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | Function result code.<br>         {@link AV_SCREEN_CAPTURE_ERR_OK} if the execution is successful.<br>         {@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL} capture value is nullptr.<br>         {@link AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT} operation not permitted. |

### OH_AVScreenCapture_ResumeScreenCapture()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ResumeScreenCapture(struct OH_AVScreenCapture *capture)
```

**描述**

Resume screen capture

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Initialized screen capture instance. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | Function result code.<br>         {@link AV_SCREEN_CAPTURE_ERR_OK} if the execution is successful.<br>         {@link AV_SCREEN_CAPTURE_ERR_INVALID_VAL} capture value is nullptr.<br>         {@link AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT} operation not permitted. |


