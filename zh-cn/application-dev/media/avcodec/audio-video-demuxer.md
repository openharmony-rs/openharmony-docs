# 媒体数据解封装

<!--Kit: AVCodec Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yangjunhui10; @hanzhengshi-->
<!--Designer: @dpy2650--->
<!--Tester: @cyakee-->
<!--Adviser: @w_Machine_cc-->

开发者可以调用本模块的Native API接口，完成媒体数据的解封装相关操作，即从比特流数据中取出音频、视频、字幕等媒体sample，获得DRM相关信息。

当前支持的数据输入类型有：远程连接(http协议)和文件描述符(fd)。

当前支持的解封装格式请参考[AVCodec支持的格式](avcodec-support-formats.md#媒体数据解封装)。

**适用场景**：

- 播放
  
  播放媒体文件时，需要先对媒体流进行解封装，然后使用解封装获取的sample进行解码和播放。

- 音视频编辑
  
  编辑媒体文件时，需要先对媒体流进行解封装，获取到指定sample进行编辑。

- 媒体文件格式转换（转封装）

  媒体文件格式转换时，需要先对媒体流进行解封装，然后按需将媒体流封装至新的格式文件内。

## 开发指导

详细的API说明参考[AVDemuxer](../../reference/apis-avcodec-kit/capi-avdemuxer.md)和[AVSource](../../reference/apis-avcodec-kit/capi-avsource.md)

> **说明**
>
> - 调用解封装能力解析网络播放路径，需要[声明权限](../../security/AccessToken/declare-permissions.md)：ohos.permission.INTERNET。
> - 如需获取媒体库资源的文件描述符（fd），可参考[使用Picker选择媒体库资源](../medialibrary/photoAccessHelper-photoviewpicker.md)文档。
> - 如果使用ResourceManager.getRawFd打开HAP资源文件描述符，使用方法请参考[getRawFd](../../reference/apis-localization-kit/js-apis-resource-manager.md#getrawfd9)。

### 在CMake脚本中链接动态库

``` cmake
target_link_libraries(sample PUBLIC libnative_media_codecbase.so)
target_link_libraries(sample PUBLIC libnative_media_avdemuxer.so)
target_link_libraries(sample PUBLIC libnative_media_avsource.so)
target_link_libraries(sample PUBLIC libnative_media_core.so)
```

> **说明：**
>
> 上述'sample'字样仅为示例，此处由开发者根据实际工程目录自定义。
>

示例代码引用了示例工程中自定义的工具宏与数据结构（如CHECK_AND_RETURN_RET_LOG、AVCODEC_SAMPLE_ERR_\*、AVCODEC_SAMPLE_LOG\*、SampleInfo等），不属于SDK的接口，完整定义请参见示例工程，移植时需自行实现或替换。

### 开发步骤

1. 添加头文件。

   <!-- @[Demuxer::IncludeHeaders](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/demuxer.cpp) -->
   
   ``` C++
   #include <multimedia/player_framework/native_avdemuxer.h>
   #include <multimedia/player_framework/native_avsource.h>
   #include <multimedia/player_framework/native_avcodec_base.h>
   #include <multimedia/player_framework/native_avformat.h>
   #include <multimedia/player_framework/native_avbuffer.h>
   #include <multimedia/drm_framework/native_drm_common.h>
   #include <sys/stat.h>
   #include <fstream>
   #include <string>
   ```

2. 创建资源管理实例。

   示例支持URI（网络或本地路径）、自定义数据源（沙箱文件路径）和fd三种输入方式，按优先级依次选择。

   fd方式下offset（文件起始偏移）、fileSize（文件大小）需与待解封装文件匹配：
   - fd指向单个资源文件时，offset为0、fileSize为资源文件大小。
   - fd指向多个连续拼接的资源文件时（如多个mp3二进制拼接），offset、fileSize按待解封装文件实际偏移和大小设置。

   <!-- @[Demuxer::CreateSourceWithURI](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/demuxer.cpp) -->
   
   ``` C++
   // 为uri资源文件创建source资源实例（可选）。使用网络URI前需先在module.json5中申请Internet权限。
   source_ = OH_AVSource_CreateWithURI(const_cast<char *>(info.source.inputUri.c_str()));
   CHECK_AND_RETURN_RET_LOG(source_ != nullptr, AVCODEC_SAMPLE_ERR_ERROR,
       "Create demuxer source failed, uri: %{public}s", info.source.inputUri.c_str());
   ```

   <!-- @[Demuxer::CreateSourceWithDataSource](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/demuxer.cpp) -->
   
   ``` C++
   // 为自定义数据源创建source资源实例（可选）。使用该方式前，需要先实现AVSourceReadAt接口函数实现。
   g_filePath = info.source.inputFilePath;
   struct stat fileStatus {};
   CHECK_AND_RETURN_RET_LOG(stat(g_filePath.c_str(), &fileStatus) == 0, AVCODEC_SAMPLE_ERR_ERROR,
       "Get file status failed, path: %{public}s", g_filePath.c_str());
   OH_AVDataSource dataSource = {fileStatus.st_size, AVSourceReadAt};
   source_ = OH_AVSource_CreateWithDataSource(&dataSource);
   CHECK_AND_RETURN_RET_LOG(source_ != nullptr, AVCODEC_SAMPLE_ERR_ERROR,
       "Create demuxer source with data source failed, path: %{public}s", g_filePath.c_str());
   ```

   <!-- @[Demuxer::CreateSourceWithFD](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/demuxer.cpp) -->
   
   ``` C++
   // fd由应用侧打开后传入。offset（文件起始偏移）、fileSize（文件大小）需与待解封装文件匹配：
   // fd指向单个资源文件时，offset为0、fileSize为资源文件大小；
   // fd指向多个连续拼接的资源文件时（如多个mp3二进制拼接），offset、fileSize按实际偏移和大小设置。
   source_ = OH_AVSource_CreateWithFD(info.source.inputFd, info.source.inputFileOffset,
       info.source.inputFileSize);
   CHECK_AND_RETURN_RET_LOG(source_ != nullptr, AVCODEC_SAMPLE_ERR_ERROR,
       "Create demuxer source failed, fd: %{public}d, offset: %{public}" PRId64", file size: %{public}" PRId64,
       info.source.inputFd, info.source.inputFileOffset, info.source.inputFileSize);
   ```

   开发者HAP中使用open获取fd时，filepath需要转换为[沙箱路径](../../file-management/app-sandbox-directory.md#应用沙箱路径和真实物理路径的对应关系)，才能获取沙盒资源。

   为自定义数据源方式实现AVSourceReadAt接口函数，需要放在创建资源管理实例前实现。

   <!-- @[Demuxer::AVSourceReadAt](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/demuxer.cpp) -->
   
   ``` C++
   // 自定义数据源读取回调：按pos和length从g_filePath指向的文件读取数据填充到data。
   // 使用OH_AVSource_CreateWithDataSource创建source前需要先实现该函数，并将待解封装文件路径写入g_filePath。
   // g_filePath在Demuxer::Create中、解封装线程启动前完成赋值；当前播放链路同一时刻仅持有一个Demuxer实例。
   static std::string g_filePath;
   
   enum MediaDataSourceError : int32_t {
       SOURCE_ERROR_IO = -2,
       SOURCE_ERROR_EOF = -1
   };
   
   static int32_t AVSourceReadAt(OH_AVBuffer *data, int32_t length, int64_t pos)
   {
       // 回调可能由解封装器内部多线程触发，每次读取独立打开文件以保证线程安全。
       if (data == nullptr) {
           AVCODEC_SAMPLE_LOGW("AVSourceReadAt: data is nullptr");
           return MediaDataSourceError::SOURCE_ERROR_IO;
       }
       char *addr = reinterpret_cast<char *>(OH_AVBuffer_GetAddr(data));
       if (addr == nullptr) {
           AVCODEC_SAMPLE_LOGW("AVSourceReadAt: buffer address is nullptr");
           return MediaDataSourceError::SOURCE_ERROR_IO;
       }
       std::ifstream infile(g_filePath, std::ifstream::binary);
       if (!infile.is_open()) {
           AVCODEC_SAMPLE_LOGW("AVSourceReadAt: open file failed, file: %{public}s", g_filePath.c_str());
           return MediaDataSourceError::SOURCE_ERROR_IO;  // 打开文件失败。
       }
       infile.seekg(0, std::ios::end);
       int64_t fileSize = infile.tellg();
       if (pos >= fileSize) {
           AVCODEC_SAMPLE_LOGW("AVSourceReadAt: pos is over or equals file size");
           return MediaDataSourceError::SOURCE_ERROR_EOF;  // pos已经是文件末尾位置，无法读取。
       }
       if (pos + length > fileSize) {
           length = static_cast<int32_t>(fileSize - pos);  // pos+length超过文件大小时，读取从pos到文件末尾的数据。
       }
       infile.seekg(pos, std::ios::beg);
       if (length <= 0) {
           AVCODEC_SAMPLE_LOGW("AVSourceReadAt: read length is less than zero");
           return MediaDataSourceError::SOURCE_ERROR_IO;
       }
       infile.read(addr, length);
       return length;
   }
   ```

3. 创建解封装器实例。

   <!-- @[Demuxer::CreateDemuxer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/demuxer.cpp) -->
   
   ``` C++
   // 为资源实例创建对应的解封装器。
   demuxer_ = OH_AVDemuxer_CreateWithSource(source_);
   CHECK_AND_RETURN_RET_LOG(demuxer_ != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "Create demuxer failed");
   ```

4. （可选）注册DRM信息监听函数，接口参考[Demuxer_MediaKeySystemInfoCallback()](../../reference/apis-avcodec-kit/capi-native-avdemuxer-h.md#demuxer_mediakeysysteminfocallback)。如果不是DRM码流或已获得DRM信息，可跳过此步骤。DRM信息内容参考[DRM_MediaKeySystemInfo](../../reference/apis-drm-kit/capi-drm-drm-mediakeysysteminfo.md)。

   设置DRM信息监听的接口，回调函数支持返回解封装器实例，适用于多个解封装器场景。

   <!-- @[Demuxer::OnDrmInfoChangedWithObj](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/demuxer.cpp) -->
   
   ``` C++
   // DRM信息监听回调OnDrmInfoChangedWithObj实现。
   static void OnDrmInfoChangedWithObj(OH_AVDemuxer *demuxer, DRM_MediaKeySystemInfo *drmInfo)
   {
       // 解析DRM信息，包括数量、DRM类型及对应pssh，用于后续创建MediaKeySystem、MediaKeySession并设置解码器解密配置。
       if (drmInfo == nullptr) {
           return;
       }
       AVCODEC_SAMPLE_LOGI("Demuxer DRM info changed, demuxer: %{public}p, pssh count: %{public}u",
           static_cast<void *>(demuxer), drmInfo->psshCount);
       for (uint32_t index = 0; index < drmInfo->psshCount && index < MAX_PSSH_INFO_COUNT; index++) {
           const DRM_PsshInfo &pssh = drmInfo->psshInfo[index];
           // 将uuid逐字节转换为两个十六进制字符。
           char uuid[UUID_TEXT_LEN] = {0};
           for (uint32_t uuidIndex = 0; uuidIndex < DRM_UUID_LEN; uuidIndex++) {
               const uint8_t byte = pssh.uuid[uuidIndex];
               uuid[uuidIndex * UUID_HEX_LEN_PER_BYTE] = HEX_DIGITS[byte >> BITS_PER_HEX_DIGIT];
               uuid[uuidIndex * UUID_HEX_LEN_PER_BYTE + LOW_NIBBLE_OFFSET] = HEX_DIGITS[byte & HEX_DIGIT_MASK];
           }
           AVCODEC_SAMPLE_LOGI("Demuxer DRM pssh[%{public}u] uuid: %{public}s, dataLen: %{public}d", index, uuid,
               pssh.dataLen);
       }
   }
   ```

   <!-- @[Demuxer::SetDemuxerMediaKeySystemInfoCallback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/demuxer.cpp) -->
   
   ``` C++
   // 注册DRM信息监听回调（可选，非DRM码流不会触发）。回调返回解封装器实例，适用于多个解封装器场景。
   Demuxer_MediaKeySystemInfoCallback callback = &OnDrmInfoChangedWithObj;
   OH_AVErrCode drmRet = OH_AVDemuxer_SetDemuxerMediaKeySystemInfoCallback(demuxer_, callback);
   if (drmRet != AV_ERR_OK) {
       AVCODEC_SAMPLE_LOGW("Set demuxer media key system info callback failed, ret: %{public}d", drmRet);
   }
   ```

   在监听到DRM信息后，也可主动调用获取DRM信息（uuid及对应pssh）接口。

   <!-- @[Demuxer::GetMediaKeySystemInfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/demuxer.cpp) -->
   
   ``` C++
   int32_t Demuxer::GetMediaKeySystemInfo(DRM_MediaKeySystemInfo &mediaKeySystemInfo)
   {
       std::lock_guard<std::mutex> lock(demuxerMutex_);
       CHECK_AND_RETURN_RET_LOG(demuxer_ != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "Demuxer is null");
       // 在监听到DRM信息后，可主动调用该接口获取DRM信息（uuid及对应pssh）。
       OH_AVErrCode ret = OH_AVDemuxer_GetMediaKeySystemInfo(demuxer_, &mediaKeySystemInfo);
       CHECK_AND_RETURN_RET_LOG(ret == AV_ERR_OK, AVCODEC_SAMPLE_ERR_ERROR,
           "Get media key system info failed, ret: %{public}d", ret);
       return AVCODEC_SAMPLE_ERR_OK;
   }
   ```

   在获取、解析DRM信息后，需创建对应DRM解决方案的[MediaKeySystem、MediaKeySession](../drm/drm-c-dev-guide.md)，获取DRM许可证等。并根据需要设置音频解密配置(详见异步模式音频解码的[开发步骤](audio-decoding.md#开发步骤)第4步)、设置视频解密配置（详见异步模式视频解码的[Surface模式](video-decoding.md#surface模式)第5步或[Buffer模式](video-decoding.md#buffer模式)第4步），实现DRM内容解密。

5. 获取文件信息。

   获取文件用户自定义属性（可选，若用户无需获取自定义属性，可跳过此步）。

   > **注意：**
   > - customKey需与封装时写入的key完全一致（含完整命名层级）。例如，封装时写入key为“com.openharmony.custom.meta.abc.efg”，获取时必须使用完整key，截断使用“com.openharmony.custom.meta.abc”会失败。
   > - value类型需与封装时数据类型匹配，示例为string类型。其余类型需调用对应接口，支持int/float类型。API版本20开始，支持buffer类型。

   <!-- @[Demuxer::GetCustomMetadataFormat](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/demuxer.cpp) -->
   
   ``` C++
   // 获取文件用户自定义属性（可选，仅当封装时写入了自定义属性时返回非空）。
   // customKey需与封装时写入的key完全一致（含完整命名层级），value类型需与封装时数据类型匹配。
   std::shared_ptr<OH_AVFormat> customMetadataFormat(OH_AVSource_GetCustomMetadataFormat(source_),
       OH_AVFormat_Destroy);
   if (customMetadataFormat != nullptr) {
       info.source.customMetadataDump = CopyFormatDump(customMetadataFormat.get());
       AVCODEC_SAMPLE_LOGI("Custom metadata: %{public}s", info.source.customMetadataDump.c_str());
   }
   ```

   获取文件轨道数等文件级属性（可选，若用户已知轨道信息，可跳过此步），具体支持信息参考[文件级别属性支持范围](#文件级别属性支持范围)。trackCount为0表示文件中无轨道，需根据业务做其他处理。

   <!-- @[Demuxer::GetSourceFormat](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/demuxer.cpp) -->
   
   ``` C++
   // 获取文件级属性（sourceFormat），轨道数、时长等从中读取。
   auto sourceFormat = std::shared_ptr<OH_AVFormat>(OH_AVSource_GetSourceFormat(source_), OH_AVFormat_Destroy);
   CHECK_AND_RETURN_RET_LOG(sourceFormat != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "Get source format failed");
   ```

   <!-- @[Demuxer::GetTrackCount](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/demuxer.cpp) -->
   
   ``` C++
   // 获取文件轨道数等文件级属性（可选，若用户已知轨道信息，可跳过此步）。
   // trackCount为0表示文件中无轨道，需根据业务做其他处理。
   OH_AVFormat_GetLongValue(sourceFormat.get(), OH_MD_KEY_DURATION, &info.source.durationUs);
   OH_AVFormat_GetIntValue(sourceFormat.get(), OH_MD_KEY_TRACK_COUNT, &info.source.trackCount);
   info.source.sourceFormatDump = CopyFormatDump(sourceFormat.get());
   ```

6. 获取轨道index及信息（可选，若用户已知轨道信息，可跳过此步）。

   遍历轨道获取轨道级属性，具体支持信息参考[轨道级别属性支持范围](#轨道级别属性支持范围)。不支持的类型不会修改trackType的值，注意trackType初始值建议设为非有效值（如-1），避免误用。

   <!-- @[Demuxer::GetTrackInfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/demuxer.cpp) -->
   
   ``` C++
   // 遍历轨道获取轨道级属性。不支持的类型不会修改trackType的值，
   // trackType初始值建议设为非有效值（如-1），避免误用。
   info.source.trackFormats.clear();
   for (int32_t index = 0; index < info.source.trackCount; index++) {
       auto trackFormat = GetTrackFormat(index);
       if (trackFormat == nullptr) {
           AVCODEC_SAMPLE_LOGW("Get track format failed, index: %{public}d", index);
           continue;
       }
       int trackType = GetTrackType(trackFormat);
       SaveTrackFormat(trackFormat, index, trackType, info);
       if (trackType == MEDIA_TYPE_VID) {
           ProcessVideoTrack(trackFormat, index, info);
       } else if (trackType == MEDIA_TYPE_AUD) {
           ProcessAudioTrack(trackFormat, index, info);
       }
   }
   return AVCODEC_SAMPLE_ERR_OK;
   ```

   获取辅助轨参考关系：referenceType为辅助轨类型，referenceIds为被参考的轨道ID，可根据辅助轨类型处理轨道参考关系。

   <!-- @[Demuxer::SaveTrackFormat](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/demuxer.cpp) -->
   
   ``` C++
   void Demuxer::SaveTrackFormat(std::shared_ptr<OH_AVFormat> trackFormat, int32_t index, int32_t trackType,
       SampleInfo &info)
   {
       MediaTrackFormatInfo trackInfo;
       trackInfo.trackIndex = index;
       trackInfo.trackType = trackType;
       char *codecMime = nullptr;
       OH_AVFormat_GetStringValue(trackFormat.get(), OH_MD_KEY_CODEC_MIME, const_cast<char const **>(&codecMime));
       trackInfo.codecMime = codecMime == nullptr ? "" : codecMime;
       // 辅助轨：根据辅助轨类型处理轨道参考关系。
       // referenceType为辅助轨类型，referenceIds为被参考的轨道ID。
       if (trackType == MEDIA_TYPE_AUXILIARY) {
           const char *referenceType = nullptr;
           if (OH_AVFormat_GetStringValue(trackFormat.get(), OH_MD_KEY_TRACK_REFERENCE_TYPE, &referenceType) &&
               referenceType != nullptr) {
               trackInfo.referenceType = referenceType;
           }
           int32_t *referenceIds = nullptr;
           size_t referenceIdsCount = 0;
           if (OH_AVFormat_GetIntBuffer(trackFormat.get(), OH_MD_KEY_REFERENCE_TRACK_IDS, &referenceIds,
               &referenceIdsCount) && referenceIds != nullptr) {
               trackInfo.referenceTrackIds.assign(referenceIds, referenceIds + referenceIdsCount);
           }
           AVCODEC_SAMPLE_LOGI("Auxiliary track, index: %{public}d, reference type: %{public}s, reference track count: "
               "%{public}zu", index, trackInfo.referenceType.c_str(), trackInfo.referenceTrackIds.size());
       }
       if (trackType == MEDIA_TYPE_AUD) {
           OH_AVFormat_GetIntValue(trackFormat.get(), OH_MD_KEY_AUD_SAMPLE_RATE, &trackInfo.audioSampleRate);
           OH_AVFormat_GetIntValue(trackFormat.get(), OH_MD_KEY_AUD_CHANNEL_COUNT, &trackInfo.audioChannelCount);
       }
       OH_AVFormat_GetLongValue(trackFormat.get(), OH_MD_KEY_BITRATE, &trackInfo.bitrate);
       trackInfo.formatDump = CopyFormatDump(trackFormat.get());
       info.source.trackFormats.push_back(std::move(trackInfo));
   }
   ```

   获取视频轨宽高、比特率、帧率、mimetype及codecConfig等属性。

   <!-- @[Demuxer::ProcessVideoTrack](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/demuxer.cpp) -->
   
   ``` C++
   void Demuxer::ProcessVideoTrack(std::shared_ptr<OH_AVFormat> trackFormat, int32_t index, SampleInfo &info)
   {
       OH_AVDemuxer_SelectTrackByID(demuxer_, index);
   
       char *videoCodecMime = nullptr;
       OH_AVFormat_GetStringValue(trackFormat.get(), OH_MD_KEY_CODEC_MIME, const_cast<char const **>(&videoCodecMime));
       if (videoCodecMime == nullptr || strncmp(videoCodecMime, "video/", strlen("video/")) != 0) {
           AVCODEC_SAMPLE_LOGW("Not a video track, mime: %{public}s", videoCodecMime);
           return;
       }
   
       OH_AVFormat_GetIntValue(trackFormat.get(), OH_MD_KEY_WIDTH, &info.video.videoWidth);
       OH_AVFormat_GetIntValue(trackFormat.get(), OH_MD_KEY_HEIGHT, &info.video.videoHeight);
       OH_AVFormat_GetDoubleValue(trackFormat.get(), OH_MD_KEY_FRAME_RATE, &info.video.frameRate);
       OH_AVFormat_GetLongValue(trackFormat.get(), OH_MD_KEY_BITRATE, &info.video.bitrate);
       OH_AVFormat_GetIntValue(trackFormat.get(), OH_MD_KEY_ROTATION, &info.video.rotation);
       int32_t colorPrimary = static_cast<int32_t>(info.video.primary);
       if (OH_AVFormat_GetIntValue(trackFormat.get(), OH_MD_KEY_COLOR_PRIMARIES, &colorPrimary)) {
           info.video.primary = static_cast<OH_ColorPrimary>(colorPrimary);
       }
       int32_t transfer = static_cast<int32_t>(info.video.transfer);
       if (OH_AVFormat_GetIntValue(trackFormat.get(), OH_MD_KEY_TRANSFER_CHARACTERISTICS, &transfer)) {
           info.video.transfer = static_cast<OH_TransferCharacteristic>(transfer);
       }
       int32_t matrix = static_cast<int32_t>(info.video.matrix);
       if (OH_AVFormat_GetIntValue(trackFormat.get(), OH_MD_KEY_MATRIX_COEFFICIENTS, &matrix)) {
           info.video.matrix = static_cast<OH_MatrixCoefficient>(matrix);
       }
       OH_AVFormat_GetIntValue(trackFormat.get(), OH_MD_KEY_RANGE_FLAG, &info.video.rangFlag);
       int32_t hdrVividContainerSignaled = 0;
       if (OH_AVFormat_GetIntValue(trackFormat.get(), OH_MD_KEY_VIDEO_IS_HDR_VIVID,
           &hdrVividContainerSignaled)) {
           info.video.hdrVividContainerSignaled = hdrVividContainerSignaled == 1;
       }
   
       info.video.videoCodecMime = videoCodecMime;
       OH_AVFormat_GetIntValue(trackFormat.get(), OH_MD_KEY_PROFILE, &info.video.hevcProfile);
       videoTrackId_ = index;
   
       LogVideoConfig(info, videoCodecMime);
   }
   ```

7. 添加解封装轨道。

   示例中视频轨与默认音轨在创建阶段（参考步骤2、3）内选择；切换音轨时调用如下SelectAudioTrack函数，内部会先调用OH_AVDemuxer_UnselectTrackByID取消旧音轨再调用OH_AVDemuxer_SelectTrackByID选择新音轨，选择失败时回滚（重新选择旧音轨）。

   <!-- @[Demuxer::SelectAudioTrack](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/demuxer.cpp) -->
   
   ``` C++
   int32_t Demuxer::SelectAudioTrack(int32_t trackIndex, SampleInfo &info)
   {
       std::lock_guard<std::mutex> lock(demuxerMutex_);
       CHECK_AND_RETURN_RET_LOG(demuxer_ != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "Demuxer is null");
       auto trackFormat = GetTrackFormat(trackIndex);
       CHECK_AND_RETURN_RET_LOG(trackFormat != nullptr, AVCODEC_SAMPLE_ERR_ERROR,
           "Get audio track format failed, index: %{public}d", trackIndex);
       CHECK_AND_RETURN_RET_LOG(GetTrackType(trackFormat) == MEDIA_TYPE_AUD, AVCODEC_SAMPLE_ERR_ERROR,
           "Selected track is not an audio track, index: %{public}d", trackIndex);
       // 先解析到临时对象。切换失败时，当前元数据和Demuxer已选轨集合必须保持不变。
       SampleInfo candidateInfo = info;
       CHECK_AND_RETURN_RET_LOG(PopulateAudioTrackInfo(trackFormat, trackIndex, candidateInfo) == AVCODEC_SAMPLE_ERR_OK,
           AVCODEC_SAMPLE_ERR_ERROR, "Parse audio track failed, index: %{public}d", trackIndex);
   
       // Seek和ReadSample要求轨道处于选中状态。先取消旧音轨，否则Demuxer会继续推进旧流。
       const int32_t previousTrackId = audioTrackId_;
       if (previousTrackId >= 0 && previousTrackId != trackIndex) {
           OH_AVDemuxer_UnselectTrackByID(demuxer_, static_cast<uint32_t>(previousTrackId));
       }
       if (OH_AVDemuxer_SelectTrackByID(demuxer_, static_cast<uint32_t>(trackIndex)) != AV_ERR_OK) {
           if (previousTrackId >= 0) {
               OH_AVDemuxer_SelectTrackByID(demuxer_, static_cast<uint32_t>(previousTrackId));
           }
           AVCODEC_SAMPLE_LOGE("Select audio track failed, index: %{public}d", trackIndex);
           return AVCODEC_SAMPLE_ERR_ERROR;
       }
   
       info.audio = candidateInfo.audio;
       // 读取音频样本时使用此容器轨道ID，因此必须和上方选中的元数据同步。
       audioTrackId_ = trackIndex;
       LogAudioConfig(info, info.audio.audioCodecMime.c_str());
       return AVCODEC_SAMPLE_ERR_OK;
   }
   ```

8. 调整轨道到指定时间点（可选）。

   <!-- @[Demuxer::Seek](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/demuxer.cpp) -->
   
   ``` C++
   int32_t Demuxer::Seek(int64_t positionMs, OH_AVSeekMode mode)
   {
       std::lock_guard<std::mutex> lock(demuxerMutex_);
       CHECK_AND_RETURN_RET_LOG(demuxer_ != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "Demuxer is null");
       int32_t ret = OH_AVDemuxer_SeekToTime(demuxer_, positionMs, mode);
       if (ret == AV_ERR_OK) {
           AVCODEC_SAMPLE_LOGI("Demuxer seek succeeded: position=%{public}lld ms, mode=%{public}d, "
               "video track=%{public}d, audio track=%{public}d", static_cast<long long>(positionMs),
               static_cast<int32_t>(mode), videoTrackId_, audioTrackId_);
           return AVCODEC_SAMPLE_ERR_OK;
       }
       AVCODEC_SAMPLE_LOGW("Demuxer seek failed: position=%{public}lld ms, mode=%{public}d, ret=%{public}d, "
           "video track=%{public}d, audio track=%{public}d", static_cast<long long>(positionMs),
           static_cast<int32_t>(mode), ret, videoTrackId_, audioTrackId_);
       // 精确定位通常从前一个同步帧开始。部分MP4索引无法提供该帧，但仍能提供邻近或后续同步帧。
       // 仅当前序同步帧请求失败后才重试，常规Seek仍优先使用前序同步帧。
       if (mode != SEEK_MODE_PREVIOUS_SYNC) {
           return AVCODEC_SAMPLE_ERR_ERROR;
       }
       ret = OH_AVDemuxer_SeekToTime(demuxer_, positionMs, SEEK_MODE_CLOSEST_SYNC);
       if (ret == AV_ERR_OK) {
           AVCODEC_SAMPLE_LOGW("Demuxer seek recovered with closest sync sample: position=%{public}lld ms",
               static_cast<long long>(positionMs));
           return AVCODEC_SAMPLE_ERR_OK;
       }
       ret = OH_AVDemuxer_SeekToTime(demuxer_, positionMs, SEEK_MODE_NEXT_SYNC);
       if (ret == AV_ERR_OK) {
           AVCODEC_SAMPLE_LOGW("Demuxer seek recovered with following sync sample: position=%{public}lld ms",
               static_cast<long long>(positionMs));
           return AVCODEC_SAMPLE_ERR_OK;
       }
       AVCODEC_SAMPLE_LOGE("Demuxer seek fallback failed: position=%{public}lld ms, ret=%{public}d",
           static_cast<long long>(positionMs), ret);
       return AVCODEC_SAMPLE_ERR_ERROR;
   }
   ```

   > **注意：**
   >
   > 1. mpegts、mpg格式文件使用OH_AVDemuxer_SeekToTime功能时，跳转到的位置可能为非关键帧。可在跳转后调用OH_AVDemuxer_ReadSampleBuffer，通过获取到的OH_AVCodecBufferAttr判断当前帧是否为关键帧。若非关键帧影响应用侧显示等功能，可在跳转后循环读取，获取到后续第一帧关键帧后，再进行解码等处理。
   >
   > 2. ogg格式文件使用OH_AVDemuxer_SeekToTime功能时，会跳转到传入时间millisecond所在时间间隔(秒)的起始处，可能会导致一定数量的帧误差。
   >
   > 3. demuxer的seek处理只针对解码行为一致的码流进行处理，如果seek后需要解码器重新配置参数，或者需要重新送入参数集的数据才可以正确解码的码流，seek后可能会出现花屏、解码卡死等问题。

9. 开始解封装，循环获取sample（以含音频、视频两轨的文件为例）。

   BufferAttr包含的属性：
   - size：sample尺寸；
   - offset：数据在AVBuffer中的偏移，一般为0；
   - pts：文件封装的显示时间戳；
   - flags：sample属性。

   | flag | 描述 |
   | -------- | -------- |
   | AVCODEC_BUFFER_FLAGS_NONE | 默认。 |
   | AVCODEC_BUFFER_FLAGS_EOS | 结尾sample，数据为空。 |
   | AVCODEC_BUFFER_FLAGS_SYNC_FRAME | IDR帧或I帧。 |
   | AVCODEC_BUFFER_FLAGS_INCOMPLETE_FRAME | 非完整的sample，一般由于buffer过小，无法拷贝完整的sample。 |
   | AVCODEC_BUFFER_FLAGS_CODEC_DATA | 含参数集信息的帧。 |
   | AVCODEC_BUFFER_FLAGS_DISCARD  | 可丢弃的帧。 |

   OH_AVDemuxer_ReadSampleBuffer接口本身可能存在耗时久，取决于文件IO，建议以异步方式进行调用。

   示例在音频、视频各自的解码器输入线程中读取sample（读取前需选中轨道）：

   <!-- @[Demuxer::ReadSample](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/demuxer.cpp) -->
   
   ``` C++
   int32_t Demuxer::ReadSample(int32_t trackId, OH_AVBuffer *buffer, OH_AVCodecBufferAttr &attr)
   {
       // 在调用OH_AVDemuxer_ReadSampleBuffer接口获取数据前，需要先调用OH_AVDemuxer_SelectTrackByID选中需要获取数据的轨道。
       // 注意：在avi、mpg、wmv格式下，由于容器标准不支持封装时间戳信息，
       // demuxer解出的帧中不含pts信息，需要调用方根据帧率及解码出帧后的显示顺序自行计算显示时间戳信息。
       std::lock_guard<std::mutex> lock(demuxerMutex_);
       CHECK_AND_RETURN_RET_LOG(demuxer_ != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "Demuxer is null");
       int32_t ret = OH_AVDemuxer_ReadSampleBuffer(demuxer_, trackId, buffer);
       CHECK_AND_RETURN_RET_LOG(ret == AV_ERR_OK, AVCODEC_SAMPLE_ERR_ERROR, "Read sample failed");
       ret = OH_AVBuffer_GetBufferAttr(buffer, &attr);
       CHECK_AND_RETURN_RET_LOG(ret == AV_ERR_OK, AVCODEC_SAMPLE_ERR_ERROR, "GetBufferAttr failed");
       return AVCODEC_SAMPLE_ERR_OK;
   }
   ```

   <!-- @[Player::AudioDecInputThread](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/sample/player/output/audio/PlayerAudioOutput.cpp) -->
   
   ``` C++
   void Player::AudioDecInputThread()
   {
       while (isStarted_ && audioWorkerRunning_) {
           WaitIfPaused(true);
           CHECK_AND_BREAK_LOG(isStarted_ && audioWorkerRunning_, "Decoder input thread out");
           std::shared_ptr<CodecBufferInfo> bufferInfo = audioDecContext_->inputBufferQueue.Dequeue();
           std::shared_lock<std::shared_mutex> codecLock(audioDecContext_->codecMutex);
           CHECK_AND_BREAK_LOG(isStarted_ && audioWorkerRunning_, "Work done, thread out");
           CHECK_AND_CONTINUE_LOG(bufferInfo != nullptr, "Buffer queue is empty, continue");
           audioDecContext_->inputFrameCount++;
           int32_t ret = demuxer_->ReadSample(demuxer_->GetAudioTrackId(), bufferInfo->buffer, bufferInfo->attr);
           if (ret != AVCODEC_SAMPLE_ERR_OK) {
               AVCODEC_SAMPLE_LOGE("Read audio sample failed");
               playbackFailed_ = true;
               isStarted_ = false;
               break;
           }
           ret = audioDecoder_->PushInputBuffer(*bufferInfo);
           if (ret != AVCODEC_SAMPLE_ERR_OK) {
               playbackFailed_ = true;
               isStarted_ = false;
               break;
           }
           CHECK_AND_BREAK_LOG(!(bufferInfo->attr.flags & AVCODEC_BUFFER_FLAGS_EOS), "Catch EOS, thread out");
       }
   }
   ```

10. 销毁解封装实例。

    <!-- @[Demuxer::Release](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVCodec/AVCodec/entry/src/main/cpp/capabilities/demuxer.cpp) -->
    
    ``` C++
    int32_t Demuxer::Release()
    {
        std::lock_guard<std::mutex> lock(demuxerMutex_);
        // 需要用户调用OH_AVDemuxer_Destroy接口成功后，手动将实例置为nullptr，对同一实例重复调用会导致程序错误。
        // Demuxer必须先于Source销毁；fd由应用侧管理，不由解封装模块关闭。
        if (demuxer_ != nullptr) {
            OH_AVDemuxer_Destroy(demuxer_);
            demuxer_ = nullptr;
        }
        if (source_ != nullptr) {
            OH_AVSource_Destroy(source_);
            source_ = nullptr;
        }
        return AVCODEC_SAMPLE_ERR_OK;
    }
    ```

    > **说明：**
    >
    > - 调用OH_AVSource_Destroy、OH_AVDemuxer_Destroy接口成功后，需要手动将实例设置为nullptr。
    >
    > - 对同一实例重复调用会导致程序错误。
    >
    > - Demuxer必须先于Source销毁。
    >
    > - fd由应用侧管理，不由解封装模块关闭。

## 附表
### 文件级别属性支持范围

> **说明：**
>
> - 正常解封装时才可以获取对应属性数据，如果文件信息错误或缺失，将导致解封装异常，无法获取数据。
> - 当前GBK格式字符集数据会转换为UTF8提供，其他类型字符集如果需要转换为UTF8格式使用，需要调用方自行转换，参考[icu4c](../../reference/native-lib/icu4c.md)。
> - 从API version 23开始，部分OGG格式资源，如OH_MD_KEY_TITLE、OH_MD_KEY_ARTIST和OH_MD_KEY_ALBUM存在于轨道属性中，可从轨道级别属性中获取。
> - 数据类型及详细取值范围参考[媒体数据键值对](../../reference/apis-avcodec-kit/capi-codecbase.md#媒体数据键值对)。

**表1** 文件级别属性支持范围
| 名称 | 描述 |
| -- | -- |
|OH_MD_KEY_TITLE|文件标题的键|
|OH_MD_KEY_ARTIST|文件艺术家的键|
|OH_MD_KEY_ALBUM|文件专辑的键|
|OH_MD_KEY_ALBUM_ARTIST|文件专辑艺术家的键|
|OH_MD_KEY_DATE|文件日期的键|
|OH_MD_KEY_COMMENT|文件注释的键|
|OH_MD_KEY_GENRE|文件流派的键|
|OH_MD_KEY_COPYRIGHT|文件版权的键|
|OH_MD_KEY_LANGUAGE|文件语言的键|
|OH_MD_KEY_DESCRIPTION|文件描述的键|
|OH_MD_KEY_LYRICS|文件歌词的键|
|OH_MD_KEY_TRACK_COUNT|文件轨道数量的键|
|OH_MD_KEY_DURATION|文件时长的键|
|OH_MD_KEY_START_TIME|文件起始时间的键|

### 轨道级别属性支持范围

> **说明：**
>
> 正常解封装时才可以获取对应属性数据；如果文件信息错误或缺失，将导致解封装异常，无法获取数据。
> 辅助轨属性范围与实际媒体类型（音频、视频）保持一致。
> 
> 数据类型及详细取值范围参考[媒体数据键值对](../../reference/apis-avcodec-kit/capi-codecbase.md#媒体数据键值对)。

**表2** 轨道级别属性支持范围
| 名称 | 描述 | 视频轨支持 | 音频轨支持 | 字幕轨支持 | 辅助轨支持 |
| -- | -- | -- | -- | -- | -- |
|OH_MD_KEY_CODEC_MIME|码流编解码器类型的键。|√|√|√|√|
|OH_MD_KEY_TRACK_TYPE|码流媒体类型的键。|√|√|√|√|
|OH_MD_KEY_TRACK_START_TIME|码流起始时间的键。|√|√|√|√|
|OH_MD_KEY_BITRATE|码流比特率的键。|√|√|-|√|
|OH_MD_KEY_LANGUAGE|码流语言类型的键。|√|√|-|√|
|OH_MD_KEY_CODEC_CONFIG|编解码器特定数据的键，视频中表示传递参数集，音频中表示传递解码器的参数配置信息。|√|√|-|√|
|OH_MD_KEY_WIDTH|视频流宽度的键。|√|-|-|√|
|OH_MD_KEY_HEIGHT|视频流高度的键。|√|-|-|√|
|OH_MD_KEY_FRAME_RATE|视频流帧率的键。|√|-|-|√|
|OH_MD_KEY_ROTATION|视频流旋转角度的键。|√|-|-|√|
|OH_MD_KEY_VIDEO_SAR|视频流样本长宽比的键。|√|-|-|√|
|OH_MD_KEY_PROFILE|视频流编码档次，只针对h265码流使用。|√|-|-|√|
|OH_MD_KEY_RANGE_FLAG|视频流视频YUV值域标志的键，只针对h265码流使用。|√|-|-|√|
|OH_MD_KEY_COLOR_PRIMARIES|视频流视频色域的键，只针对h265码流使用。|√|-|-|√|
|OH_MD_KEY_TRANSFER_CHARACTERISTICS|视频流视频传递函数的键，只针对h265码流使用。|√|-|-|√|
|OH_MD_KEY_MATRIX_COEFFICIENTS|视频矩阵系数的键，只针对h265码流使用。|√|-|-|√|
|OH_MD_KEY_VIDEO_IS_HDR_VIVID|视频流标记是否为HDR Vivid的键，只针对HDR Vivid码流使用。|√|-|-|√|
|OH_MD_KEY_AUD_SAMPLE_RATE|音频流采样率的键。|-|√|-|√|
|OH_MD_KEY_AUD_CHANNEL_COUNT|音频流通道数的键。|-|√|-|√|
|OH_MD_KEY_CHANNEL_LAYOUT|音频流所需编码通道布局的键。|-|√|-|√|
|OH_MD_KEY_AUDIO_SAMPLE_FORMAT|音频流样本格式的键。|-|√|-|√|
|OH_MD_KEY_AAC_IS_ADTS|aac格式的键，只针对aac码流使用。|-|√|-|√|
|OH_MD_KEY_BITS_PER_CODED_SAMPLE|音频流每个编码样本位数的键。|-|√|-|√|
|OH_MD_KEY_REFERENCE_TRACK_IDS|媒体文件轨道间参考、被参考关系。|√|√|√|√|
|OH_MD_KEY_TRACK_REFERENCE_TYPE|媒体文件辅助轨类型。|-|-|-|√|
|OH_MD_KEY_TRACK_DESCRIPTION|媒体文件辅助轨描述信息。|-|-|-|√|
