# ArkTS静态类型应用迁移改造常见问题
<!--Kit: ArkTS-->
<!--Subsystem: RuntimeCore-->
<!--Owner: @lijin1039-->
<!--Designer: @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @zhang_yixin13-->

## 'use static'声明应该放在文件的什么位置

必须放在文件第一行，在所有import和注释语句之前。只能放在.ets文件中。

**正确写法**

```typescript
'use static'

import { Component } from '@kit.ArkUI';

export class MyClass {
  // ...
}
```

**规范要求**

1. 位置要求：必须是文件的**第一行**，在所有import和注释语句之前。
2. 文件要求：只能放在`.ets`文件中，不能放在`.ts`或 `.js`文件中。
3. 全局生效：声明后，整个文件都遵循ArkTS静态类型语法规则。

**错误示例**

```typescript
// 错误：'use static' 必须在第一行，不能在注释行后
'use static'
import { Component } from '@kit.ArkUI';

```

**注意事项**

- 添加`'use static'`后，该文件将无法使用动态类型特性（如`any`、动态属性访问等）。
- 如果需要与动态类型代码互操作，需要使用 `ESValue`或 `STValue`接口。
- 建议在DevEco Studio中使用EasyTrans工具辅助添加`'use static'`声明。

## EasyTrans迁移工具扫描到大量问题，如何高效处理

建议采用问题分类策略，按照问题类型和严重程度分批处理。

**问题分类策略**

EasyTrans工具扫描到的问题可以分为以下几类，按优先级处理：

| 优先级 | 问题类型 | 处理方式 | 工具支持 |
|--------|---------|---------|---------|
| **P0** | 语法错误、类型错误 | 必须修复 | 部分支持自动修复。 |
| **P1** | 互操作问题 | 手动修复 | 需要参考文档。 |
| **P2** | 案例建议 | 可选修复 | 提供修改建议。 |
| **P3** | 代码风格问题 | 可选修复 | 支持自动修复。 |

**高效处理流程**

**步骤1：批量自动修复**

1. 打开EasyTrans工具。
2. 选择扫描范围（建议先在单个文件或小型目录中验证）。
3. 使用Full Scan模式进行全面扫描。
4. 勾选所有可自动修复的问题。
5. 点击"Fix All"或"Fix Selected"。

**步骤2：按模块分批处理**

1. 将问题按模块/文件分组。
2. 优先处理核心模块的问题。
3. 每个模块修复后进行编译验证。
4. 按依赖关系顺序扩展到其他模块。

**步骤3：重点问题优先处理**

| 问题类型 | 优先级 | 原因 |
|---------|-------|------|
| 'use static'缺失 | 高 | 影响整个文件。 |
| 动态属性访问 | 高 | 静态类型不支持。 |
| any类型使用 | 高 | 违反静态类型原则。 |
| 状态变量使用不当 | 中 | 影响并行化。 |
| 不支持的API | 中 | 需要替换或绕过。 |

**步骤4：建立问题清单**

建议使用表格记录问题处理进度：

| 文件 | 问题类型 | 问题描述 | 优先级 | 状态 | 备注 |
|------|---------|---------|-------|------|------|
| File1.ets | 语法错误 | xxx | P0 | 待处理 | xxx |
| File2.ets | 互操作 | xxx | P1 | 已修复 | xxx |

**处理建议**

1. 小步快跑：每次修复1-3个问题，及时验证。
2. 版本控制：每次修复后提交代码，便于回滚。
3. 团队协作：不同成员负责不同模块。
4. 文档记录：记录特殊问题的解决方案。


## 静态类型改造过程中，如何保证向后兼容性

采用双实现并存策略，在应用中同时保留动态和静态实现，根据设备能力自动选择。

**兼容性保障策略**

**双实现并存**

在应用中同时保留动态和静态实现，根据设备能力自动选择：

```typescript
// dispatch.js
export function createDataParser(): void {
  if (getSdkApiVersion() >= 23) {
    // 使用静态实现
    return new DataParserSta()
  } else {
    // 使用动态实现
    return new DataParserDyn()
  }
}
```

## 如何配置项目支持ArkTS静态类型开发

在项目的`build-profile.json5`文件中添加`arkTSVersion`字段并设置值为`1.2`即可启用ArkTS静态类型支持。

**配置步骤**

**步骤1：安装或升级DevEco Studio**

1. 下载最新版DevEco Studio。
2. 安装或升级到推荐版本。

**步骤2：配置项目编译选项**

在项目的`build-profile.json5`文件中，配置静态类型编译选项：

```json
{
  "app": {
    "products": [
      {
        "arkTSVersion": "1.2"
      }
    ]
  }
}
```
> **说明：** 
>
> 在原有工程项目中增加`arkTSVersion`字段，设置值为`1.2`即可启用ArkTS静态类型支持。

## DevEco Studio如何使用debug功能进行调试

DevEco Studio使用debug功能需要手机切换到debug模式配合。 

**打开手机debug模式：**
```shell
hdc shell param set persist.ark.enableDebugMode true
hdc shell reboot
```

**关闭手机debug模式：**

```shell
hdc shell param set persist.ark.enableDebugMode false
hdc shell reboot
```