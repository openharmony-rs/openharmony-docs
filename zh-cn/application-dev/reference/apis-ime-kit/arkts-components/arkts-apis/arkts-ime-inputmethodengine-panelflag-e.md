# PanelFlag

```TypeScript
export enum PanelFlag
```

输入法面板状态类型枚举。<br>

| 名称 | 值 | 说明 |  
| ------------ | -- | ------------------ |  
| FLG_FIXED | 0 | 固定态面板类型。 |
| FLG_FLOATING | 1 | 悬浮态面板类型。 |
| FLAG_CANDIDATE&lt;sup&gt;15+&lt;/sup&gt; | 2 | 候选词态面板类型。 |

**起始版本：** 10

<!--Device-inputMethodEngine-export enum PanelFlag--><!--Device-inputMethodEngine-export enum PanelFlag-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## FLG_FIXED

```TypeScript
FLG_FIXED = 0
```

固定态面板类型。<br> <br><p>提供给 SOFT_KEYBOARD 类型的面板。当该标志被设置时，软键盘将固定在屏幕底部。</p>

**起始版本：** 10

<!--Device-PanelFlag-FLG_FIXED = 0--><!--Device-PanelFlag-FLG_FIXED = 0-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## FLG_FLOATING

```TypeScript
FLG_FLOATING
```

悬浮态面板类型。<br> <br><p>提供给 SOFT_KEYBOARD 类型的面板。当该标志被设置时，软键盘处于浮动状态。</p>

**起始版本：** 10

<!--Device-PanelFlag-FLG_FLOATING--><!--Device-PanelFlag-FLG_FLOATING-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## FLAG_CANDIDATE

```TypeScript
FLAG_CANDIDATE
```

候选词态面板类型。<br> <br><p>提供给 SOFT_KEYBOARD 类型的面板。当该标志被设置时，软键盘为候选窗口，在用户输入编码时显示可能的候选字符。候选样式的面板不会被输入法服务自动显示或隐藏。输入法应用开发者需要自行控制面板的显示状态。</p>

**起始版本：** 15

<!--Device-PanelFlag-FLAG_CANDIDATE--><!--Device-PanelFlag-FLAG_CANDIDATE-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework
