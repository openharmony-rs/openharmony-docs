# UiTest 文档更新 Prompt

请严格按照规范文件 `/home/c00810129/docs_qj/uitest-doc-rules.md` 中的规则，参考 d.ts 文件 `/home/c00810129/interface/interface_sdk-js_4924/api/@ohos.test.PerfTest.d.ts` 中的接口 JSDoc 定义，更新目标文档 `/home/c00810129/docs_qj/zh-cn/application-dev/reference/apis-test-kit/js-apis-perftest.md`。

**操作前必须先读取规范文件** `/home/c00810129/docs_qj/uitest-doc-rules.md`，确保所有修改严格遵循其中的规则。

**背景**：该文档共约 8800 行、191 个接口方法条目。目标是让所有接口文档统一符合 ArkTS-Dyn/ArkTS-Sta 双模式的文档规范。

**工作步骤**：

1. **分批次处理所有类**（按文档中 `## ClassName` 出现的顺序）：
   - 每次会话处理若干个类，避免上下文溢出
   - 对于方法数量特别多的类（如 Component 类 30+ 个方法），允许在单次会话中只处理该类的一部分方法，下次会话继续处理剩余方法
   - 每次开始前先确认当前进度

2. **逐个方法检查并修正**（包括已部分修改过的类）：
   - 对每个类中的**每一个方法**，从 d.ts 文件的 JSDoc 中读取 `@since X dynamic`、`@since Y static`、`@atomicservice` 等标签信息
   - 逐一比对当前文档是否符合规范，不符合的立即修正
   - 已修改过的方法也需要重新检查，确保之前没有遗漏或错误

3. **同名方法分开声明**：当 d.ts 中同名方法有两段独立的 JSDoc（一段标注 `@since X dynamic`，另一段标注 `@since Y static`），说明 ArkTS-Dyn 和 ArkTS-Sta 的声明有差异（如返回类型不同），需要在文档中分别列出两个独立条目，并通过"相关接口"互相关联

4. **示例代码统一修改**（所有类处理完毕后）：
   - 对所有通过 `findComponent`、`findComponents`、`findWindow`、`waitForComponent`、`scrollSearch` 等可能返回 `null` 的方法获取的对象，在调用其方法前必须添加判空检查
   - 变量类型声明改为 `| null`，调用前加 `if (obj) { ... }` 判空

5. **每个类（或该类的批次）处理完毕后，输出完整的修改清单**，包含该类的**所有方法**，格式如下：
   ```
   ## XXX类 修改清单
   - ✅ methodName<sup>X+</sup> - [新增/修正/补全] ArkTS模式信息
   - ✅ methodName<sup>Y+</sup> - [新增] ArkTS-Sta独立条目
   - ⏭️ methodName<sup>Z+</sup> - 无需修改（已符合规范）
   ```
   > **"无需修改"项必须列出**，目的是防止模型因理解错误而遗漏应修改的方法

6. **不处理 deprecated 类**：By、UiComponent、UiDriver 等标记为 deprecated 的类保持原样，不修改

**不要修改的内容**：
- 不改变接口的方法签名、描述文字、参数表、返回值表、错误码表
- 不修改 deprecated 类中的任何内容
- 不添加任何注释

**关键规则**：
- 接口标题格式为 `### 方法名<sup>起始版本+</sup>`，**标题中不包含入参**，所有接口标题必须有版本号标记
- 仅适用于 ArkTS-Sta 的接口**不应有**"原子化服务API"字段
- 信息排列顺序为：方法签名 → 描述 → 原子化服务API（如有）→ ArkTS模式 → 相关接口（如有）→ 系统能力 → 版本信息 → 设备行为差异（如有）→ 参数 → 返回值 → 错误码 → 示例
- 版本信息格式必须正确，不要使用 `**起始版本：** X` 这种格式，应使用 `**ArkTS-Dyn起始版本：** X` 和 `**ArkTS-Sta起始版本：** Y`
- 锚点格式必须正确，ArkTS-Dyn → ArkTS-Sta 使用 `[方法名(参数列表)](#小写方法名版本号)`，ArkTS-Sta → ArkTS-Dyn 使用 `[方法名](#小写方法名版本号)`

