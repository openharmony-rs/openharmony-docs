# Asynchronous Audio Encoding
<!--Kit: AVCodec Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @mr-chencxy-->
<!--Designer: @dpy2650--->
<!--Tester: @baotianhao-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=66c49c549588a50aa036f806393d8098f913c4aa translatedAt=2026-10-22T03:51:19.785Z pushedAt=2026-10-22T11:07:04.795Z nl=1 -->

You can call native APIs to perform audio encoding, which compresses audio PCM data into a desired format.

PCM data can be from any source. For example, you can use a microphone to record audio data or import edited PCM data. After audio encoding, you can output streams in the desired format and multiplex the streams into a target file.

For details about the supported encoding capabilities, see [AVCodec Supported Formats](avcodec-support-formats.md#audio-encoding).

**When to Use**

- Audio recording

  Record PCM data, encode it into the desired format, and then [multiplex](audio-video-muxer.md) it into an audio file in the desired format.
- Audio editing

  Export edited PCM data, encode it into the corresponding audio format, and then [multiplex](audio-video-muxer.md) it into a file.
> **NOTE**
>
> - AAC encoders adopt the VBR mode by default. This may result in differences from the configured parameters.
> - By default, AAC encoders include an ADTS header in its output, which occupies the first 7 bytes of each frame.

## Development Guidelines

For detailed API descriptions, see [native_avcodec_audiocodec.h](../../reference/apis-avcodec-kit/capi-native-avcodec-audiocodec-h.md).

Refer to the code snippet below to complete the entire audio encoding process, including creating an encoder, setting encoding parameters (such as the sample rate, bit rate, and audio channel count), and starting, refreshing, resetting, and destroying the encoder.

The sample code references custom utility macros and data structures defined in the sample project (such as CHECK_AND_RETURN_RET_LOG, AVCODEC_SAMPLE_ERR_\*, AVCODEC_SAMPLE_LOG\*, CodecUserData, CodecBufferInfo, and SampleInfo). These are not SDK APIs. For their complete definitions, see the sample project. You need to implement or replace them when porting the code.

During application development, you must call the APIs in the defined sequence. Otherwise, an exception or undefined behavior may occur.

The figure below shows the call relationship of audio encoding.

- The dotted line indicates an optional operation.

- The solid line indicates a mandatory operation.

![Call relationship of audio encoding](figures/audio-codec.png)

### Linking the Dynamic Libraries in the CMake Script

```cmake
target_link_libraries(sample PUBLIC libnative_media_codecbase.so)
target_link_libraries(sample PUBLIC libnative_media_core.so)
target_link_libraries(sample PUBLIC libnative_media_acodec.so)
```
> **NOTE**
>
> The word **sample** in the preceding code snippet is only an example. Use the actual project directory name.

### How to Develop

1. Add the required header files.

   ```cpp
   #include <multimedia/player_framework/native_avcodec_audiocodec.h>
   #include <multimedia/native_audio_channel_layout.h>
   #include <multimedia/player_framework/native_avcapability.h>
   #include <multimedia/player_framework/native_avcodec_base.h>
   #include <multimedia/player_framework/native_avformat.h>
   #include <multimedia/player_framework/native_avbuffer.h>
   ```

2. Create an encoder instance. In the code snippet below, OH_AVCodec * is the pointer to the encoder instance created.

   You can create an encoder by MIME type or codec name.

   - Method 1: Create an encoder by MIME type.

   <!-- @[AudioEncoder::Create](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/Media/AVCodec/entry/src/main/cpp/capabilities/audio_encoder.cpp) -->
   
   ``` C++
   int32_t AudioEncoder::Create(const std::string &codecMime)
   {
       // Set whether this is encoding. true indicates that it is currently encoding.
       constexpr bool isEncoder = true;
       // Create an encoder by mime type. The mime type passed here depends on the actual encoding format.
       encoder_ = OH_AudioCodec_CreateByMime(codecMime.c_str(), isEncoder);
       CHECK_AND_RETURN_RET_LOG(encoder_ != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "Create failed");
       return AVCODEC_SAMPLE_ERR_OK;
   }
   ```

   - Method 2: Create an encoder by codec name.

   <!-- @[AudioEncoder::CreateByName](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/Media/AVCodec/entry/src/main/cpp/capabilities/audio_encoder.cpp) -->
   
   ``` C++
   int32_t AudioEncoder::CreateByName(const std::string &codecMime)
   {
       // Create the encoder by codec name.
       OH_AVCapability *capability = OH_AVCodec_GetCapability(codecMime.c_str(), true);
       CHECK_AND_RETURN_RET_LOG(capability != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "GetCapability failed");
       const char *name = OH_AVCapability_GetName(capability);
       encoder_ = OH_AudioCodec_CreateByName(name);
       CHECK_AND_RETURN_RET_LOG(encoder_ != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "CreateByName failed");
       return AVCODEC_SAMPLE_ERR_OK;
   }
   ```

3. Call **OH_AudioCodec_RegisterCallback()** to register callback functions.

   Register the **OH_AVCodecCallback** struct that defines the following callback function pointers:

   - **OH_AVCodecOnError**, a callback used to report a codec operation error
   - **OH_AVCodecOnStreamChanged**, a callback not supported by the audio encoder yet
   - **OH_AVCodecOnNeedInputBuffer**, a callback used to report input data required, which means that the encoder is ready for receiving PCM data
   - **OH_AVCodecOnNewOutputBuffer**, a callback used to report output data generated, which means that encoding is complete

   You need to process the callback functions to ensure that the encoder runs properly.

   In the sample, **CodecUserData** is an application-defined pass-through data structure used to pass the buffer queue between the callback thread and the consumer thread.

   > **NOTE**
   >
   > Do not call the encoder APIs or perform time-consuming operations in the callbacks.

   <!-- @[SampleCallback::OnCodecError](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/Media/AVCodec/entry/src/main/cpp/common/sample_callback.cpp) -->
   
   ``` C++
   void SampleCallback::OnCodecError(OH_AVCodec *codec, int32_t errorCode, void *userData)
   {
       (void)codec;
       auto *codecUserData = static_cast<CodecUserData *>(userData);
       if (codecUserData != nullptr && !codecUserData->isDestroyed.load()) {
           codecUserData->SignalError();
       }
       AVCODEC_SAMPLE_LOGE("On codec error, error code: %{public}d", errorCode);
   }
   ```

   <!-- @[SampleCallback::OnNeedInputBuffer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/Media/AVCodec/entry/src/main/cpp/common/sample_callback.cpp) -->
   
   ``` C++
   void SampleCallback::OnNeedInputBuffer(OH_AVCodec *codec, uint32_t index, OH_AVBuffer *buffer, void *userData)
   {
       auto *codecUserData = static_cast<CodecUserData *>(userData);
       if (codecUserData == nullptr || codecUserData->isDestroyed.load()) {
           return;
       }
       if (codec == nullptr || buffer == nullptr) {
           AVCODEC_SAMPLE_LOGE("Invalid codec input callback argument");
           codecUserData->SignalError();
           return;
       }
       UpdateEncoderFirstInputDescription(codec, codecUserData);
       // Push the input frame data buffer and its corresponding index into the inputBufferQueue queue.
       codecUserData->inputBufferQueue.Enqueue(std::make_shared<CodecBufferInfo>(index, buffer));
   }
   ```

   The **UpdateEncoderFirstInputDescription()** call in **OnNeedInputBuffer()** obtains the first-frame information for video encoding (it internally calls **OH_VideoEncoder_GetInputDescription()**). It does not take effect in audio encoding scenarios and can be ignored.

   <!-- @[SampleCallback::OnNewOutputBuffer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/Media/AVCodec/entry/src/main/cpp/common/sample_callback.cpp) -->
   
   ``` C++
   void SampleCallback::OnNewOutputBuffer(OH_AVCodec *codec, uint32_t index, OH_AVBuffer *buffer, void *userData)
   {
       auto *codecUserData = static_cast<CodecUserData *>(userData);
       if (codecUserData == nullptr || codecUserData->isDestroyed.load()) {
           return;
       }
       if (codec == nullptr || buffer == nullptr) {
           AVCODEC_SAMPLE_LOGE("Invalid codec output callback argument");
           codecUserData->SignalError();
           return;
       }
       if (codecUserData->isDecFirstFrame) {
           OH_AVFormat *format = OH_VideoDecoder_GetOutputDescription(codec);
           if (format != nullptr) {
               UpdateVideoOutputInfo(format, codecUserData);
               OH_AVFormat_Destroy(format);
           }
           codecUserData->isDecFirstFrame = false;
       }
       // Push the output frame data buffer and its corresponding index into the outputBufferQueue queue.
       codecUserData->outputBufferQueue.Enqueue(std::make_shared<CodecBufferInfo>(index, buffer));
   
       // Obtain the time-domain layer information from AVBuffer.
       int32_t layerID = GetTemporalLayerID(buffer);
       if (layerID >= 0 && index % LIMIT_LOGD_FREQUENCY == 0) {
           AVCODEC_SAMPLE_LOGD("Temporal layer ID: %{public}d", layerID);
       }
   }
   ```

   > **NOTE**
   >
   > The **isDecFirstFrame** branch internally calls **OH_VideoDecoder_GetOutputDescription()**, which is declared in **native_avcodec_videodecoder.h** and belongs to the video decoding library. In the sample, the **isDecFirstFrame** branch and the acquisition of temporal layer information (**GetTemporalLayerID()**) are extension logic for video scenarios. They do not take effect in audio encoding scenarios and can be ignored.

   Configure the callbacks:

   <!-- @[AudioEncoder::SetCallback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/Media/AVCodec/entry/src/main/cpp/capabilities/audio_encoder.cpp) -->
   
   ``` C++
   int32_t AudioEncoder::SetCallback(CodecUserData *codecUserData)
   {
       // The encoder calls back userData on an internal thread; stop the encoder and wait for the consumer thread to exit before releasing.
       int32_t ret = AV_ERR_OK;
       ret = OH_AudioCodec_RegisterCallback(encoder_,
                                            { SampleCallback::OnCodecError, SampleCallback::OnCodecFormatChange,
                                              SampleCallback::OnNeedInputBuffer, SampleCallback::OnNewOutputBuffer },
                                            codecUserData);
       CHECK_AND_RETURN_RET_LOG(ret == AV_ERR_OK, AVCODEC_SAMPLE_ERR_ERROR, "Set callback failed, ret: %{public}d", ret);
   
       return AVCODEC_SAMPLE_ERR_OK;
   }
   ```

4. Call **OH_AudioCodec_Configure** to configure the encoder.

   Key values of configuration options are described as follows:

   <!--RP2-->
   ![Audio encoder key configuration](figures/encoder_key.png)
   <!--RP2End-->

   The sample below lists the value range of each audio encoding type.

   <!--RP3-->
   ![Audio encoder format range description](figures/encoder_format.png)
   <!--RP3End-->

   The code snippet below shows the API call process, where AAC encoding at the bit rate of 32000 bit/s is carried out on the PCM audio with the 44100 Hz sample rate, 2-channel stereo, and SAMPLE_S16LE sample format.

   Before configuration, you are advised to use the **OH_AVCapability** capability query API to verify that the parameters to be configured are within the supported range of the encoder, and then write them to format and call **OH_AudioCodec_Configure()**.

   <!--RP4-->
   <!-- @[AudioEncoder::Configure](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/Media/AVCodec/entry/src/main/cpp/capabilities/audio_encoder.cpp) -->
   
   ``` C++
   int32_t AudioEncoder::Configure(const SampleInfo &sampleInfo)
   {
       CHECK_AND_RETURN_RET_LOG(CodecCapability::ValidateAudioConfiguration(sampleInfo, true),
           AVCODEC_SAMPLE_ERR_ERROR, "Audio encoder configuration is not supported");
       // The configuration object is not taken over by the encoder; after successful configuration, it is destroyed by this function, and the caller does not need to take it over.
       OH_AVFormat *format = OH_AVFormat_Create();
       CHECK_AND_RETURN_RET_LOG(format != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "AVFormat create failed");
   
       // Required: sample format, number of channels, sample rate, bit rate, and channel layout.
       OH_AVFormat_SetIntValue(format, OH_MD_KEY_AUDIO_SAMPLE_FORMAT, sampleInfo.audio.audioSampleFormat);
       OH_AVFormat_SetIntValue(format, OH_MD_KEY_AUD_CHANNEL_COUNT, sampleInfo.audio.audioChannelCount);
       OH_AVFormat_SetIntValue(format, OH_MD_KEY_AUD_SAMPLE_RATE, sampleInfo.audio.audioSampleRate);
       OH_AVFormat_SetLongValue(format, OH_MD_KEY_BITRATE, sampleInfo.audio.audioBitRate);
       OH_AVFormat_SetLongValue(format, OH_MD_KEY_CHANNEL_LAYOUT, sampleInfo.audio.audioChannelLayout);
       // Optional: maximum input length. After being set for frame-aligned encoders such as FLAC and MP3, it allows input data not to be aligned to the frame size.
       OH_AVFormat_SetIntValue(format, OH_MD_KEY_MAX_INPUT_SIZE, sampleInfo.audio.audioMaxInputSize);
       if (sampleInfo.codec.codecSyncMode) {
           OH_AVFormat_SetIntValue(format, OH_MD_KEY_ENABLE_SYNC_MODE, sampleInfo.codec.codecSyncMode);
       }
   
       // Configure the encoder.
       int ret = OH_AudioCodec_Configure(encoder_, format);
       CHECK_AND_RETURN_RET_LOG(ret == AV_ERR_OK, AVCODEC_SAMPLE_ERR_ERROR, "Config failed, ret: %{public}d", ret);
       OH_AVFormat_Destroy(format);
       format = nullptr;
   
       return AVCODEC_SAMPLE_ERR_OK;
   }
   ```
   <!--RP4End-->

   <!--RP1--><!--RP1End-->

   In addition to the parameters configured above, you can also configure the following optional parameters during the configuration phase:

   - `OH_MD_KEY_AUDIO_MAX_INPUT_BUFFER_SIZE`: Configures the maximum input buffer size (in bytes) for the audio encoder. For frame-aligned encoders such as FLAC and MP3, setting this parameter enables the internal PCM caching mechanism, allowing input data to be accepted without frame-size alignment. The encoder automatically caches and splits frames. The actual buffer size is subject to encoder implementation limits. If the configured value exceeds the upper limit, it is set to the upper limit (10 MB).

   - `OH_MD_KEY_AUDIO_ENCODER_PTS_MODE`: Configures the output PTS mode of the audio encoder. The value type is [OH_AudioEncoderPTSMode](../../reference/apis-avcodec-kit/capi-native-avcodec-base-h.md#oh_audioencoderptsmode). The PTS calculation method for output frames varies by mode:
     - `OH_AUDIO_ENCODER_PTS_MODE_DEFAULT`: Default behavior. The PTS output method may vary across different encoders.
     - `OH_AUDIO_ENCODER_PTS_MODE_ZERO_START`: PTS starts from 0 and increments by frame duration. This mode is suitable for scenarios where input PTS is not relied upon and timing needs to start from 0.
     - `OH_AUDIO_ENCODER_PTS_MODE_FIRST_INPUT_START`: PTS starts from the PTS of the first input frame and increments by frame duration. This mode is suitable for scenarios where PTS continuity with the input stream must be maintained.

   - `OH_MD_KEY_AUDIO_ENCODER_ENABLE_SAMPLE_FORMAT_CONVERT`: Configures the sample format conversion switch for the audio encoder. 1 indicates enabled, and 0 indicates disabled (default). Audio encoders natively support a limited set of sample formats (for example, G711mu supports only SAMPLE_S16LE). When enabled, the encoder automatically converts the input PCM data to a format supported by the encoder for encoding. The supported input sample formats are extended to: SAMPLE_U8, SAMPLE_S16LE, SAMPLE_S24LE, SAMPLE_S32LE, and SAMPLE_F32LE. This is suitable for scenarios where the input PCM format differs from the encoder's native format.

   ```cpp
   // Configure the maximum input buffer size of the encoder (optional). After this is set for FLAC/MP3, non-frame-aligned input data can be accepted. The value 4096 here is only a reference; you can set it dynamically based on actual needs.
   OH_AVFormat_SetIntValue(format, OH_MD_KEY_AUDIO_MAX_INPUT_BUFFER_SIZE, 4096);
   // Configure the PTS output mode of the encoder (optional).
   OH_AVFormat_SetIntValue(format, OH_MD_KEY_AUDIO_ENCODER_PTS_MODE,
       OH_AUDIO_ENCODER_PTS_MODE_FIRST_INPUT_START);
   // Configure the sample format conversion switch of the encoder (optional). When enabled, more sample formats are supported for input.
   OH_AVFormat_SetIntValue(format, OH_MD_KEY_AUDIO_ENCODER_ENABLE_SAMPLE_FORMAT_CONVERT, 1);
   ```

5. Call **OH_AudioCodec_Prepare()** to prepare internal resources for the encoder.

   In the sample project, **OH_AudioCodec_Prepare()** is encapsulated in the **Config()** function: the **Config()** function first completes the **Configure()** configuration and callback registration, and then calls **OH_AudioCodec_Prepare()** to make the encoder ready. The following shows the Prepare part of the code:

   <!-- @[AudioEncoder::Config](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/Media/AVCodec/entry/src/main/cpp/capabilities/audio_encoder.cpp) -->
   
   ``` C++
   {
       // The encoder is ready.
       int ret = OH_AudioCodec_Prepare(encoder_);
       CHECK_AND_RETURN_RET_LOG(ret == AV_ERR_OK, AVCODEC_SAMPLE_ERR_ERROR, "Prepare failed, ret: %{public}d", ret);
   }
   ```

6. Call **OH_AudioCodec_Start()** to start the encoder.

   <!-- @[AudioEncoder::Start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/Media/AVCodec/entry/src/main/cpp/capabilities/audio_encoder.cpp) -->
   
   ``` C++
   int32_t AudioEncoder::Start()
   {
       CHECK_AND_RETURN_RET_LOG(encoder_ != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "Encoder is null");
   
       int ret = OH_AudioCodec_Start(encoder_);
       CHECK_AND_RETURN_RET_LOG(ret == AV_ERR_OK, AVCODEC_SAMPLE_ERR_ERROR, "Start failed, ret: %{public}d", ret);
       return AVCODEC_SAMPLE_ERR_OK;
   }
   ```

7. Call **OH_AudioCodec_PushInputBuffer()** to write the data to encode. You should fill in complete input data before calling this API.

   The method for determining the number of samples per frame (**SAMPLES_PER_FRAME**) is as follows:

   AAC-LC encodes 1024 PCM samples per frame. Therefore, you are advised to input exactly 1024 samples at a time.

   <!--RP5--><!--RP5End-->

   For FLAC encoding, set **SAMPLES_PER_FRAME** based on the table below.

   | Sample Rate| Sample Count|
   | :----: | :----: |
   |  8000  |  576  |
   | 16000 |  1152  |
   | 22050 |  2304  |
   | 24000 |  2304  |
   | 32000 |  2304  |
   | 44100 |  4608  |
   | 48000 |  4608  |
   | 88200 |  8192  |
   | 96000 |  8192  |

   > **NOTE**
   >
   > Data volume (in bytes) of a single encoding input: Number of samples (**SAMPLES_PER_FRAME**) * Number of channels * Number of bytes per sample.
   >
   > In the case of FLAC encoding, use the table below to set the number of samples based on the sample rate to prevent possible file corruption.

   <!-- @[AudioEncoder::PushInputData](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/Media/AVCodec/entry/src/main/cpp/capabilities/audio_encoder.cpp) -->
   
   ``` C++
   int32_t AudioEncoder::PushInputData(CodecBufferInfo &info)
   {
       CHECK_AND_RETURN_RET_LOG(encoder_ != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "Encoder is null");
       CHECK_AND_RETURN_RET_LOG(info.buffer != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "Input buffer is null");
       int32_t ret = OH_AVBuffer_SetBufferAttr(info.buffer, &info.attr);
       CHECK_AND_RETURN_RET_LOG(ret == AV_ERR_OK, AVCODEC_SAMPLE_ERR_ERROR, "Set avbuffer attr failed");
       ret = OH_AudioCodec_PushInputBuffer(encoder_, info.bufferIndex);
       CHECK_AND_RETURN_RET_LOG(ret == AV_ERR_OK, AVCODEC_SAMPLE_ERR_ERROR, "Push input data failed");
       return AVCODEC_SAMPLE_ERR_OK;
   }
   ```

   In the sample, microphone recording (AudioCapturer) is used as the PCM data source. The recorded data is first written to an application-defined PCM cache. After enough data for one input buffer is accumulated, it is filled into the encoder input buffer and sent to the encoder. The following shows an example of the input thread:

   <!-- @[Recorder::AudioEncInputThread](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/Media/AVCodec/entry/src/main/cpp/sample/recorder/Recorder.cpp) -->
   
   ``` C++
   void Recorder::AudioEncInputThread()
   {
       while (true) {
           CHECK_AND_BREAK_LOG(!isEos_, "Work done, thread out");
           CHECK_AND_BREAK_LOG(isStarted_, "Encoder input thread out");
           if (isStopping_.load()) {
               std::this_thread::sleep_for(std::chrono::milliseconds(AUDIO_INPUT_STOP_POLL_INTERVAL_MS));
               continue;
           }
           if (!WaitForAudioInputFrame(5s)) {
               continue;
           }
           std::shared_ptr<CodecBufferInfo> bufferInfo = audioEncContext_->inputBufferQueue.Dequeue();
           std::shared_lock<std::shared_mutex> codecLock(audioEncContext_->codecMutex);
           CHECK_AND_CONTINUE_LOG(bufferInfo != nullptr, "Audio buffer queue is empty, continue");
           if (!SubmitAudioInputFrame(*bufferInfo, bufferInfo->buffer, false)) {
               break;
           }
       }
   }
   ```

   In the preceding example, **attr.flags** indicates the type of the buffer flag.

   At the end, set flags to **AVCODEC_BUFFER_FLAGS_EOS**. In the sample, when recording ends, an input buffer is obtained, filled with zero-length data, marked with the EOS flag, and then sent to the encoder.

   <!-- @[AudioEncoder::NotifyEndOfStream](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/Media/AVCodec/entry/src/main/cpp/capabilities/audio_encoder.cpp) -->
   
   ``` C++
   int32_t AudioEncoder::NotifyEndOfStream()
   {
       CHECK_AND_RETURN_RET_LOG(encoder_ != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "Encoder is null");
   
       // Use an empty input buffer to carry EOS. Even if there is no media data, you must submit this buffer so that the encoder outputs the trailing data.
       CodecBufferInfo bufferInfo;
       auto buffer = GetInputBuffer(bufferInfo, TIMEOUT_US);
       if (buffer == nullptr) {
           AVCODEC_SAMPLE_LOGW("GetInputBuffer for EOS failed");
           return AVCODEC_SAMPLE_ERR_ERROR;
       }
   
       // EOS does not contain valid audio bytes. After PushInputBuffer is called, this buffer is immediately managed by the codec.
       bufferInfo.attr.size = 0;
       bufferInfo.attr.flags = AVCODEC_BUFFER_FLAGS_EOS;
       int32_t ret = OH_AVBuffer_SetBufferAttr(buffer, &bufferInfo.attr);
       if (ret != AV_ERR_OK) {
           AVCODEC_SAMPLE_LOGE("SetBufferAttr for EOS failed, ret: %{public}d", ret);
           return AVCODEC_SAMPLE_ERR_ERROR;
       }
   
       bufferInfo.buffer = buffer;
       ret = OH_AudioCodec_PushInputBuffer(encoder_, bufferInfo.bufferIndex);
       CHECK_AND_RETURN_RET_LOG(ret == AV_ERR_OK, AVCODEC_SAMPLE_ERR_ERROR,
                                "PushInputBuffer for EOS failed, ret: %{public}d", ret);
       return AVCODEC_SAMPLE_ERR_OK;
   }
   ```

   | Value| Description| 
   | -------- | -------- |
   | AVCODEC_BUFFER_FLAGS_NONE | Common frame.| 
   | AVCODEC_BUFFER_FLAGS_EOS | The buffer is an end-of-stream frame.| 
   | AVCODEC_BUFFER_FLAGS_CODEC_DATA | The buffer contains codec-specific data.| 

8. Call **OH_AudioCodec_FreeOutputBuffer()** to release the encoded data.

   Once you have retrieved the encoded stream, call **OH_AudioCodec_FreeOutputBuffer()** to free up the data.

   <!-- @[AudioEncoder::FreeOutputData](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/Media/AVCodec/entry/src/main/cpp/capabilities/audio_encoder.cpp) -->
   
   ``` C++
   int32_t AudioEncoder::FreeOutputData(uint32_t bufferIndex)
   {
       CHECK_AND_RETURN_RET_LOG(encoder_ != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "Encoder is null");
   
       int32_t ret = AVCODEC_SAMPLE_ERR_OK;
       ret = OH_AudioCodec_FreeOutputBuffer(encoder_, bufferIndex);
       CHECK_AND_RETURN_RET_LOG(ret == AV_ERR_OK, AVCODEC_SAMPLE_ERR_ERROR, "Free output data failed");
       return AVCODEC_SAMPLE_ERR_OK;
   }
   ```

   In the sample, the encoded output stream is written to the muxer module. After a frame is written, the output buffer is released in time. The following shows an example of output consumption:

   <!-- @[Recorder::AudioEncOutputThread](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/Media/AVCodec/entry/src/main/cpp/sample/recorder/Recorder.cpp) -->
   
   ``` C++
   void Recorder::AudioEncOutputThread()
   {
       while (true) {
           CHECK_AND_BREAK_LOG(!isEos_, "Work done, thread out");
           CHECK_AND_BREAK_LOG(isStarted_, "Work done, thread out");
   
           std::shared_ptr<CodecBufferInfo> bufferInfo = audioEncContext_->outputBufferQueue.Dequeue();
           std::shared_lock<std::shared_mutex> codecLock(audioEncContext_->codecMutex);
           CHECK_AND_BREAK_LOG(isStarted_, "Work done, thread out");
           CHECK_AND_CONTINUE_LOG(bufferInfo != nullptr, "Buffer queue is empty, continue");
   
           audioEncContext_->outputFrameCount++;
           AVCODEC_SAMPLE_LOGW(
               "Audio Out buffer count: %{public}u, size: %{public}d, flag: %{public}u, pts: %{public}" PRId64,
               audioEncContext_->outputFrameCount, bufferInfo->attr.size, bufferInfo->attr.flags, bufferInfo->attr.pts);
           // After writing, return it by the same index. When the output queue is exhausted, the audio encoder stops the callback.
           muxer_->WriteSample(muxer_->GetAudioTrackId(), bufferInfo->buffer,
                               bufferInfo->attr);
           int32_t ret = audioEncoder_->FreeOutputData(bufferInfo->bufferIndex);
           CHECK_AND_BREAK_LOG(ret == AVCODEC_SAMPLE_ERR_OK, "Encoder output thread out");
       }
       AVCODEC_SAMPLE_LOGI("Exit, frame count: %{public}u", audioEncContext_->inputFrameCount);
   }
   ```

9. (Optional) Call **OH_AudioCodec_Flush()** to refresh the encoder.

   After **OH_AudioCodec_Flush()** is called, the current encoding queue is cleared.

   To continue encoding, you must call **OH_AudioCodec_Start()** again.

   Usage:

   * To use the same encoder configuration after **AVCODEC_BUFFER_FLAGS_EOS** of the output buffer is set, call **OH_AudioCodec_Flush()** to refresh the encoder.
   * If a recoverable error occurs during the execution (**OH_AudioCodec_IsValid()** returns **true**), you can call **OH_AudioCodec_Flush()** to refresh the encoder and then call **OH_AudioCodec_Start()** to start encoding again.

   <!-- @[AudioEncoder::Flush](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/Media/AVCodec/entry/src/main/cpp/capabilities/audio_encoder.cpp) -->
   
   ``` C++
   int32_t AudioEncoder::Flush()
   {
       CHECK_AND_RETURN_RET_LOG(encoder_ != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "Encoder is null");
   
       // Flush the encoder, clear the current queue, and then call Start() to restart encoding.
       int32_t ret = OH_AudioCodec_Flush(encoder_);
       CHECK_AND_RETURN_RET_LOG(ret == AV_ERR_OK, AVCODEC_SAMPLE_ERR_ERROR, "Flush failed, ret: %{public}d", ret);
       return AVCODEC_SAMPLE_ERR_OK;
   }
   ```

10. (Optional) Call **OH_AudioCodec_Reset()** to reset the encoder.

    After **OH_AudioCodec_Reset()** is called, the encoder returns to the initialized state. The input and output buffers obtained before the reset cannot be used. You must call **OH_AudioCodec_Configure()** to reconfigure the encoder and then call **OH_AudioCodec_Start()** to start encoding again. Obtain the input and output buffers again after the encoder is started.

    <!-- @[AudioEncoder::Reset](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/Media/AVCodec/entry/src/main/cpp/capabilities/audio_encoder.cpp) -->
    
    ``` C++
    int32_t AudioEncoder::Reset()
    {
        CHECK_AND_RETURN_RET_LOG(encoder_ != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "Encoder is null");
    
        // Reset the encoder. After that, call Configure() to configure and Start() to start again.
        int32_t ret = OH_AudioCodec_Reset(encoder_);
        CHECK_AND_RETURN_RET_LOG(ret == AV_ERR_OK, AVCODEC_SAMPLE_ERR_ERROR, "Reset failed, ret: %{public}d", ret);
        return AVCODEC_SAMPLE_ERR_OK;
    }
    ```

11. Call **OH_AudioCodec_Stop()** to stop the encoder.

    After the encoder is stopped, you can call **OH_AudioCodec_Start()** to start it again. The input and output buffers obtained before the encoder is stopped cannot be reused. You must obtain them again after the encoder is started.

    <!-- @[AudioEncoder::Stop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/Media/AVCodec/entry/src/main/cpp/capabilities/audio_encoder.cpp) -->
    
    ``` C++
    int32_t AudioEncoder::Stop()
    {
        CHECK_AND_RETURN_RET_LOG(encoder_ != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "Encoder is null");
    
        int ret = Flush();
        CHECK_AND_RETURN_RET_LOG(ret == AVCODEC_SAMPLE_ERR_OK, AVCODEC_SAMPLE_ERR_ERROR,
                                 "Flush failed, ret: %{public}d", ret);
    
        ret = OH_AudioCodec_Stop(encoder_);
        CHECK_AND_RETURN_RET_LOG(ret == AV_ERR_OK, AVCODEC_SAMPLE_ERR_ERROR, "Stop failed, ret: %{public}d", ret);
        return AVCODEC_SAMPLE_ERR_OK;
    }
    ```

12. Call **OH_AudioCodec_Destroy()** to destroy the encoder instance and release resources.

    > **NOTE**
    >
    > You only need to call this API once.

    <!-- @[AudioEncoder::Release](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/Media/AVCodec/entry/src/main/cpp/capabilities/audio_encoder.cpp) -->
    
    ``` C++
    int32_t AudioEncoder::Release()
    {
        if (encoder_ != nullptr) {
            // Refresh and stop the encoder before destroying it. Do not call destroy repeatedly.
            Flush();
            Stop();
            OH_AudioCodec_Destroy(encoder_);
            encoder_ = nullptr;
        }
        return AVCODEC_SAMPLE_ERR_OK;
    }
    ```
