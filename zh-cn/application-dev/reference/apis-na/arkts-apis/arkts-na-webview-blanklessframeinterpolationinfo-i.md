# BlanklessFrameInterpolationInfo

Defines the frame interpolation information. Device behavior differences: Only the mobile phone is supported. For other devices, 801 is returned.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-webview-interface BlanklessFrameInterpolationInfo--><!--Device-webview-interface BlanklessFrameInterpolationInfo-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## key

```TypeScript
key: string
```

Key value that uniquely identifies the page. Device behavior differences: Only the mobile phone is supported. For other devices, 801 is returned.

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlanklessFrameInterpolationInfo-key: string--><!--Device-BlanklessFrameInterpolationInfo-key: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## reason

```TypeScript
reason: string
```

Reason for the frame interpolation failure. Device behavior differences: Only the mobile phone is supported. For other devices, 801 is returned.

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlanklessFrameInterpolationInfo-reason: string--><!--Device-BlanklessFrameInterpolationInfo-reason: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## state

```TypeScript
state: BlanklessFrameInterpolationState
```

Current frame interpolation state. Device behavior differences: Only the mobile phone is supported. For other devices, 801 is returned.

**类型：** [BlanklessFrameInterpolationState](arkts-na-webview-blanklessframeinterpolationstate-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlanklessFrameInterpolationInfo-state: BlanklessFrameInterpolationState--><!--Device-BlanklessFrameInterpolationInfo-state: BlanklessFrameInterpolationState-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## timestamp

```TypeScript
timestamp: int
```

Time when a frame is interpolated or removed. Device behavior differences: Only the mobile phone is supported. For other devices, 801 is returned. The value must be an integer. &lt;br&gt;Unit: ms.

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlanklessFrameInterpolationInfo-timestamp: int--><!--Device-BlanklessFrameInterpolationInfo-timestamp: int-End-->

**系统能力：** SystemCapability.Web.Webview.Core

