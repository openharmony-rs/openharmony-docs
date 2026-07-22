# DepthComponentCompleteCallback（系统接口）

```TypeScript
declare type DepthComponentCompleteCallback = (event: DepthComponentCompleteEvent) => void
```

背景资源加载成功的回调函数。使用callback异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type DepthComponentCompleteCallback = (event: DepthComponentCompleteEvent) => void--><!--Device-unnamed-declare type DepthComponentCompleteCallback = (event: DepthComponentCompleteEvent) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [DepthComponentCompleteEvent](arkts-arkui-depthcomponentcompleteevent-i-sys.md) | 是 | 背景资源加载成功的事件信息。  |

