# RenderStrategy

Enumerates rendering strategies for drawing rounded corners.

**起始版本：** 22

<!--Device-unnamed-declare enum RenderStrategy--><!--Device-unnamed-declare enum RenderStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FAST

```TypeScript
FAST = 0
```

Online rendering mode. The content to be rendered is clipped with rounded corners and directly rendered to the main canvas.

Note: Online rendering may cause display anomalies in certain scenarios. For example, when blur effects are applied within rounded corner components, background colors may interact and create gradient overlay effects. For detailed behavior, see [Example 3: Configuring Offscreen Rounded Corners](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-border.md#example-3-configuring-offscreen-rounded-corners).

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-RenderStrategy-FAST = 0--><!--Device-RenderStrategy-FAST = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## OFFSCREEN

```TypeScript
OFFSCREEN = 1
```

Offscreen rendering mode. The content to be rendered is first rendered to the offscreen canvas without rounded corners, and then clipped with rounded corners and rendered to the main canvas.

**NOTE**

1. Compared with online rendering, offscreen rendering requires additional performance overhead.2. In offscreen rendering, the content is first rendered on an additional canvas, and then rendered on the main canvas.3. Use offscreen rendering primarily for multi-layer components requiring rounded corners. For single components,it has effect only when the [clip](../arkts-components/arkts-arkui-common-commonmethod-c.md#clip-1) attribute, [background](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md),or [foreground color](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md) is configured.

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-RenderStrategy-OFFSCREEN = 1--><!--Device-RenderStrategy-OFFSCREEN = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

