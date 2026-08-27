# PanelInfo

输入法面板属性信息。用于描述输入法面板的类型和显示状态，在创建输入法面板时作为配置参数传入。   
- 含义/功能：定义输入法面板的类型（软键盘或状态栏）和显示状态（固定态、悬浮态或候选词态），作为`InputMethodAbility.createPanel()`的配置参数，决定创建的面板形态。   
- 使用场景：当输入法应用需要通过`createPanel()`创建输入法面板时使用，用于指定面板的类型和状态。例如：创建默认的固定态软键盘面板、创建可自由拖动的悬浮态软键盘面板、创建独立显示候选词的候选词态面板。   
- 使用后效果：设置的`type`和`flag`将决定创建的面板类型和显示形态。设置完成后，系统将按指定类型和状态创建面板，面板的显隐行为由`flag`决定——固定态和悬浮态由系统控制显隐，候选词态由开发者自行控制。   
 PanelInfo参数使用建议：   
- type参数：   
 - 取值范围：[PanelType](arkts-ime-inputmethod-panel-paneltype-e.md)枚举值，即`SOFT_KEYBOARD`(0)或`STATUS_BAR`(1)。   
 - 默认值：`SOFT_KEYBOARD`(0)。不填写时默认创建软键盘类型面板。   
 - 相关参数间的配合/制约关系：`flag`属性当前仅用于描述`SOFT_KEYBOARD`类型面板的状态。当`type`为`STATUS_BAR`时，`flag`的设置不产生实际效果。   
- flag参数：   
 - 取值范围：[PanelFlag](arkts-ime-inputmethod-panel-panelflag-e.md)枚举值，即`FLAG_FIXED`(0)、`FLAG_FLOATING`(1)或`FLAG_CANDIDATE`(2)。   
 - 默认值：`FLAG_FIXED`(0)。不填写时默认为固定态面板。   
 - 使用场景：不同场景应选择不同的flag值：   
 - `FLAG_FIXED`(0)：适用于大多数默认输入场景，面板固定在屏幕底部，由系统控制显隐。   
 - `FLAG_FLOATING`(1)：适用于需要自由调整面板位置的场景（如横屏输入、多窗口环境），面板可拖动，由系统控制显隐。   
 - `FLAG_CANDIDATE`(2)：适用于需要独立展示候选词的场景，面板为候选词窗口，由开发者自行控制显隐时机。   
 - 使用后效果：   
 - 设置`FLAG_FIXED`时：面板固定在屏幕底部，系统控制面板的显示和隐藏。   
 - 设置`FLAG_FLOATING`时：面板为悬浮窗口，可自由拖动位置，系统控制面板的显示和隐藏。   
 - 设置`FLAG_CANDIDATE`时：面板为候选词窗口，系统不会主动控制其显隐，开发者需通过`Panel.show()`和`Panel.hide()`自行控制显示和隐藏时机。   
 - 规格限制：当前仅用于`SOFT_KEYBOARD`类型面板。对`STATUS_BAR`类型面板设置`flag`不产生实际效果。   
 - 注意事项：选择`FLAG_CANDIDATE`时，开发者需自行管理候选词面板的显隐，包括在用户开始输入时调用`Panel.show()`显示面板、在输入结束或用户选择候选词后调用`Panel.hide()`隐藏面板。

**起始版本：** 11

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## 导入模块

```TypeScript
import { PanelInfo, PanelType, PanelFlag } from '@kit.IMEKit';
```

## flag

```TypeScript
flag?: PanelFlag
```

输入法面板状态类型。   
- 默认值为`FLAG_FIXED`(0)，表示固定态面板类型。   
- 当前仅用于描述软键盘类型的面板的状态，对`STATUS_BAR`类型面板设置不产生实际效果。   
- 不同状态类型下面板的显隐行为不同：`FLAG_FIXED`和`FLAG_FLOATING`由系统控制显隐，`FLAG_CANDIDATE`由开发者自行控制显隐。

**类型：** [PanelFlag](arkts-ime-inputmethod-panel-panelflag-e.md)

**默认值：** FLG_FIXED

**起始版本：** 11

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## type

```TypeScript
type: PanelType
```

输入法面板类型。决定面板是软键盘还是状态栏。不填写时默认为`SOFT_KEYBOARD`(0)。

**类型：** [PanelType](arkts-ime-inputmethod-panel-paneltype-e.md)

**起始版本：** 11

**系统能力：** SystemCapability.MiscServices.InputMethodFramework
