# ArkTS-Sta迁移工具(EasyTrans)用户手册
## EasyTrans简介
ArkTS-Sta版本引入了静态类型系统、增强的协程并发能力及声明式UI的语法等特性，同时与ArkTS-Dyn版本存在语法和语义上的差异，这些差异可能导致存量应用或模块在升级后出现不兼容问题。为此，设计并开发了迁移工具EasyTrans，帮助开发者将应用从ArkTS-Dyn版本迁移到ArkTS-Sta版本，提高迁移效率，识别大部分不兼容变更并提供修复建议，同时支持对高频语法变更的自动修复。

## 适用对象
迁移工具（EasyTrans）面向OpenHarmony生态应用的开发者。<br>
使用ArkTS-Dyn进行开发，请参照[ArkTS-Sta用户指导](./arkts-sta-user-guide.md)。<br>
ArkTS-Sta的基础语法，请参照[ArkTS-Sta规范](https://gitee.com/openharmony/arkcompiler_runtime_core/releases)。

## 使用指导
迁移工具支持两种使用方式：
- 在命令行中使用（具体请参考：[ArkTS-Sta迁移工具使用指导](arkts-easytrans-cli-instructions.md)）。
- 在DevEco Studio中使用（待发布）。

由于ArkTS-Sta尚未正式发布，对应的DevEco Studio也未发布，推荐用户暂时使用命令行方式。

## 从ArkTS-Dyn迁移到ArkTS-Sta的语法变更规则
从ArkTS-Dyn迁移到ArkTS-Sta涉及的语法变更规则如下：
- 了解ArkTS-Sta的基础语法和规则变更：[ArkTS基础规则变更](./arkts-dyn-to-sta-syntax-rules.md)。
- 了解新的并发特性和使用方法：[并发特性变更](./arkts-dyn-to-sta-concurrency-rules.md)。
- 了解与其他系统交互的规则变更：[ArkTS互操作规则变更](./arkts-dyn-to-sta-interop-rules.md)。
- 了解builtin的语法和规则变更：[builtin规则变更](./arkts-dyn-to-sta-builtin-rules.md)。
- 了解ArkUI的语法和接口变更：[从ArkTS-Dyn到ArkTS-Sta的UI语法规则适配](../ui/arkts-dyn-sta-ui-rules.md)。

以上规则详解提供了每条变更规则的讲解和示例，帮助开发者理解ArkTS-Sta与ArkTS-Dyn语法的差异，并根据示例修改代码。

## 常见问题
### 迁移工具的性能表现
迁移工具适用于20万行以下的代码工程或模块包。对于这类工程，工具的扫描和自动修复过程流畅，内存消耗在默认值范围内。不过，处理超过100万行代码的大工程时，就需要较长的时间和较大的内存消耗。迁移工具开发团队将持续提升性能和减少内存消耗。

### 迁移工具是否能扫描和修复所有语法变更
迁移工具可以扫描所有语法变更，但可能遗漏极少数corner case。对于扫描到的语法变更，迁移工具无法自动修复所有问题，因为部分变更涉及复杂的代码逻辑。

### 迁移工具是否能扫描和修复单个文件中的部分代码
迁移工具用于代码静态扫描和自动修复，不是代码编辑器或ArkTS编译器。开发者可以每次选择一部分文件进行扫描和修复，但无法只扫描或修复单个文件中的部分代码。

### 迁移工具能否回退修改
迁移工具在修复代码前会备份源代码。在DevEco Studio中，开发者可以回退打开的文件修改，也可以回退整个代码工程。

### 迁移工具能减少多少迁移代码的工作量
迁移工具旨在将开发者应用的迁移工作量减少到10%。不同应用和模块的减少比例可能不同。