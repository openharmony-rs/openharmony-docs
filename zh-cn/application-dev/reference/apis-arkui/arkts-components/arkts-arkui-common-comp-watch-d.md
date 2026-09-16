# @Watch

```TypeScript
declare const Watch: (value: string) => PropertyDecorator
```

@Watch装饰器用于状态管理V1中，监听状态变量的变化，并在变量变化时触发指定回调函数。适用于状态变量变化时需要自动执行联动逻辑、数据同步或计算衍生值的场景。

开发指南参考：[@Watch装饰器：状态变量更改通知](../../../ui/state-management/arkts-watch.md)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
