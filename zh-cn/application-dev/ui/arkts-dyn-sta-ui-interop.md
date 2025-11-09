# UI互操作概述

ArkUI开发框架针对ArkTS-Sta静态类型在UI构建和状态管理上进行了适配，相关接口和实现与ArkTS-Dyn动态类型存在差异。这些差异要求ArkTS-Sta与ArkTS-Dyn的UI互操作需遵循额外规则。

在阅读本文档前，建议提前阅读[ArkTS-Sta互操作概述](../quick-start/arkts-interop-overview.md)中的基本原则和规范。


## 使用说明

- 遵循[语言互操作](../quick-start/arkts-interop-overview.md#交互基本原则)的基本规范。


## 使用场景

开发者使用ArkTS-Sta静态类型的主要场景包括：

1. **ArkTS-Dyn模块迁移适配为ArkTS-Sta模块**：使用迁移工具将存量模块适配到ArkTS-Sta静态类型。

2. **ArkTS-Dyn模块使用ArkTS-Sta模块**：工程中部分模块适配为ArkTS-Sta静态类型，未进行静态化适配的模块依赖这些模块，使用互操作能力进行动静态交互。

3. **ArkTS-Sta模块使用ArkTS-Dyn模块**：工程中部分模块适配为ArkTS-Sta静态类型，但依赖部分未静态化适配（如三方库），动静态交互界面使用互操作能力桥接。

针对场景1，主要使用迁移工具进行全量静态适配，不涉及互操作，本指南不再额外阐述。

针对场景2和场景3，开发者可以在模块级别或文件级别导出内容，然后通过互操作机制在不同上下文中导入使用。本指南主要介绍这两个场景的UI互操作指导和规格限制。


## 环境准备

以ArkTS-Dyn项目为例，进行ArkTS-Sta模块的集成开发，需完成以下环境准备工作：

- 创建ArkTS-Dyn项目，具体步骤请参考[ArkTS-Dyn项目创建](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-tools-overview)。

- 在ArkTS-Dyn项目根目录`build-profile.json5`配置文件中，将`app.products`节点下的`arkTSVersion`字段指定为`1.2`。

```json
{
  "app": {
    "products": [
      {
        "name": "default",
        "arkTSVersion": "1.2"  // 需显式配置为1.2以支持互操作
      }
    ]
  }
}
```
