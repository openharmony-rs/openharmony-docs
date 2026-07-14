# HitTestMode

定义触摸测试的响应逻辑及节点阻塞规则。

> **说明：**
>
> 当Stack组件中有多个节点触摸区域重叠时，如果最上层节点的子组件命中，则默认只会对显示在最上层的节点做触摸测试。此时只有给显示在最上层的节点设置
> [hitTestBehavior](arkts-arkui-commonmethod-c.md#hittestbehavior-1)为HitTestMode.Transparent时，才能使显示在下层的节点触发触摸测试。

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Default

```TypeScript
Default
```

默认触摸测试效果。自身及子节点响应触摸测试，但阻塞兄弟节点的触摸测试，不影响祖先节点的触摸测试。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Block

```TypeScript
Block
```

自身响应触摸测试，阻塞子节点、兄弟节点和祖先节点的触摸测试。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Transparent

```TypeScript
Transparent
```

自身和子节点均响应触摸测试，不会阻塞兄弟节点和祖先节点的触摸测试。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## None

```TypeScript
None
```

自身不响应触摸测试，不会阻塞子节点、兄弟节点和祖先节点的触摸测试。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BLOCK_HIERARCHY

```TypeScript
BLOCK_HIERARCHY
```

自身和子节点响应触摸测试，阻止所有优先级较低的兄弟节点和父节点参与触摸测试。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BLOCK_DESCENDANTS

```TypeScript
BLOCK_DESCENDANTS
```

自身不响应触摸测试，并且所有的后代（孩子，孙子等）也不响应触摸测试，不会影响祖先节点的触摸测试。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

