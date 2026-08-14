# @ohos.inputMethod.ExtraConfig(输入法扩展信息)

/*
 Copyright (c) 2025 Huawei Device Co., Ltd.
 Licensed under the Apache License, Version 2.0 (the "License");
 you may not use this file except in compliance with the License.
 You may obtain a copy of the License at
 http://www.apache.org/licenses/LICENSE-2.0
 Unless required by applicable law or agreed to in writing, software
 distributed under the License is distributed on an "AS IS" BASIS,
 WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 See the License for the specific language governing permissions and
 limitations under the License.
 /
 **@ohos.inputMethod.ExtraConfig**模块提供输入法扩展信息的数据定义，支持ArkUI编辑框在拉起输入法时传递自定义配置信息给输入法应用。
 本模块是输入法框架的扩展信息数据模块，定义了`InputMethodExtraConfig`接口和`CustomValueType`联合类型，用于承载编辑框应用向输入法应用传递的自定义键值对配置数据。
 本模块提供编辑框应用向输入法应用传递个性化配置的能力。编辑框应用可将用户的输入习惯、快捷键设置、主题颜色、输入模式偏好等自定义信息以键值对形式封装，在绑定输入法时一并传递给输入法应用，使输入法应用据此提供个性化体验。信息总长度不超过3
 2KB。
 当编辑框应用需要向输入法应用传递额外的配置信息以定制输入行为时使用本模块。典型场景包括：聊天应用希望输入法默认展示表情面板、搜索应用希望输入法使用特定输入模式、笔记应用希望配置输入法的快捷键行为等。
 本模块定义了输入法扩展信息的数据结构，用于编辑框应用向输入法应用传递自定义配置。`InputMethodExtraConfig`作为数据类型需与`@ohos.inputMethod`模块的API组合使用——在
 `InputMethodController.attach()`方法中，通过`TextConfig`的`extraConfig`属性将扩展信息传递给输入法应用。输入法应用侧通过`@ohos.inputMethodEngine`模块的
 `InputClient`获取并处理这些扩展信息，据此调整输入行为（如切换输入模式、更改主题等），实现编辑框应用与输入法应用之间的个性化配置协同。
 典型使用流程：编辑框应用构造`InputMethodExtraConfig` → 注入`TextConfig.extraConfig` → 通过`attach()`传递 → 输入法应用通过`InputClient`接收 → 输入法应用
 据此调整行为。
 本模块定义了以下关键Interface和数据类型：
 本模块为纯数据定义模块，`InputMethodExtraConfig`作为数据类型需与其他模块的API组合使用。典型组合为：在`@ohos.inputMethod`模块的
 `InputMethodController.attach()`方法中，通过`TextConfig`将`InputMethodExtraConfig`传递给输入法应用。


## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [InputMethodExtraConfig](arkts-ime-inputmethod-extraconfig-inputmethodextraconfig-i.md) | 输入法扩展信息。用于编辑框应用向输入法应用传递自定义键值对配置数据，实现编辑框应用对输入法行为的个性化定制。 - **含义/功能**：定义编辑框应用传递给输入法应用的自定义配置键值对，以`Record&lt;string, CustomValueType&gt;`形式存储。键（key）为配置项名称，值（value）为配置项内容，值类型支持number、 string、boolean三种。 - **使用场景**：当编辑框应用需要向输入法应用传递额外的个性化配置信息以定制输入行为时使用。例如：聊天应用希望输入法默认展示表情面板、搜索应用希望输入法使用特定输入模式、笔记应用希望配置输入法的快捷键行为等。 - **使用后效果**：设置的扩展信息将在输入法应用与编辑框绑定时加载并传递给输入法应用，输入法应用可据此调整输入行为，提供个性化用户体验。若未设置扩展信息，输入法应用将使用默认配置。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [CustomValueType](arkts-ime-customvaluetype-t.md) | 表示扩展信息值的类型，接口参数具体类型根据其功能而定。开发者可根据配置项的含义选择合适的值类型：数值型配置（如字号大小、权重系数等）使用number；文本型配置（如输入模式名称、主题标识等）使用string；开关型配置（如是否启用某功 能、是否展示某面板等）使用boolean。 |

