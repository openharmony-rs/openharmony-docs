# Vulkan External Memory Development

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @andrew1993-->
<!--Designer: @ext4FAT1-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

## When to Use

The VK_OHOS_external_memory extension is designed for zero-copy memory sharing between the GPU Vulkan environment and OpenHarmony OHNativeBuffer.

This extension allows you to import OHNativeBuffers created by OpenHarmony or other components (such as Camera, RenderService, video decoders, and OHNativeWindow) as Vulkan memory (and bind it to VkImage or VkBuffer).

This enables efficient sharing of video frames, camera outputs, and image decoder outputs between the producer and Vulkan rendering/computation ends, avoiding additional copying or pixel conversion.

This guide introduces how to achieve zero-copy between video decoders and renderers by directly importing OHNativeBuffers output by the decoder into Vulkan.



## Available APIs


### Structs

| Name| Description|
| -------- | -------- |
| [VkNativeBufferPropertiesOHOS](capi-vulkan-vknativebufferpropertiesohos.md) | Describes the properties of the NativeBuffer.|
| [VkNativeBufferFormatPropertiesOHOS](capi-vulkan-vknativebufferformatpropertiesohos.md) | Describes the format properties of the NativeBuffer.|
| [VkImportNativeBufferInfoOHOS](capi-vulkan-vkimportnativebufferinfoohos.md) | Describes the pointer to an OH_NativeBuffer struct.|
| [VkMemoryGetNativeBufferInfoOHOS](capi-vulkan-vkmemorygetnativebufferinfoohos.md) | Used to obtain an OH_NativeBuffer from the Vulkan memory.|
| [VkExternalFormatOHOS](capi-vulkan-vkexternalformatohos.md) | Describes an externally defined format.|

### Functions

