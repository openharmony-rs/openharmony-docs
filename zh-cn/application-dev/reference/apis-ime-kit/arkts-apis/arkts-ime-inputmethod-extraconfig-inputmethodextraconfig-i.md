# InputMethodExtraConfig

输入法扩展信息。用于编辑框应用向输入法应用传递自定义键值对配置数据，实现编辑框应用对输入法行为的个性化定制。   
- 含义/功能：定义编辑框应用传递给输入法应用的自定义配置键值对，以`Record&lt;string, CustomValueType&gt;`形式存储。键（key）为配置项名称，值（value）为配置项内容，值类型支持number、 string、boolean三种。   
- 使用场景：当编辑框应用需要向输入法应用传递额外的个性化配置信息以定制输入行为时使用。例如：聊天应用希望输入法默认展示表情面板、搜索应用希望输入法使用特定输入模式、笔记应用希望配置输入法的快捷键行为等。   
- 使用后效果：设置的扩展信息将在输入法应用与编辑框绑定时加载并传递给输入法应用，输入法应用可据此调整输入行为，提供个性化用户体验。若未设置扩展信息，输入法应用将使用默认配置。   
 customSettings参数使用建议：   
- 取值范围：键（key）为任意非空字符串；值（value）的类型为[CustomValueType](arkts-ime-customvaluetype-t.md)，即number、string或boolean。同一个键只能对应一个值。   
- 规格限制：信息的总长度不超过32KB。当总长度超过32KB时，超出部分的信息将不被传递。开发者可通过计算所有键值对的JSON序列化长度来判断是否超出限制。   
- 注意事项：   
 - 开发建议：键名建议采用有意义的命名规范（如'inputMode'、'showEmojiPanel'），便于输入法应用解析和使用；避免使用过于简短或无意义的键名（如'a'、'x1'），以免降低可读性和可维护性。   
 - 开发建议：键名应避免与输入法框架内部使用的键名冲突。建议使用应用专属前缀（如'com.example.chat.inputMode'）以防止命名冲突。   
- 相关接口间的配合/制约关系：典型组合为：在`TextInput`控件的 `onWillAttachIME`方法中，通过`IMEClient.setExtraConfig`将`InputMethodExtraConfig`传递给输入法应用，输入法应用侧通过`@ohos.inputMethodEngine`模块的`EditorAttribute`接收并处理该配置。

**起始版本：** 22

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## 导入模块

```TypeScript
import { InputMethodExtraConfig } from '@kit.IMEKit';
```

## customSettings

```TypeScript
customSettings: Record<string, CustomValueType>
```

输入法扩展信息，用于储存自定义的键值对。这些键值对可以是任何与输入法相关的配置信息。例如用户的输入习惯、快捷键设置、主题颜色等。这些设置信息将在输入法应用绑定时加载，以提供个性化的用户体验。不设置时，输入法应用将使用默认配置。

**类型：** Record&lt;string, [CustomValueType](arkts-ime-customvaluetype-t.md)&gt;

**起始版本：** 22

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**示例**

```TypeScript
import { InputMethodExtraConfig, inputMethod } from '@kit.IMEKit';

// 构造输入法扩展信息
let extraConfig: InputMethodExtraConfig = {
  customSettings: {
    'inputMode': 'chat',
    'showEmojiPanel': true,
    'themeColor': 'dark',
    'autoCapitalize': false,
    'fontSize': 16
  }
};

// 将扩展信息注入TextConfig（配合@ohos.inputMethod模块使用）
let textConfig = {
  inputAttribute: { textInputType: 0, enterKeyType: 0 },
  cursorInfo: { left: 100, top: 200, width: 2, height: 20 },
  extraConfig: extraConfig
};

// 通过attach传递给输入法应用
let controller = inputMethod.getController();
controller.attach(true, textConfig);
```
