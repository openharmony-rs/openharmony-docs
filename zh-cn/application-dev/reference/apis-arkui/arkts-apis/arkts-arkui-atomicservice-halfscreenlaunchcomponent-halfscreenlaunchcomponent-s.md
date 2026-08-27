# HalfScreenLaunchComponent

半屏嵌入式启动原子化服务组件，当被拉起方未授权嵌入式运行原子化服务时，宿主将使用跳出式拉起原子化服务。

> **说明：**
> 
> 该组件从API version 18开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 
> 当需要在该组件中实现一个可嵌入式运行的原子化服务时，原子化服务必须继承自
> [EmbeddableUIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-embeddableuiability-embeddableuiability-c.md)。若不继承自EmbeddableUIAbility，系统无
> 法确保原子化服务正常运行。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { HalfScreenLaunchComponent } from '@kit.ArkUI';
```

## appId

```TypeScript
appId: string
```

原子化服务appId。

**类型：** string

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content: Callback<void>
```

组件显示内容。

**类型：** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt;

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onError

```TypeScript
onError?: ErrorCallback
```

被拉起的原子化服务在运行过程中发生异常时触发本回调。

**类型：** [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onReceive

```TypeScript
onReceive?: Callback<Record<string, Object>>
```

被拉起的嵌入式运行原子化服务通过[@ohos.window (窗口)](arkts-arkui-window-n.md)调用相关API时，触发本回调。

**类型：** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Record&lt;string, Object&gt;&gt;

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onTerminated

```TypeScript
onTerminated?: Callback<TerminationInfo>
```

被拉起的嵌入式运行原子化服务通过点击原子化服务退出按钮、手势侧滑、调用 terminateSelfWithResult 或者 [terminateSelf](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md#terminateself) 正常退出时，触发本回调。

**类型：** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;TerminationInfo&gt;

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options?: AtomicServiceOptions
```

拉起原子化服务参数。不填时使用默认参数拉起原子化服务。

**类型：** [AtomicServiceOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-atomicserviceoptions-atomicserviceoptions-c.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
