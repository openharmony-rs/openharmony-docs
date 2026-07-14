# BlanklessFrameInterpolationInfo

1.定义插帧状态信息
2.ArkWeb使能白屏插帧优化的场景

设备行为差异:仅支持手机平台，其他平台返回801

**起始版本：** 23

**系统能力：** SystemCapability.Web.Webview.Core

## key

```TypeScript
key: string
```

1.唯一标识本页面的key值

设备行为差异:仅支持手机平台，其他平台返回801

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

## reason

```TypeScript
reason: string
```

插帧失败的原因

设备行为差异:仅支持手机平台，其他平台返回801

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

## state

```TypeScript
state: BlanklessFrameInterpolationState
```

1.当前插帧状态

设备行为差异:仅支持手机平台，其他平台返回801

**类型：** BlanklessFrameInterpolationState

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

## timestamp

```TypeScript
timestamp: number
```

帧插入或者移除的时间点
设备行为差异:仅支持手机平台，其他平台返回801
取值限定为整数。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