| Name| Description|
| -------- | -------- |
| VKAPI_ATTR VkResult VKAPI_CALL [vkGetNativeBufferPropertiesOHOS](capi-vulkan-ohos-h.md#vkgetnativebufferpropertiesohos) (VkDevice device, const struct OH_NativeBuffer \*buffer, [VkNativeBufferPropertiesOHOS](capi-vulkan-vknativebufferpropertiesohos.md) \*pProperties) | Obtains the properties of an OH_NativeBuffer instance. |


## How to Develop

The following steps illustrate how to import the OHNativeBuffer output by the video decoder as Vulkan memory and bind it to VkImage or VkBuffer.

1. Launch the rendering child thread, initialize the Vulkan environment, dynamically load libvulkan.so, and load the pointers of the Vulkan base functions.
    ```c++
    void VulkanRenderThread::ThreadMainLoop() {
        threadId_ = std::this_thread::get_id();
        if (!InitRenderContext()) {
            return;
        }
        if (!InitNativeVsync()) {
            return;
        }
        if (!CreateNativeImage()) {
            return;
        }
        while (running_) {
            {
                OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN, "RenderThread", "Waiting for Vsync.");
                std::unique_lock<std::mutex> Lock(wakeUpMutex_);
                wakeUpCond_.wait(Lock, [this]() { return wakeup_ || vSyncCnt_ > 0 || availableFrameCnt_ > 0; });
                wakeup_ = false;
                vSyncCnt_--;
                (void)OH_NativeVSync_RequestFrame(nativeVsync_, &VulkanRenderThread::OnVsync, this);
            }

            std::vector<VulkanRenderTask> tasks;
            {
                std::lock_guard<std::mutex> lock(taskMutex_);
                tasks.swap(tasks_);
            }
            for (const auto &task : tasks) {
                task(*vulkanRenderContext_);
            }
            if (availableFrameCnt_ <= 0) {
                continue;
            }
            DrawImage();
            availableFrameCnt_--;
        }
    }
    ```
    Dynamically load libvulkan.so, and load the pointers of the Vulkan base functions.
    ```c++
    // Dynamically load Vulkan library and base function pointers.
    bool LoadVulkanLibrary() {
        // Load the Vulkan library.
        constexpr char *path = "libvulkan.so";
        dlerror();
        g_libVulkan = dlopen(path, RTLD_NOW | RTLD_LOCAL);
        if (!g_libVulkan) {
            OH_LOG_ERROR(LOG_APP, "Failed to load vulkan Library, %{public}s", dlerror());
            return false;
        }

        // Load the base function pointers.
        vkEnumerateInstanceExtensionProperties = reinterpret_cast<PFN_vkEnumerateInstanceExtensionProperties>(
            dlsym(g_libVulkan, "vkEnumerateInstanceExtensionProperties"));
        vkEnumerateInstanceLayerProperties = reinterpret_cast<PFN_vkEnumerateInstanceLayerProperties>(
            dlsym(g_libVulkan, "vkEnumerateInstanceLayerProperties"));
        vkCreateInstance = reinterpret_cast<PFN_vkCreateInstance>(dlsym(g_libVulkan, "vkCreateInstance"));
        vkGetInstanceProcAddr = reinterpret_cast<PFN_vkGetInstanceProcAddr>(dlsym(g_libVulkan, "vkGetInstanceProcAddr"));
        vkGetDeviceProcAddr = reinterpret_cast<PFN_vkGetDeviceProcAddr>(dlsym(g_libVulkan, "vkGetDeviceProcAddr"));

        return true;
    }
    ```

2. Create a NativeImage object as the consumer of OHNativeBuffer, and obtain the corresponding NativeWindow object from the NativeImage object. Pass the NativeWindow handle to the video codec as the producer of OHNativeBuffer to generate video frame content.
    ```c++
    bool VulkanRenderThread::CreateNativeImage() {
        nativeImage_ = OH_ConsumerSurface_Create();
        if (nativeImage_ == nullptr) {
            OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN, "RenderThread", "OH_NativeImage_Create failed.");
            return false;
        }
        int ret = 0;
        {
            std::lock_guard<std::mutex> Lock(nativeImageSurfaceIdMutex_);
            nativeImageWindow_ = OH_NativeImage_AcquireNativeWindow(nativeImage_);
            ret = OH_NativeImage_GetSurfaceId(nativeImage_, &nativeImageSurfaceId_);
        }
        if (ret != 0) {
            OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN, "RenderThread",
                        "OH_NativeImage_GetSurfaceId failed, ret is %{public}d.", ret);
            return false;
        }

        nativeImageFrameAvailableListener_.context = this;
        nativeImageFrameAvailableListener_.onFrameAvailable = &VulkanRenderThread::OnNativeImageFrameAvailable;
        ret = OH_NativeImage_SetOnFrameAvailableListener(nativeImage_, nativeImageFrameAvailableListener_);
        if (ret != 0) {
            OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN, "RenderThread",
                        "OH_NativeImage_SetonFrameAvailableListener failed, ret is %{public}d.", ret);
            return false;
        }
        return true;
    }
    ```


3. Obtain the NativeWindow object of the XComponent, and create a VkSurface in the Vulkan environment based on the NativeWindow object for drawing and displaying content.
    ```c++
    void VulkanRenderThread::UpdateNativeWindow(void *window, uint64_t width, uint64_t height) {
        OH_LOG_Print(LOG_APP, LOG_DEBUG, LOG_PRINT_DOMAIN, "RenderThread", "UpdateNativeWindow.");
        auto nativeWindow = reinterpret_cast<OHNativeWindow *>(window);
        PostTask([this, nativeWindow, width, height](VulkanRender &renderContext) {
            if (nativeWindow_ != nativeWindow) {
                if (nativeWindow_ != nullptr) {
                    (void)OH_NativeWindow_NativeObjectUnreference(nativeWindow_);
                }
                nativeWindow_ = nativeWindow;
                if (nativeWindow_ != nullptr) {
                    (void)OH_NativeWindow_NativeObjectReference(nativeWindow_);
                }
            }
            if (nativeWindow_ != nullptr) {
                vulkanRenderContext_->SetupWindow(nativeWindow_);
            }
        });
    }
    ```

    Update the Vulkan initialization context, including the Vulkan instance, selecting the physical device, and creating the rendering pipeline.
    ```c++
    void VulkanRender::SetupWindow(NativeWindow *nativeWindow) {
        nativeWindow_ = nativeWindow;
        CreateInstance();
        vkExample::utils::LoadVulkanFunctions(instance);
        CreateSurface();
        PickPhysicalDevice();
        CreateLogicalDevice();
        vkExample::utils::LoadVulkanFunctions(device);

        createSwapChain();
        createRenderPass();
        createFrameBuffersAndImages();
        createVertexBuffer();
        createUniformBuffer();
        deviceInfoInitialized = true;
    }
    ```

    Call vkCreateSurfaceOHOS() to create a VkSurface object.
    ```c++
    bool VulkanRender::CreateSurface() {
        VkSurfaceCreateInfoOHOS surfaceCreateInfo{};
        surfaceCreateInfo.sType = VK_STRUCTURE_TYPE_SURFACE_CREATE_INFO_OHOS;
        if (nativeWindow_ == nullptr) {
            OH_LOG_INFO(LOG_APP, "nativeWindow_ is nulptr.Failed to create surface !");
            return false;
        }
        surfaceCreateInfo.window = nativeWindow_;
        surfaceCreateInfo.flags = 0;
        surfaceCreateInfo.pNext = nullptr;
        bool res = CheckResult(vkCreateSurfaceOHOS(instance, &surfaceCreateInfo, nullptr, &surface));
        return res;
    }
    ```


4. Initialize the video decoding environment, including initializing the demuxer and decoder.
    ```c++
    napi_value PluginRender::StartPlayer(napi_env env, napi_callback_info info)
    {
        SampleInfo sampleInfo;
        size_t argc = 4;
        napi_value args[4] = {nullptr};
        napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);
        napi_get_value_int32(env, args[0], &sampleInfo.inputFd);
        napi_get_value_int64(env, args[1], &sampleInfo.inputFileOffset);
        napi_get_value_int64(env, args[2], &sampleInfo.inputFileSize);
        size_t length = 0;
        napi_status status = napi_get_value_string_utf8(env, args[3], nullptr, 0, &length);
        char* buf = new char[length + 1];
        std::memset(buf, 0, length + 1);
        status = napi_get_value_string_utf8(env, args[3], buf, length + 1, &length);
        std::string type = buf;
        PluginRender *render = PluginRender::GetInstance(type);
        if (render != nullptr) {
            if (type == "Vulkan") {
                sampleInfo.window = render->vulkanRenderThread_->GetNativeImageWindow();
            } else {
                sampleInfo.window = render->nativeWindow;
            }
        }
        int32_t ret = Player::GetInstance().Init(sampleInfo);
        if (ret != AVCODEC_SAMPLE_ERR_OK) {
            return nullptr;
        }
        Player::GetInstance().Start();
        return nullptr;
    }
    ```


5. Start the decoder, decoder input thread, and decoder output thread.
    ```c++
    int32_t Player::Start() {
        std::unique_lock<std::mutex> lock(mutex_);
        int32_t ret;
        if (isStarted_ || demuxer_ == nullptr) {
            OH_LOG_ERROR(LOG_APP, "Already started.");
            return AVCODEC_SAMPLE_ERR_ERROR;
        }
        
        if (videoDecContext_) {
            ret = videoDecoder_->Start();
            if (ret != AVCODEC_SAMPLE_ERR_OK) {
                OH_LOG_ERROR(LOG_APP, "Video Decoder start failed");
                lock.unlock();
                StartRelease();
                return AVCODEC_SAMPLE_ERR_ERROR;
            }
            isStarted_ = true;
            videoDecInputThread_ = std::make_unique<std::thread>(&Player::VideoDecInputThread, this);
            videoDecOutputThread_ = std::make_unique<std::thread>(&Player::VideoDecOutputThread, this);

            if (videoDecInputThread_ == nullptr || videoDecOutputThread_ == nullptr) {
                OH_LOG_ERROR(LOG_APP, "Create thread failed");
                lock.unlock();
                StartRelease();
                return AVCODEC_SAMPLE_ERR_ERROR;
            }
        }

        OH_LOG_INFO(LOG_APP, "Succeed");
        doneCond_.notify_all();
        return AVCODEC_SAMPLE_ERR_OK;
    }
    ```

6. In the decoder input thread, read video data using the demuxer and pass it to the decoder.
    ```c++
    void Player::VideoDecInputThread() {
        while (true) {
            if (!isStarted_) {
                OH_LOG_ERROR(LOG_APP, "Decoder input thread out");
                break;;
            }
            
            std::unique_lock<std::mutex> lock(videoDecContext_->inputMutex);
            bool condRet = videoDecContext_->inputCond.wait_for(
                lock, 5s, [this]() { return !isStarted_ || !videoDecContext_->inputBufferInfoQueue.empty(); });
            if (!isStarted_) {
                OH_LOG_ERROR(LOG_APP, "Work done, thread out");
                break;
            }
            if (videoDecContext_->inputBufferInfoQueue.empty()) {
                OH_LOG_ERROR(LOG_APP, "Buffer queue is empty, continue, cond ret: %{public}d", condRet);
                continue;
            }

            CodecBufferInfo bufferInfo = videoDecContext_->inputBufferInfoQueue.front();
            videoDecContext_->inputBufferInfoQueue.pop();
            videoDecContext_->inputFrameCount++;
            lock.unlock();

            demuxer_->ReadSample(demuxer_->GetVideoTrackId(), reinterpret_cast<OH_AVBuffer *>(bufferInfo.buffer),
                                bufferInfo.attr);

            int32_t ret = videoDecoder_->PushInputBuffer(bufferInfo);
            if (ret != AVCODEC_SAMPLE_ERR_OK) {
                OH_LOG_ERROR(LOG_APP, "Push data failed, thread out");
                break;
            }

            if (bufferInfo.attr.flags & AVCODEC_BUFFER_FLAGS_EOS) {
                OH_LOG_ERROR(LOG_APP, "Catch EOS, thread out");
                break;
            }
        }
    }
    ```

7. In the decoder output thread, submit the decoded video to the output surface.
    ```c++
    void Player::VideoDecOutputThread() {
        sampleInfo_.frameInterval = MICROSECOND / sampleInfo_.frameRate;
        while (true) {
            thread_local auto lastPushTime = std::chrono::system_clock::now();
            if (!isStarted_) {
                OH_LOG_ERROR(LOG_APP, "Decoder output thread out");
                break;
            }
            std::unique_lock<std::mutex> lock(videoDecContext_->outputMutex);
            bool condRet = videoDecContext_->outputCond.wait_for(
                lock, 5s, [this]() { return !isStarted_ || !videoDecContext_->outputBufferInfoQueue.empty(); });
            if (!isStarted_) {
                OH_LOG_ERROR(LOG_APP, "Decoder output thread out");
                break;
            }
            if (videoDecContext_->outputBufferInfoQueue.empty()) {
                OH_LOG_ERROR(LOG_APP, "Buffer queue is empty, continue, cond ret: %{public}d", condRet);
                continue;
            }

            CodecBufferInfo bufferInfo = videoDecContext_->outputBufferInfoQueue.front();
            videoDecContext_->outputBufferInfoQueue.pop();
            if (bufferInfo.attr.flags & AVCODEC_BUFFER_FLAGS_EOS) {
                OH_LOG_ERROR(LOG_APP, "Catch EOS, thread out");
                break;
            }
            videoDecContext_->outputFrameCount++;
            OH_LOG_INFO(LOG_APP,"Out buffer count: %{public}u, size: %{public}d, flag: %{public}u, pts: %{public}ld",
                                videoDecContext_->outputFrameCount, bufferInfo.attr.size, bufferInfo.attr.flags,
                                bufferInfo.attr.pts);
            lock.unlock();

            int32_t ret = videoDecoder_->FreeOutputBuffer(bufferInfo.bufferIndex, true);
            if (ret != AVCODEC_SAMPLE_ERR_OK) {
                OH_LOG_ERROR(LOG_APP, "Decoder output thread out");
                break;
            }

            std::this_thread::sleep_until(lastPushTime + std::chrono::microseconds(sampleInfo_.frameInterval));
            lastPushTime = std::chrono::system_clock::now();
        }
        StartRelease();
    }
    ```

8. After NativeImage has available data, call OH_NativeImage_AcquireNativeWindowBuffer() to obtain video data and call OH_NativeBuffer_FromNativeWindowBuffer() to convert the type of NativeBuffer.
    ```c++
    void VulkanRenderThread::DrawImage() {
        OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN, "VulkanRenderThread", "DrawImage.");
        int ret;
        OHNativeWindowBuffer *inBuffer = nullptr;
        OH_NativeBuffer *nativeBuffer = nullptr;
        int32_t fenceFd1 = -1;
        ret = OH_NativeImage_AcquireNativeWindowBuffer(nativeImage_, &inBuffer, &fenceFd1);
        ret = OH_NativeWindow_NativeObjectReference(inBuffer);
        ret = OH_NativeBuffer_FromNativeWindowBuffer(inBuffer, &nativeBuffer);
        if (nativeBuffer == nullptr) {
            OH_NativeWindow_NativeObjectUnreference(inBuffer);
            OH_NativeImage_ReleaseNativeWindowBuffer(nativeImage_, inBuffer, -1);
            OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN, "VulkanRenderThread", "nativeBuffer is null.");
            return;
        }
        ret = OH_NativeImage_GetTransformMatrix(nativeImage_, matrix_);
        int32_t transformTmp = 0;
        ComputeTransform(transformTmp, matrix_);
        vulkanRenderContext_->hwBufferToTexture(nativeBuffer, matrix_);
        vulkanRenderContext_->render();
        if (lastInBuffer_ != nullptr) {
            OH_NativeWindow_NativeObjectUnreference(lastInBuffer_);
            OH_NativeImage_ReleaseNativeWindowBuffer(nativeImage_, lastInBuffer_, -1);
        }
        lastInBuffer_ = inBuffer;
    }
    ```


9.  Create a corresponding ImageView in Vulkan for rendering and display based on NativeBuffer, and create a sampler of the corresponding format to sample the YUV format image into an RGBA image for correct rendering and display.
    > **NOTE**
    >
    > - Before API version 23, the system supports the extension type VK_EXTERNAL_MEMORY_HANDLE_TYPE_OHOS_NATIVE_BUFFER_BIT_OHOS based on the standard library VkExternalMemoryImageCreateInfo struct.
    > - Starting from API version 23, **VK_EXTERNAL_MEMORY_HANDLE_TYPE_OHOS_NATIVE_BUFFER_BIT_OHOS** is deprecated. Use **VK_EXTERNAL_MEMORY_HANDLE_TYPE_OH_NATIVE_BUFFER_BIT_OHOS** instead.
    ```c++
    void VulkanRender::hwBufferToTexture(OH_NativeBuffer *buffer, float transformMatrix[16]) {
        OH_LOG_Print(LOG_APP, LOG_INFO, 0xFF00, "VulkanRenderThread", "hwBufferToTexture.");
        if (!deviceInfoInitialized) {
            return;
        }
        UniformBufferObject ubo{};
        memcpy(ubo.mvp, transformMatrix, sizeof(float) * 16);
        memcpy(buffersInfo.uniformBufferMapped, &ubo, sizeof(ubo));
        VkNativeBufferFormatPropertiesOHOS nbFormatProps = {
            .sType = VK_STRUCTURE_TYPE_NATIVE_BUFFER_FORMAT_PROPERTIES_OHOS,
            .pNext = nullptr
        };
        VkNativeBufferPropertiesOHOS nbProps = {.sType = VK_STRUCTURE_TYPE_NATIVE_BUFFER_PROPERTIES_OHOS,
                                                .pNext = &nbFormatProps};
        CheckResult(vkGetNativeBufferPropertiesOHOS(device, buffer, &nbProps));

        VkImportNativeBufferInfoOHOS importBufferInfo = {
            .sType = VK_STRUCTURE_TYPE_IMPORT_NATIVE_BUFFER_INFO_OHOS,
            .pNext = nullptr,
            .buffer = buffer
        };

        VkMemoryDedicatedAllocateInfo dedicatedAllocateInfo = {
            .sType = VK_STRUCTURE_TYPE_MEMORY_DEDICATED_ALLOCATE_INFO,
            .pNext = &importBufferInfo,
            .image = VK_NULL_HANDLE, // It will be set later.
            .buffer = VK_NULL_HANDLE
        };

        VkPhysicalDeviceMemoryProperties physicalDeviceMemProps;
        uint32_t foundTypeIndex = 0;
        vkGetPhysicalDeviceMemoryProperties(gpuDevice, &physicalDeviceMemProps);
        uint32_t memTypeCnt = physicalDeviceMemProps.memoryTypeCount;
        for (uint32_t i = 0; i < memTypeCnt; ++i) {
            if (nbProps.memoryTypeBits & (1 << i)) {
                const VkPhysicalDeviceMemoryProperties &pdmp = physicalDeviceMemProps;
                uint32_t supportedFLags = pdmp.memoryTypes[i].propertyFlags & VK_MEMORY_PROPERTY_DEVICE_LOCAL_BIT;
                if (supportedFLags == VK_MEMORY_PROPERTY_DEVICE_LOCAL_BIT) {
                    foundTypeIndex = i;
                    break;
                }
            }
        }

        VkMemoryAllocateInfo allocInfo{
            .sType = VK_STRUCTURE_TYPE_MEMORY_ALLOCATE_INFO,
            .pNext = &dedicatedAllocateInfo,
            .allocationSize = nbProps.allocationSize,
            .memoryTypeIndex = 0 // The memory type is assigned in the next step.
        };

        mapMemoryTypeToIndex(nbProps.memoryTypeBits, VK_MEMORY_PROPERTY_DEVICE_LOCAL_BIT, &allocInfo.memoryTypeIndex);
        VkExternalFormatOHOS externalFormat;
        externalFormat.sType = VK_STRUCTURE_TYPE_EXTERNAL_FORMAT_OHOS;
        externalFormat.pNext = nullptr;
        externalFormat.externalFormat = 0;
        if (nbFormatProps.format == VK_FORMAT_UNDEFINED) {
            externalFormat.externalFormat = nbFormatProps.externalFormat;
        }

        VkExternalMemoryImageCreateInfo externalMemoryImageInfo = {
            .sType = VK_STRUCTURE_TYPE_EXTERNAL_MEMORY_IMAGE_CREATE_INFO,
            .pNext = &externalFormat,
            .handleTypes = VK_EXTERNAL_MEMORY_HANDLE_TYPE_OH_NATIVE_BUFFER_BIT_OHOS,
        };

        VkImageUsageFlags usageFlags = VK_IMAGE_USAGE_SAMPLED_BIT;
        if (nbFormatProps.format != VK_FORMAT_UNDEFINED) {
            usageFlags = usageFlags | VK_IMAGE_USAGE_TRANSFER_SRC_BIT | VK_IMAGE_USAGE_TRANSFER_DST_BIT |
                        VK_IMAGE_USAGE_COLOR_ATTACHMENT_BIT | VK_IMAGE_USAGE_INPUT_ATTACHMENT_BIT;
        }
        OH_NativeBuffer_Config config;
        OH_NativeBuffer_GetConfig(buffer, &config);
        VkImageCreateInfo image_create_info = {
            .sType = VK_STRUCTURE_TYPE_IMAGE_CREATE_INFO,
            .pNext = &externalMemoryImageInfo,
            .flags = 0,
            .imageType = VK_IMAGE_TYPE_2D,
            .format = nbFormatProps.format,
            .extent = {static_cast<uint32_t>(config.width), static_cast<uint32_t>(config.height), 1},
            .mipLevels = 1,
            .arrayLayers = 1,
            .samples = VK_SAMPLE_COUNT_1_BIT,
            .tiling = VK_IMAGE_TILING_OPTIMAL,
            .usage = usageFlags,
            .sharingMode = VK_SHARING_MODE_EXCLUSIVE,
            .queueFamilyIndexCount = 1,
            .pQueueFamilyIndices = &queueFamilyIndex_,
            // VK_IMAGE_LAYOUT_UNDEFINED is mandatory when external memory is used.
            .initialLayout = VK_IMAGE_LAYOUT_UNDEFINED
        };

        CheckResult(vkCreateImage(device, &image_create_info, nullptr, &externalTextureImage));
        dedicatedAllocateInfo.image = externalTextureImage;
        CheckResult(vkAllocateMemory(device, &allocInfo, nullptr, &externalTextureMemory));
        CheckResult(vkBindImageMemory(device, externalTextureImage, externalTextureMemory, 0));

        VkSamplerYcbcrConversionCreateInfo ycbcrCreateInfo = {
            .sType = VK_STRUCTURE_TYPE_SAMPLER_YCBCR_CONVERSION_CREATE_INFO,
            .ycbcrRange = nbFormatProps.suggestedYcbcrRange,
            .components = nbFormatProps.samplerYcbcrConversionComponents,
            .xChromaOffset = nbFormatProps.suggestedXChromaOffset,
            .yChromaOffset = nbFormatProps.suggestedYChromaOffset,
            .chromaFilter = VK_FILTER_LINEAR,
            .forceExplicitReconstruction = false
        };

        if (nbFormatProps.format == VK_FORMAT_UNDEFINED) {
            ycbcrCreateInfo.pNext = &externalFormat;
            ycbcrCreateInfo.format = VK_FORMAT_UNDEFINED;
            ycbcrCreateInfo.ycbcrModel = nbFormatProps.suggestedYcbcrModel;
        }

        CheckResult(
            vkCreateSamplerYcbcrConversion(device, &ycbcrCreateInfo, nullptr, &externalTextureInfo.ycbcrConversion));

        VkSamplerYcbcrConversionInfo convInfoWrap = {
            .sType = VK_STRUCTURE_TYPE_SAMPLER_YCBCR_CONVERSION_INFO,
            .conversion = externalTextureInfo.ycbcrConversion,
            .pNext = nullptr,
        };

        VkImageViewCreateInfo view = {
            .sType = VK_STRUCTURE_TYPE_IMAGE_VIEW_CREATE_INFO,
            .pNext = &convInfoWrap,
            .flags = 0,
            .image = externalTextureImage,
            .viewType = VK_IMAGE_VIEW_TYPE_2D,
            .format = nbFormatProps.format,
            .components =
                {
                    VK_COMPONENT_SWIZZLE_IDENTITY,
                    VK_COMPONENT_SWIZZLE_IDENTITY,
                    VK_COMPONENT_SWIZZLE_IDENTITY,
                    VK_COMPONENT_SWIZZLE_IDENTITY
                },
            .subresourceRange = {VK_IMAGE_ASPECT_COLOR_BIT, 0, 1, 0, 1},
        };
        CheckResult(vkCreateImageView(device, &view, nullptr, &externalTextureInfo.view));

        // Create a sampler.
        const VkSamplerCreateInfo sampler = {
            .sType = VK_STRUCTURE_TYPE_SAMPLER_CREATE_INFO,
            .pNext = &convInfoWrap,
            .magFilter = VK_FILTER_NEAREST,
            .minFilter = VK_FILTER_NEAREST,
            .mipmapMode = VK_SAMPLER_MIPMAP_MODE_NEAREST,
            .addressModeU = VK_SAMPLER_ADDRESS_MODE_CLAMP_TO_EDGE,
            .addressModeV = VK_SAMPLER_ADDRESS_MODE_CLAMP_TO_EDGE,
            .addressModeW = VK_SAMPLER_ADDRESS_MODE_CLAMP_TO_EDGE,
            .mipLodBias = 0.0f,
            .compareEnable = VK_FALSE,
            .anisotropyEnable = VK_FALSE,
            .maxAnisotropy = 1,
            .compareOp = VK_COMPARE_OP_NEVER,
            .minLod = 0.0f,
            .maxLod = 0.0f,
            .borderColor = VK_BORDER_COLOR_FLOAT_OPAQUE_WHITE,
            .unnormalizedCoordinates = VK_FALSE
        };
        CheckResult(vkCreateSampler(device, &sampler, nullptr, &externalTextureInfo.sampler));

        createDescriptorSetLayout();
        createDescriptorSet();

        VkDescriptorImageInfo imageInfo = {
            .sampler = externalTextureInfo.sampler,
            .imageView = externalTextureInfo.view,
            .imageLayout = VK_IMAGE_LAYOUT_SHADER_READ_ONLY_OPTIMAL
        };

        VkDescriptorBufferInfo bufferInfo = {
            .buffer = buffersInfo.uniformBuf, .offset = 0, .range = sizeof(UniformBufferObject)};
        VkWriteDescriptorSet bufferWrite = {.sType = VK_STRUCTURE_TYPE_WRITE_DESCRIPTOR_SET,
                                            .dstSet = gfxPipelineInfo.descSet,
                                            .dstBinding = 0,
                                            .dstArrayElement = 0,
                                            .descriptorCount = 1,
                                            .descriptorType = VK_DESCRIPTOR_TYPE_UNIFORM_BUFFER,
                                            .pImageInfo = nullptr,
                                            .pBufferInfo = &bufferInfo,
                                            .pTexelBufferView = nullptr};
        VkWriteDescriptorSet imageWrite = {.sType = VK_STRUCTURE_TYPE_WRITE_DESCRIPTOR_SET,
                                        .dstSet = gfxPipelineInfo.descSet,
                                        .dstBinding = 1,
                                        .dstArrayElement = 0,
                                        .descriptorCount = 1,
                                        .descriptorType = VK_DESCRIPTOR_TYPE_COMBINED_IMAGE_SAMPLER,
                                        .pImageInfo = &imageInfo,
                                        .pBufferInfo = nullptr,
                                        .pTexelBufferView = nullptr};
        gfxPipelineInfo.descWrites[0] = bufferWrite;
        gfxPipelineInfo.descWrites[1] = imageWrite;
        vkUpdateDescriptorSets(device, 2, gfxPipelineInfo.descWrites, 0, nullptr);

        createGraphicsPipeline();
        createOtherStaff();

        recordCommandBuffer();
        OH_LOG_INFO(LOG_APP, "hwBufferToTexture end");
    }
    ```




