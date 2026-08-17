# BlanklessLoadingParam

无白屏加载插帧方案的加载参数。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

<!--Device-webview-interface BlanklessLoadingParam--><!--Device-webview-interface BlanklessLoadingParam-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## callback

```TypeScript
callback?: Callback<BlanklessFrameInterpolationInfo>
```

插帧成功、失败或移除后执行的回调。 只有在enable为true时生效。可选，不设置则不进行任何操作。

**类型：** [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[BlanklessFrameInterpolationInfo](arkts-arkweb-webview-blanklessframeinterpolationinfo-i.md)&gt;

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlanklessLoadingParam-callback?: Callback<BlanklessFrameInterpolationInfo>--><!--Device-BlanklessLoadingParam-callback?: Callback<BlanklessFrameInterpolationInfo>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## duration

```TypeScript
duration?: number
```

插帧持续时间。 取值范围：[200, 2000] ∪ {0}，其中0表示不指定持续时间，由系统自动设置合适的持续时间。 单位：ms。

**类型：** number

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlanklessLoadingParam-duration?: number--><!--Device-BlanklessLoadingParam-duration?: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## enable

```TypeScript
enable: boolean
```

是否启用无白屏加载插帧方案。 true表示启用，false表示不启用。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlanklessLoadingParam-enable: boolean--><!--Device-BlanklessLoadingParam-enable: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## expirationTime

```TypeScript
expirationTime?: number
```

历史帧失效时间，UTC时间。 用T表示当前UTC时间，同时已知30天为2592000000ms，取值范围：(T, T + 2592000000] ∪ {0}，其中0表示不指定失效时间，采用系统默认失效时间（7天）。 单位：ms。

**类型：** number

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlanklessLoadingParam-expirationTime?: number--><!--Device-BlanklessLoadingParam-expirationTime?: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

