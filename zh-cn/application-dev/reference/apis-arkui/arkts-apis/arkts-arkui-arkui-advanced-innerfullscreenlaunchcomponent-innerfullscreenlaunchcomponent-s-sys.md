# InnerFullScreenLaunchComponent（系统接口）

非显式全屏拉起原子化服务组件，拉起方可以选择拉起原子化服务的时机。当被拉起方授权使用方嵌入式运行原子化服务时，使用方全屏嵌入式运行原子化服务；未授权时，使用方跳出式拉起原子化服务。

> **说明：**
> 
> 该组件从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 
> 当需要在该组件中实现一个可嵌入式运行的原子化服务时，必须继承自
> [EmbeddableUIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-embeddableuiability-embeddableuiability-c.md)。若不继承自EmbeddableUIAbility，系统无
> 法保证原子化服务功能正常。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { InnerFullScreenLaunchComponent, LaunchController } from '@kit.ArkUI';
```

## content

```TypeScript
content: Callback<void>
```

组件显示内容。

**类型：** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt;

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## controller

```TypeScript
controller: LaunchController
```

拉起原子化服务的控制器。

**类型：** [LaunchController](arkts-arkui-arkui-advanced-innerfullscreenlaunchcomponent-launchcontroller-c-sys.md)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## onError

```TypeScript
onError?: ErrorCallback
```

被拉起的嵌入式运行原子化服务在运行过程中发生异常时触发本回调。可通过回调参数中的code、name和message获取错误信息并做处理。

**类型：** [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md)

**起始版本：** 23

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## onReceive

```TypeScript
onReceive?: Callback<Record<string, Object>>
```

被拉起的嵌入式运行原子化服务通过[@ohos.window (窗口)](arkts-arkui-window-n.md)调用相关API时，触发本回调。

**类型：** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Record&lt;string, Object&gt;&gt;

**起始版本：** 20

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## onTerminated

```TypeScript
onTerminated?: Callback<TerminationInfo>
```

被拉起的嵌入式运行原子化服务通过点击原子化服务退出按钮、手势侧滑、调用 terminateSelfWithResult 或者 [terminateSelf](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md#terminateself) 正常退出时，触发本回调。

**类型：** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;TerminationInfo&gt;

**起始版本：** 23

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
