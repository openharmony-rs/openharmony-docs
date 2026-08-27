# @ohos.InputMethodSubtype(输入法子类型)

## 导入模块

```TypeScript
import { InputMethodSubtype } from '@kit.IMEKit';
```

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [InputMethodSubtype(输入法子类型)](arkts-ime-inputmethodsubtype-i.md) | @ohos.InputMethodSubtype模块提供输入法子类型的属性数据定义，支持描述输入法在不同语言或模式下的子类型信息。 本模块是输入法框架的子类型数据模块，定义了`InputMethodSubtype`接口，用于描述输入法的一种具体输入模式或语言——如中文键盘、英文键盘、大写模式键盘等，每个子类型代表输入法在特定语言或模式下的形态。 本模块提供输入法子类型的属性描述能力。通过`InputMethodSubtype`可获取子类型的标识（`id`、`name`）、语言和区域（`locale`、`language`）、显示标签（`label`）、模式（`mode`：大写 /小写）、图标等属性，用于输入法子类型的识别、展示和切换。 当需要查询、展示或切换输入法的不同语言/模式子类型时使用本模块。典型场景包括：系统设置应用展示输入法子类型列表供用户选择、输入法应用根据子类型信息切换语言或模式、应用获取当前输入法子类型信息等。 |
