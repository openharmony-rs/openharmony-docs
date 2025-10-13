# Media Data Demultiplexing

<!--Kit: AVCodec Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zhanghongran-->
<!--Designer: @dpy2650--->
<!--Tester: @cyakee-->
<!--Adviser: @w_Machine_cc-->

You can call native APIs to demultiplex media data. The demultiplexing involves extracting media samples such as audio, video, and subtitles from bit stream data, and obtaining information related to Digital Rights Management (DRM).

Currently, two data input types are supported: remote connection (over HTTP) and File Descriptor (FD).

For details about the supported demultiplexing formats, see [AVCodec Supported Formats](avcodec-support-formats.md#media-data-demultiplexing).

**When to Use**

- Audio and video playback
  
  Demultiplex media streams, decode the samples obtained through demultiplexing, and play the samples.

- Audio and video editing
  
  Demultiplex media streams, and edit the specified samples.

- Media file format conversion

  Demultiplex media streams, and encapsulate them into a new file format.

## Development Guidelines

Read [AVDemuxer](../../reference/apis-avcodec-kit/capi-avdemuxer.md) and [AVSource](../../reference/apis-avcodec-kit/capi-avsource.md) for the API reference.

> **NOTE**
>
> - To call the demuxer APIs to parse a network playback path, declare the ohos.permission.INTERNET permission by following the instructions provided in [Declaring Permissions](../../security/AccessToken/declare-permissions.md).
> - To call the demuxer APIs to write a local file, request the ohos.permission.READ_MEDIA permission by following the instructions provided in [Requesting User Authorization](../../security/AccessToken/request-user-authorization.md).
> - You can also use **ResourceManager.getRawFd** to obtain the FD of a file packed in the HAP file. For details, see [ResourceManager API Reference](../../reference/apis-localization-kit/js-apis-resource-manager.md#getrawfd9).

### Linking the Dynamic Libraries in the CMake Script

``` cmake
target_link_libraries(sample PUBLIC libnative_media_codecbase.so)
target_link_libraries(sample PUBLIC libnative_media_avdemuxer.so)
target_link_libraries(sample PUBLIC libnative_media_avsource.so)
target_link_libraries(sample PUBLIC libnative_media_core.so)
```

> **NOTE**
>
> The word **sample** in the preceding code snippet is only an example. Use the actual project directory name.
>

### How to Develop

1. Add the header files.

   ```c++
   #include <multimedia/player_framework/native_avdemuxer.h>
   #include <multimedia/player_framework/native_avsource.h>
   #include <multimedia/player_framework/native_avcodec_base.h>
   #include <multimedia/player_framework/native_avformat.h>
   #include <multimedia/player_framework/native_avbuffer.h>
   #include <fcntl.h>
   #include <sys/stat.h>
   #include <string>
   ```

2. Create a resource instance.

   When using **open** to obtain the FD, convert the value of **filepath** to a [sandbox path](../../file-management/app-sandbox-directory.md#mappings-between-application-sandbox-paths-and-physical-paths) to obtain sandbox resources.

   ```c++
   // Create the FD. You must have the read permission on the file instance to open the file. (filePath indicates the path of the file to be demultiplexed. The file must exist.)
   std::string filePath = "test.mp4";
   int32_t fd = open(filePath.c_str(), O_RDONLY);
   struct stat fileStatus {};
   int64_t fileSize = 0;
   if (stat(filePath.c_str(), &fileStatus) == 0) {
      fileSize = static_cast<int64_t>(fileStatus.st_size);
   } else {
      printf("get stat failed");
      return;
   }
   // Create a source resource instance for the FD resource file. If offset is not the start position of the file or size is not the actual file size, the data obtained may be incomplete. Consequently, the source resource object may fail to create or subsequent demultiplexing may fail.
   OH_AVSource *source = OH_AVSource_CreateWithFD(fd, 0, fileSize);
   if (source == nullptr) {
      printf("create source failed");
      return;
   }
   // (Optional) Create a source resource instance for the URI resource file.
   // OH_AVSource *source = OH_AVSource_CreateWithURI(uri);

   // (Optional) Create a source resource instance for the custom data source. Before the operation, you must implement AVSourceReadAt.
   // Add g_filePath when OH_AVSource_CreateWithDataSource is used.
   // g_filePath = filePath ;
   // OH_AVDataSource dataSource = {fileSize, AVSourceReadAt};
   // OH_AVSource *source = OH_AVSource_CreateWithDataSource(&dataSource);
   ```

   Implement the **AVSourceReadAt** API before creating the resource instance.

   ```c++
   // Add the header file.
   #include <fstream>
   ```

   ```c++
   static std::string g_filePath;

   enum MediaDataSourceError : int32_t {
      SOURCE_ERROR_IO = -2,
      SOURCE_ERROR_EOF = -1
   };

   int32_t AVSourceReadAt(OH_AVBuffer *data, int32_t length, int64_t pos)
   {
      if (data == nullptr) {
         printf("AVSourceReadAt : data is nullptr!\n");
         return MediaDataSourceError::SOURCE_ERROR_IO;
      }

      std::ifstream infile(g_filePath, std::ofstream::binary);
      if (!infile.is_open()) {
         printf("AVSourceReadAt : open file failed! file:%s\n", g_filePath.c_str());
         return MediaDataSourceError::SOURCE_ERROR_IO; // Failed to open the file.
      }

      infile.seekg(0, std::ios::end);
      int64_t fileSize = infile.tellg();
      if (pos >= fileSize) {
         printf("AVSourceReadAt : pos over or equals file size!\n");
         return MediaDataSourceError::SOURCE_ERROR_EOF; // pos is already at the end of the file and cannot be read.
      }

      if (pos + length > fileSize) {
         length of length = fileSize - pos; // When the sum of pos and length exceeds the file size, the data from pos to the end of the file is read.
      }

      infile.seekg(pos, std::ios::beg);
      if (length <= 0) {
         printf("AVSourceReadAt : raed length less than zero!\n");
         return MediaDataSourceError::SOURCE_ERROR_IO;
      }
      char* buffer = new char[length];
      infile.read(buffer, length);
      infile.close();

      memcpy(reinterpret_cast<char *>(OH_AVBuffer_GetAddr(data)),
         buffer, length);
      delete[] buffer;

      return length;
   }
   ```
3. Create a demuxer instance.
   ```c++
   // Create a demuxer for the resource instance.
   OH_AVDemuxer *demuxer = OH_AVDemuxer_CreateWithSource(source);
   if (demuxer == nullptr) {
      printf("create demuxer failed");
      return;
   }
   ```
4. (Optional) Register a [callback to obtain the media key system information](../../reference/apis-avcodec-kit/capi-native-avdemuxer-h.md#demuxer_mediakeysysteminfocallback). If the stream is not a DRM stream or the [media key system information](../../reference/apis-drm-kit/capi-drm-drm-mediakeysysteminfo.md) has been obtained, you can skip this step.

   In the API for setting DRM information listeners, the callback function can return a demuxer instance. It is suitable for the scenario where multiple demuxer instances are used.

   ```c++
   // Implement the OnDrmInfoChangedWithObj callback.
   static void OnDrmInfoChangedWithObj(OH_AVDemuxer *demuxer, DRM_MediaKeySystemInfo *drmInfo)
   {
      // Parse the media key system information, including the quantity, DRM type, and corresponding PSSH.
   }

   Demuxer_MediaKeySystemInfoCallback callback = &OnDrmInfoChangedWithObj;
   Drm_ErrCode ret = OH_AVDemuxer_SetDemuxerMediaKeySystemInfoCallback(demuxer, callback);
   ```
   After the callback is invoked, you can call the API to proactively obtain the media key system information (UUID and corresponding PSSH).

   ```c++
   DRM_MediaKeySystemInfo mediaKeySystemInfo;
   OH_AVDemuxer_GetMediaKeySystemInfo(demuxer, &mediaKeySystemInfo);
   ```
   After obtaining and parsing DRM information, create [MediaKeySystem and MediaKeySession](../drm/drm-c-dev-guide.md) instances of the corresponding DRM scheme to obtain a media key. If required, set the audio decryption configuration by following step 4 in [Audio Decoding](audio-decoding.md#how-to-develop), and set the video decryption configuration by following step 5 in [Surface Mode in Video Decoding](video-decoding.md#surface-mode) or step 4 in [Buffer Mode in Video Decoding](video-decoding.md#buffer-mode).

5. Obtain file information.

   ```c++
   // (Optional) Obtain custom file attributes. If custom file attributes are not required, skip this step.
   // Obtain custom attributes from the source file.
   OH_AVFormat *customMetadataFormat = OH_AVSource_GetCustomMetadataFormat(source);
   if (customMetadataFormat == nullptr) {
      // Release resources from the previous steps. For details, see step 10.
      printf("get custom metadata format failed");
      return;
   }
   // Precautions:
   // 1. customKey must exactly match the key used during multiplexing (including the complete naming hierarchy).
   //    The example key is for demonstration only. Replace it with the actual custom string.
   //    For example, if the key used during multiplexing is com.openharmony.custom.meta.abc.efg,
   //       you must use the full key. Using a truncated key like com.openharmony.custom.meta.abc will fail.
   // 2. The value type must match the data type used during multiplexing. In this example, it is a string. For other types, use the right API. The types ints and floats are supported. Starting from API version 20, the type buffer is also supported.
   const char *customKey = "com.openharmony.custom.meta.string"; // Replace it with the actual key used during multiplexing.
   const char *customValue;
   if (!OH_AVFormat_GetStringValue(customMetadataFormat, customKey, &customValue)) {
      printf("get custom metadata from custom metadata format failed");
   }
   OH_AVFormat_Destroy(customMetadataFormat);
   customMetadataFormat = nullptr;

   // (Optional) Obtain the number of tracks. If you know the track information, skip this step.
   // Obtain the number of tracks from the file source information. You can call the API to obtain file-level attributes. For details, see Table 1 in Appendix 1.
   OH_AVFormat *sourceFormat = OH_AVSource_GetSourceFormat(source);
   if (sourceFormat == nullptr) {
      // Release resources from the previous steps. For details, see step 10.
      printf("get source format failed");
      return;
   }
   int32_t trackCount = 0;
   if (!OH_AVFormat_GetIntValue(sourceFormat, OH_MD_KEY_TRACK_COUNT, &trackCount)) {
      printf("get track count from source format failed");
   }
   if (trackCount == 0) {
      // If the file does not contain any track, perform other operations based on the service.
      printf("no track");
   }
   OH_AVFormat_Destroy(sourceFormat);
   sourceFormat = nullptr;
   ```

6. (Optional) Obtain the track index and format. If you know the track information, skip this step.

   ```c++
   uint32_t audioTrackIndex = 0;
   uint32_t videoTrackIndex = 0;
   int32_t w = 0;
   int32_t h = 0;
   int64_t bitRate = 0; // Configure the bit rate, in bit/s.
   double frameRate = 0.0;
   const char* mimetype = nullptr;
   uint8_t *codecConfig = nullptr;
   size_t bufferSize = 0;
   int32_t trackType;
   for (uint32_t index = 0; index < (static_cast<uint32_t>(trackCount)); index++) {
      // Obtain the track information. You can call the API to obtain track-level attributes. For details, see Table 2 in Appendix.
      OH_AVFormat *trackFormat = OH_AVSource_GetTrackFormat(source, index);
      if (trackFormat == nullptr) {
         printf("get track format failed");
         return;
      }
      if (!OH_AVFormat_GetIntValue(trackFormat, OH_MD_KEY_TRACK_TYPE, &trackType)) {
         printf("get track type from track format failed");
         return;
      }
      if (trackType == OH_MediaType::MEDIA_TYPE_AUXILIARY) {
         const char *referenceType;
         if (!OH_AVFormat_GetStringValue(trackFormat, OH_MD_KEY_TRACK_REFERENCE_TYPE, &referenceType)) {
            printf("get reference type from auxiliary track failed");
         }
         int32_t* referenceIds;
         size_t referenceIdsCount;
         if (!OH_AVFormat_GetIntBuffer(trackFormat, OH_MD_KEY_TRACK_REFERENCE_TYPE, &referenceIds, &referenceIdsCount)) {
            printf("get reference track ids from auxiliary track failed");
         }
         // Process the track reference relationship based on the auxiliary track type.
      }
      static_cast<OH_MediaType>(trackType) == OH_MediaType::MEDIA_TYPE_AUD ? audioTrackIndex = index : videoTrackIndex = index;
      // Obtain the width and height of the video track.
      if (trackType == OH_MediaType::MEDIA_TYPE_VID) {
         if (!OH_AVFormat_GetIntValue(trackFormat, OH_MD_KEY_WIDTH, &w)) {
            printf("get track width from track format failed");
            return;
         }
         if (!OH_AVFormat_GetIntValue(trackFormat, OH_MD_KEY_HEIGHT, &h)) {
            printf("get track height from track format failed");
            return;
         }
         if (!OH_AVFormat_GetLongValue(trackFormat, OH_MD_KEY_BITRATE, &bitRate)) {
            printf("get track bitRate from track format failed");
            return;
         }
         if (!OH_AVFormat_GetDoubleValue(trackFormat, OH_MD_KEY_FRAME_RATE, &frameRate)) {
            printf("get track frameRate from track format failed");
            return;
         }
         if (!OH_AVFormat_GetStringValue(trackFormat, OH_MD_KEY_CODEC_MIME, &mimetype)) {
            printf("get track mimetype from track format failed");
            return;
         }
         if (!OH_AVFormat_GetBuffer(trackFormat, OH_MD_KEY_CODEC_CONFIG, &codecConfig, &bufferSize)) {
            printf("get track codecConfig from track format failed");
            return;
         }
         printf(" track width%d, track height: %d, track bitRate: %ld, track frameRate: %f, track mimetype: %s\n", w, h, bitRate, frameRate, mimetype);
      }
      OH_AVFormat_Destroy(trackFormat);
      trackFormat = nullptr;
   }
   ```

7. Select a track, from which the demuxer reads data.

   ```c++
   if(OH_AVDemuxer_SelectTrackByID(demuxer, audioTrackIndex) != AV_ERR_OK){
      printf("select audio track failed: %d", audioTrackIndex);
      return;
   }
   if(OH_AVDemuxer_SelectTrackByID(demuxer, videoTrackIndex) != AV_ERR_OK){
      printf("select video track failed: %d", videoTrackIndex);
      return;
   }
   // (Optional) Deselect the track.
   // OH_AVDemuxer_UnselectTrackByID(demuxer, audioTrackIndex);
   ```

8. (Optional) Seek to the specified time for the selected track.

   ```c++
   // Demultiplexing is performed from this time.
   // Note:
   // 1. If OH_AVDemuxer_SeekToTime is called for an MPEG TS or MPG file, the target position may be a non-key frame. You can then call OH_AVDemuxer_ReadSampleBuffer to check whether the current frame is a key frame based on the obtained OH_AVCodecBufferAttr. If it is a non-key frame, which causes display issues on the application side, cyclically read the frames until you reach the first key frame, where you can perform processing such as decoding.
   // 2. If OH_AVDemuxer_SeekToTime is called for an OGG file, the file seeks to the start of the time interval (second) where the input parameter millisecond is located, which may cause a certain number of frame errors.
   // 3. The seek operation of the demuxer is performed only on streams with consistent decoding behavior. If a stream requires the decoder to reconfigure or re-input parameter data after seeking to decode correctly, it may result in artifacts or decoder freezing.
   OH_AVDemuxer_SeekToTime(demuxer, 0, OH_AVSeekMode::SEEK_MODE_CLOSEST_SYNC);
   ```

9. Start demultiplexing and cyclically obtain samples. The code snippet below uses a file that contains audio and video tracks as an example.

   A BufferAttr object contains the following attributes.
   - **size**: sample size.
   - **offset**: offset of the data in the AVBuffer. The value is generally 0.
   - **pts**: timestamp when the file is multiplexed.
   - **flags**: sample attributes.

   | flag | Description|
   | -------- | -------- |
   | AVCODEC_BUFFER_FLAGS_NONE | Default value.|
   | AVCODEC_BUFFER_FLAGS_EOS | End of Stream (EOS). The data is empty.|
   | AVCODEC_BUFFER_FLAGS_SYNC_FRAME | IDR frame or I-frame.|
   | AVCODEC_BUFFER_FLAGS_INCOMPLETE_FRAME | Incomplete sample. Generally, a complete sample fails to be copied because the buffer is too small.|
   | AVCODEC_BUFFER_FLAGS_CODEC_DATA | Frame containing parameter set information.|
   | AVCODEC_BUFFER_FLAGS_DISCARD  | Frames that can be discarded.|

   The **OH_AVDemuxer_ReadSampleBuffer** function can be time-consuming, particularly due to file I/O operations. You are advised to call this function in asynchronous mode.
   ```c++
   // Define a processing function for each thread.
   void ReadTrackSamples(OH_AVFormatDemuxer *demuxer, uint32_t trackIndex, int buffer_size, 
                         std::atomic<bool>& isEnd, std::atomic<bool>& threadFinished)
   {
      // Create a buffer.
      OH_AVBuffer *buffer = OH_AVBuffer_Create(buffer_size);
      if (buffer == nullptr) {
         printf("Create buffer failed for track %d\n", trackIndex);
         threadFinished.store(true);
         return;
      }
      OH_AVCodecBufferAttr info;
      int32_t ret;

      while (!isEnd.load()) {
         ret = OH_AVDemuxer_ReadSampleBuffer(demuxer, trackIndex, buffer);
         if (ret == AV_ERR_OK) {
               OH_AVBuffer_GetBufferAttr(buffer, &info);
               printf("Track %d sample size: %d\n", trackIndex, info.size);
               // Check the EOS flag.
               if (info.flags == OH_AVCodecBufferFlags::AVCODEC_BUFFER_FLAGS_EOS) {
                  isEnd.store(true);
               }
               // Process the buffer data (decode the data as required).
         } else {
               printf("Read sample failed for track %d\n", trackIndex);
               break;
         }
      }
      // Destroy the buffer.
      OH_AVBuffer_Destroy(buffer);
      buffer = nullptr;
      threadFinished.store(true);
   }

   // Calculate the buffer size based on your requirements.
   int audioBufferSize = 4096; // Typical audio buffer size.
   int videoBufferSize = w * h * 3 >> 1; // Raw video buffer size.

   // Create atomic variables for thread communication.
   std::atomic<bool> audioIsEnd{false}, videoIsEnd{false}; // Specify whether the stream ends.
   std::atomic<bool> audioThreadFinished{false}, videoThreadFinished{false}; // Specify whether the thread is paused.

   // Create a thread.
   std::thread audioThread(ReadTrackSamples, demuxer, audioTrackIndex, audioBufferSize, 
                           std::ref(audioIsEnd), std::ref(audioThreadFinished));
   std::thread videoThread(ReadTrackSamples, demuxer, videoTrackIndex, videoBufferSize, 
                           std::ref(videoIsEnd), std::ref(videoThreadFinished));
   audioThread.join();
   videoThread.join();
   ```

10. Destroy the demuxer instance.
      ```c++
      // Manually set the instance to nullptr after OH_AVSource_Destroy is called. Do not call this API repeatedly for the same instance; otherwise, a program error occurs.
      if (OH_AVSource_Destroy(source) != AV_ERR_OK) {
         printf("destroy source pointer error");
      }
      source = nullptr;
      // Manually set the instance to nullptr after OH_AVDemuxer_Destroy is called. Do not call this API repeatedly for the same instance; otherwise, a program error occurs.
      if (OH_AVDemuxer_Destroy(demuxer) != AV_ERR_OK) {
         printf("destroy demuxer pointer error");
      }
      demuxer = nullptr;
      close(fd);
      ```

## Appendix
### Supported File-Level Attributes

> **NOTE**
>
> Attribute data can be obtained only when the file is parsed normally. If the file information is incorrect or missing, the parsing is abnormal and the corresponding data cannot be obtained.
> 
> Currently, data in the GBK character set is converted to UTF-8. If other character sets need to be converted to UTF-8, you must handle the conversion. For details, see [icu4c](../../reference/native-lib/icu4c.md).
> 
> For details about the data type and value range, see [Media Data Key-Value Pairs](../../reference/apis-avcodec-kit/_codec_base.md#media-data-key-value-pairs).

**Table 1** Supported file-level attributes
| Name| Description|
| -- | -- |
|OH_MD_KEY_TITLE|Title.|
|OH_MD_KEY_ARTIST|Artist.|
|OH_MD_KEY_ALBUM|Album.|
|OH_MD_KEY_ALBUM_ARTIST|Album artist.|
|OH_MD_KEY_DATE|Date.|
|OH_MD_KEY_COMMENT|Comment.|
|OH_MD_KEY_GENRE|Genre.|
|OH_MD_KEY_COPYRIGHT|Copyright.|
|OH_MD_KEY_LANGUAGE|Language.|
|OH_MD_KEY_DESCRIPTION|Description.|
|OH_MD_KEY_LYRICS|Lyrics.|
|OH_MD_KEY_TRACK_COUNT|Track count.|
|OH_MD_KEY_DURATION|Duration.|
|OH_MD_KEY_START_TIME|Start time.|

### Supported Track-Level Attributes

> **NOTE**
>
> Attribute data can be obtained only when the file is parsed normally. If the file information is incorrect or missing, the parsing is abnormal and the corresponding data cannot be obtained.
> The supported attributes of the auxiliary track must match the actual media type (audio or video).
> 
> For details about the data type and value range, see [Media Data Key-Value Pairs](../../reference/apis-avcodec-kit/_codec_base.md#media-data-key-value-pairs).

**Table 2** Supported track-level attributes
| Name| Description| Supported by Video Tracks| Supported by Audio Tracks| Supported by Subtitle Tracks| Supported by Auxiliary Tracks|
| -- | -- | -- | -- | -- | -- |
|OH_MD_KEY_CODEC_MIME|Stream codec type.|Supported|Supported|Supported|Supported|
|OH_MD_KEY_TRACK_TYPE|Stream track type.|Supported|Supported|Supported|Supported|
|OH_MD_KEY_TRACK_START_TIME|Start time of the stream.|Supported|Supported|Supported|Supported|
|OH_MD_KEY_BITRATE|Stream bit rate.|Supported|Supported|Not supported|Supported|
|OH_MD_KEY_LANGUAGE|Stream language type.|Supported|Supported|Not supported|Supported|
|OH_MD_KEY_CODEC_CONFIG|Codec-specific data. In the case of video, a parameter set is transferred. In the case of audio, parameter configuration information of the decoder is transferred.|Supported|Supported|Not supported|Supported|
|OH_MD_KEY_WIDTH|Video stream width.|Supported|Not supported|Not supported|Supported|
|OH_MD_KEY_HEIGHT|Video stream height.|Supported|Not supported|Not supported|Supported|
|OH_MD_KEY_FRAME_RATE|Video stream frame rate.|Supported|Not supported|Not supported|Supported|
|OH_MD_KEY_ROTATION|Rotation angle of the video stream.|Supported|Not supported|Not supported|Supported|
|OH_MD_KEY_VIDEO_SAR|Aspect ratio of the video stream sample.|Supported|Not supported|Not supported|Supported|
|OH_MD_KEY_PROFILE|Encoding profile of the video stream. This key is valid only for H.265 streams.|Supported|Not supported|Not supported|Supported|
|OH_MD_KEY_RANGE_FLAG|Video YUV value range flag of the video stream. This key is valid only for H.265 streams.|Supported|Not supported|Not supported|Supported|
|OH_MD_KEY_COLOR_PRIMARIES|Video primary color of the video stream. This key is valid only for H.265 streams.|Supported|Not supported|Not supported|Supported|
|OH_MD_KEY_TRANSFER_CHARACTERISTICS|Video transfer characteristics of the video stream. This key is valid only for H.265 streams.|Supported|Not supported|Not supported|Supported|
|OH_MD_KEY_MATRIX_COEFFICIENTS|Video matrix coefficient. This key is valid only for H.265 streams.|Supported|Not supported|Not supported|Supported|
|OH_MD_KEY_VIDEO_IS_HDR_VIVID|Flag indicating whether the video stream is HDR Vivid. This key is valid only for HDR Vivid streams.|Supported|Not supported|Not supported|Supported|
|OH_MD_KEY_AUD_SAMPLE_RATE|Audio stream sample rate.|Not supported|Supported|Not supported|Supported|
|OH_MD_KEY_AUD_CHANNEL_COUNT|Number of audio stream channels.|Not supported|Supported|Not supported|Supported|
|OH_MD_KEY_CHANNEL_LAYOUT|Encoding channel layout required by the audio stream.|Not supported|Supported|Not supported|Supported|
|OH_MD_KEY_AUDIO_SAMPLE_FORMAT|Audio stream sample format.|Not supported|Supported|Not supported|Supported|
|OH_MD_KEY_AAC_IS_ADTS|AAC format. This key is valid only for AAC streams.|Not supported|Supported|Not supported|Supported|
|OH_MD_KEY_BITS_PER_CODED_SAMPLE|Number of bits per coded sample in the audio stream.|Not supported|Supported|Not supported|Supported|
|OH_MD_KEY_REFERENCE_TRACK_IDS|Reference relationship between media file tracks.|Supported|Supported|Supported|Supported|
|OH_MD_KEY_TRACK_REFERENCE_TYPE|Auxiliary track type of the media file.|Not supported|Not supported|Not supported|Supported|
|OH_MD_KEY_TRACK_DESCRIPTION|Description of the auxiliary track of the media file.|Not supported|Not supported|Not supported|Supported|
