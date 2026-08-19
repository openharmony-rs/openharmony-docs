# TransitionFinishCallback

```TypeScript
export type TransitionFinishCallback = (transitionIn: boolean) => void
```

组件转场动画的结束回调类型。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type TransitionFinishCallback = (transitionIn: boolean) => void--><!--Device-unnamed-export type TransitionFinishCallback = (transitionIn: boolean) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| transitionIn | boolean | 是 | 该入参表示转场动画的结束回调类型。<br/>该参数为true表示该转场回调是出现动画的结束回调，该参数为false表示该转场回调是消失动画的结束回调。 |

