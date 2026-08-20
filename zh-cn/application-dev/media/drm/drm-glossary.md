# DRM Kit术语

<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @qin_wei_jie-->

## C

### Cencinfo；视音频数据帧加密信息

视音频数据帧加密的描述信息，包括加密算法及模式、密钥标识（KeyId）、初始向量（IV）、子样本加密信息（subsample）等。在使用AVCodec Kit时，可将这些加密描述信息设置到AVBuffer的CencInfo中，在调用PushInputBuffer时，根据这些信息完成视音频数据帧的解密和解码。

### Content Protection Level；内容保护级别

DRM解决方案所支持的内容保护安全级别，用于描述内容解密、解码和渲染的安全程度。常见级别包括：未知内容保护级别（CONTENT_PROTECTION_LEVEL_UNKNOWN）、软件内容保护级别（CONTENT_PROTECTION_LEVEL_SW_CRYPTO）、硬件内容保护级别（CONTENT_PROTECTION_LEVEL_HW_CRYPTO）、硬件增强内容保护级别（CONTENT_PROTECTION_LEVEL_ENHANCED_HW）、最高内容保护级别（CONTENT_PROTECTION_LEVEL_MAX）。

## D

### DRM Certificate；DRM证书

DRM解决方案正常工作所需的设备证书，用于验证设备的合法性和安全性。不同DRM解决方案对应不同的设备证书。一般情况下，设备证书由DRM系统在设备注册时自动下发，无需应用层处理。

### DRM Content Authorization；DRM节目授权

支持在线许可证请求及处理、离线许可证的加载、媒体密钥状态查询，并支持按照DRM许可证的权限要求对DRM节目授权。权限控制策略包括安全级别、输出控制、起始播放时间、结束播放时间等。

### DRM Content Decryption；DRM节目解密

对加密的DRM节目内容进行解密的过程。DRM Kit支持的媒体协议包括HLS、DASH；封装格式包括MP4、TS；视频编码格式包括H264；音频编码格式包括AAC。

### DRM Content License；DRM内容许可证

DRM解决方案使用许可证实现对设备的DRM授权。许可证包含内容密钥和权限控制信息，支持的权限控制策略包括安全级别、输出控制、起始播放时间、结束播放时间等。不同的DRM解决方案采用的许可证格式和支持的权限控制策略不同。

### DRM Kit；数字版权保护服务

数字版权保护服务（Digital Rights Management Kit）提供了DRM加密节目授权解密的功能，包括DRM插件管理、DRM证书管理、DRM许可证管理、DRM节目授权、DRM节目解密等功能。可实现DRM解决方案的集成、DRM解决方案的证书下载、节目的授权及解密。

### DRM MediaKeySystemInfo；DRM信息

DRM节目加密的描述信息，包括DRM解决方案UUID及pssh数据等。应用可以通过业务提供的DRM描述得到节目的DRM信息，也可以根据Media Kit或AVCodec Kit在ArkTS环境下抛出的mediaKeySystemInfoUpdate事件或在C/C++环境下抛出的MediaKeySystemInfo回调得到节目的DRM信息。

### DRM Plugin；DRM插件

集成于系统中，实现DRM HDI层接口的DRM解决方案驱动，用于实现DRM相关功能。一般由DRM解决方案集成方实现，通过实现DRM Kit提供的DRM HDI接口来支持不同的DRM解决方案。

### DRM Provision；DRM证书下载

DRM解决方案采用证书下载流程获取设备证书。不同DRM解决方案的证书下载流程不同，通常情况下，DRM证书由设备出厂预置或DRM系统自动完成下载，应用层无需额外处理。如需应用主动触发下载，请向所选用DRM解决方案的提供商索取证书管理接口文档。

### DRM Solution；DRM解决方案

提供数字版权保护功能的系统或服务，不同的DRM解决方案有不同的UUID（唯一标识符）、证书体系、许可证格式和权限控制策略。常见的DRM解决方案包括Widevine、FairPlay、PlayReady等。

## M

### Media Key；媒体密钥

用于解密DRM保护内容的密钥。包括在线媒体密钥和离线媒体密钥两种类型：在线媒体密钥用于实时流媒体播放，离线媒体密钥支持持久化存储用于离线播放。

### MediaKeySession

用于许可证管理及媒体节目解密的会话对象，生命周期由MediaKeySystem管理。支持许可证的请求、处理、更新和删除等操作，并可与Media Kit或AVCodec Kit配合实现DRM节目解密。

### MediaKeySystem

DRM Kit的核心对象，用于DRM证书管理及MediaKeySession管理。负责管理DRM解决方案的生命周期、证书下载流程和会话实例的创建。

## O

### Offline Media Key；离线媒体密钥

可以在设备上持久化存储的媒体密钥，支持离线播放场景。通过离线媒体密钥标识进行管理，支持恢复、查询状态和删除等操作。

## P

### Protection System Specific Header Box(PSSH)；内容保护系统专有头

DRM解决方案用于描述DRM节目如何加密的数据。包含在DRM信息中，用于生成许可证请求时的初始化数据。

### Provision Request；证书请求

DRM设备证书下载过程中生成的请求信息，包含设备信息和证书请求数据，需发送给DRM证书服务器以获取设备证书响应。

## S

### Secure Decoder；安全解码

在受保护的硬件环境中进行的解码操作，防止解密后的内容被非法访问。需要安全解码时，解密后的内容不会暴露给非安全环境，直接在安全硬件中进行解码。

### Secure Video Path；安全视频通路

实现安全解密、安全解码、安全渲染、安全输出的完整视频处理通路。确保内容在整个处理过程中不被非法获取，依赖DRM解决方案及操作系统的硬件安全能力支持。

## U

### Universally Unique Identifier(UUID)；唯一标识符

用于标识不同的DRM解决方案。每个DRM解决方案都有唯一的UUID，应用通过UUID识别并创建对应的MediaKeySystem实例。