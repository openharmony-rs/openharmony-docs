# InputMethodExtraConfig

输入法扩展信息。用于编辑框应用向输入法应用传递自定义键值对配置数据，实现编辑框应用对输入法行为的个性化定制。

- **含义/功能**：定义编辑框应用传递给输入法应用的自定义配置键值对，以`Record&lt;string, CustomValueType&gt;`形式存储。键（key）为配置项名称，值（value）为配置项内容，值类型支持number、string、boolean三种。  
- **使用场景**：当编辑框应用需要向输入法应用传递额外的个性化配置信息以定制输入行为时使用。例如：聊天应用希望输入法默认展示表情面板、搜索应用希望输入法使用特定输入模式、笔记应用希望配置输入法的快捷键行为等。  
- **使用后效果**：设置的扩展信息将在输入法应用与编辑框绑定时加载并传递给输入法应用，输入法应用可据此调整输入行为，提供个性化用户体验。若未设置扩展信息，输入法应用将使用默认配置。

**起始版本：** 22

<!--Device-unnamed-export interface InputMethodExtraConfig--><!--Device-unnamed-export interface InputMethodExtraConfig-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## 导入模块

```TypeScript
import { InputMethodExtraConfig } from '@kit.IMEKit';
```

## customSettings

```TypeScript
customSettings: Record<string, CustomValueType>
```

输入法扩展信息，用于储存自定义的键值对。这些键值对可以是任何与输入法相关的配置信息。例如用户的输入习惯、快捷键设置、主题颜色等。这些设置信息将在输入法应用绑定时加载，以提供个性化的用户体验。

**类型：** Record&lt;string, CustomValueType&gt;

**起始版本：** 22

<!--Device-InputMethodExtraConfig-customSettings: Record<string, CustomValueType>--><!--Device-InputMethodExtraConfig-customSettings: Record<string, CustomValueType>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

