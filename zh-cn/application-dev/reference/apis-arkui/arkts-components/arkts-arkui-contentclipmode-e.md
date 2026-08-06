# ContentClipMode

表示滚动容器的内容裁剪模式。

**起始版本：** 14

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为14。

<!--Device-unnamed-declare enum ContentClipMode--><!--Device-unnamed-declare enum ContentClipMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CONTENT_ONLY

```TypeScript
CONTENT_ONLY = 0
```

按内容区裁剪，对应图中的绿色区域。

**起始版本：** 14

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为14。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-ContentClipMode-CONTENT_ONLY = 0--><!--Device-ContentClipMode-CONTENT_ONLY = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BOUNDARY

```TypeScript
BOUNDARY = 1
```

按组件区域裁剪，对应图中的整个蓝色区域。

**起始版本：** 14

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为14。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-ContentClipMode-BOUNDARY = 1--><!--Device-ContentClipMode-BOUNDARY = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SAFE_AREA

```TypeScript
SAFE_AREA = 2
```

按组件配置的SafeArea区域裁剪，对应图中的整个黄色区域。

**起始版本：** 14

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为14。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-ContentClipMode-SAFE_AREA = 2--><!--Device-ContentClipMode-SAFE_AREA = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

