# @ohos.inputMethod.Panel(输入法面板)

<br>
 <br>本模块是输入法框架的面板属性数据模块，定义了`PanelInfo`接口以及`PanelType`、`PanelFlag`两个枚举类型，用于描述输入法面板的类型（软键盘或状态栏）和显示状态（固定态、悬浮态、候选词态）。
 <br>
 <br>本模块提供输入法面板属性的配置能力。输入法应用可通过`PanelInfo`指定面板类型和状态类型，实现不同形态的面板展示——固定态软键盘（默认，固定在屏幕底部）、悬浮态软键盘（可自由拖动位置）、候选词态面板（独立窗口展示候选词，由开发
 者自行控制显隐）。
 <br>
 <br>当输入法应用需要创建和配置输入法面板时使用本模块。典型场景包括：输入法应用创建默认固定态软键盘面板、输入法应用创建悬浮态键盘以支持自由拖动、输入法应用创建候选词面板以展示输入候选。
 <br>
 <br> > **说明：**
 <br> >
 <br> > - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
 <br> > 数据类型需与`@ohos.inputMethodEngine`模块的API组合使用——在`InputMethodAbility.createPanel()`创建面板时传入`PanelInfo`指定面板类型和状态。典型使用流程：构造
 <br> > PanelInfo → 通过createPanel传入 → 系统据此创建对应类型的面板。不同PanelFlag值对应不同的面板行为：固定态面板固定在屏幕底部、悬浮态面板可自由拖动、候选词态面板由开发者自行控制显隐。
 <br>
 <br>本模块定义了以下关键Interface和枚举类型：
 <br>
 | Interface/类型 | 说明 |
 |---|---|
| [PanelInfo](arkts-ime-inputmethod-panel-panelinfo-i.md) | 输入法面板属性信息接口，包含`type`（面板类型）和`flag`（面板状态类型，默认`FLAG_FIXED`）两个属性，用于描述一个输入法面板的类型和显示形态。 |
| [PanelType](arkts-ime-inputmethod-panel-paneltype-e.md) | 输入法面板类型枚举，定义面板的类别：`SOFT_KEYBOARD`（软键盘，值为0）、`STATUS_BAR`（状态栏，值为1）。 |
| [PanelFlag](arkts-ime-inputmethod-panel-panelflag-e.md) | 输入法面板状态类型枚举，定义面板的显示状态：`FLAG_FIXED`（固定态，值为0）、`FLAG_FLOATING`（悬浮态，值为1）、`FLAG_CANDIDATE`（候选词态，值为2）。候选词态面板的显隐需由开发者自行控制。 |
 <br>
 <br>本模块为纯数据定义模块，`PanelInfo`作为面板属性配置需与其他模块的API组合使用。典型组合为：在`@ohos.inputMethodEngine`模块中，通过
 `InputMethodAbility.createPanel()`创建面板时传入`PanelInfo`指定面板类型和状态。
 <br>
 <br> > **说明：**
 <br> >
 <br> > `FLAG_CANDIDATE`（候选词态）面板的显示和隐藏不受系统控制，开发者需根据应用场景自行管理候选词面板的显隐时机。


## 导入模块

```TypeScript
import { PanelInfo, PanelType, PanelFlag } from '@kit.IMEKit';
```

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [PanelInfo(输入法面板)](arkts-ime-inputmethod-panel-panelinfo-i.md) | 输入法面板属性信息。用于描述输入法面板的类型和显示状态，在创建输入法面板时作为配置参数传入。  - 含义/功能：定义输入法面板的类型（软键盘或状态栏）和显示状态（固定态、悬浮态或候选词态），作为`InputMethodAbility.createPanel()`的配置参数，决定创建的面板形态。  - 使用场景：当输入法应用需要通过`createPanel()`创建输入法面板时使用，用于指定面板的类型和状态。例如：创建默认的固定态软键盘面板、创建可自由拖动的悬浮态软键盘面板、创建独立显示候选词的候选词态面板。  - 使用后效果：设置的`type`和`flag`将决定创建的面板类型和显示形态。设置完成后，系统将按指定类型和状态创建面板，面板的显隐行为由`flag`决定——固定态和悬浮态由系统控制显隐，候选词态由开发者自行控制。   PanelInfo参数使用建议：  - type参数：   - 取值范围：[PanelType](arkts-ime-inputmethod-panel-paneltype-e.md)枚举值，即`SOFT_KEYBOARD`(0)或`STATUS_BAR`(1)。   - 默认值：`SOFT_KEYBOARD`(0)。不填写时默认创建软键盘类型面板。   - 相关参数间的配合/制约关系：`flag`属性当前仅用于描述`SOFT_KEYBOARD`类型面板的状态。当`type`为`STATUS_BAR`时，`flag`的设置不产生实际效果。  - flag参数：   - 取值范围：[PanelFlag](arkts-ime-inputmethod-panel-panelflag-e.md)枚举值，即`FLAG_FIXED`(0)、`FLAG_FLOATING`(1)或`FLAG_CANDIDATE`(2)。   - 默认值：`FLAG_FIXED`(0)。不填写时默认为固定态面板。   - 使用场景：不同场景应选择不同的flag值：   - `FLAG_FIXED`(0)：适用于大多数默认输入场景，面板固定在屏幕底部，由系统控制显隐。   - `FLAG_FLOATING`(1)：适用于需要自由调整面板位置的场景（如横屏输入、多窗口环境），面板可拖动，由系统控制显隐。   - `FLAG_CANDIDATE`(2)：适用于需要独立展示候选词的场景，面板为候选词窗口，由开发者自行控制显隐时机。   - 使用后效果：   - 设置`FLAG_FIXED`时：面板固定在屏幕底部，系统控制面板的显示和隐藏。   - 设置`FLAG_FLOATING`时：面板为悬浮窗口，可自由拖动位置，系统控制面板的显示和隐藏。   - 设置`FLAG_CANDIDATE`时：面板为候选词窗口，系统不会主动控制其显隐，开发者需通过`Panel.show()`和`Panel.hide()`自行控制显示和隐藏时机。   - 规格限制：当前仅用于`SOFT_KEYBOARD`类型面板。对`STATUS_BAR`类型面板设置`flag`不产生实际效果。   - 注意事项：选择`FLAG_CANDIDATE`时，开发者需自行管理候选词面板的显隐，包括在用户开始输入时调用`Panel.show()`显示面板、在输入结束或用户选择候选词后调用`Panel.hide()`隐藏面板。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [PanelFlag(输入法面板)](arkts-ime-inputmethod-panel-panelflag-e.md) | 输入法面板状态类型枚举。定义面板的显示状态形态，决定面板是固定态、悬浮态还是候选词态。 |
| [PanelType(输入法面板)](arkts-ime-inputmethod-panel-paneltype-e.md) | 输入法面板类型枚举。定义面板的类别，决定面板是软键盘还是状态栏。 PanelType使用建议：  - 选取原则：输入法应用通常需要创建一个`SOFT_KEYBOARD`面板作为主键盘界面。`STATUS_BAR`面板为可选面板，仅在需要显示输入法状态信息时创建。  - 规格限制：单个输入法应用仅允许创建一个`SOFT_KEYBOARD`类型和一个`STATUS_BAR`类型的面板。重复创建同类型面板将返回错误。  - 相关接口间的配合/制约关系：`PanelType`需配合`PanelFlag`使用。当前`PanelFlag`仅用于描述`SOFT_KEYBOARD`类型面板的状态；对`STATUS_BAR`类型面板，`PanelFlag`的设置 不产生实际效果。 |
