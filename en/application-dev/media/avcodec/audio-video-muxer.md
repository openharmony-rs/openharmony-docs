# Media Data Multiplexing

<!--Kit: AVCodec Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @mr-chencxy-->
<!--Designer: @dpy2650--->
<!--Tester: @baotianhao-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=8edc9bc0a2cabc0f28ab37f9be848d5c11ab3bbc translatedAt=2026-11-09T07:44:51.825Z pushedAt=2026-11-09T08:09:58.220Z nl=1 -->

You can call native APIs to multiplex audio and video streams, that is, to store encoded audio and video data to a file in a certain format.

For details about the currently supported multiplexing capabilities, see [Media Data Multiplexing](avcodec-support-formats.md#media-data-multiplexing) in AVCodec supported formats.

<!--RP2--><!--RP2End-->

**When to Use**

- Video and audio recording
  
  After you encode audio and video streams, multiplex them into files.

- Audio and video editing
  
  After you edit audio and video, multiplex them into files.

- Audio and video transcoding

  After you transcode audio and video, multiplex them into files.

## Development Guidelines

For details about the APIs, see [native_avmuxer.h](../../reference/apis-avcodec-kit/capi-native-avmuxer-h.md).

> **NOTE**
>
> - The output file descriptor (fd) for muxing must be opened in read/write mode and closed by the caller. For details, see [OH_AVMuxer_Create()](../../reference/apis-avcodec-kit/capi-native-avmuxer-h.md#oh_avmuxer_create).
>
> - To save the muxing result to the media library (Gallery) and obtain a writable fd, see [Saving Media Assets](../medialibrary/photoAccessHelper-savebutton.md). If you create the media asset through a security control or an authorization dialog box, the **ohos.permission.WRITE_IMAGEVIDEO** permission is not required.

### Linking the Dynamic Libraries in the CMake Script

``` cmake
target_link_libraries(sample PUBLIC libnative_media_avmuxer.so)
target_link_libraries(sample PUBLIC libnative_media_core.so)
```

The sample code uses custom utility macros and data structures defined in the sample project, such as CHECK_AND_RETURN_RET_LOG, AVCODEC_SAMPLE_ERR_\*, AVCODEC_SAMPLE_LOG\*, SampleInfo. These are not SDK APIs. Refer to the sample project for their complete definitions, and implement or replace them when porting the code.

### MP4 Format Multiplexing

Refer to the following sample code to complete the entire process of multiplexing audio and video into an MP4 file.

For details about the keys to be configured for different container formats, see [Media Data Multiplexing](avcodec-support-formats.md#media-data-multiplexing) in AVCodec supported formats.

1. Add the header files.

   ```c++
   #include <multimedia/player_framework/native_avmuxer.h>
   #include <multimedia/player_framework/native_avcodec_base.h>
   #include <multimedia/player_framework/native_avformat.h>
   #include <multimedia/player_framework/native_avbuffer.h>
   #include <fcntl.h>
   ```

2. Call **OH_AVMuxer_Create()** to create an OH_AVMuxer instance.

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

   In this sample, the output format is MP4 (AV_OUTPUT_FORMAT_MPEG_4), and fd is the output file descriptor opened in read/write mode.

3. (Optional) Call **OH_AVMuxer_SetRotation()** to set the rotation angle.

   Set this when the video image needs rotation. This sample sets the rotation angle for MP4; FLV does not support rotation metadata.

   <!-- @[Muxer::SetRotation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/muxer.cpp) -->
   
   ``` C++
   int32_t Muxer::SetRotation()
   {
       CHECK_AND_RETURN_RET_LOG(muxer_ != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "Muxer is null");
   
       // FLV does not support rotation metadata.
       if (outputFormat_ == AV_OUTPUT_FORMAT_FLV) {
           return AVCODEC_SAMPLE_ERR_OK;
       }
       // The camera profile supports only 1920 x 1080, not 1080 x 1920. Mux a 90-degree rotation into the file for portrait playback.
       int32_t ret = OH_AVMuxer_SetRotation(muxer_, VERTICAL_ANGLE);
       if (ret != AV_ERR_OK) {
           AVCODEC_SAMPLE_LOGW("Set rotation failed, ret: %{public}d", ret);
       }
       return AVCODEC_SAMPLE_ERR_OK;
   }
   ```

4. Add file-level data.

   For details about the defined keys of file-level data, see [Media Data Multiplexing](avcodec-support-formats.md#media-data-multiplexing) in AVCodec supported formats.

   Custom keys must start with **''com.openharmony.''**. The value type can be int32_t, float, or string. The value type uint8_t* is supported since API version 20.

   > **NOTE**
   >
   > The defined keys must be set before **OH_AVMuxer_Start()** is called, and custom keys can be set before **OH_AVMuxer_Stop()** is called.

   ```c++
   OH_AVFormat *format = OH_AVFormat_Create(); // Create a format using OH_AVFormat_Create.

   // Set the defined keys.
   OH_AVFormat_SetStringValue(format, OH_MD_KEY_CREATION_TIME, "2024-12-28T00:00:00.000000Z"); // Starting from API version 14, supports setting the creation time (in ISO 8601 standard time format, UTC time).
   OH_AVFormat_SetStringValue(format, OH_MD_KEY_COMMENT, "comment test"); // Starting from API version 20, supports setting a comment. The value type is string.
   OH_AVFormat_SetIntValue(format, OH_MD_KEY_ENABLE_MOOV_FRONT, 1); // Starting from API version 20, supports placing the moov box before the mdat box. The default value is 0. Set to 1 to place the moov box before the mdat box.
   OH_AVFormat_SetFloatValue(format, OH_MD_KEY_LATITUDE, 39.9); // Starting from API version 24, supports setting the latitude. The value type is float, with a range of [-90.0, 90.0]. When setting geographic location information, both latitude and longitude are mandatory; you cannot set only one of them.
   OH_AVFormat_SetFloatValue(format, OH_MD_KEY_LONGITUDE, 116.3); // Starting from API version 24, supports setting the longitude. The value type is float, with a range of [-180.0, 180.0]. When setting geographic location information, both latitude and longitude are mandatory; you cannot set only one of them.
   OH_AVFormat_SetFloatValue(format, OH_MD_KEY_ALTITUDE, 44.4); // Starting from API version 24, supports setting the altitude. The value type is float. Altitude is optional when setting geographic location information.

   // Set a custom key (starting with com.openharmony.).
   OH_AVFormat_SetIntValue(format, "com.openharmony.testInt", 1024); // The value type is int32_t.
   OH_AVFormat_SetFloatValue(format, "com.openharmony.testFloat", 1.024); // The value type is float.
   OH_AVFormat_SetStringValue(format, "com.openharmony.testString", "string test"); // The value type is string, with a maximum length of 256 characters.
   uint8_t testData[] = {1, 2, 3};
   OH_AVFormat_SetBuffer(format, "com.openharmony.testBuffer", testData, sizeof(testData)); // Starting from API version 20, supports the value type uint8_t*.

   int ret = OH_AVMuxer_SetFormat(muxer, format); // Set format data to the muxer.
   if (ret != AV_ERR_OK) {
      // Failed to set the format because no valid key data to be written is found.
   }
   OH_AVFormat_Destroy(format); // Destroy the format.
   ```

5. Add an audio track.

   **Method 1: Use OH_AVFormat_Create to create the format.**

   ```c++
   int audioTrackId = -1;
   uint8_t *buffer = ...; // Encoding configuration data. If there is no configuration data, leave the parameter unspecified.
   size_t size = ...;  // Length of the encoding configuration data. Set this parameter based on project requirements.
   OH_AVFormat *formatAudio = OH_AVFormat_Create(); // Use OH_AVFormat_Create to create a format. This example muxes AAC-LC audio with a 44100 Hz sample rate and 2 channels.
   OH_AVFormat_SetStringValue(formatAudio, OH_MD_KEY_CODEC_MIME, OH_AVCODEC_MIMETYPE_AUDIO_AAC); // Mandatory.
   OH_AVFormat_SetIntValue(formatAudio, OH_MD_KEY_AUD_SAMPLE_RATE, 44100); // Mandatory.
   OH_AVFormat_SetIntValue(formatAudio, OH_MD_KEY_AUD_CHANNEL_COUNT, 2); // Mandatory.
   OH_AVFormat_SetIntValue(formatAudio, OH_MD_KEY_PROFILE, AAC_PROFILE_LC); // Optional.
   OH_AVFormat_SetBuffer(formatAudio, OH_MD_KEY_CODEC_CONFIG, buffer, size); // Optional.
   
   int ret = OH_AVMuxer_AddTrack(muxer, &audioTrackId, formatAudio);
   if (ret != AV_ERR_OK || audioTrackId < 0) {
       // Failure to add the audio track.
   }
   OH_AVFormat_Destroy (formatAudio); // Destroy the format.
   ```

   **Method 2: Use OH_AVFormat_CreateAudioFormat to create the format.**

   <!-- @[Muxer::AddAudioTrack](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/muxer.cpp) -->
   
   ``` C++
   int32_t Muxer::AddAudioTrack(SampleInfo &sampleInfo)
   {
       CHECK_AND_RETURN_RET_LOG(muxer_ != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "Muxer is null");
   
       // Add an audio track: create format with OH_AVFormat_CreateAudioFormat. This example muxes AAC audio.
       OH_AVFormat *formatAudio = OH_AVFormat_CreateAudioFormat(sampleInfo.audio.audioCodecMime.data(),
           sampleInfo.audio.audioSampleRate, sampleInfo.audio.audioChannelCount);
       CHECK_AND_RETURN_RET_LOG(formatAudio != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "Create audio format failed");
       // Set the audio profile (optional).
       OH_AVFormat_SetIntValue(formatAudio, OH_MD_KEY_PROFILE, AAC_PROFILE_LC);
       int32_t ret = OH_AVMuxer_AddTrack(muxer_, &audioTrackId_, formatAudio);
       OH_AVFormat_Destroy(formatAudio);
       CHECK_AND_RETURN_RET_LOG(ret == AV_ERR_OK && audioTrackId_ >= 0, AVCODEC_SAMPLE_ERR_ERROR,
           "Add audio track failed, ret: %{public}d", ret);
       return AVCODEC_SAMPLE_ERR_OK;
   }
   ```

6. Add a video track.
   > **NOTE**
   >
   > - When you need to set color information, you must ensure that the values of `OH_MD_KEY_COLOR_PRIMARIES`, `OH_MD_KEY_TRANSFER_CHARACTERISTICS`, and `OH_MD_KEY_MATRIX_COEFFICIENTS` all fall within their respective parameter ranges. Otherwise, the system will not recognize the data as valid color information. For details about the parameter ranges, see [OH_ColorPrimary](../../reference/apis-avcodec-kit/capi-native-avcodec-base-h.md#oh_colorprimary), [OH_TransferCharacteristic](../../reference/apis-avcodec-kit/capi-native-avcodec-base-h.md#oh_transfercharacteristic), and [OH_MatrixCoefficient](../../reference/apis-avcodec-kit/capi-native-avcodec-base-h.md#oh_matrixcoefficient).
   > - If the color information you input is inconsistent with the color information in the parameter sets of the video bitstream, the system uses the color information in the video bitstream.

   **Method 1: Use OH_AVFormat_Create to create the format.**

   ```c++
   int videoTrackId = -1;
   uint8_t *buffer = ...; // Encoding configuration data. If there is no configuration data, leave the parameter unspecified.
   size_t size = ...;  // Length of the encoding configuration data. Set this parameter based on project requirements.
   OH_AVFormat *formatVideo = OH_AVFormat_Create();
   OH_AVFormat_SetStringValue(formatVideo, OH_MD_KEY_CODEC_MIME, OH_AVCODEC_MIMETYPE_VIDEO_AVC); // Mandatory.
   OH_AVFormat_SetIntValue(formatVideo, OH_MD_KEY_WIDTH, 1280); // Mandatory.
   OH_AVFormat_SetIntValue(formatVideo, OH_MD_KEY_HEIGHT, 720); // Mandatory.
   OH_AVFormat_SetBuffer(formatVideo, OH_MD_KEY_CODEC_CONFIG, buffer, size); // Optional.
   OH_AVFormat_SetIntValue(formatVideo, OH_MD_KEY_COLOR_PRIMARIES, OH_ColorPrimary::COLOR_PRIMARY_BT709); // Color information, optional.
   OH_AVFormat_SetIntValue(formatVideo, OH_MD_KEY_TRANSFER_CHARACTERISTICS, OH_TransferCharacteristic::TRANSFER_CHARACTERISTIC_BT709); // Color information, optional.
   OH_AVFormat_SetIntValue(formatVideo, OH_MD_KEY_MATRIX_COEFFICIENTS, OH_MatrixCoefficient::MATRIX_COEFFICIENT_BT709); // Color information, optional.
   OH_AVFormat_SetIntValue(formatVideo, OH_MD_KEY_RANGE_FLAG, 1); // Color information, optional. A value of 0 indicates limited range, and a value of 1 indicates full range.
   
   int ret = OH_AVMuxer_AddTrack(muxer, &videoTrackId, formatVideo);
   if (ret != AV_ERR_OK || videoTrackId < 0) {
       // Failure to add the video track.
   }
   OH_AVFormat_Destroy(formatVideo); // Destroy the format.
   ```

   **Method 2: Use OH_AVFormat_CreateVideoFormat to create the format.**

   <!-- @[Muxer::AddVideoTrack](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/muxer.cpp) -->
   
   ``` C++
   int32_t Muxer::AddVideoTrack(SampleInfo &sampleInfo)
   {
       CHECK_AND_RETURN_RET_LOG(muxer_ != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "Muxer is null");
   
       // Add a video track: create format with OH_AVFormat_CreateVideoFormat.
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
       // Set the color information keys for HDR Vivid video (optional).
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

7. Add an auxiliary track.
   > **NOTE**
   >
   > When setting **OH_MD_KEY_TRACK_TYPE**, set the value to **MEDIA_TYPE_AUXILIARY** to add an auxiliary track.<br>
   > When setting **OH_MD_KEY_TRACK_REFERENCE_TYPE**, the value must be one of **hint**, **cdsc**, **font**, **hind**, **vdep**, **vplx**, **subt**, **thmb**, **auxl**, **cdtg**, **shsc**, or **aest**.<br>
   > When setting **OH_MD_KEY_TRACK_DESCRIPTION**, the value must be a string that starts with **com.openharmony.** and does not exceed 256 characters.<br>
   > When setting **OH_MD_KEY_REFERENCE_TRACK_IDS**, the track ID value must be greater than or equal to 0 and must be an existing track ID.

   Add an audio auxiliary track.

   ```c++
   int32_t audioAuxlTrackId = -1;
   std::vector<int32_t> audioTrackIDsVector = {0}; // Set the IDs of the audio auxiliary tracks based on the actual situation. Multiple values can be entered.
   int32_t *audioAuxlTrackIDs = audioTrackIDsVector.data();
   OH_AVFormat *audioAuxlFormat = OH_AVFormat_Create();
   OH_AVFormat_SetStringValue(audioAuxlFormat, OH_MD_KEY_CODEC_MIME, OH_AVCODEC_MIMETYPE_AUDIO_AAC); // Mandatory.
   OH_AVFormat_SetIntValue(audioAuxlFormat, OH_MD_KEY_AUD_SAMPLE_RATE, 44100); // Mandatory.
   OH_AVFormat_SetIntValue(audioAuxlFormat, OH_MD_KEY_AUD_CHANNEL_COUNT, 2); // Mandatory.
   OH_AVFormat_SetIntValue(audioAuxlFormat, OH_MD_KEY_PROFILE, AAC_PROFILE_LC); // Optional.
   OH_AVFormat_SetIntValue(audioAuxlFormat, OH_MD_KEY_TRACK_TYPE, static_cast<int32_t>(OH_MediaType::MEDIA_TYPE_AUXILIARY)); // Mandatory.
   OH_AVFormat_SetStringValue(audioAuxlFormat, OH_MD_KEY_TRACK_REFERENCE_TYPE, "auxl"); // Mandatory.
   OH_AVFormat_SetStringValue(audioAuxlFormat, OH_MD_KEY_TRACK_DESCRIPTION, "com.openharmony.audiomode.auxiliary"); // Mandatory.
   OH_AVFormat_SetIntBuffer(audioAuxlFormat, OH_MD_KEY_REFERENCE_TRACK_IDS, audioAuxlTrackIDs, audioTrackIDsVector.size()); // Mandatory.

   int ret = OH_AVMuxer_AddTrack(muxer, &audioAuxlTrackId, audioAuxlFormat);
   if (ret != AV_ERR_OK || audioAuxlTrackId < 0) {
       // Failed to add the audio auxiliary track.
   }
   ```

   Add a video auxiliary track.

   ```c++
   int32_t videoAuxlTrackId = -1;
   std::vector<int32_t> videoTrackIDsVector = {0}; // Set the IDs of the video auxiliary tracks based on the actual situation. Multiple values can be entered.
   int32_t *videoAuxlTrackIDs = videoTrackIDsVector.data();
   OH_AVFormat *videoAuxlFormat = OH_AVFormat_Create();
   OH_AVFormat_SetStringValue(videoAuxlFormat, OH_MD_KEY_CODEC_MIME, OH_AVCODEC_MIMETYPE_VIDEO_AVC); // Mandatory.
   OH_AVFormat_SetIntValue(videoAuxlFormat, OH_MD_KEY_WIDTH, 1280); // Mandatory.
   OH_AVFormat_SetIntValue(videoAuxlFormat, OH_MD_KEY_HEIGHT, 720); // Mandatory.
   OH_AVFormat_SetIntValue(videoAuxlFormat, OH_MD_KEY_TRACK_TYPE, static_cast<int32_t>(OH_MediaType::MEDIA_TYPE_AUXILIARY)); // Mandatory.
   OH_AVFormat_SetStringValue(videoAuxlFormat, OH_MD_KEY_TRACK_REFERENCE_TYPE, "vdep"); // Mandatory.
   OH_AVFormat_SetStringValue(videoAuxlFormat, OH_MD_KEY_TRACK_DESCRIPTION, "com.openharmony.moviemode.depth"); // Mandatory.
   OH_AVFormat_SetIntBuffer(videoAuxlFormat, OH_MD_KEY_REFERENCE_TRACK_IDS, videoAuxlTrackIDs, videoTrackIDsVector.size()); // Mandatory.

   int ret = OH_AVMuxer_AddTrack(muxer, &videoAuxlTrackId, videoAuxlFormat);
   if (ret != AV_ERR_OK || videoAuxlTrackId < 0) {
       // Failed to add the video auxiliary track.
   }
   ```

8. Add a cover track.

   **Method 1: Use OH_AVFormat_Create to create the format.**

   ```c++
   int coverTrackId = -1;
   OH_AVFormat *formatCover = OH_AVFormat_Create();
   OH_AVFormat_SetStringValue(formatCover, OH_MD_KEY_CODEC_MIME, OH_AVCODEC_MIMETYPE_IMAGE_JPG);
   OH_AVFormat_SetIntValue(formatCover, OH_MD_KEY_WIDTH, 1280);
   OH_AVFormat_SetIntValue(formatCover, OH_MD_KEY_HEIGHT, 720);
   
   int ret = OH_AVMuxer_AddTrack(muxer, &coverTrackId, formatCover);
   if (ret != AV_ERR_OK || coverTrackId < 0) {
       // Failure to add the cover track.
   }
   OH_AVFormat_Destroy(formatCover); // Destroy the format.
   ```

   **Method 2: Use OH_AVFormat_CreateVideoFormat to create the format.**

   ```c++
   int coverTrackId = -1;
   OH_AVFormat *formatCover = OH_AVFormat_CreateVideoFormat(OH_AVCODEC_MIMETYPE_IMAGE_JPG, 1280, 720);
   
   int ret = OH_AVMuxer_AddTrack(muxer, &coverTrackId, formatCover);
   if (ret != AV_ERR_OK || coverTrackId < 0) {
       // Failure to add the cover track.
   }
   OH_AVFormat_Destroy(formatCover); // Destroy the format.
   ```

9. Call **OH_AVMuxer_Start()** to start multiplexing.

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

   After calling start to write the container header, you cannot set media parameters or add audio or video tracks.

10. Call **OH_AVMuxer_WriteSampleBuffer()** to write data.

    The encapsulated data includes video, audio, and cover data.

    <!-- @[Muxer::WriteSample](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/muxer.cpp) -->
    
    ``` C++
    int32_t Muxer::WriteSample(int32_t trackId, OH_AVBuffer *buffer, OH_AVCodecBufferAttr &attr)
    {
        // Encoded audio and video output may arrive on different threads. Keep the entire attribute-update and container-write operation atomic.
        std::lock_guard<std::mutex> lock(writeMutex_);
    
        CHECK_AND_RETURN_RET_LOG(muxer_ != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "Muxer is null");
        CHECK_AND_RETURN_RET_LOG(buffer != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "Get a empty buffer");
    
        int32_t ret = OH_AVBuffer_SetBufferAttr(buffer, &attr);
        CHECK_AND_RETURN_RET_LOG(ret == AV_ERR_OK, AVCODEC_SAMPLE_ERR_ERROR, "SetBufferAttr failed");
    
        ret = OH_AVMuxer_WriteSampleBuffer(muxer_, trackId, buffer);
        CHECK_AND_RETURN_RET_LOG(ret == AV_ERR_OK, AVCODEC_SAMPLE_ERR_ERROR, "Write sample failed");
        // The muxer does not take ownership of encoder output buffers. The caller must return the buffer to the encoder using the original bufferIndex.
        return AVCODEC_SAMPLE_ERR_OK;
    }
    ```

    In this sample, buffer is an AVBuffer output by the encoder. Before muxing, call OH_AVBuffer_SetBufferAttr() to set attributes such as pts, size, and flags, and select the audio or video track with GetAudioTrackId()/GetVideoTrackId(). When muxing cover art, write an entire image in one operation. The following example shows how to write data:

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
                // Encode AAC only once. Write the same output buffer to the two muxers in sequence, then return it using its original index.
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

11. Call **OH_AVMuxer_Stop()** to stop multiplexing.

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

    After calling stop to write the container trailer, you cannot write media data.

12. Call **OH_AVMuxer_Destroy()** to release the instance.

    Do not repeatedly destroy the instance. Otherwise, the program may crash.

    <!-- @[Muxer::Release](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/muxer.cpp) -->
    
    ``` C++
    int32_t Muxer::Release()
    {
        if (muxer_ != nullptr) {
            // Destroy releases only muxer resources. It does not close the file descriptor supplied by the app to Create().
            OH_AVMuxer_Destroy(muxer_);
            muxer_ = nullptr;
        }
        return AVCODEC_SAMPLE_ERR_OK;
    }
    ```

    When closing the file after muxing is complete, also call close(fd) to close the file descriptor.

### FLV Format Multiplexing

FLV format multiplexing is supported since API version 26.0.0.

The FLV format supports only one audio track and one video track. It does not support setting the rotation angle, cover track, or auxiliary track.

For details about the keys to be configured for FLV format multiplexing, see [Media Data Multiplexing](avcodec-support-formats.md#media-data-multiplexing) in AVCodec supported formats.

1. Add the header files.

   ```c++
   #include <multimedia/player_framework/native_avmuxer.h>
   #include <multimedia/player_framework/native_avcodec_base.h>
   #include <multimedia/player_framework/native_avformat.h>
   #include <multimedia/player_framework/native_avbuffer.h>
   #include <fcntl.h>
   ```

2. Call `OH_AVMuxer_Create()` to create a muxer instance.

   In this sample, fd is opened in read/write mode and the output format is FLV (AV_OUTPUT_FORMAT_FLV). Creating the muxer with OH_AVMuxer_Create() is implemented as in step 2 of [MP4 Format Multiplexing](#mp4-format-multiplexing).

3. The FLV format does not support calling `OH_AVMuxer_SetRotation()` to set the rotation angle. Calling this API will return an error.

4. Add file-level data.

   For details about the defined keys of file-level data, see [Media Data Multiplexing](avcodec-support-formats.md#media-data-multiplexing) in AVCodec supported formats.

   Custom keys must start with **''com.openharmony.''**. The value type is string.

   > **NOTE**
   >
   > - The defined keys must be set before **OH_AVMuxer_Start()** is called, and custom keys can be set before **OH_AVMuxer_Stop()** is called.
   > - The FLV format does not support **OH_MD_KEY_ENABLE_MOOV_FRONT**.

   ```c++
   OH_AVFormat *format = OH_AVFormat_Create(); // Use OH_AVFormat_Create to create the format.

   // Set the defined keys.
   OH_AVFormat_SetStringValue(format, OH_MD_KEY_CREATION_TIME, "2024-12-28T00:00:00.000000Z"); // Setting the creation time is supported since API version 14 (using the ISO 8601 standard time format in UTC).
   OH_AVFormat_SetStringValue(format, OH_MD_KEY_COMMENT, "comment test"); // Setting the comment is supported since API version 20. The value type is string.

   // Set a user-defined key (must start with com.openharmony.).
   OH_AVFormat_SetStringValue(format, "com.openharmony.testString", "string test"); // The value type is string, with a maximum length of 256 characters.

   int ret = OH_AVMuxer_SetFormat(muxer, format); // Set the muxer format.
   if (ret != AV_ERR_OK) {
      // Failed to set the format. No valid key data to write was found.
   }
   OH_AVFormat_Destroy(format); // Destroy.
   ```

5. Add an audio track (only one audio track is supported).

   **Adding an AAC Audio Track**

   > **NOTE**
   >
   > When the audio codec type is HE-AAC (AAC_PROFILE_HE or AAC_PROFILE_HE_V2), only sample rates greater than or equal to 16000 Hz are supported.
   
   ```c++
   int audioTrackId = -1;
   // Example: multiplexing AAC-LC audio with a 44100 Hz sample rate and 2 channels.
   OH_AVFormat *formatAudio = OH_AVFormat_CreateAudioFormat(OH_AVCODEC_MIMETYPE_AUDIO_AAC, 44100, 2);
   OH_AVFormat_SetIntValue(formatAudio, OH_MD_KEY_PROFILE, AAC_PROFILE_LC); // Optional.

   int ret = OH_AVMuxer_AddTrack(muxer, &audioTrackId, formatAudio);
   OH_AVFormat_Destroy(formatAudio);
   if (ret != AV_ERR_OK || audioTrackId < 0) {
       // Failed to add the audio track.
   }
   ```

   Adding an audio track is implemented as in method 2 of step 5 in [MP4 Format Multiplexing](#mp4-format-multiplexing).

   <!--RP3--><!--RP3End-->

6. Add a video track (only one video track is supported).

   > **NOTE**
   >
   > When you need to set color information, you must ensure that the values of `OH_MD_KEY_COLOR_PRIMARIES`, `OH_MD_KEY_TRANSFER_CHARACTERISTICS`, and `OH_MD_KEY_MATRIX_COEFFICIENTS` all fall within their respective parameter ranges. Otherwise, the system will not recognize the data as valid color information. For details about the parameter ranges, see [OH_ColorPrimary](../../reference/apis-avcodec-kit/capi-native-avcodec-base-h.md#oh_colorprimary), [OH_TransferCharacteristic](../../reference/apis-avcodec-kit/capi-native-avcodec-base-h.md#oh_transfercharacteristic), and [OH_MatrixCoefficient](../../reference/apis-avcodec-kit/capi-native-avcodec-base-h.md#oh_matrixcoefficient).

   Adding a video track is implemented as in method 2 of step 6 in [MP4 Format Multiplexing](#mp4-format-multiplexing). Optionally, set additional color information keys for HDR Vivid video.

   When color information needs to be set for a video track, set the color information-related keys before calling `OH_AVMuxer_AddTrack()`.

   ```c++
   OH_AVFormat_SetIntValue(formatVideo, OH_MD_KEY_COLOR_PRIMARIES, OH_ColorPrimary::COLOR_PRIMARY_BT709); // Optional.
   OH_AVFormat_SetIntValue(formatVideo, OH_MD_KEY_TRANSFER_CHARACTERISTICS, OH_TransferCharacteristic::TRANSFER_CHARACTERISTIC_BT709); // Optional.
   OH_AVFormat_SetIntValue(formatVideo, OH_MD_KEY_MATRIX_COEFFICIENTS, OH_MatrixCoefficient::MATRIX_COEFFICIENT_BT709); // Optional.
   OH_AVFormat_SetIntValue(formatVideo, OH_MD_KEY_RANGE_FLAG, 1); // Optional. A value of 0 indicates limited range, and a value of 1 indicates full range.
   ```

7. Call `OH_AVMuxer_Start()` to start multiplexing.

   Calling OH_AVMuxer_Start() is implemented as in step 9 of [MP4 Format Multiplexing](#mp4-format-multiplexing).

   After calling start to write the container header, you cannot set media parameters or add audio or video tracks.

8. Call `OH_AVMuxer_WriteSampleBuffer()` to write multiplexing data.

   The data to mux includes video and audio data. Before writing, call OH_AVBuffer_SetBufferAttr() to set the current data attributes. attr.pts is the relative playback start time in microseconds (us). It is 0 for the first frame and increases by number of samples * 1000000 / sample rate for subsequent frames.

   Writing muxed data with OH_AVMuxer_WriteSampleBuffer() is implemented as in step 10 of [MP4 Format Multiplexing](#mp4-format-multiplexing). Select the audio or video track with GetAudioTrackId()/GetVideoTrackId() when writing.

9. Call `OH_AVMuxer_Stop()` to stop multiplexing.

   Calling OH_AVMuxer_Stop() is implemented as in step 11 of [MP4 Format Multiplexing](#mp4-format-multiplexing).

   After calling stop to write the container trailer, you cannot write media data.

10. Call `OH_AVMuxer_Destroy()` to destroy the instance and release resources.

    Do not destroy the instance repeatedly. Otherwise, the program will crash.

    Destroying the instance with OH_AVMuxer_Destroy() is implemented as in step 12 of [MP4 Format Multiplexing](#mp4-format-multiplexing).

    When closing the file after muxing is complete, also call close(fd) to close the file descriptor.
