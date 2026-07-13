# BlanklessLoadingParam

1.插帧加载参数

设备行为差异:仅支持手机平台，其他平台返回801

**起始版本：** 23

**系统能力：** SystemCapability.Web.Webview.Core

## callback

```TypeScript
callback?: Callback<BlanklessFrameInterpolationInfo>
```

白屏插帧回调函数，用于返回白屏插帧信息

设备行为差异:仅支持手机平台，其他平台返回801

**类型：** Callback<BlanklessFrameInterpolationInfo>

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

## duration

```TypeScript
duration?: number
```

本次插入帧的存续时间，单位ms
有效时长范围为 {0} 和[200, 2000]的并集
设备行为差异:仅支持手机平台，其他平台返回801
取值限定为整数。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

## enable

```TypeScript
enable: boolean
```

本次是否使能开始插帧，true：使能，false：不使能

设备行为差异:仅支持手机平台，其他平台返回801

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

## expirationTime

```TypeScript
expirationTime?: number
```

历史帧失效时间，UTC时间，单位：ms。用T表示当前UTC时间，同时已知30天为2592000000ms，取值范围：(T, T + 2592000000] 和 {0}的并集，其中0表示不指定失效时间，采用系统默认失效时间（7天）。

设备行为差异:仅支持手机平台，其他平台返回801

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

