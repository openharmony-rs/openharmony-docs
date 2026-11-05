---
kits: ["AVCodec Kit / 音视频编解码服务"]
description: "介绍将编码后的音视频数据按mp4、m4a、flv等格式封装为媒体文件的开发流程，支持音视频轨添加、封面与文件级元数据设置，适用于录像录音、编辑导出与转码保存场景。"
keywords: [媒体数据封装, 封装器, OH_AVMuxer, mp4, m4a, flv, 音视频轨, 封面, 文件元数据]
doctype: guide
status: active
---

# 媒体数据封装

<!--Kit: AVCodec Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @mr-chencxy-->
<!--Designer: @dpy2650--->
<!--Tester: @baotianhao-->
<!--Adviser: @w_Machine_cc-->

开发者可以调用本模块的Native API接口，完成音视频封装，即将音频、视频等编码后的媒体数据，按一定的格式存储到文件里。

当前支持的封装能力请参考AVCodec支持的格式中的[媒体数据封装](avcodec-support-formats.md#媒体数据封装)。

<!--RP2--><!--RP2End-->

**适用场景**

- 录像、录音
  
  保存录像、录音文件时，需要先对音视频流进行编码，再封装为文件。

- 音视频编辑
  
  完成编辑后的音视频，需要封装为文件。

- 音视频转码

  转码后，保存文件时需要封装。

## 开发指导

详细的API说明请参考[native_avmuxer.h](../../reference/apis-avcodec-kit/capi-native-avmuxer-h.md)。

> **说明：**
>
> 如果调用封装模块写本地文件，需要[向用户申请授权](../../security/AccessToken/request-user-authorization.md)：ohos.permission.READ_MEDIA, ohos.permission.WRITE_MEDIA。

### 在 CMake 脚本中链接动态库

``` cmake
target_link_libraries(sample PUBLIC libnative_media_avmuxer.so)
target_link_libraries(sample PUBLIC libnative_media_core.so)
```

示例代码引用了示例工程中自定义的工具宏与数据结构（如CHECK_AND_RETURN_RET_LOG、AVCODEC_SAMPLE_ERR_\*、AVCODEC_SAMPLE_LOG\*、SampleInfo等），不属于SDK的接口，完整定义请参见示例工程，移植时需自行实现或替换。

### mp4格式封装开发步骤

参考以下示例代码，完成音视频封装mp4的全流程。

不同的封装格式需要配置的key请参考AVCodec支持的格式中的[媒体数据封装](avcodec-support-formats.md#媒体数据封装)。

1. 添加头文件。

   ```c++
   #include <multimedia/player_framework/native_avmuxer.h>
   #include <multimedia/player_framework/native_avcodec_base.h>
   #include <multimedia/player_framework/native_avformat.h>
   #include <multimedia/player_framework/native_avbuffer.h>
   #include <fcntl.h>
   ```

2. 调用OH_AVMuxer_Create()创建封装器实例对象。

   <!-- @[Muxer::Create](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/muxer.cpp) -->
   
   ``` C++
   int32_t Muxer::Create(int32_t fd, int32_t outputFormat)
   {
       outputFormat_ = outputFormat;
       muxer_ = OH_AVMuxer_Create(fd, static_cast<OH_AVOutputFormat>(outputFormat));
       CHECK_AND_RETURN_RET_LOG(muxer_ != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "Muxer create failed, fd: %{public}d", fd);
       return AVCODEC_SAMPLE_ERR_OK;
   }
   ```

   示例中封装格式为mp4（AV_OUTPUT_FORMAT_MPEG_4），fd为以读写方式打开的输出文件描述符。

3. （可选）调用OH_AVMuxer_SetRotation()设置旋转角度。

   视频画面需要旋转的时候设置，示例中对mp4格式设置旋转角度，flv格式不支持旋转元数据。

   <!-- @[Muxer::SetRotation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/muxer.cpp) -->
   
   ``` C++
   int32_t Muxer::SetRotation()
   {
       CHECK_AND_RETURN_RET_LOG(muxer_ != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "Muxer is null");
   
       // flv不支持旋转元数据。
       if (outputFormat_ == AV_OUTPUT_FORMAT_FLV) {
           return AVCODEC_SAMPLE_ERR_OK;
       }
       // 由于相机的profile只有1920×1080，没有1080×1920，所以得往文件中封装一个90度的角度信息，后续播放才会是竖屏显示。
       int32_t ret = OH_AVMuxer_SetRotation(muxer_, VERTICAL_ANGLE);
       if (ret != AV_ERR_OK) {
           AVCODEC_SAMPLE_LOGW("Set rotation failed, ret: %{public}d", ret);
       }
       return AVCODEC_SAMPLE_ERR_OK;
   }
   ```

4. 添加文件级数据。

   文件级数据已定义的key详见AVCodec支持的格式中的[媒体数据封装](avcodec-support-formats.md#媒体数据封装)。

   用户自定义的key必须以"com.openharmony."为开头。值类型可以为int32_t、float、string，从API version 20开始增加支持uint8_t*。

   > **说明：**
   >
   > 已定义的key必须在OH_AVMuxer_Start()前设置，用户自定义的key可以在OH_AVMuxer_Stop()前设置。

   ```c++
   OH_AVFormat *format = OH_AVFormat_Create(); // 使用OH_AVFormat_Create创建format。

   // 设置已定义的key。
   OH_AVFormat_SetStringValue(format, OH_MD_KEY_CREATION_TIME, "2024-12-28T00:00:00.000000Z"); // 从API version 14开始支持设置创建时间（使用ISO 8601标准的时间格式且为UTC时间）。
   OH_AVFormat_SetStringValue(format, OH_MD_KEY_COMMENT, "comment test"); // 从API version 20开始支持设置备注。值类型为string。
   OH_AVFormat_SetIntValue(format, OH_MD_KEY_ENABLE_MOOV_FRONT, 1); // 从API version 20开始支持moov box位于mdat box前。默认值为0，设置1代表moov box位于mdat box前。
   OH_AVFormat_SetFloatValue(format, OH_MD_KEY_LATITUDE, 39.9); // 从API version 24开始支持设置纬度，值类型为float，范围为[-90.0, 90.0]。当需要设置地理位置信息时，纬度和经度是必选的，不能仅设置一种。
   OH_AVFormat_SetFloatValue(format, OH_MD_KEY_LONGITUDE, 116.3); // 从API version 24开始支持设置经度，值类型为float，范围为[-180.0, 180.0]。当需要设置地理位置信息时，纬度和经度是必选的，不能仅设置一种。
   OH_AVFormat_SetFloatValue(format, OH_MD_KEY_ALTITUDE, 44.4); // 从API version 24开始支持设置海拔，值类型为float，设置地理位置信息时海拔是可选的。

   // 设置用户自定义key（需要com.openharmony.开头）。
   OH_AVFormat_SetIntValue(format, "com.openharmony.testInt", 1024); // 值类型为int32_t。
   OH_AVFormat_SetFloatValue(format, "com.openharmony.testFloat", 1.024); // 值类型为float。
   OH_AVFormat_SetStringValue(format, "com.openharmony.testString", "string test"); // 值类型为string，长度不超过256个字符。
   uint8_t testData[] = {1, 2, 3};
   OH_AVFormat_SetBuffer(format, "com.openharmony.testBuffer", testData, sizeof(testData)); // 从API version 20开始支持值类型为uint8_t*。

   int ret = OH_AVMuxer_SetFormat(muxer, format); // 设置封装的format。
   if (ret != AV_ERR_OK) {
      // 设置format失败，未找到有效待写入的key数据。
   }
   OH_AVFormat_Destroy(format); // 销毁。
   ```

5. 添加音频轨。

   **方法一：用OH_AVFormat_Create创建format**

   ```c++
   int audioTrackId = -1;
   uint8_t *buffer = ...; // 编码config data，如果没有可以不传。
   size_t size = ...;  // 编码config data的长度，根据实际情况配置。
   OH_AVFormat *formatAudio = OH_AVFormat_Create(); // 使用OH_AVFormat_Create创建format，这里以封装44100Hz采样率、2声道的AAC-LC音频为例。
   OH_AVFormat_SetStringValue(formatAudio, OH_MD_KEY_CODEC_MIME, OH_AVCODEC_MIMETYPE_AUDIO_AAC); // 必填。
   OH_AVFormat_SetIntValue(formatAudio, OH_MD_KEY_AUD_SAMPLE_RATE, 44100); // 必填。
   OH_AVFormat_SetIntValue(formatAudio, OH_MD_KEY_AUD_CHANNEL_COUNT, 2); // 必填。
   OH_AVFormat_SetIntValue(formatAudio, OH_MD_KEY_PROFILE, AAC_PROFILE_LC); // 选填。
   OH_AVFormat_SetBuffer(formatAudio, OH_MD_KEY_CODEC_CONFIG, buffer, size); // 选填。
   
   int ret = OH_AVMuxer_AddTrack(muxer, &audioTrackId, formatAudio);
   if (ret != AV_ERR_OK || audioTrackId < 0) {
       // 音频轨添加失败。
   }
   OH_AVFormat_Destroy(formatAudio); // 销毁。
   ```

   **方法二：用OH_AVFormat_CreateAudioFormat创建format**

   <!-- @[Muxer::AddAudioTrack](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/muxer.cpp) -->
   
   ``` C++
   int32_t Muxer::AddAudioTrack(SampleInfo &sampleInfo)
   {
       CHECK_AND_RETURN_RET_LOG(muxer_ != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "Muxer is null");
   
       // 添加音频轨：用OH_AVFormat_CreateAudioFormat创建format，这里以封装AAC音频为例。
       OH_AVFormat *formatAudio = OH_AVFormat_CreateAudioFormat(sampleInfo.audio.audioCodecMime.data(),
           sampleInfo.audio.audioSampleRate, sampleInfo.audio.audioChannelCount);
       CHECK_AND_RETURN_RET_LOG(formatAudio != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "Create audio format failed");
       // 设置音频profile，选填。
       OH_AVFormat_SetIntValue(formatAudio, OH_MD_KEY_PROFILE, AAC_PROFILE_LC);
       int32_t ret = OH_AVMuxer_AddTrack(muxer_, &audioTrackId_, formatAudio);
       OH_AVFormat_Destroy(formatAudio);
       CHECK_AND_RETURN_RET_LOG(ret == AV_ERR_OK && audioTrackId_ >= 0, AVCODEC_SAMPLE_ERR_ERROR,
           "Add audio track failed, ret: %{public}d", ret);
       return AVCODEC_SAMPLE_ERR_OK;
   }
   ```

6. 添加视频轨。
   > **说明：**
   >
   > - 当开发者需要设置色彩信息时，必须保证OH_MD_KEY_COLOR_PRIMARIES、OH_MD_KEY_TRANSFER_CHARACTERISTICS、OH_MD_KEY_MATRIX_COEFFICIENTS三个key设置的值都在其各自的参数范围内，系统才会识别这是有效色彩信息数据。参数设置范围可参考[OH_ColorPrimary](../../reference/apis-avcodec-kit/capi-native-avcodec-base-h.md#oh_colorprimary)、[OH_TransferCharacteristic](../../reference/apis-avcodec-kit/capi-native-avcodec-base-h.md#oh_transfercharacteristic)和[OH_MatrixCoefficient](../../reference/apis-avcodec-kit/capi-native-avcodec-base-h.md#oh_matrixcoefficient)。
   > - 当开发者输入的色彩信息与视频码流的参数集中的色彩信息不一致时，系统以视频码流中的色彩信息为准。

   **方法一：用OH_AVFormat_Create创建format**

   ```c++
   int videoTrackId = -1;
   uint8_t *buffer = ...; // 编码config data，如果没有可以不传。
   size_t size = ...;  // 编码config data的长度，根据实际情况配置。
   OH_AVFormat *formatVideo = OH_AVFormat_Create();
   OH_AVFormat_SetStringValue(formatVideo, OH_MD_KEY_CODEC_MIME, OH_AVCODEC_MIMETYPE_VIDEO_AVC); // 必填。
   OH_AVFormat_SetIntValue(formatVideo, OH_MD_KEY_WIDTH, 1280); // 必填。
   OH_AVFormat_SetIntValue(formatVideo, OH_MD_KEY_HEIGHT, 720); // 必填。
   OH_AVFormat_SetBuffer(formatVideo, OH_MD_KEY_CODEC_CONFIG, buffer, size); // 选填。
   OH_AVFormat_SetIntValue(formatVideo, OH_MD_KEY_COLOR_PRIMARIES, OH_ColorPrimary::COLOR_PRIMARY_BT709); // 色彩信息，选填。
   OH_AVFormat_SetIntValue(formatVideo, OH_MD_KEY_TRANSFER_CHARACTERISTICS, OH_TransferCharacteristic::TRANSFER_CHARACTERISTIC_BT709); // 色彩信息，选填。
   OH_AVFormat_SetIntValue(formatVideo, OH_MD_KEY_MATRIX_COEFFICIENTS, OH_MatrixCoefficient::MATRIX_COEFFICIENT_BT709); // 色彩信息，选填。
   OH_AVFormat_SetIntValue(formatVideo, OH_MD_KEY_RANGE_FLAG, 1); // 色彩信息，选填。值为0代表limited range，值为1代表full range。
   
   int ret = OH_AVMuxer_AddTrack(muxer, &videoTrackId, formatVideo);
   if (ret != AV_ERR_OK || videoTrackId < 0) {
       // 视频轨添加失败。
   }
   OH_AVFormat_Destroy(formatVideo); // 销毁。
   ```

   **方法二：用OH_AVFormat_CreateVideoFormat创建format**

   <!-- @[Muxer::AddVideoTrack](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/muxer.cpp) -->
   
   ``` C++
   int32_t Muxer::AddVideoTrack(SampleInfo &sampleInfo)
   {
       CHECK_AND_RETURN_RET_LOG(muxer_ != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "Muxer is null");
   
       // 添加视频轨：用OH_AVFormat_CreateVideoFormat创建format。
       int32_t encodedWidth = sampleInfo.video.videoWidth;
       int32_t encodedHeight = sampleInfo.video.videoHeight;
       if (sampleInfo.video.preprocMode == VIDEO_PREPROC_DOWNSAMPLING) {
           encodedWidth = sampleInfo.video.downsamplingWidth;
           encodedHeight = sampleInfo.video.downsamplingHeight;
       } else if (sampleInfo.video.preprocMode == VIDEO_PREPROC_CROP) {
           encodedWidth = sampleInfo.video.cropRight - sampleInfo.video.cropLeft + 1;
           encodedHeight = sampleInfo.video.cropBottom - sampleInfo.video.cropTop + 1;
       }
       OH_AVFormat *formatVideo = OH_AVFormat_CreateVideoFormat(sampleInfo.video.videoCodecMime.data(),
           encodedWidth, encodedHeight);
       CHECK_AND_RETURN_RET_LOG(formatVideo != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "Create video format failed");

       OH_AVFormat_SetDoubleValue(formatVideo, OH_MD_KEY_FRAME_RATE, sampleInfo.video.frameRate);
       OH_AVFormat_SetIntValue(formatVideo, OH_MD_KEY_WIDTH, encodedWidth);
       OH_AVFormat_SetIntValue(formatVideo, OH_MD_KEY_HEIGHT, encodedHeight);
       OH_AVFormat_SetStringValue(formatVideo, OH_MD_KEY_CODEC_MIME, sampleInfo.video.videoCodecMime.data());
       // HDR Vivid视频需要设置色彩信息相关key，选填。
       if (sampleInfo.video.isHDRVivid) {
           OH_AVFormat_SetIntValue(formatVideo, OH_MD_KEY_VIDEO_IS_HDR_VIVID, 1);
           OH_AVFormat_SetIntValue(formatVideo, OH_MD_KEY_RANGE_FLAG, sampleInfo.video.rangFlag);
           OH_AVFormat_SetIntValue(formatVideo, OH_MD_KEY_COLOR_PRIMARIES, sampleInfo.video.primary);
           OH_AVFormat_SetIntValue(formatVideo, OH_MD_KEY_TRANSFER_CHARACTERISTICS, sampleInfo.video.transfer);
           OH_AVFormat_SetIntValue(formatVideo, OH_MD_KEY_MATRIX_COEFFICIENTS, sampleInfo.video.matrix);
       }
   
       int32_t ret = OH_AVMuxer_AddTrack(muxer_, &videoTrackId_, formatVideo);
       OH_AVFormat_Destroy(formatVideo);
       CHECK_AND_RETURN_RET_LOG(ret == AV_ERR_OK && videoTrackId_ >= 0, AVCODEC_SAMPLE_ERR_ERROR, "AddTrack failed");
       return AVCODEC_SAMPLE_ERR_OK;
   }
   ```

7. 添加辅助轨。
   > **说明：**
   >
   > 设置OH_MD_KEY_TRACK_TYPE时，值为MEDIA_TYPE_AUXILIARY代表添加辅助轨。<br>
   > 设置OH_MD_KEY_TRACK_REFERENCE_TYPE时，值必须为"hint"、"cdsc"、"font"、"hind"、"vdep"、"vplx"、"subt"、"thmb"、"auxl"、"cdtg"、"shsc"或"aest"其中一项。<br>
   > 设置OH_MD_KEY_TRACK_DESCRIPTION时，值必须为"com.openharmony."开头且长度不超过256个字符的字符串。<br>
   > 设置OH_MD_KEY_REFERENCE_TRACK_IDS时，track id值必须大于等于0，且必须是已经存在的track id。

   **添加音频辅助轨**

   ```c++
   int32_t audioAuxlTrackId = -1;
   std::vector<int32_t> audioTrackIDsVector = {0}; // 根据实际情况设置被辅助音频轨的编号，可填写多个值。
   int32_t *audioAuxlTrackIDs = audioTrackIDsVector.data();
   OH_AVFormat *audioAuxlFormat = OH_AVFormat_Create();
   OH_AVFormat_SetStringValue(audioAuxlFormat, OH_MD_KEY_CODEC_MIME, OH_AVCODEC_MIMETYPE_AUDIO_AAC); // 必填。
   OH_AVFormat_SetIntValue(audioAuxlFormat, OH_MD_KEY_AUD_SAMPLE_RATE, 44100); // 必填。
   OH_AVFormat_SetIntValue(audioAuxlFormat, OH_MD_KEY_AUD_CHANNEL_COUNT, 2); // 必填。
   OH_AVFormat_SetIntValue(audioAuxlFormat, OH_MD_KEY_PROFILE, AAC_PROFILE_LC); // 选填。
   OH_AVFormat_SetIntValue(audioAuxlFormat, OH_MD_KEY_TRACK_TYPE, static_cast<int32_t>(OH_MediaType::MEDIA_TYPE_AUXILIARY)); // 必填。
   OH_AVFormat_SetStringValue(audioAuxlFormat, OH_MD_KEY_TRACK_REFERENCE_TYPE, "auxl"); // 必填。
   OH_AVFormat_SetStringValue(audioAuxlFormat, OH_MD_KEY_TRACK_DESCRIPTION, "com.openharmony.audiomode.auxiliary"); // 必填。
   OH_AVFormat_SetIntBuffer(audioAuxlFormat, OH_MD_KEY_REFERENCE_TRACK_IDS, audioAuxlTrackIDs, audioTrackIDsVector.size()); // 必填。

   int ret = OH_AVMuxer_AddTrack(muxer, &audioAuxlTrackId, audioAuxlFormat);
   if (ret != AV_ERR_OK || audioAuxlTrackId < 0) {
       // 音频辅助轨添加失败。
   }
   ```

   **添加视频辅助轨**

   ```c++
   int32_t videoAuxlTrackId = -1;
   std::vector<int32_t> videoTrackIDsVector = {0}; // 根据实际情况设置被辅助视频轨的编号，可填写多个值。
   int32_t *videoAuxlTrackIDs = videoTrackIDsVector.data();
   OH_AVFormat *videoAuxlFormat = OH_AVFormat_Create();
   OH_AVFormat_SetStringValue(videoAuxlFormat, OH_MD_KEY_CODEC_MIME, OH_AVCODEC_MIMETYPE_VIDEO_AVC); // 必填。
   OH_AVFormat_SetIntValue(videoAuxlFormat, OH_MD_KEY_WIDTH, 1280); // 必填。
   OH_AVFormat_SetIntValue(videoAuxlFormat, OH_MD_KEY_HEIGHT, 720); // 必填。
   OH_AVFormat_SetIntValue(videoAuxlFormat, OH_MD_KEY_TRACK_TYPE, static_cast<int32_t>(OH_MediaType::MEDIA_TYPE_AUXILIARY)); // 必填。
   OH_AVFormat_SetStringValue(videoAuxlFormat, OH_MD_KEY_TRACK_REFERENCE_TYPE, "vdep"); // 必填。
   OH_AVFormat_SetStringValue(videoAuxlFormat, OH_MD_KEY_TRACK_DESCRIPTION, "com.openharmony.moviemode.depth"); // 必填。
   OH_AVFormat_SetIntBuffer(videoAuxlFormat, OH_MD_KEY_REFERENCE_TRACK_IDS, videoAuxlTrackIDs, videoTrackIDsVector.size()); // 必填。

   int ret = OH_AVMuxer_AddTrack(muxer, &videoAuxlTrackId, videoAuxlFormat);
   if (ret != AV_ERR_OK || videoAuxlTrackId < 0) {
       // 视频辅助轨添加失败。
   }
   ```

8. 添加封面轨。

   **方法一：用OH_AVFormat_Create创建format**

   ```c++
   int coverTrackId = -1;
   OH_AVFormat *formatCover = OH_AVFormat_Create();
   OH_AVFormat_SetStringValue(formatCover, OH_MD_KEY_CODEC_MIME, OH_AVCODEC_MIMETYPE_IMAGE_JPG);
   OH_AVFormat_SetIntValue(formatCover, OH_MD_KEY_WIDTH, 1280);
   OH_AVFormat_SetIntValue(formatCover, OH_MD_KEY_HEIGHT, 720);
   
   int ret = OH_AVMuxer_AddTrack(muxer, &coverTrackId, formatCover);
   if (ret != AV_ERR_OK || coverTrackId < 0) {
       // 添加封面失败。
   }
   OH_AVFormat_Destroy(formatCover); // 销毁。
   ```

   **方法二：用OH_AVFormat_CreateVideoFormat创建format**

   ```c++
   int coverTrackId = -1;
   OH_AVFormat *formatCover = OH_AVFormat_CreateVideoFormat(OH_AVCODEC_MIMETYPE_IMAGE_JPG, 1280, 720);
   
   int ret = OH_AVMuxer_AddTrack(muxer, &coverTrackId, formatCover);
   if (ret != AV_ERR_OK || coverTrackId < 0) {
       // 添加封面失败。
   }
   OH_AVFormat_Destroy(formatCover); // 销毁。
   ```

9. 调用OH_AVMuxer_Start()开始封装。

   <!-- @[Muxer::Start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/muxer.cpp) -->
   
   ``` C++
   int32_t Muxer::Start()
   {
       CHECK_AND_RETURN_RET_LOG(muxer_ != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "Muxer is null");
   
       int ret = OH_AVMuxer_Start(muxer_);
       CHECK_AND_RETURN_RET_LOG(ret == AV_ERR_OK, AVCODEC_SAMPLE_ERR_ERROR, "Start failed, ret: %{public}d", ret);
       return AVCODEC_SAMPLE_ERR_OK;
   }
   ```

   调用start写封装文件头后，不能设置媒体参数、不能添加音视频轨。

10. 调用OH_AVMuxer_WriteSampleBuffer()，写入封装数据。

    封装数据包括视频、音频、封面等数据。

    <!-- @[Muxer::WriteSample](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/muxer.cpp) -->
    
    ``` C++
    int32_t Muxer::WriteSample(int32_t trackId, OH_AVBuffer *buffer, OH_AVCodecBufferAttr &attr)
    {
        // 音视频编码输出可能由不同线程到达；整个“更新属性并写入容器”过程需要保持原子性。
        std::lock_guard<std::mutex> lock(writeMutex_);
    
        CHECK_AND_RETURN_RET_LOG(muxer_ != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "Muxer is null");
        CHECK_AND_RETURN_RET_LOG(buffer != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "Get a empty buffer");
    
        int32_t ret = OH_AVBuffer_SetBufferAttr(buffer, &attr);
        CHECK_AND_RETURN_RET_LOG(ret == AV_ERR_OK, AVCODEC_SAMPLE_ERR_ERROR, "SetBufferAttr failed");
    
        ret = OH_AVMuxer_WriteSampleBuffer(muxer_, trackId, buffer);
        CHECK_AND_RETURN_RET_LOG(ret == AV_ERR_OK, AVCODEC_SAMPLE_ERR_ERROR, "Write sample failed");
        // Muxer不接管编码器输出Buffer；调用方仍需使用原bufferIndex将该Buffer归还给编码器。
        return AVCODEC_SAMPLE_ERR_OK;
    }
    ```

    示例中buffer来自编码器输出的AVBuffer，封装前通过OH_AVBuffer_SetBufferAttr()设置当前数据的pts、size、flags等属性，通过GetAudioTrackId()/GetVideoTrackId()选择写的音视频轨，封装封面时必须一次写完一张图片。写入示例如下：

    <!-- @[Recorder::AudioEncOutputThread](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/sample/recorder/Recorder.cpp) -->
    
    ``` C++
    void Recorder::AudioEncOutputThread()
    {
        while (true) {
            CHECK_AND_BREAK_LOG(isStarted_, "Work done, thread out");

            std::shared_ptr<CodecBufferInfo> bufferInfo = audioEncContext_->outputBufferQueue.Dequeue();
            std::shared_lock<std::shared_mutex> codecLock(audioEncContext_->codecMutex);
            CHECK_AND_BREAK_LOG(isStarted_, "Work done, thread out");
            CHECK_AND_CONTINUE_LOG(bufferInfo != nullptr, "Buffer queue is empty, continue");

            audioEncContext_->outputFrameCount++;
            AVCODEC_SAMPLE_LOGW(
                "Audio Out buffer count: %{public}u, size: %{public}d, flag: %{public}u, pts: %{public}" PRId64,
                audioEncContext_->outputFrameCount, bufferInfo->attr.size, bufferInfo->attr.flags, bufferInfo->attr.pts);
            const bool isEosBuffer = (bufferInfo->attr.flags & AVCODEC_BUFFER_FLAGS_EOS) != 0;
            int32_t writeRet = AVCODEC_SAMPLE_ERR_OK;
            if (!isEosBuffer && bufferInfo->attr.size > 0) {
                // AAC只编码一次；同一输出Buffer依次写入两个Muxer，之后仍按原索引归还。
                writeRet = muxer_->WriteSample(muxer_->GetAudioTrackId(), bufferInfo->buffer, bufferInfo->attr);
                if (writeRet == AVCODEC_SAMPLE_ERR_OK && secondaryMuxer_ != nullptr) {
                    writeRet = secondaryMuxer_->WriteSample(secondaryMuxer_->GetAudioTrackId(), bufferInfo->buffer,
                        bufferInfo->attr);
                }
            }
            int32_t ret = audioEncoder_->FreeOutputData(bufferInfo->bufferIndex);
            CHECK_AND_BREAK_LOG(ret == AVCODEC_SAMPLE_ERR_OK, "Encoder output thread out");
            if (writeRet != AVCODEC_SAMPLE_ERR_OK) {
                AbortRecording("Write encoded audio sample failed");
                break;
            }
            if (isEosBuffer) {
                AVCODEC_SAMPLE_LOGI("Audio EOS processed, exiting output thread");
                isAudioEos_.store(true);
                videoEosCond_.notify_all();
                break;
            }
        }
        AVCODEC_SAMPLE_LOGI("Exit, frame count: %{public}u", audioEncContext_->inputFrameCount);
    }
    ```

11. 调用OH_AVMuxer_Stop()，停止封装。

    <!-- @[Muxer::Stop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/muxer.cpp) -->
    
    ``` C++
    int32_t Muxer::Stop()
    {
        CHECK_AND_RETURN_RET_LOG(muxer_ != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "Muxer is null");
    
        int32_t ret = OH_AVMuxer_Stop(muxer_);
        CHECK_AND_RETURN_RET_LOG(ret == AV_ERR_OK, AVCODEC_SAMPLE_ERR_ERROR, "Muxer stop failed");
        return AVCODEC_SAMPLE_ERR_OK;
    }
    ```

    调用stop写封装文件尾后，不能写入媒体数据。

12. 调用OH_AVMuxer_Destroy()销毁实例，释放资源。

    注意不能重复销毁，否则将会导致程序崩溃。

    <!-- @[Muxer::Release](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/muxer.cpp) -->
    
    ``` C++
    int32_t Muxer::Release()
    {
        if (muxer_ != nullptr) {
            // Destroy只释放封装器资源，不关闭Create()时由业务侧传入的文件描述符。
            OH_AVMuxer_Destroy(muxer_);
            muxer_ = nullptr;
        }
        return AVCODEC_SAMPLE_ERR_OK;
    }
    ```

    示例中封装完成关闭文件时，还需调用close(fd)关闭文件描述符。

### flv格式封装开发步骤

从API版本26.0.0开始支持flv格式封装。

flv格式仅支持一个音频轨和一个视频轨，不支持设置旋转角度、封面轨和辅助轨。

flv格式封装需要配置的key请参考AVCodec支持的格式中的[媒体数据封装](avcodec-support-formats.md#媒体数据封装)。

1. 添加头文件。

   ```c++
   #include <multimedia/player_framework/native_avmuxer.h>
   #include <multimedia/player_framework/native_avcodec_base.h>
   #include <multimedia/player_framework/native_avformat.h>
   #include <multimedia/player_framework/native_avbuffer.h>
   #include <fcntl.h>
   ```

2. 调用OH_AVMuxer_Create()创建封装器实例对象。

   示例中以读写方式打开fd，并设置封装格式为flv（AV_OUTPUT_FORMAT_FLV）。调用OH_AVMuxer_Create()创建封装器的实现与[mp4格式封装开发步骤](#mp4格式封装开发步骤)中步骤2一致。

3. flv格式不支持调用OH_AVMuxer_SetRotation()设置旋转角度，调用将返回错误。

4. 添加文件级数据。

   文件级数据已定义的key详见AVCodec支持的格式中的[媒体数据封装](avcodec-support-formats.md#媒体数据封装)。

   用户自定义的key必须以"com.openharmony."为开头。值类型为string。

   > **说明：**
   >
   > - 已定义的key必须在OH_AVMuxer_Start()前设置，用户自定义的key可以在OH_AVMuxer_Stop()前设置。
   > - flv格式不支持OH_MD_KEY_ENABLE_MOOV_FRONT。

   ```c++
   OH_AVFormat *format = OH_AVFormat_Create(); // 使用OH_AVFormat_Create创建format。

   // 设置已定义的key。
   OH_AVFormat_SetStringValue(format, OH_MD_KEY_CREATION_TIME, "2024-12-28T00:00:00.000000Z"); // 从API version 14开始支持设置创建时间（使用ISO 8601标准的时间格式且为UTC时间）。
   OH_AVFormat_SetStringValue(format, OH_MD_KEY_COMMENT, "comment test"); // 从API version 20开始支持设置备注。值类型为string。

   // 设置用户自定义key（需要com.openharmony.开头）。
   OH_AVFormat_SetStringValue(format, "com.openharmony.testString", "string test"); // 值类型为string，长度不超过256个字符。

   int ret = OH_AVMuxer_SetFormat(muxer, format); // 设置封装的format。
   if (ret != AV_ERR_OK) {
      // 设置format失败，未找到有效待写入的key数据。
   }
   OH_AVFormat_Destroy(format); // 销毁。
   ```

5. 添加音频轨（仅支持添加一个音频轨）。

   **添加AAC音频轨**

   > **说明：**
   >
   > 音频编解码类型为HE-AAC（AAC_PROFILE_HE或AAC_PROFILE_HE_V2）时，仅支持采样率大于等于16000Hz。
   
   ```c++
   int audioTrackId = -1;
   // 以封装44100Hz采样率、2声道的AAC-LC音频为例。
   OH_AVFormat *formatAudio = OH_AVFormat_CreateAudioFormat(OH_AVCODEC_MIMETYPE_AUDIO_AAC, 44100, 2);
   OH_AVFormat_SetIntValue(formatAudio, OH_MD_KEY_PROFILE, AAC_PROFILE_LC); // 选填。

   int ret = OH_AVMuxer_AddTrack(muxer, &audioTrackId, formatAudio);
   OH_AVFormat_Destroy(formatAudio);
   if (ret != AV_ERR_OK || audioTrackId < 0) {
       // 音频轨添加失败。
   }
   ```

   示例中添加音频轨的实现与[mp4格式封装开发步骤](#mp4格式封装开发步骤)中步骤5的方法二一致。

   <!--RP3--><!--RP3End-->

6. 添加视频轨（仅支持添加一个视频轨）。

   > **说明：**
   >
   > 当开发者需要设置色彩信息时，必须保证OH_MD_KEY_COLOR_PRIMARIES、OH_MD_KEY_TRANSFER_CHARACTERISTICS、OH_MD_KEY_MATRIX_COEFFICIENTS三个key设置的值都在其各自的参数范围内，系统才会识别这是有效色彩信息数据。参数设置范围可参考[OH_ColorPrimary](../../reference/apis-avcodec-kit/capi-native-avcodec-base-h.md#oh_colorprimary)、[OH_TransferCharacteristic](../../reference/apis-avcodec-kit/capi-native-avcodec-base-h.md#oh_transfercharacteristic)和[OH_MatrixCoefficient](../../reference/apis-avcodec-kit/capi-native-avcodec-base-h.md#oh_matrixcoefficient)。

   示例中添加视频轨的实现（HDR Vivid视频需额外设置色彩信息相关key，选填）与[mp4格式封装开发步骤](#mp4格式封装开发步骤)中步骤6的方法二一致。

   当视频轨需要设置色彩信息时，在使用OH_AVMuxer_AddTrack()之前先设置色彩信息相关key。

   ```c++
   OH_AVFormat_SetIntValue(formatVideo, OH_MD_KEY_COLOR_PRIMARIES, OH_ColorPrimary::COLOR_PRIMARY_BT709); // 选填。
   OH_AVFormat_SetIntValue(formatVideo, OH_MD_KEY_TRANSFER_CHARACTERISTICS, OH_TransferCharacteristic::TRANSFER_CHARACTERISTIC_BT709); // 选填。
   OH_AVFormat_SetIntValue(formatVideo, OH_MD_KEY_MATRIX_COEFFICIENTS, OH_MatrixCoefficient::MATRIX_COEFFICIENT_BT709); // 选填。
   OH_AVFormat_SetIntValue(formatVideo, OH_MD_KEY_RANGE_FLAG, 1); // 选填。值为0代表limited range，值为1代表full range。
   ```

7. 调用OH_AVMuxer_Start()开始封装。

   调用OH_AVMuxer_Start()的实现与[mp4格式封装开发步骤](#mp4格式封装开发步骤)中步骤9一致。

   调用start写封装文件头后，不能设置媒体参数、不能添加音视频轨。

8. 调用OH_AVMuxer_WriteSampleBuffer()，写入封装数据。

   封装数据包括视频、音频数据。写入前通过OH_AVBuffer_SetBufferAttr()设置当前数据的属性，其中attr.pts为当前数据的开始播放的时间，单位微秒（us），相对时间，首帧为0，后续按“采样点数*1000000/采样率”递增。

   调用OH_AVMuxer_WriteSampleBuffer()写入封装数据的实现与[mp4格式封装开发步骤](#mp4格式封装开发步骤)中步骤10一致，写入时通过GetAudioTrackId()/GetVideoTrackId()选择写的音视频轨。

9. 调用OH_AVMuxer_Stop()，停止封装。

   调用OH_AVMuxer_Stop()的实现与[mp4格式封装开发步骤](#mp4格式封装开发步骤)中步骤11一致。

   调用stop写封装文件尾后，不能写入媒体数据。

10. 调用OH_AVMuxer_Destroy()销毁实例，释放资源。

    注意不能重复销毁，否则将会导致程序崩溃。

    调用OH_AVMuxer_Destroy()销毁实例的实现与[mp4格式封装开发步骤](#mp4格式封装开发步骤)中步骤12一致。

    示例中封装完成关闭文件时，还需调用close(fd)关闭文件描述符。
