# CustomComponentV2

自定义组件V2

**继承/实现关系：** CustomComponentV2 extends [BaseCustomComponent](arkts-arkui-basecustomcomponent-c.md)

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## aboutToReuse

```TypeScript
aboutToReuse?(): void
```

当一个状态管理V2的可复用自定义组件从复用缓存中重新加入到节点树时，触发aboutToReuse生命周期回调。在频繁调用场景下，应避免在其中执行耗时操作，否则可能导致丢帧卡顿。详细内容请参考[\@ReusableV2](../../../ui/state-management/arkts-new-reusableV2.md)。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
