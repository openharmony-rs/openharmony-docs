# Vulkan开发概述

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @andrew1993-->
<!--Designer: @ext4FAT1-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

Vulkan是一套用来做2D和3D渲染的图形应用程序接口，在OpenHarmony中，新增两组扩展`VK_OHOS_surface`和`VK_OHOS_external_memory`。

其中通过扩展`VK_OHOS_surface`相关的API创建出来的VkSurfaceKHR会对接到本机窗口（OHNativeWindow）模块，实现本机缓冲区（OHNativeBuffer）的轮转，用于屏幕显示。

而扩展`VK_OHOS_external_memory`用于在GPU Vulkan环境下与OpenHarmony的OHNativeBuffer之间做零拷贝的内存共享，典型场景如下：

1. 相机/摄像头流水线：Camera产出OHNativeBuffer后直接在Vulkan中采样或作为渲染目标。

2. 视频解码器与渲染器零拷贝：解码器输出OHNativeBuffer，直接导入Vulkan做后处理或合成。

3. Surface/OHNativeWindow互操作：把OHNativeWindow/Surface的Buffer导入Vulkan，或把Vulkan的渲染结果导出成OHNativeBuffer供系统（例如RenderService）或其他客户端使用。

4. 多API互操作：与OpenGL/EGL、Vulkan共用同一OHNativeBuffer做跨API资源共享（零拷贝）。



后续更多Vulkan的用法请参考[Vulkan官方网站](https://www.vulkan.org/)。