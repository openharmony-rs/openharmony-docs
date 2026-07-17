# PanelFlag

输入法面板状态类型枚举。定义面板的显示状态形态，决定面板是固定态、悬浮态还是候选词态。

**起始版本：** 11

<!--Device-unnamed-export enum PanelFlag--><!--Device-unnamed-export enum PanelFlag-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## FLAG_FIXED

```TypeScript
FLAG_FIXED = 0
```

固定态面板类型。

**起始版本：** 11

<!--Device-PanelFlag-FLAG_FIXED = 0--><!--Device-PanelFlag-FLAG_FIXED = 0-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## FLAG_FLOATING

```TypeScript
FLAG_FLOATING
```

悬浮态面板类型。

**起始版本：** 11

<!--Device-PanelFlag-FLAG_FLOATING--><!--Device-PanelFlag-FLAG_FLOATING-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## FLAG_CANDIDATE

```TypeScript
FLAG_CANDIDATE
```

候选词态面板类型。

- 当输入面板为候选词态时，面板为显示用户输入候选词的窗口。  
- 输入法服务不会主动控制候选词态面板的显示和隐藏，需要开发者根据应用场景自行控制候选词态面板的显示和隐藏。

**起始版本：** 11

<!--Device-PanelFlag-FLAG_CANDIDATE--><!--Device-PanelFlag-FLAG_CANDIDATE-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