---

## 补充规范说明

### 1. 废弃类处理规则
**修正**: 第6条规则需要更新。

**正确规则**: 废弃类（By、UiComponent、UiDriver）也需要添加 ArkTS 模式信息。这些类的方法都是 `@since 8 dynamiconly`，因此需要为每个方法添加：
```markdown
**ArkTS模式**：该接口仅适用于ArkTS-Dyn。

**系统能力**：SystemCapability.Test.UiTest

**ArkTS-Dyn起始版本：** 8
```

### 2. 避免使用多子任务
**修正**: 第1条规则需要补充。

**正确规则**: 每次会话处理若干个类，但**避免使用多个 task 子代理并行处理**，因为多个子任务可能会相互覆盖文件内容，导致数据丢失。改为逐个方法顺序处理。

### 3. 锚点格式详细规则
**错误示例**（使用完整参数作为锚点）:
```markdown
**相关接口**：该接口对应的ArkTS-Sta接口是[findComponents(on)](#findcomponentson-on)。
```

**正确格式**（仅使用方法名+版本号）:
```markdown
**相关接口**：该接口对应的ArkTS-Sta接口是[findComponents(on)](#findcomponents23)。
```

**规则总结**:
- 锚点统一使用 `#小写方法名版本号` 格式
- 版本号使用接口标题中的版本号（如 9、20、23、26.0.0 等）
- 不要在锚点中包含参数类型信息（如 `-point-`、`-number-` 等）

### 4. 版本信息格式详细规则
**错误示例**（使用独立的 `**起始版本：**` 行）:
```markdown
**起始版本：** 26.0.0

**原子化服务API**：从API版本26开始，该接口支持在原子化服务中使用。

**ArkTS模式**：该接口同时支持ArkTS-Dyn、ArkTS-Sta。

**系统能力**：SystemCapability.Test.UiTest

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0
```

**正确格式**:
```markdown
**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**ArkTS模式**：该接口同时支持ArkTS-Dyn、ArkTS-Sta。

**系统能力**：SystemCapability.Test.UiTest

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 23
```

**规则总结**:
- 不要使用独立的 `**起始版本：** X` 行
- 原子化服务API 的版本格式应为 `从API version X开始`（使用中文字符"版本"）
- ArkTS 模式版本信息统一使用 `**ArkTS-Dyn起始版本：** X` 和 `**ArkTS-Sta起始版本：** Y` 格式
- 版本号不要重复，`**起始版本：**` 和 `**ArkTS-X起始版本：**` 不能同时出现

### 5. 同名方法分开声明说明
当 d.ts 中同名方法有两段独立的 JSDoc（一段标注 `@since X dynamic`，另一段标注 `@since Y static`），说明需要分开声明两个独立条目。但如果 d.ts 中只有一个 `@since X dynamic&static`（两个 @since 在同一块注释中），则只需要一个条目，支持两种模式。

**示例**（需要分开声明）:
```typescript
// d.ts 中有两段独立的 JSDoc
/**
 * @since 9 dynamic
 */
method1(...): ...

/**
 * @since 23 static
 */
method1(...): ...
```

**示例**（不需要分开声明）:
```typescript
// d.ts 中只有一段 JSDoc，同时标注 dynamic 和 static
/**
 * @since 9 dynamic
 * @since 23 static
 */
method2(...): ...
```

### 6. 接口/枚举也需要 ArkTS 模式信息
除了类方法外，所有的枚举（Enum）和接口（Interface）也需要添加 ArkTS 模式信息，格式与类方法相同。

### 7. scrollSearch 特殊说明
scrollSearch 方法只有 dynamic 版本（v9 和 v18），没有 static 版本，因此只有两个动态单模式的条目，不需要添加静态版本的条目。

