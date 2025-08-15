# 音频编码

<!--Kit: AVCodec Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @mr-chencxy-->
<!--Designer: @dpy2650--->
<!--Tester: @baotianhao-->
<!--Adviser: @zengyawen-->

开发者可以调用本模块的Native API接口，完成音频编码，即将音频PCM编码压缩成不同的格式。

接口不限制PCM数据的来源，开发者可以调用麦克风录制获取、也可以导入编辑后的PCM数据，通过音频编码，输出对应格式的码流，最后封装为目标格式文件。

当前支持的编码能力请参考[AVCodec支持的格式](avcodec-support-formats.md#音频编码)。

**适用场景**

- 音频录制

  通过录制传入PCM，然后编码出对应格式的码流，最后[封装](audio-video-muxer.md)成想要的格式。
- 音频编辑

  编辑PCM后导出音频文件的场景，需要编码成对应音频格式后再[封装](audio-video-muxer.md)成文件。
> **说明：**
>
> AAC编码器默认采用的VBR可变码率模式，与配置的预期参数可能存在偏差。

## 开发指导

详细的API说明请参考[API文档](../../reference/apis-avcodec-kit/_audio_codec.md)。

参考以下示例代码，完成音频编码的全流程，包括：创建编码器、设置编码参数（采样率/码率/声道数等）、开始、刷新、重置、销毁资源。

在应用开发过程中，开发者应按一定顺序调用方法，执行对应操作，否则系统可能会抛出异常或生成其他未定义的行为。具体顺序可参考下列开发步骤及对应说明。

如下为音频编码调用关系图：

- 虚线表示可选。

- 实线表示必选。

![Invoking relationship of audio encode stream](figures/audio-codec.png)

### 在 CMake 脚本中链接动态库

```cmake
target_link_libraries(sample PUBLIC libnative_media_codecbase.so)
target_link_libraries(sample PUBLIC libnative_media_core.so)
target_link_libraries(sample PUBLIC libnative_media_acodec.so)
```
> **说明：**
>
> 上述'sample'字样仅为示例，此处由开发者根据实际工程目录自定义。

### 开发步骤

1. 添加头文件。

    ```cpp
    #include <multimedia/player_framework/native_avcodec_audiocodec.h>
    #include <multimedia/native_audio_channel_layout.h>
    #include <multimedia/player_framework/native_avcapability.h>
    #include <multimedia/player_framework/native_avcodec_base.h>
    #include <multimedia/player_framework/native_avformat.h>
    #include <multimedia/player_framework/native_avbuffer.h>
    ```

2. 创建编码器实例对象，OH_AVCodec *为编码器实例指针。

   应用可以通过媒体类型或编解码器名称创建编码器。

   方法一：通过 Mimetype 创建编码器。
    ```cpp
    // 设置判定是否为编码；设置true表示当前是编码。
    bool isEncoder = true;
    // 通过媒体类型创建编码器。
    OH_AVCodec *audioEnc_ = OH_AudioCodec_CreateByMime(OH_AVCODEC_MIMETYPE_AUDIO_AAC, isEncoder);
    ```
   方法二：通过 codec name 创建编码器。
    ```cpp
    // 通过 codecname 创建编码器。
    OH_AVCapability *capability = OH_AVCodec_GetCapability(OH_AVCODEC_MIMETYPE_AUDIO_AAC, true);
    const char *name = OH_AVCapability_GetName(capability);
    OH_AVCodec *audioEnc_ = OH_AudioCodec_CreateByName(name);
    ```
   添加头文件和命名空间:
    ```cpp
    #include <mutex>
    #include <queue>
    // c++标准库命名空间。
    using namespace std;
    ```
   示例代码：
    ```cpp
    // 初始化队列。
    class AEncBufferSignal {
    public:
        std::mutex inMutex_;
        std::mutex outMutex_;
        std::mutex startMutex_;
        std::condition_variable inCond_;
        std::condition_variable outCond_;
        std::condition_variable startCond_;
        std::queue<uint32_t> inQueue_;
        std::queue<uint32_t> outQueue_;
        std::queue<OH_AVBuffer *> inBufferQueue_;
        std::queue<OH_AVBuffer *> outBufferQueue_;
    };
    AEncBufferSignal *signal_;
    ```

3. 调用OH_AudioCodec_RegisterCallback()注册回调函数。

   注册回调函数指针集合OH_AVCodecCallback，包括：

   - OH_AVCodecOnError：编码器运行错误。
   - OH_AVCodecOnStreamChanged：音频编码器暂未支持此回调。
   - OH_AVCodecOnNeedInputBuffer：运行过程中需要新的输入数据，即编码器已准备好，可以输入PCM数据。
   - OH_AVCodecOnNewOutputBuffer：运行过程中产生了新的输出数据，即编码完成。

   开发者可以通过处理该回调报告的信息，确保编码器正常运转。

   > **注意：**
   > 回调中不建议进行耗时操作。

    ```cpp
    // OH_AVCodecOnError回调函数的实现。
    static void OnError(OH_AVCodec *codec, int32_t errorCode, void *userData)
    {
        (void)codec;
        (void)errorCode;
        (void)userData;
    }
    // OH_AVCodecOnStreamChanged回调函数的实现。
    static void OnOutputFormatChanged(OH_AVCodec *codec, OH_AVFormat *format, void *userData)
    {
        (void)codec;
        (void)format;
        (void)userData;
    }
    // OH_AVCodecOnNeedInputBuffer回调函数的实现。
    static void OnInputBufferAvailable(OH_AVCodec *codec, uint32_t index, OH_AVBuffer *data, void *userData)
    {
        (void)codec;
        // 编码输入码流送入InputBuffer队列。
        AEncBufferSignal *signal = static_cast<AEncBufferSignal *>(userData);
        unique_lock<mutex> lock(signal->inMutex_);
        signal->inQueue_.push(index);
        signal->inBufferQueue_.push(data);
        signal->inCond_.notify_all();
    }
    // OH_AVCodecOnNewOutputBuffer回调函数的实现。
    static void OnOutputBufferAvailable(OH_AVCodec *codec, uint32_t index, OH_AVBuffer *data, void *userData)
    {
        (void)codec;
        // 将对应输出buffer的index送入OutputQueue_队列。
        // 将对应编码完成的数据data送入outBuffer队列。
        AEncBufferSignal *signal = static_cast<AEncBufferSignal *>(userData);
        unique_lock<mutex> lock(signal->outMutex_);
        signal->outQueue_.push(index);
        signal->outBufferQueue_.push(data);
        signal->outCond_.notify_all();
    }
    ```
    配置回调：
    ```cpp
    signal_ = new AEncBufferSignal();
    OH_AVCodecCallback cb_ = {&OnError, &OnOutputFormatChanged, &OnInputBufferAvailable, &OnOutputBufferAvailable};
    // 配置异步回调。
    int32_t ret = OH_AudioCodec_RegisterCallback(audioEnc_, cb_, signal_);
    if (ret != AV_ERR_OK) {
        // 异常处理。
    }
    ```

4. 调用OH_AudioCodec_Configure设置编码器。

   配置选项key值说明：

   <!--RP2-->
   |             key               |       描述       |  AAC  |  Flac | MPEG(MP3) | G711mu |
   | ----------------------------- | :--------------: | :---: | :---: | :------: | :---: |
   | OH_MD_KEY_AUD_SAMPLE_RATE     |      采样率      |  必须  |  必须 |   必须   |  必须  |
   | OH_MD_KEY_AUD_CHANNEL_COUNT   |      声道数      |  必须  |  必须 |   必须   |  必须  |
   | OH_MD_KEY_AUDIO_SAMPLE_FORMAT |  输出音频流格式   |  必须  |  必须 |   必须   |  必须  |
   | OH_MD_KEY_BITRATE             |       码率       |  可选  |  必须 |   必须   |   -   |
   | OH_MD_KEY_CHANNEL_LAYOUT      |     声道布局     |  可选  |  必须 |    -     |   -   |
   | OH_MD_KEY_MAX_INPUT_SIZE      |   最大输入长度    |  可选  |  可选 |   可选   |  可选  |
   | OH_MD_KEY_AAC_IS_ADTS         |     是否adts     |  可选  |   -   |    -    |   -    |
   | OH_MD_KEY_COMPLIANCE_LEVEL    |    兼容性等级     |  -    |  可选 |    -     |   -    |
   <!--RP2End-->

   各音频编码类型参数范围说明：
   | 音频编码类型 | 采样率(Hz)                                                                       |       声道数       |
   | ----------- | ------------------------------------------------------------------------------- | :----------------: |
   | <!--DelRow-->AAC         | 8000、11025、12000、16000、22050、24000、32000、44100、48000、64000、88200、96000 | 1、2、3、4、5、6、8 |
   | Flac        | 8000、11025、12000、16000、22050、24000、32000、44100、48000、64000、88200、96000 |        1~8         |
   | MP3         | 8000、11025、12000、16000、22050、24000、32000、44100、48000                     |        1~2         |
   | G711mu      | 8000                                                                            |         1          |
   <!--RP3--><!--RP3End-->

   例如对一个44100Hz采样率、2声道立体声、SAMPLE_S16LE采样格式的PCM音频，以32000bps的码率进行AAC编码的调用流程如下：
    <!--RP4-->
    ```cpp
    int32_t ret;
    // 配置音频采样率（必须）。
    constexpr uint32_t DEFAULT_SAMPLERATE = 44100;
    // 配置音频码率（必须）。
    constexpr uint64_t DEFAULT_BITRATE = 32000;
    // 配置音频声道数（必须）。
    constexpr uint32_t DEFAULT_CHANNEL_COUNT = 2;
    // 配置音频声道布局（必须）。
    constexpr OH_AudioChannelLayout CHANNEL_LAYOUT = OH_AudioChannelLayout::CH_LAYOUT_STEREO;
    // 配置音频位深（必须）。
    constexpr OH_BitsPerSample SAMPLE_FORMAT = OH_BitsPerSample::SAMPLE_S16LE;

    OH_AVFormat *format = OH_AVFormat_Create();
    // 写入format。
    OH_AVFormat_SetIntValue(format, OH_MD_KEY_AUD_CHANNEL_COUNT, DEFAULT_CHANNEL_COUNT);
    OH_AVFormat_SetIntValue(format, OH_MD_KEY_AUD_SAMPLE_RATE, DEFAULT_SAMPLERATE);
    OH_AVFormat_SetLongValue(format, OH_MD_KEY_BITRATE, DEFAULT_BITRATE);
    OH_AVFormat_SetIntValue(format, OH_MD_KEY_AUDIO_SAMPLE_FORMAT, SAMPLE_FORMAT);
    OH_AVFormat_SetLongValue(format, OH_MD_KEY_CHANNEL_LAYOUT, CHANNEL_LAYOUT);

    // 配置编码器。
    ret = OH_AudioCodec_Configure(audioEnc_, format);
    if (ret != AV_ERR_OK) {
        // 异常处理。
    }
    ```
    <!--RP4End-->
    例FLAC调用流程：

    ```cpp
    int32_t ret;
    // 配置音频采样率（必须）。
    constexpr uint32_t DEFAULT_SAMPLERATE = 44100;
    // 配置音频码率（必须）。
    constexpr uint64_t DEFAULT_BITRATE = 261000;
    // 配置音频声道数（必须）。
    constexpr uint32_t DEFAULT_CHANNEL_COUNT = 2;
    // 配置音频声道布局（必须）。
    // 值为CH_LAYOUT_MONO、CH_LAYOUT_STEREO、CH_LAYOUT_SURROUND、CH_LAYOUT_QUAD、CH_LAYOUT_5POINT0、CH_LAYOUT_5POINT1、CH_LAYOUT_6POINT1或CH_LAYOUT_7POINT1其中一项。
    constexpr OH_AudioChannelLayout CHANNEL_LAYOUT = OH_AudioChannelLayout::CH_LAYOUT_STEREO;
    // 配置音频位深（必须） flac只有SAMPLE_S16LE和SAMPLE_S32LE。
    constexpr OH_BitsPerSample SAMPLE_FORMAT = OH_BitsPerSample::SAMPLE_S32LE;
    // 配置音频compliance level (默认值0，取值范围-2~2)。
    constexpr int32_t COMPLIANCE_LEVEL = 0;
    
    OH_AVFormat *format = OH_AVFormat_Create();
    // 写入format。
    OH_AVFormat_SetIntValue(format, OH_MD_KEY_AUD_CHANNEL_COUNT, DEFAULT_CHANNEL_COUNT);
    OH_AVFormat_SetIntValue(format, OH_MD_KEY_AUD_SAMPLE_RATE, DEFAULT_SAMPLERATE);
    OH_AVFormat_SetLongValue(format, OH_MD_KEY_BITRATE, DEFAULT_BITRATE);
    // 配置音频精度。API 20前，FLAC编码必须设置此参数，设置为1即可；未设置此参数配置FLAC编码器时，调用OH_AudioCodec_Configure会返回错误码AV_ERR_INVALID_VAL。该值无实际作用，不会影响编码结果。从API 20开始，无需设置此参数。
    // constexpr int32_t BITS_PER_CODED_SAMPLE = 1;
    // OH_AVFormat_SetIntValue(format, OH_MD_KEY_BITS_PER_CODED_SAMPLE, BITS_PER_CODED_SAMPLE);
    OH_AVFormat_SetIntValue(format, OH_MD_KEY_AUDIO_SAMPLE_FORMAT, SAMPLE_FORMAT); 
    OH_AVFormat_SetLongValue(format, OH_MD_KEY_CHANNEL_LAYOUT, CHANNEL_LAYOUT);
    OH_AVFormat_SetLongValue(format, OH_MD_KEY_COMPLIANCE_LEVEL, COMPLIANCE_LEVEL); 
    // 配置编码器。
    ret = OH_AudioCodec_Configure(audioEnc_, format);
    if (ret != AV_ERR_OK) {
        // 异常处理。
    }
    ```

    <!--RP1--><!--RP1End-->

5. 调用OH_AudioCodec_Prepare()，编码器就绪。

    ```cpp
    int32_t ret = OH_AudioCodec_Prepare(audioEnc_);
    if (ret != AV_ERR_OK) {
        // 异常处理。
    }
    ```

6. 调用OH_AudioCodec_Start()启动编码器，进入运行态。

   添加头文件：
    ```c++
    #include <fstream>
    ```
   使用示例：
    ```c++
    ifstream inputFile_;
    ofstream outFile_;

    // 根据实际使用情况填写输入文件路径。
    const char* inputFilePath = "/";
    // 根据实际使用情况填写输出文件路径。
    const char* outputFilePath = "/";
    // 打开待编码二进制文件路径（此处以输入为PCM文件为例）。
    inputFile_.open(inputFilePath, ios::in | ios::binary); 
    // 配置编码文件输出路径（此处以输出为编码码流文件为例）。
    outFile_.open(outputFilePath, ios::out | ios::binary);
    // 开始编码。
    int32_t ret = OH_AudioCodec_Start(audioEnc_);
    if (ret != AV_ERR_OK) {
        // 异常处理。
    }
    ```

7. 调用OH_AudioCodec_PushInputBuffer()，写入待编码器的数据。需开发者填充完整的输入数据后调用。

   每次输入的采样点数（SAMPLES_PER_FRAME）取值方法如下：

   AAC-LC编码每帧包含1024个PCM样点，建议单次输入1024个样点的数据量。

   <!--RP5--><!--RP5End-->

   flac比较特殊，需要根据如下表格进行设置。

   | 采样率 | 样点数 |
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

   > **说明：**
   >
   > 单次编码输入的数据量（单位：字节）为：采样点数（SAMPLES_PER_FRAME） * 声道数 * 单个采样点的占用字节。
   >
   > flac编码的样点数建议参考表格根据采样率对应的样点数进行设置，否则可能出现编码文件损坏问题。

   ```c++
    // 声道数。
    constexpr int32_t DEFAULT_CHANNEL_COUNT = 2;
    // 采样点数，这里以AAC-LC为例，采样点数为1024。
    constexpr int32_t SAMPLES_PER_FRAME = 1024;
    // 单次编码输入的数据量（单位：字节）为：采样点数 * 声道数 * 单个采样点的占用字节（以采样格式SAMPLE_S16LE为例）。
    // 如果最后一帧数据不满足长度，建议进行丢弃或填充处理。
    constexpr int32_t INPUT_FRAME_BYTES = SAMPLES_PER_FRAME * DEFAULT_CHANNEL_COUNT * sizeof(short);
    uint32_t index = signal_->inQueue_.front();
    auto buffer = signal_->inBufferQueue_.front();
    OH_AVCodecBufferAttr attr = {0};
    if (!inputFile_.eof()) {
        inputFile_.read((char *)OH_AVBuffer_GetAddr(buffer), INPUT_FRAME_BYTES);
        attr.size = INPUT_FRAME_BYTES;
        attr.flags = AVCODEC_BUFFER_FLAGS_NONE;
    } else {
        attr.size = 0;
        attr.flags = AVCODEC_BUFFER_FLAGS_EOS;
    }
    OH_AVBuffer_SetBufferAttr(buffer, &attr);
    // 送入编码输入队列进行编码, index为对应队列下标。
    int32_t ret = OH_AudioCodec_PushInputBuffer(audioEnc_, index);
    if (ret != AV_ERR_OK) {
        // 异常处理。
    }
    ```
   在上方案例中，attr.flags代表缓冲区标记的类别。

   如果是结束，需要将flags标识成AVCODEC_BUFFER_FLAGS_EOS。

   | 枚举值 | 描述 | 
   | -------- | -------- |
   | AVCODEC_BUFFER_FLAGS_NONE | 表示为普通帧。 | 
   | AVCODEC_BUFFER_FLAGS_EOS | 表示缓冲区是流结束帧。 | 
   | AVCODEC_BUFFER_FLAGS_CODEC_DATA | 表示缓冲区包含编解码特定数据。 | 

8. 调用OH_AudioCodec_FreeOutputBuffer()，释放编码后的数据。

   在取走编码码流后，就应及时调用OH_AudioCodec_FreeOutputBuffer()进行释放。

    ```c++
    uint32_t index = signal_->outQueue_.front();
    OH_AVBuffer *avBuffer = signal_->outBufferQueue_.front();
    if (avBuffer == nullptr) {
        // 异常处理
    }
    // 获取buffer attributes。
    OH_AVCodecBufferAttr attr = {0};
    int32_t ret = OH_AVBuffer_GetBufferAttr(avBuffer, &attr);
    if (ret != AV_ERR_OK) {
        // 异常处理。
    }
    // 将编码完成数据data写入到对应输出文件中。
    outFile_.write(reinterpret_cast<char *>(OH_AVBuffer_GetAddr(avBuffer)), attr.size);
    // 释放已完成写入的数据。
    ret = OH_AudioCodec_FreeOutputBuffer(audioEnc_, index);
    if (ret != AV_ERR_OK) {
        // 异常处理。
    }
    if (attr.flags == AVCODEC_BUFFER_FLAGS_EOS) {
        // 结束。
    }
    ```

9. （可选）调用OH_AudioCodec_Flush()刷新编码器。

   调用OH_AudioCodec_Flush()后，编码器处于Flush状态，会将当前编码队列清空。

   此时需要调用OH_AudioCodec_Start()重新开始编码。

   使用情况：

   * 在文件EOS之后，需要调用刷新。
   * 在执行过程中遇到可继续执行的错误时（即OH_AudioCodec_IsValid 为true）可以调用，然后重新调用OH_AudioCodec_Start。

    ```c++
    // 刷新编码器 audioEnc_。
    int32_t ret = OH_AudioCodec_Flush(audioEnc_);
    if (ret != AV_ERR_OK) {
        // 异常处理。
    }
    // 重新开始编码。
    ret = OH_AudioCodec_Start(audioEnc_);
    if (ret != AV_ERR_OK) {
        // 异常处理。
    }
    ```

10. （可选）调用OH_AudioCodec_Reset()重置编码器。

    调用OH_AudioCodec_Reset()后，编码器回到初始化的状态，需要调用OH_AudioCodec_Configure()重新配置，然后调用OH_AudioCodec_Start()重新开始编码。

    ```c++
    // 重置编码器 audioEnc_。
    int32_t ret = OH_AudioCodec_Reset(audioEnc_);
    if (ret != AV_ERR_OK) {
        // 异常处理。
    }
    // 重新配置编码器参数。
    ret = OH_AudioCodec_Configure(audioEnc_, format);
    if (ret != AV_ERR_OK) {
        // 异常处理。
    }
    ```

11. 调用OH_AudioCodec_Stop()停止编码器。

    停止后，可以通过Start重新进入已启动状态（started），但需要注意的是，如果编码器之前已输入数据，则需要重新输入编码器数据。

    ```c++
    // 终止编码器 audioEnc_。
    int32_t ret = OH_AudioCodec_Stop(audioEnc_);
    if (ret != AV_ERR_OK) {
        // 异常处理。
    }
    ```

12. 调用OH_AudioCodec_Destroy()销毁编码器实例，释放资源。

    > **说明：**
    > 资源不能重复销毁

    ```c++
    // 调用OH_AudioCodec_Destroy, 注销编码器。
    int32_t ret = OH_AudioCodec_Destroy(audioEnc_);
    if (ret != AV_ERR_OK) {
        // 异常处理。
    } else {
        audioEnc_ = NULL; // 不可重复destroy。
    }
    ```

## 相关实例

针对音频编码，有以下相关实例可供参考：

- [音频编码](https://gitee.com/openharmony/multimedia_av_codec/blob/master/test/nativedemo/audio_demo/avcodec_audio_avbuffer_aac_encoder_demo.cpp)
