# AccessibilitySamePageMode

Defines the same page mode

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare enum AccessibilitySamePageMode--><!--Device-unnamed-export declare enum AccessibilitySamePageMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SEMI_SILENT

```TypeScript
SEMI_SILENT = 0
```

the first page and root page event is not send.but if application load new page whith navigation,the page event will be sent. this mode is to solve skipping focus

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilitySamePageMode-SEMI_SILENT = 0--><!--Device-AccessibilitySamePageMode-SEMI_SILENT = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FULL_SILENT

```TypeScript
FULL_SILENT = 1
```

the all page event is not send

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilitySamePageMode-FULL_SILENT = 1--><!--Device-AccessibilitySamePageMode-FULL_SILENT = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

