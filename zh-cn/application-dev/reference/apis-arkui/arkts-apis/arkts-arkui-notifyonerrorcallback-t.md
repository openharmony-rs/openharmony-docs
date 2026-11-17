# NotifyOnErrorCallback

```TypeScript
export type NotifyOnErrorCallback = (error: RecoverableStorageError) => void
```

定义用于上报[RecoverableStorage](../../../ui/state-management/arkts-new-recoverablestorage.md)错误的回调。回调在UI线程执行，回调内不应抛出异常。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-unnamed-export type NotifyOnErrorCallback = (error: RecoverableStorageError) => void--><!--Device-unnamed-export type NotifyOnErrorCallback = (error: RecoverableStorageError) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| error | [RecoverableStorageError](arkts-arkui-arkui-statemanagement-recoverablestorageerror-i.md) | 是 | 错误信息。 |
