# PageTransitionCallback

```TypeScript
declare type PageTransitionCallback = (type: RouteType, progress: number) => void
```

页面转场事件回调。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type PageTransitionCallback = (type: RouteType, progress: number) => void--><!--Device-unnamed-declare type PageTransitionCallback = (type: RouteType, progress: number) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [RouteType](arkts-arkui-routetype-e.md) | 是 | transition route type  |
| progress | number | 是 | transition progess  |

