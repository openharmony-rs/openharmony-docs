# SystemPanelStatus（系统接口）

```TypeScript
interface SystemPanelStatus
```

系统面板状态信息，用于描述当前系统面板的输入类型、面板标志、升起状态和功能按钮需求。当系统面板状态发生变化时，会通过onSystemPanelStatusChange接口通知订阅者。<br> <br>| 名称 | 类型 | 只读 | 可选 | 说明 |

| -------- | -------- | -------- | -------- | -------- |  
| inputType | [InputMethodInputType](arkts-ime-inputmethodsystempanelmanager-inputmethodinputtype-e-sys.md) | 否 | 否 | 输入法的输入类型，标识当前系统面板所处的输入模式。<br>使用场景：当需要根据不同输入模式调整面板行为或布局时，使用此属性判断当前输入类型。<br>使用后效果：不同inputType值对应不同的面板交互行为，例如SECURITY_INPUT类型下面板会进入安全输入模式。 |

| panelFlag | PanelFlag | 否 | 否 | 输入法软键盘面板的面板标志，表示面板的显示状态（固定态、悬浮态或候选词态）。<br>使用场景：当需要根据面板显示状态调整布局或交互行为时，使用此属性。<br>使用后效果：不同panelFlag值对应不同的面板显示形态：FLAG_FIXED表示面板固定在屏幕底部，FLAG_FLOATING表示面板悬浮显示，FLAG_CANDIDATE表示面板为候选词窗口。<br>相关参数间的配合/制约关系：panelFlag目前仅用于SOFT_KEYBOARD类型的面板。 |

| isPanelRaised | boolean | 否 | 否 | 系统面板是否需要底部抬高。true表示面板需要底部抬高（面板底部区域向上偏移，为下方其他UI元素留出空间），false表示不需要。<br>使用场景：当系统面板下方有其他UI元素（如导航栏、工具条等）需要显示时，通过设置此属性为true使面板底部抬高，避免面板遮挡下方内容。<br>使用后效果：设置为true时，面板底部区域会向上偏移；设置为false时，面板正常显示不做抬高处理。 |

| needFuncButton | boolean | 否 | 否 | 系统面板是否需要功能按钮。true表示面板需要显示功能按钮（如设置、切换输入法等操作按钮），false表示不需要。<br>使用场景：当需要在面板上提供快捷功能入口时，通过设置此属性为true在面板区域显示功能按钮。<br>使用后效果：设置为true时，面板上将显示功能按钮区域；设置为false时，面板不显示功能按钮区域。 |

**起始版本：** 26.0.0

<!--Device-inputMethodSystemPanelManager-interface SystemPanelStatus--><!--Device-inputMethodSystemPanelManager-interface SystemPanelStatus-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { inputMethodSystemPanelManager } from '@kit.IMEKit';
```

## inputType

```TypeScript
inputType: InputMethodInputType
```

输入法的输入类型。

**类型：** [InputMethodInputType](arkts-ime-inputmethodsystempanelmanager-inputmethodinputtype-e-sys.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SystemPanelStatus-inputType: InputMethodInputType--><!--Device-SystemPanelStatus-inputType: InputMethodInputType-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

## isPanelRaised

```TypeScript
isPanelRaised: boolean
```

系统面板是否需要底部抬高。true表示面板需要底部抬高（面板底部区域向上偏移，为下方其他UI元素留出空间），false表示不需要。<br>使用场景：当系统面板下方有其他UI元素（如导航栏、工具条等）需要显示时，通过设置此属性为true使面板底部抬高，避免面板遮挡下方内容。<br>使用后效果：设置为true时，面板底部区域会向上偏移；设置为false时，面板正常显示不做抬高处理。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SystemPanelStatus-isPanelRaised: boolean--><!--Device-SystemPanelStatus-isPanelRaised: boolean-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

## needFuncButton

```TypeScript
needFuncButton: boolean
```

系统面板的功能按钮是否需要。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SystemPanelStatus-needFuncButton: boolean--><!--Device-SystemPanelStatus-needFuncButton: boolean-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

## panelFlag

```TypeScript
panelFlag: PanelFlag
```

输入法软键盘面板的面板标志。

**类型：** [PanelFlag](arkts-ime-inputmethod-panel-panelflag-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SystemPanelStatus-panelFlag: PanelFlag--><!--Device-SystemPanelStatus-panelFlag: PanelFlag-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。
