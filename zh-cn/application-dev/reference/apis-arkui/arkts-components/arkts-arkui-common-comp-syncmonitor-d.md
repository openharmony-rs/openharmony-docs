# @SyncMonitor

```TypeScript
declare const SyncMonitor: MonitorDecorator
```

@SyncMonitor用于[状态管理V2](../../../ui/state-management/arkts-state-management-overview.md#状态管理v2)，同步监听状态变量修改，使得状态变量支持深度监听。适用于需要精确监听对象嵌套属性变化、数组元素修改等深层状态变化的场景，解决了传统监听方式无法感知深层属性变化的问题，提升状态管理的精确性和开发效率。

开发指南参考：[@SyncMonitor装饰器：状态变量修改同步监听](../../../ui/state-management/arkts-new-syncmonitor.md)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [130001](../errorcode-stateManagement.md#130001-addmonitorclearmonitor非法路径) | The path is invalid. |
