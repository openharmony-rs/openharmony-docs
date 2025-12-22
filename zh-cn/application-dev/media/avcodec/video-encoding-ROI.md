# ROI视频编码

<!--Kit: AVCodec Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yang-xiaoyu5-->
<!--Designer: @dpy2650--->
<!--Tester: @cyakee-->
<!--Adviser: @w_Machine_cc-->

## 基础概念

感兴趣区域视频编码(Region Of Interest Video Encoding)，简称ROI视频编码，是基于硬件 H.264/H.265 编码能力扩展的高级优化技术。其核心逻辑为对画面中指定的重点区域分配更高编码资源实现高编码质量，对非重点区域降低编码质量(如减少比特率分配)，最终在有限带宽条件下保障 ROI 区域内容清晰呈现，显著提升整体视觉体验。

开发者可自主定义视频画面中的 ROI 区域（如直播中的人脸、监控中的车牌等），并通过设定质量偏移参数，调节 ROI 区域与非 ROI 区域的编码质量差异，实现编码资源的差异化分配。

## 适用场景

ROI 编码技术的使用需满足两大核心条件：**ROI信息的可获得性**、**画面内容存在明显的优先级差异**，二者缺一不可。

**1. ROI 信息的可获得性**

AVCodec 仅提供底层 ROI 编码能力，完整的ROI编码方案需配套 ROI 区域检测能力。

