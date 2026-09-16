# @Monitor

```TypeScript
declare const Monitor: MonitorDecorator
```

@Monitor装饰器在状态管理V2中用于监听状态变量修改，使得状态变量支持深度监听。适用于需要在状态变量或其嵌套属性发生变化时执行自定义逻辑（如数据同步、UI刷新、日志记录等）的场景。相比状态管理V1的@Watch，@Monitor支持深度监听嵌套对象属性的变化，并从API版本26.0.0开始支持通配符能力，可更灵活地匹配状态变量路径。

开发指南参考：[@Monitor装饰器：状态变量修改异步监听](../../../ui/state-management/arkts-new-monitor.md)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
