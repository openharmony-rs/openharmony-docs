# AccessibilitySamePageMode

当前跨进程嵌入式显示的组件和宿主应用的同page模式。

**起始版本：** 18

<!--Device-unnamed-declare enum AccessibilitySamePageMode--><!--Device-unnamed-declare enum AccessibilitySamePageMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SEMI_SILENT

```TypeScript
SEMI_SILENT = 0
```

跨进程嵌入式显示的组件拉起来的进程的page事件中如果是首次加载页面或者该事件页面的根节点发送的page事件会被忽略。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-AccessibilitySamePageMode-SEMI_SILENT = 0--><!--Device-AccessibilitySamePageMode-SEMI_SILENT = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FULL_SILENT

```TypeScript
FULL_SILENT = 1
```

跨进程嵌入式显示的组件将忽略所有的page事件。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-AccessibilitySamePageMode-FULL_SILENT = 1--><!--Device-AccessibilitySamePageMode-FULL_SILENT = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

