# BlanklessFrameInterpolationInfo

无白屏加载插帧状态信息，作为[BlanklessLoadingParam](arkts-arkweb-webview-blanklessloadingparam-i.md)中的回调入参使用。

**起始版本：** 23

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## key

```TypeScript
key: string
```

唯一标识插帧页面的key值。与[setBlanklessLoadingWithParams](arkts-arkweb-webview-webviewcontroller-c.md#setblanklessloadingwithparams)的key 值相同。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

## reason

```TypeScript
reason: string
```

插帧失败的原因。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

## state

```TypeScript
state: BlanklessFrameInterpolationState
```

当前插帧状态。

**类型：** [BlanklessFrameInterpolationState](arkts-arkweb-webview-blanklessframeinterpolationstate-e.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

## timestamp

```TypeScript
timestamp: number
```

插帧成功、失败或移除的时间点，UTC时间，单位ms。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core
