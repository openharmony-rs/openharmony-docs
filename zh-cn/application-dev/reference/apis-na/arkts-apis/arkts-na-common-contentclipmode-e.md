# ContentClipMode

Enum of scrollable containers' content clip mode.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare enum ContentClipMode--><!--Device-unnamed-export declare enum ContentClipMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CONTENT_ONLY

```TypeScript
CONTENT_ONLY = 0
```

Clip to content rect inside margin & padding.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContentClipMode-CONTENT_ONLY = 0--><!--Device-ContentClipMode-CONTENT_ONLY = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BOUNDARY

```TypeScript
BOUNDARY = 1
```

Clip to scrollable's outer rect, including padding but inside margin.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContentClipMode-BOUNDARY = 1--><!--Device-ContentClipMode-BOUNDARY = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SAFE_AREA

```TypeScript
SAFE_AREA = 2
```

Clip to the safeArea of scrollable container.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContentClipMode-SAFE_AREA = 2--><!--Device-ContentClipMode-SAFE_AREA = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

