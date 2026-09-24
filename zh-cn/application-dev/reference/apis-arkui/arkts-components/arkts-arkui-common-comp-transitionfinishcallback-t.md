# TransitionFinishCallback

```TypeScript
declare type TransitionFinishCallback = (transitionIn: boolean) => void
```

定义组件转场动画结束回调的类型。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| transitionIn | boolean | 是 | 转场动画的结束回调类型。<br>true表示出现动画结束回调，false表示消失动画结束回调。 |
