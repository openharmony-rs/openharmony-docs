# @ohos.multimodalAwareness.metadataBinding

本模块提供记忆链接能力调用，包括编码内容传递、订阅事件和取消订阅事件。记忆链接允许系统应用获取第三方应用的编码内容，支持实时事件监听和回调机制，适用于系统应用请求（如截图）并获取应用链接数据的场景，通过跨应用数据传递提升用户体验。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace metadataBinding--><!--Device-unnamed-declare namespace metadataBinding-End-->

**系统能力：** SystemCapability.MultimodalAwareness.MetadataBinding

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [offOperationSubmitMetadata](arkts-multimodalawareness-metadatabinding-offoperationsubmitmetadata-f.md#offOperationSubmitMetadata) | 取消订阅系统获取编码内容的事件。 |
| off_operationSubmitMetadata | 取消订阅系统获取编码内容的事件。 |
| [onOperationSubmitMetadata](arkts-multimodalawareness-metadatabinding-onoperationsubmitmetadata-f.md#onOperationSubmitMetadata) | 订阅系统获取编码内容的事件。 |
| on_operationSubmitMetadata | 订阅系统获取编码内容的事件。应用注册回调，事件发生时通过回调通知应用。调用on()方法订阅事件后，必须在不再需要监听事件时调用off()方法取消订阅，释放监听资源。 |
| [submitMetadata](arkts-multimodalawareness-metadatabinding-submitmetadata-f.md#submitMetadata) | 第三方应用将需要编码的内容传递给接口服务，接口服务将内容传递给调用编码接口的系统应用或服务。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [decodeImage](arkts-multimodalawareness-metadatabinding-decodeimage-f-sys.md#decodeImage) | 解析图片中携带的信息。通过对应的解码算法从图片中提取嵌入的metadata信息。使用promise异步回调。 |
| [encodeImage](arkts-multimodalawareness-metadatabinding-encodeimage-f-sys.md#encodeImage) | 在图片中加入信息。通过特定的编码算法将metadata信息嵌入到图片中。可用于防伪、版权保护等场景。使用promise异步回调。 |
| [notifyMetadataBindingEvent](arkts-multimodalawareness-metadatabinding-notifymetadatabindingevent-f-sys.md#notifyMetadataBindingEvent) | 推送待嵌入的信息给调用编码接口的应用或服务。使用promise异步回调。 |
<!--DelEnd-->

