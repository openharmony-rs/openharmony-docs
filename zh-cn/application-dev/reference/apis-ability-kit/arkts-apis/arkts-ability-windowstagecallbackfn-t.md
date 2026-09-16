# WindowStageCallbackFn

```TypeScript
type WindowStageCallbackFn = (ability: any, windowStage: window.WindowStage) => void
```

当同时注册监听Ability和WindowStage时，调用该回调函数。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | any | 是 | 表示注册监听的Ability。 |
| windowStage | [window.WindowStage](../../apis-arkui/arkts-apis/arkts-arkui-window-windowstage-i.md) | 是 | 表示注册监听的WindowStage。 |
