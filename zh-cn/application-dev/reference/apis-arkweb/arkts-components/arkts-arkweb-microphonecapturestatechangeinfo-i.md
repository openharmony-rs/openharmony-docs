# MicrophoneCaptureStateChangeInfo

提供麦克风触发回调时的状态变化信息，包括改变前的状态和改变后的状态。适用于需要监控麦克风状态变化的场景，提升麦克风管理的可见性和用户体验。

**起始版本：** 23

<!--Device-unnamed-declare interface MicrophoneCaptureStateChangeInfo--><!--Device-unnamed-declare interface MicrophoneCaptureStateChangeInfo-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## newState

```TypeScript
newState: MicrophoneCaptureState
```

改变后的状态

**类型：** [MicrophoneCaptureState](arkts-arkweb-microphonecapturestate-e.md)

**起始版本：** 23

<!--Device-MicrophoneCaptureStateChangeInfo-newState: MicrophoneCaptureState--><!--Device-MicrophoneCaptureStateChangeInfo-newState: MicrophoneCaptureState-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## originalState

```TypeScript
originalState: MicrophoneCaptureState
```

改变前的状态

**类型：** [MicrophoneCaptureState](arkts-arkweb-microphonecapturestate-e.md)

**起始版本：** 23

<!--Device-MicrophoneCaptureStateChangeInfo-originalState: MicrophoneCaptureState--><!--Device-MicrophoneCaptureStateChangeInfo-originalState: MicrophoneCaptureState-End-->

**系统能力：** SystemCapability.Web.Webview.Core

