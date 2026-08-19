# RestoreStateCallback

```TypeScript
declare type RestoreStateCallback = (savedState: Record<string, Object> | null) => void
```

自定义页面状态恢复回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type RestoreStateCallback = (savedState: Record<string, Object> | null) => void--><!--Device-unnamed-declare type RestoreStateCallback = (savedState: Record<string, Object> | null) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| savedState | Record&lt;string, Object&gt; \| null | 是 | onSaveState保存的自定义页面状态。 |

