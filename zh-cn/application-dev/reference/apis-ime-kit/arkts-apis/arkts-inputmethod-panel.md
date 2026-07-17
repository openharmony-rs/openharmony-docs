# @ohos.inputMethod.Panel

## 导入模块

```TypeScript
import { PanelInfo, PanelType, PanelFlag } from '@kit.IMEKit';
```

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [PanelInfo](arkts-ime-inputmethod-panel-panelinfo-i.md) | 输入法面板属性信息。用于描述输入法面板的类型和显示状态，在创建输入法面板时作为配置参数传入。- **含义/功能**：定义输入法面板的类型（软键盘或状态栏）和显示状态（固定态、悬浮态或候选词态），作为`InputMethodAbility.createPanel()`的配置参数，决定创建的面板形态。 - **使用场景**：当输入法应用需要通过`createPanel()`创建输入法面板时使用，用于指定面板的类型和状态。例如：创建默认的固定态软键盘面板、创建可自由拖动的悬浮态软键盘面板、创建独立显示候选词的候选词态面板。 - **使用后效果**：设置的`type`和`flag`将决定创建的面板类型和显示形态。设置完成后，系统将按指定类型和状态创建面板，面板的显隐行为由`flag`决定——固定态和悬浮态由系统控制显隐，候选词态由开发者自行控制。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [PanelFlag](arkts-ime-inputmethod-panel-panelflag-e.md) | 输入法面板状态类型枚举。定义面板的显示状态形态，决定面板是固定态、悬浮态还是候选词态。 |
| [PanelType](arkts-ime-inputmethod-panel-paneltype-e.md) | 输入法面板类型枚举。定义面板的类别，决定面板是软键盘还是状态栏。 |

