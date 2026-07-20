# @ohos.inputMethod.ExtraConfig

## 导入模块

```TypeScript
import { InputMethodExtraConfig } from '@kit.IMEKit';
```

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [InputMethodExtraConfig](arkts-ime-inputmethod-extraconfig-inputmethodextraconfig-i.md) | 输入法扩展信息。用于编辑框应用向输入法应用传递自定义键值对配置数据，实现编辑框应用对输入法行为的个性化定制。  - **含义/功能**：定义编辑框应用传递给输入法应用的自定义配置键值对，以`Record<string, CustomValueType>`形式存储。键（key）为配置项名称，值（value）为配置项内容，值类型支持number、string、boolean三种。  - **使用场景**：当编辑框应用需要向输入法应用传递额外的个性化配置信息以定制输入行为时使用。例如：聊天应用希望输入法默认展示表情面板、搜索应用希望输入法使用特定输入模式、笔记应用希望配置输入法的快捷键行为等。  - **使用后效果**：设置的扩展信息将在输入法应用与编辑框绑定时加载并传递给输入法应用，输入法应用可据此调整输入行为，提供个性化用户体验。若未设置扩展信息，输入法应用将使用默认配置。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [CustomValueType](arkts-ime-customvaluetype-t.md) | 表示扩展信息值的类型，接口参数具体类型根据其功能而定。开发者可根据配置项的含义选择合适的值类型：数值型配置（如字号大小、权重系数等）使用number；文本型配置（如输入模式名称、主题标识等）使用string；开关型配置（如是否启用某功能、是否展示某面板等）使用boolean。 |

