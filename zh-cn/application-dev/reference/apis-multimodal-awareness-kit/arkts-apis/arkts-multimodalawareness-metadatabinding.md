# @ohos.multimodalAwareness.metadataBinding

本模块提供记忆链接能力调用，用于向图片加入和解析元数据信息，实现信息传递，包括编码内容传递、订阅事件和取消订阅事件。记忆链接允许系统应用获取第三方应用的编码内容， <br>支持实时事件监听和回调机制，适用于需要在图片中存储和传递元数据的场景，可用于防伪、版权保护等场景，为开发者提供灵活的信息嵌入和解析机制。

**起始版本：** 23

<!--Device-unnamed-declare namespace metadataBinding--><!--Device-unnamed-declare namespace metadataBinding-End-->

**系统能力：** SystemCapability.MultimodalAwareness.MetadataBinding

## 导入模块

```TypeScript
import { metadataBinding } from '@kit.MultimodalAwarenessKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [offOperationSubmitMetadata](arkts-multimodalawareness-metadatabinding-offoperationsubmitmetadata-f.md) | 取消订阅系统获取编码内容的事件。 |
| [off_operationSubmitMetadata](arkts-multimodalawareness-metadatabinding-offoperationsubmitmetadata-f.md) | 取消订阅系统获取编码内容的事件。需先调用on('operationSubmitMetadata')方法订阅事件，未订阅时调用不产生效果。取消订阅后，应用将不再接收编码内容传递事件。 |
| [onOperationSubmitMetadata](arkts-multimodalawareness-metadatabinding-onoperationsubmitmetadata-f.md) | 订阅系统获取编码内容的事件。 |
| [on_operationSubmitMetadata](arkts-multimodalawareness-metadatabinding-onoperationsubmitmetadata-f.md) | 订阅系统应用请求获取编码内容的事件。当系统应用（如截图）请求获取应用的编码内容时触发该事件，应用注册回调后，事件发生时通过回调通知应用。调用on()方法订阅事件后， <br>必须在不再需要监听事件时调用off()方法取消订阅，释放监听资源。 |
| [submitMetadata](arkts-multimodalawareness-metadatabinding-submitmetadata-f.md) | 第三方应用将需要编码的内容传递给接口服务，接口服务将内容传递给调用编码接口的系统应用或服务。本接口由第三方应用调用，供系统应用订阅获取数据。 <br>系统应用需先通过on('operationSubmitMetadata')方法订阅事件，才能接收到编码内容。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [decodeImage](arkts-multimodalawareness-metadatabinding-decodeimage-f-sys.md) | 解析图片中携带的信息。通过对应的解码算法从图片中提取嵌入的metadata信息。使用Promise异步回调。 |
| [encodeImage](arkts-multimodalawareness-metadatabinding-encodeimage-f-sys.md) | 在图片中加入信息。通过特定的编码算法将metadata信息嵌入到图片中，编码过程对图片的视觉呈现影响极小，嵌入的信息可通过decodeImage接口解析。可用于防伪、版权保护等场景。 <br>使用Promise异步回调。 |
| [notifyMetadataBindingEvent](arkts-multimodalawareness-metadatabinding-notifymetadatabindingevent-f-sys.md) | 推送待嵌入的元数据信息给调用编码接口的应用或服务。系统会向指定包名的应用推送信息，并返回当前所在页面的applink信息，用于后续的编码处理。使用Promise异步回调。 |
<!--DelEnd-->

