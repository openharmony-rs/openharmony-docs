# PanelFlag

输入法面板状态类型枚举。

| 名称 | 值 | 说明 |  
| ------------ | -- | ------------------ |  
| FLG_FIXED | 0 | 固定态面板类型。 |  
| FLG_FLOATING | 1 | 悬浮态面板类型。 |  
| FLAG_CANDIDATE<sup>15+</sup> | 2 | 候选词态面板类型。 |

**起始版本：** 10

<!--Device-inputMethodEngine-export enum PanelFlag--><!--Device-inputMethodEngine-export enum PanelFlag-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## FLG_FIXED

```TypeScript
FLG_FIXED = 0
```

固定态面板类型。

<p>该功能是为SOFT_KEYBOARD类型的面板提供的。当该标志被设置时，软键盘将固定在屏幕底部。</p>

**起始版本：** 10

<!--Device-PanelFlag-FLG_FIXED = 0--><!--Device-PanelFlag-FLG_FIXED = 0-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## FLG_FLOATING

```TypeScript
FLG_FLOATING
```

悬浮态面板类型。

<p>该功能是为SOFT_KEYBOARD类型的面板提供的。当该标志被设置时，软键盘将是悬浮态的。</p>

**起始版本：** 10

<!--Device-PanelFlag-FLG_FLOATING--><!--Device-PanelFlag-FLG_FLOATING-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## FLAG_CANDIDATE

```TypeScript
FLAG_CANDIDATE
```

候选词态面板类型。

<p>它为类型为SOFT_KEYBOARD的面板提供支持。当该标志被设置时，软键盘将作为一个候选窗口，当用户输入代码时，该窗口会显示可能的字符。具有候选样式的面板不会由输入法服务自动显示或隐藏。输入法应用程序开发者应自行控制面板的状态。</p>

**起始版本：** 15

<!--Device-PanelFlag-FLAG_CANDIDATE--><!--Device-PanelFlag-FLAG_CANDIDATE-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