- 自主研发：开发者可根据业务场景自行设计并实现 ROI 识别能力（如商品轮廓识别、文字区域检测等）；
- 复用原生能力：可直接调用相机模块原生提供的人脸 ROI 检测能力，显著降低开发成本。[相机人脸ROI获取示例](../camera/native-camera-metadata.md#状态监听)。

**2. 画面内容存在明显的优先级差异**

画面中包含明确关键区域（如人脸、商品等）的视频编码场景，均适配 ROI 编码技术，典型场景包括：

- 秀场直播：将主播面部区域设为 ROI，优化人脸细节（如肤色、五官轮廓），提升观众沉浸式观看体验；
- 户外直播：将主播主体 / 核心拍摄景物（如自然风光、赛事画面核心区域）设为 ROI，在移动网络带宽波动时保障核心内容清晰；
- 电商直播：把商品展示区域（如美妆试色、电子产品细节）设为 ROI，清晰呈现商品外观、材质与功能细节，助力商品转化；
- 网课视频：将课件文字、讲义图表、板书内容区域设为 ROI，保证知识点清晰可读，降低视觉疲劳，提升教学效果；
- 安全监控：将摄像头画面中的人脸、车牌、出入口等关键区域设为 ROI，提升抓拍清晰度，便于后续识别分析。

**3. 典型编码场景适配说明**

基于以上两大核心条件，选择直播、录制以及编辑三种编码场景提供ROI编码开发示例供大家参考。
*注意：三种场景的ROI配置方式仅为推荐，开发者应基于实际业务需求和技术架构选择最符合的开发示例。*

| 不同场景对照点 | 直播场景| 录像场景 | 编辑场景 |
| :----: |:----:|:----:| :----: |
| **ROI信息生产者** | 相机 | 相机 | 应用 |
| **ROI信息获取方式** | 通过相机元数据回调获取 | 通过相机元数据回调获取 | 应用自管理 |
| **编码视频帧直接生产者** | 图形 | 相机 | 应用 |
| **编码模式** | Surface模式 | Surface模式 | Buffer模式 |
| **ROI管理&对齐方式** | 基于时间戳匹配 | 基于回调时机匹配 | 自选 |
| **ROI参数配置方式** | NativeBuffer元数据配置 | 编码输入参数回调配置 | 编码输入buffer回调配置 |
| **开发示例** | [直播场景开发示例](#直播场景开发示例) | [录像场景开发示例](#录像场景开发示例) | [编辑场景开发示例](#编辑场景开发示例) |

## 约束和限制

- **支持的平台**：Kirin9000及以后。
- **支持的系统**：OpenHarmony6.0及以后。
- **支持的编码器**：H.264 8bit硬件编码、H.265 8bit硬件编码、H.265 10bit硬件编码。
- **支持的码控模式**：VBR、CBR、SQR。

## 参数要求说明

支持开发者通过字符串形式下发ROI配置参数，参数需满足"Top1,Left1-Bottom1,Right1=Offset1;Top2,Left2-Bottom2,Right2=Offset2;"的格式。
- Top、Bottom指的是ROI区域上、下边界到视频帧上边界的距离；Left、Right指的是ROI区域左、右边界到视频帧左边界的距离。如下图所示。
- Offset指定deltaQp，deltaQp为负表示ROI区域编码画质优于非ROI区域；"=Offset"可以省略，省略时使用默认参数（=-3）。
- 多个ROI参数之间通过";"连接，所有参数均为整数。
- 使用前请确保传入参数有效，并尽量避免多个ROI区域之间产生交叠。
- 同一帧最多支持配置6个ROI区域，并且总ROI面积不能超过图片面积的1/5。

![ROI尺寸和坐标示意](.\figures\roi-size-and-coordinate.png)

## 生效机制说明

1. ROI参数支持随帧下发并实时生效，开发者无需进行能力查询或配置全局开关。
2. 如果底层硬件编码器不支持ROI编码能力，编码器会忽略ROI参数，进行普通编码。
3. deltaQp有效范围[-51，51]，编码器会在块级QP的基础上叠加deltaQp，然后Clip到[minQp，maxQp]范围内得到最终QP。
4. 当某一帧NativeBuffer配置方式和编码输入回调配置均有配置ROI参数，以流程靠后的随编码输入回调配置的配置为准，无论其能否解析出有效ROI信息。
5. 当某一帧未配置ROI参数，如果上一帧ROI编码，则复用该ROI信息进行ROI编码；如果上一帧是普通编码，则进行普通编码。
6. 当某一帧配置了ROI参数，但字符串无法解析出任何有效ROI信息时，进行普通编码。
7. 两个通路对于空字符串的处理存在差异。随编码输入回调配置允许配置空字符串，行为和“配置了ROI参数，但字符串无法解析出任何有效ROI信息”相同。随NativeBuffer配置不允许配置空字符串，配置空字符串会失败，行为和“未配置ROI参数”相同。
8. 如果设置的ROI总面积超过1/5图片大小，按照配置顺序依次累加，仅生效累加面积在限制之内的ROI区域。
9. 如果输入的有效ROI框超过6个，按照配置顺序，多出的ROI区域将被忽略。
10. 如果多个ROI区域产生交叠，按照配置顺序，仅第一个配置的ROI区域会在交叠处生效。
11. 随NativeBuffer配置最大支持256Byte，超出部分会被截断。

*注意：编码输入参数回调和编码输入buffer回调统称编码输入回调。*

## 直播场景开发示例

此场景下图形NativeImage对应窗口接收相机视频帧，支持获取视频时间戳并与ROI信息进行时间同步匹配，经图形处理后绘制到编码输入窗口，在绘制执行前，可获取待绘制的NativeBuffer完成ROI配置。架构图如下：

```Mermaid
flowchart LR
    classDef redNode fill:#ff4d4f,stroke:#dc3545,stroke-width:1.5px,rx:6px,ry:6px,font-size:13px,color:#fff
    classDef greenNode fill:#52c41a,stroke:#089728,stroke-width:1.5px,rx:6px,ry:6px,font-size:13px,color:#fff
    classDef blueNode fill:#1890ff,stroke:#096dd9,stroke-width:1.5px,rx:6px,ry:6px,font-size:13px,color:#fff

    A["相机"]:::redNode 
    B["图形<br>渲染窗口"]:::blueNode
    C["相机ROI回调"]:::redNode
    D["视频帧<br>和ROI同步"]:::blueNode
    E["ROI配置"]:::blueNode
    F["视频帧<br>绘制渲染"]:::blueNode
    G["编码器<br>输入窗口"]:::greenNode
    H["编码器"]:::greenNode
    I["图形前处理"]:::blueNode
    J["视频帧"]:::blueNode
    K["ROI信息"]:::blueNode

    A --> B
    A --> C
    B --> I
    I --> J
    C --> K
    J --> D
    K --> D
    D --> E
    E --> F
    F --> G
    G --> H

    linkStyle 0,1,2,3,4,5,6,7,8,9,10 stroke:#4080c0,stroke-width:1.5px,arrowheadStyle:filled
```

使用`OH_NativeBuffer_MetaDataKey`的ROI枚举`OH_REGION_OF_INTEREST_METADATA`，在NativeBuffer的元数据中配置ROI参数。

|配置参数 |语义 |格式 |
|------- |------- |------- |
|OH_REGION_OF_INTEREST_METADATA |ROI参数 |String|

详细开发步骤如下：

1. CMakeList.txt新增链接动态库

    ```cmake
    target_link_libraries(sample PUBLIC libnative_media_codecbase.so)
    target_link_libraries(sample PUBLIC libnative_media_core.so)
    target_link_libraries(sample PUBLIC libnative_media_venc.so)
    target_link_libraries(sample PUBLIC libnative_window.so)
    target_link_libraries(sample PUBLIC libnative_buffer.so)
    target_link_libraries(sample PUBLIC libohcamera.so)
    target_link_libraries(sample PUBLIC libEGL.so)
    target_link_libraries(sample PUBLIC libGLESv3.so)
    ```
    > **说明：**
    >
    > 上述'sample'字样仅为示例，此处由开发者根据实际工程目录自定义。
    >

2. 新增包含头文件

    ```c++
    #include <multimedia/player_framework/native_avcodec_videoencoder.h>
    #include <multimedia/player_framework/native_avcodec_base.h>
    #include <native_buffer/native_buffer.h>
    #include <native_window/external_window.h>
    #include <ohcamera/metadata_output.h>
    #include <EGL/egl.h>
    #include <EGL/eglext.h>
    #include <GLES3/gl3.h>
    #include <GLES2/gl2ext.h>
    ```

3. 通过相机元数据回调获取ROI信息

    如何注册相机元数据回调可以参考 [相机元数据状态监听](../camera/native-camera-metadata.md#状态监听)。相机元数据获取到的ROI位置信息为[Camera_Rect](../../reference/apis-camera-kit/capi-oh-camera-camera-rect.md), 配置接口还需进行坐标转换。

    ```c++
    #include <map>
    #include <mutex>
    #include <sstream>
    #include <string>

    const int width = 1920;   // 视频帧宽度
    const int height = 1080;  // 视频帧高度
    const int qpOffset = -6;  // QP偏移参数
    bool g_isDuplicate = false;
    int64_t g_lastTimeStamp = -1;
    std::map<int64_t, std::string> g_roiStrMap;
    std::mutex g_roiMutex;
    // 相机元数据回调处理
    void OnMetadataObjectAvailable(Camera_MetadataOutput* metadataOutput,
        Camera_MetadataObject* metadataObject, uint32_t size)
    {   
        std::string mergedRoiStr;  // 存储同一PTS下合并的ROI字符串
        int64_t basePts = -1;      // 基准PTS（首个有效人脸框的PTS）
        // 遍历所有metadataObject
        for (uint32_t i = 0; i < size; ++i) {
            // 仅处理人脸检测类型的元数据
            if (metadataObject->type != Camera_MetadataObjectType::FACE_DETECTION) {
                metadataObject++;
                continue;
            }

            Camera_Rect* box = metadataObject->boundingBox;
            if (box == nullptr) { // 过滤空框
                metadataObject++;
                continue;
            }

            int64_t currentPts = metadataObject->timestamp;
            // 当系统负载高时，因ROI识别不及时，相机元数据回调存在小概率返回上一帧ROI信息的情况
            // 因相邻图像帧ROI区域差异较小，建议在识别此场景后不配置ROI参数，默认使用上一帧ROI配置编码
            if (currentPts == g_lastTimeStamp) {
                g_isDuplicate = true; // 识别重复ROI，终止元数据解析
                return;
            }
            if (basePts == -1) {
                basePts = currentPts; // 初始化基准PTS
            } else if (currentPts != basePts) { // 单次回调不会返回不同pts的多个人脸信息
                metadataObject++;
                continue;
            }

            // 归一化坐标转像素坐标
            int left = static_cast<int32_t>(box->topLeftX * width);
            int top = static_cast<int32_t>(box->topLeftY * height);
            int right = static_cast<int32_t>(box->width * width) + left;
            int bottom = static_cast<int32_t>(box->height * height) + top;

            // 拼接当前人脸框的格式字符串（top,left-bottom,right=QpOffset;）
            std::ostringstream oss;
            oss << mergedRoiStr; // 拼接已有片段
            oss << top << "," << left << "-" << bottom << "," << right << "=" << qpOffset << ";";
            mergedRoiStr = oss.str();

            metadataObject++; // 移动到下一个对象
        }

        if (!mergedRoiStr.empty()) {
            std::lock_guard<std::mutex> lock(g_roiMutex);
            // 此场景可获取视频帧时间戳，基于时间戳匹配
            g_roiStrMap[basePts] = mergedRoiStr;
            g_lastTimeStamp = basePts;
        }
    }
    ```

4. 基于视频帧时间戳找到匹配的ROI信息

    创建OES纹理用来接收视频帧。

    ```c++
    GLuint textureId;
    glGenTextures(1, &textureId);
    // 创建 NativeImage 实例，关联 OpenGL 纹理
    OH_NativeImage* image = OH_NativeImage_Create(textureId, GL_TEXTURE_EXTERNAL_OES);
    ```

    基于NativeImage获取对应NativeWindow，作为相机预览流的目标窗口。并通过`OH_NativeImage_SetOnFrameAvailableListener`注册回调`OH_OnFrameAvailableListener`获取视频帧更新。

    ```c++
    // 在回调后更新NativeImage。
    int32_t ret = OH_NativeImage_UpdateSurfaceImage(image);
    if (ret != 0) {
        // 异常处理
    }
    // 获取视频帧时间戳
    int64_t imageTimeStamp = OH_NativeImage_GetTimestamp(image);
    // 使用视频帧时间戳找到与之对应的ROI信息
    std::lock_guard<std::mutex> lock(g_roiMutex);
    auto it = g_roiStrMap.find(imageTimeStamp);
    std::string noRoiStr = ";"; // 随元数据配置方式，需配置非空无效字符串关闭本视频帧ROI编码
    std::string roiInfo = (it != g_roiStrMap.end()) ? it->second : noRoiStr;
    ```

5. 配置ROI信息到视频帧NativeBuffer元数据中

    经过系列egl处理后，生成了用于编码的视频帧纹理。需要使用eglSwapBuffers函数将纹理绘制到编码器的输入NativeWindow中。编码输入NativeWindow获取方式如下。

    ```c++
    OH_AVCodec *codec = OH_VideoEncoder_CreateByMime(OH_AVCODEC_MIMETYPE_VIDEO_HEVC);
    OHNativeWindow *nativeWindow = nullptr;
    OH_VideoEncoder_GetSurface(codec, &nativeWindow);
    ```

    绘制之前获取最新的NativeBuffer，并配置ROI信息。
    ```c++
    if (g_isDuplicate) {
        g_isDuplicate = false; // 重复帧不配置，使用上一帧ROI配置编码
    } else {
        int fenceFd = -1;
        OHNativeWindowBuffer *winBuffer = nullptr;
        // 从Surface中请求一帧OHNativeWindowBuffer
        int32_t ret = OH_NativeWindow_NativeWindowRequestBuffer(nativeWindow, &winBuffer, &fenceFd);
        if (ret != 0) {
            // 异常处理
        }
        // 将OHNativeWindowBuffer转换为NativeBuffer
        OH_NativeBuffer *nativeBuffer = nullptr;
        OH_NativeBuffer_FromNativeWindowBuffer(winBuffer, &nativeBuffer);
        // 配置ROI信息到NativeBuffer元数据中
        int32_t ret = OH_NativeBuffer_SetMetaDataValue(nativeBuffer,
            OH_NativeBuffer_MetaDataKey::OH_REGION_OF_INTEREST_METADATA, roiInfo.size,
            reinterpret_cast<uint8_t *>(c.data()));
        if (ret != 0) {
            // 异常处理
        }
    }
    ```

    绘制过程可参考[OpenGLES示例](../../../application-dev/reference/native-lib/opengles.md#简单示例)，最终通过`eglSwapBuffers`送绘制好的数据到编码器进行编码。

## 录像场景开发示例

在此场景中，视频帧直接送入编码器的输入窗口。相机输出视频帧及其元数据（如果存在）的时间相近。设置编码输入参数回调后，编码器收到视频帧时会触发参数回调。在回调中，如果获取成功，则该视频帧有匹配的ROI信息。如果获取超时，则该视频帧无匹配的ROI信息。架构图如下：

```Mermaid
flowchart LR
    classDef redNode fill:#ff4d4f,stroke:#dc3545,stroke-width:1.5px,rx:6px,ry:6px,font-size:13px,color:#fff
    classDef greenNode fill:#52c41a,stroke:#089728,stroke-width:1.5px,rx:6px,ry:6px,font-size:13px,color:#fff
    classDef blueNode fill:#1890ff,stroke:#096dd9,stroke-width:1.5px,rx:6px,ry:6px,font-size:13px,color:#fff

    A["相机"]:::redNode
    B["相机ROI回调"]:::redNode
    C["视频帧<br>和ROI同步"]:::blueNode
    D["ROI配置"]:::blueNode
    E["编码器输入<br>参数回调"]:::greenNode
    F["编码器<br>输入窗口"]:::greenNode
    G["编码器"]:::greenNode
    H["ROI信息"]:::blueNode

    A --> F
    F --> E
    A --> B
    B --> H
    H --> C
    E --> C
    C --> D
    D --> G

    linkStyle 0,1,2,3,4,5,6,7 stroke:#4080c0,stroke-width:1.5px,arrowheadStyle:filled
```


使用视频编码参数`OH_MD_KEY_VIDEO_ENCODER_ROI_PARAMS`在编码输入参数回调中配置。
|配置参数 |语义 |格式 |
|------- |------- |------- |
|OH_MD_KEY_VIDEO_ENCODER_ROI_PARAMS |ROI参数 |String|

详细开发步骤如下：

1. CMakeList.txt新增链接动态库

    ```cmake
    target_link_libraries(sample PUBLIC libnative_media_codecbase.so)
    target_link_libraries(sample PUBLIC libnative_media_core.so)
    target_link_libraries(sample PUBLIC libnative_media_venc.so)
    target_link_libraries(sample PUBLIC libohcamera.so)
    ```
    > **说明：**
    >
    > 上述'sample'字样仅为示例，此处由开发者根据实际工程目录自定义。
    >

2. 新增包含头文件

    ```c++
    #include <multimedia/player_framework/native_avcodec_videoencoder.h>
    #include <multimedia/player_framework/native_avcodec_base.h>
    #include <multimedia/player_framework/native_avformat.h>
    #include <multimedia/player_framework/native_avbuffer.h>
    #include <ohcamera/metadata_output.h>
    ```

3. ROI管理结构定义

    编码参数回调中无法获取视频帧的时间戳，为配合后续对齐，需要使用线程安全的先入先出队列管理ROI信息。

    ```c++
    #include <queue>
    #include <string>
    #include <mutex>
    #include <condition_variable>
    #include <chrono>

    // 线程安全的FIFO ROI队列
    class RoiFifoQueue {
    public:
        void push(const std::string& roiStr) {
            std::lock_guard<std::mutex> lock(mtx);
            roiQueue.push(roiStr);
            cv.notify_one(); // 通知等待的取数线程
        }

        bool pop(std::string& outRoiStr, const std::chrono::milliseconds& timeout) {
            std::unique_lock<std::mutex> lock(mtx);
            if (!cv.wait_for(lock, timeout, [this]() {
                return !roiQueue.empty() || isStopped;
            })) {
                return false; // 超时则无ROI
            }
            if (isStopped || roiQueue.empty()) {
                return false;
            }
            outRoiStr = roiQueue.front();
            roiQueue.pop();
            return true;
        }

        void clear() {
            std::lock_guard<std::mutex> lock(mtx);
            while (!roiQueue.empty()) {
                roiQueue.pop();
            }
        }

        void stop() {
            std::lock_guard<std::mutex> lock(mtx);
            isStopped = true;
            cv.notify_all(); // 唤醒所有等待的线程
        }

        ~RoiFifoQueue() {
            stop();
        }
        };
    private:
        std::queue<std::string> roiQueue;    // 存储合并后的完整ROI字符串
        std::mutex mtx;                      // 互斥锁保护队列
        std::condition_variable cv;          // 条件变量用于超时等待
        bool isStopped = false;              // 停止标志（防止析构时死等）
    ```

4. 通过相机元数据回调获取ROI信息

    关于注册相机元数据回调的具体步骤，请参考 [Camera元数据状态监听](../camera/native-camera-metadata.md#状态监听)。

    ```c++
    #include <sstream>

    const int width = 1920;   // 视频帧宽度
    const int height = 1080;  // 视频帧高度
    const int qpOffset = -6;  // QP偏移参数
    bool g_isDuplicate = false;
    int64_t g_lastTimeStamp = -1;
    RoiFifoQueue g_roiStrQueue;
    void OnMetadataObjectAvailable(Camera_MetadataOutput* metadataOutput,
        Camera_MetadataObject* metadataObject, uint32_t size)
    {
        std::string mergedRoiStr;  // 存储同一PTS下合并的ROI字符串
        int64_t basePts = -1;      // 基准PTS（首个有效人脸框的PTS）

        // 遍历所有metadataObject
        for (uint32_t i = 0; i < size; ++i) {
            // 同直播场景实例 OnMetadataObjectAvailable 中 遍历所有 metadataObject 实现，此处省略。
        }

        if (!mergedRoiStr.empty()) {
            // 基于回调时机匹配，用先进先出队列管理
            g_roiStrQueue.push(mergedRoiStr);
            g_lastTimeStamp = basePts;
        }
    }
    ```

5. 编码输入参数回调

    ```c++
    // 创建编码器
    OH_AVCodec *codec = OH_VideoEncoder_CreateByMime(OH_AVCODEC_MIMETYPE_VIDEO_HEVC);
    ```
    视频编码的基本操作请参考[视频编码](video-encoding.md)开发指南，下面仅针对ROI编码做具体说明。
    ```c++
    const std::chrono::milliseconds ROI_WAIT_TIMEOUT = std::chrono::milliseconds(4); // 4ms超时
    static void OnNeedInputParameter(OH_AVCodec *codec, uint32_t index, OH_AVFormat *parameter, void *userData)
    {
        (void)codec;
        (void)userData;
        if (g_isDuplicate) {
            g_isDuplicate = false; // 重复帧不配置，使用上一帧ROI配置编码
        } else {
            std::string roiInfo = ";"; // 允许配置为空不生效ROI编码，与另一个通路统一
            if (!g_roiStrQueue.pop(roiInfo, ROI_WAIT_TIMEOUT)) {
                OH_LOG_INFO("No ROI info.");
            }
            // 找到ROI配置，ROI编码生效；找不到ROI，普通编码生效。
            OH_AVFormat_SetStringValue(parameter, OH_MD_KEY_VIDEO_ENCODER_ROI_PARAMS, roiInfo.c_str());
        }

        OH_VideoEncoder_PushInputParameter(codec, index);
    }

    // 注册随帧参数回调。
    OH_VideoEncoder_OnNeedInputParameter inParaCb = OnNeedInputParameter;
    OH_VideoEncoder_RegisterParameterCallback(codec, inParaCb, nullptr);
    ```


## 编辑场景开发示例

在该场景中，视频帧和ROI均由应用提供，并采用buffer模式编码。应用开发者可以参考前文所述的**基于时间戳匹配**或**基于回调时机匹配**两种对齐方式来实现ROI与视频帧的对齐，并在编码输入buffer回调中完成ROI参数的配置。架构图如下：

```Mermaid
flowchart LR
    classDef blueNode fill:#1890ff,stroke:#096dd9,stroke-width:1.5px,rx:6px,ry:6px,font-size:13px,color:#fff
    classDef greenNode fill:#52c41a,stroke:#089728,stroke-width:1.5px,rx:6px,ry:6px,font-size:13px,color:#fff

    A["应用"]:::blueNode
    B["ROI信息"]:::blueNode
    C["视频帧<br>和ROI同步"]:::blueNode
    D["ROI配置"]:::blueNode
    E["获取视频帧"]:::blueNode
    F["编码器"]:::greenNode
    G["编码器输入<br>Buffer回调"]:::greenNode

    A --> B
    B --> C
    C --> D
    E --> C
    A --> G
    G --> E
    D --> F

    linkStyle 0,1,2,3,4,5,6 stroke:#4080c0,stroke-width:1.5px,arrowheadStyle:filled
```


使用视频编码参数`OH_MD_KEY_VIDEO_ENCODER_ROI_PARAMS`，在编码输入buffer回调中配置。
|配置参数 |语义 |格式 |
|------- |------- |------- |
|OH_MD_KEY_VIDEO_ENCODER_ROI_PARAMS |ROI参数 |String|

准备步骤均可参考录像场景开发示例。仅对配置差异做说明。

1. 在编码输入buffer回调中配置ROI信息

    ```c++
    static void OnNeedInputBuffer(OH_AVCodec *codec, uint32_t index, OH_AVBuffer *buffer, void *userData)
    {
        (void)codec;
        (void)userData;
        if (g_isDuplicate) {
            g_isDuplicate = false; // 重复帧不配置，使用上一帧ROI配置编码
        } else {
            auto format = std::shared_ptr<OH_AVFormat>(OH_AVBuffer_GetParameter(buffer), OH_AVFormat_Destroy);
            if (format == nullptr) {
                // 异常处理。
            }
            std::string roiInfo = ";"; // 允许配置为空不生效ROI编码，建议与另一个通路统一
            if (!g_roiStrQueue.pop(roiInfo, ROI_WAIT_TIMEOUT)) {
                OH_LOG_INFO("No ROI info.");
            }
            OH_AVFormat_SetStringValue(format.get(), OH_MD_KEY_VIDEO_ENCODER_ROI_PARAMS, roiInfo.c_str());
        }

        // 此处还需做视频帧填充，此处忽略。
        // 通知编码器buffer输入完成。
        OH_VideoEncoder_PushInputBuffer(codec, index);
    }

    static void OnStreamChanged(OH_AVCodec *codec, OH_AVFormat *format, void *userData)
    {
        // 此处仅作定义，实现忽略
    }

    static void OnError(OH_AVCodec *codec, int32_t errorCode, void *userData)
    {
        // 此处仅作定义，实现忽略
    }

    static void OnNewOutputBuffer(OH_AVCodec *codec, uint32_t index, OH_AVBuffer *buffer, void *userData)
    {
        // 此处仅作定义，实现忽略
    }

    OH_AVCodecCallback cb = {&OnError, &OnStreamChanged, &OnNeedInputBuffer, &OnNewOutputBuffer};
    OH_AVErrCode ret = OH_VideoEncoder_RegisterCallback(videoEnc, cb, nullptr);
    ```