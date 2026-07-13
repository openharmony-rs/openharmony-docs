# IncrementalUpdatePolicy

文本渲染的增量更新策略。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NONE

```TypeScript
NONE = 0
```

不启用增量更新，采用全量布局渲染。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## PARAGRAPH_CACHE

```TypeScript
PARAGRAPH_CACHE = 1
```

启用增量更新，使用段落级缓存。该策略生效的前提是文本绑定的属性字符串对象保持不变，若属性字符串对象发生变化则无法命中缓存。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

