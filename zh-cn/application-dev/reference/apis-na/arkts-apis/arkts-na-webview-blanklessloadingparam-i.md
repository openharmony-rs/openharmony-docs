# BlanklessLoadingParam

Defines the blankless loading parameter. Device behavior differences: Only the mobile phone is supported. For other devices, 801 is returned.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-webview-interface BlanklessLoadingParam--><!--Device-webview-interface BlanklessLoadingParam-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## callback

```TypeScript
callback?: Callback<BlanklessFrameInterpolationInfo>
```

Callback for the blankless frame interpolation, which is used to return the blankless frame interpolation information. Device behavior differences: Only the mobile phone is supported. For other devices, 801 is returned.

**类型：** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[BlanklessFrameInterpolationInfo](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-blanklessframeinterpolationinfo-i.md)&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlanklessLoadingParam-callback?: Callback<BlanklessFrameInterpolationInfo>--><!--Device-BlanklessLoadingParam-callback?: Callback<BlanklessFrameInterpolationInfo>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## duration

```TypeScript
duration?: int
```

Duration of the frame interpolation. The valid range is the union of {0} and [200, 2000]. Device behavior differences: Only the mobile phone is supported. For other devices, 801 is returned. The value must be an integer. <br>Unit: ms.

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlanklessLoadingParam-duration?: int--><!--Device-BlanklessLoadingParam-duration?: int-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## enable

```TypeScript
enable: boolean
```

Whether to enable frame interpolation. The value true indicates to enable frame interpolation, and false indicates the opposite. Device behavior differences: Only the mobile phone is supported. For other devices, 801 is returned.

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlanklessLoadingParam-enable: boolean--><!--Device-BlanklessLoadingParam-enable: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## expirationTime

```TypeScript
expirationTime?: int
```

Expiration time of the historical frame, in ms (UTC time). T indicates the current UTC time. If the expiration time is 30 days, the value is 2592000000 ms. The value range is the union of (T, T + 2592000000] and {0}. 0 indicates that the expiration time is not specified and the default expiration time (7 days) is used. Device behavior differences: Only the mobile phone is supported. For other devices, 801 is returned.

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlanklessLoadingParam-expirationTime?: int--><!--Device-BlanklessLoadingParam-expirationTime?: int-End-->

**系统能力：** SystemCapability.Web.Webview.Core

