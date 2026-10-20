# InputMethodInputType（系统接口）

```TypeScript
export enum InputMethodInputType
```

输入类型枚举，用于标识系统面板支持的输入模式。不同的输入类型对应不同的输入场景和面板布局。<br> <br>| 名称 | 值 | 说明 |

| -------- | -- | -------- |  
| NONE | -1 | 无输入类型，表示系统面板不在任何特定输入模式。<br>使用场景：当系统面板处于默认或未知输入状态时使用此值。 |  
| CAMERA_INPUT | 0 | 相机输入类型，表示系统处于相机输入模式。<br>使用场景：用于拍摄输入等场景，如通过相机扫描文字或物体进行输入。<br>使用后效果：面板将切换到相机输入模式，配合相机相关功能进行交互。 |  
| SECURITY_INPUT | 1 | 安全输入类型，表示系统面板处于安全输入模式。<br>使用场景：用于密码、验证码等敏感信息输入场景，系统将启用安全输入保护机制。<br>使用后效果：面板进入安全输入模式，输入内容不会被记录或缓存，防止敏感信息泄露。 |

| VOICE_INPUT | 2 | 语音输入类型，表示系统面板处于语音输入模式。<br>使用场景：用于语音转文字输入场景，用户通过语音进行输入。<br>使用后效果：面板将切换到语音输入模式，显示语音输入相关交互界面（如麦克风按钮、语音识别状态等）。 |

| FLOATING_VOICE_INPUT | 3 | 悬浮语音输入类型，表示系统面板处于悬浮语音输入模式。<br>使用场景：与VOICE_INPUT相比，本类型以悬浮窗口形式提供语音输入功能，适用于需要在不占据固定面板区域的情况下进行语音输入的场景。<br>使用后效果：面板将以悬浮窗口形式显示语音输入交互界面，不占用固定面板区域。 |

**起始版本：** 26.0.0

<!--Device-inputMethodSystemPanelManager-export enum InputMethodInputType--><!--Device-inputMethodSystemPanelManager-export enum InputMethodInputType-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

## CAMERA_INPUT

```TypeScript
CAMERA_INPUT = 0
```

相机输入类型。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InputMethodInputType-CAMERA_INPUT = 0--><!--Device-InputMethodInputType-CAMERA_INPUT = 0-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

## FLOATING_VOICE_INPUT

```TypeScript
FLOATING_VOICE_INPUT = 3
```

浮动语音输入类型。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InputMethodInputType-FLOATING_VOICE_INPUT = 3--><!--Device-InputMethodInputType-FLOATING_VOICE_INPUT = 3-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

## NONE

```TypeScript
NONE = -1
```

无输入类型，面板不在任何输入类型中。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InputMethodInputType-NONE = -1--><!--Device-InputMethodInputType-NONE = -1-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

## SECURITY_INPUT

```TypeScript
SECURITY_INPUT = 1
```

安全输入类型。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InputMethodInputType-SECURITY_INPUT = 1--><!--Device-InputMethodInputType-SECURITY_INPUT = 1-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

## VOICE_INPUT

```TypeScript
VOICE_INPUT = 2
```

语音输入类型。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InputMethodInputType-VOICE_INPUT = 2--><!--Device-InputMethodInputType-VOICE_INPUT = 2-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。
