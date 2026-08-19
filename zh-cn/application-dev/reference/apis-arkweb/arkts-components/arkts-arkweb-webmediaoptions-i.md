# WebMediaOptions

用于配置 Web 组件的媒体策略，包括音频续播有效期、音频独占模式等。适用于需要优化音频播放体验和多实例音频管理的场景，提升媒体播放的稳定性和用户体验。

**起始版本：** 10

<!--Device-unnamed-declare interface WebMediaOptions--><!--Device-unnamed-declare interface WebMediaOptions-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## audioExclusive

```TypeScript
audioExclusive?: boolean
```

应用内多个Web实例的音频是否独占。 true表示应用内多个Web实例的音频独占，false表示不独占。 默认值：true。

**类型：** boolean

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebMediaOptions-audioExclusive?: boolean--><!--Device-WebMediaOptions-audioExclusive?: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## audioSessionType

```TypeScript
audioSessionType?: AudioSessionType
```

应用中Web音频类型。默认值对应系统音频流类型[StreamUsage](../../apis-audio-kit/arkts-apis/arkts-audio-audio-streamusage-e.md)中的STREAM_USAGE_MUSIC。用于改变组件音频类型 与系统音频类型映射关系，影响ArkWeb音频焦点策略。

**类型：** [AudioSessionType](arkts-arkweb-audiosessiontype-e.md)

**起始版本：** 20

<!--Device-WebMediaOptions-audioSessionType?: AudioSessionType--><!--Device-WebMediaOptions-audioSessionType?: AudioSessionType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## resumeInterval

```TypeScript
resumeInterval?: number
```

被其他应用暂停的Web音视频能够自动续播的有效期，单位：秒。取值范围：[-2147483648, 2147483647]。值为0时，不自动续播；大于0时，将在该时间内尝试续播；小于0时，将在无限时间内尝试续播。由于近似值原因，该有 效期可能存在一秒内的误差。 **说明：** HLS视频被打断后，回到前台将自动续播，不受该时间控制。 默认值：0。

**类型：** number

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebMediaOptions-resumeInterval?: number--><!--Device-WebMediaOptions-resumeInterval?: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

