# CompetitionStrategy

Defines whether a competition for gesture recognition results should occur between the event injector and the gesture recognizers of the target component. This strategy determines how the injected input event interacts with the target component's own gesture handling logic.

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

<!--Device-unnamed-export enum CompetitionStrategy--><!--Device-unnamed-export enum CompetitionStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

No competition strategy. The injected event does not compete with any existing gestures. Both the injected event and existing gestures can be processed independently and in parallel.

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CompetitionStrategy-DEFAULT = 0--><!--Device-CompetitionStrategy-DEFAULT = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## COMPETITION

```TypeScript
COMPETITION = 1
```

Competition strategy. The gesture recognition result from the event injector will compete with those from the target component's own recognizers.

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CompetitionStrategy-COMPETITION = 1--><!--Device-CompetitionStrategy-COMPETITION = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

