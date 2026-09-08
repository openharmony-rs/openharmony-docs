# API链接准确性检查规则说明

本文档面向 **文档作者与提交者**，专门说明门禁中「API 链接准确性检查」这一检查项的规则、报错含义与修改方法。

其他检查项请参见 [门禁检查规则说明文档](./门禁检查规则说明文档.md)。

---

## 检查目的

开发指南类文档中大量引用 API 参考文档。实践中常见以下问题：

- API 已重命名或删除，指南中的链接名称仍是旧名，读者点进去发现内容对不上。
- 链接名称写成了中文描述（如「按钮组件」），而目标 API 页面的标题是 `Button`，读者无法确认是否点对了地方。
- 链接指向了 API 文档中的某个章节，但链接名称与该章节标题、章节内表格中的 API 名称均无关联。

该检查项的目标是：**保证链接名称与目标 API 页面的实际内容一致**，使读者从链接名称即可判断跳转结果。

---

## 报错信息速查

| 报错中的 error_info | 触发场景 | 跳转 |
| --- | --- | --- |
| `链接名称不准确` | 链接带锚点，锚点对应标题存在，但标题下没有表格可供二次比对，且名称与标题、标题下说明文字均不匹配 | [查看](#场景二链接到-api-文档中的章节锚点) |
| `链接名称在标题及标题下表格均不存在` | 链接带锚点，锚点对应标题下存在表格，但名称在标题与表格内容中均未找到 | [查看](#标题下方内容的提取范围) |
| `检测到链接名称与目标页面标题不一致` | 链接指向整个 API 文档（无锚点），名称与该文档一级标题、所属模块名称、结构体别名均不匹配 | [查看](#场景一链接到整个-api-文档) |

> **说明：**
> 前两条报错在 [场景三](#场景三api-参考文档内部的锚点链接)（API 参考文档内部的锚点链接）中同样会出现，判定规则一致。

一条完整报错记录的字段格式如下：

```text
error_type: 检测到链接名称与目标页面标题不一致
error_info: [按钮组件](../reference/apis-arkui/arkui-ts/ts-basic-components-button.md)
file: docs/zh-cn/application-dev/ui/button-overview.md
```

> **说明：**
> error_info 直接给出的是出问题的链接原文，可在 file 字段所指的文档中全文搜索该字符串进行定位。

门禁同时会在结果首部输出官方指导链接，可配合查阅：

```text
API链接准确性检查，请查看指导: https://gitcode.com/openharmony/docs/blob/master/zh-cn/contribute/markdown-check/API-reference-link-check.md
```

---

## 适用范围

### 会被检查的文档

同时满足以下全部条件：

- 文档路径包含 `application-dev/`。
- 文档路径 **不** 包含 `/en/`（英文文档不检查）。
- 文档 **未** 在最后一行标注免检标记 `<!--no_check-->`。

### 会被检查的链接

在上述文档中，只对 **指向 API 参考文档的链接** 做准确性校验。判定条件：

- 链接地址中包含 `reference/` 路径片段；或
- 链接为文档内锚点（`#锚点` 形式），且当前文档本身位于 `reference/` 路径下。

指向非 API 参考文档的链接（如指向其他指南、规范、Readme）**不参与** 本项检查。

### 会被跳过的链接

| 编号 | 跳过条件 | 原因 |
| --- | --- | --- |
| 1 | 链接名称为空，方括号内无任何内容 | 由链接风格检查负责报错 |
| 2 | 链接地址以 `http://` 或 `https://` 开头 | 网络链接无法读取目标内容 |
| 3 | 链接地址不带文件后缀且不是纯锚点，例如地址仅写到目录名 | 由相对链接检查负责报错 |
| 4 | 链接地址中出现 2 个及以上 `#` | 由相对链接检查负责报错 |
| 5 | 链接目标文件不存在 | 由相对链接检查负责报错 |
| 6 | 链接锚点在目标文档中不存在 | 由相对链接检查负责报错 |
| 7 | 链接指向目标文档的一级标题 | 由相对链接检查负责报错（不可链接到一级标题） |
| 8 | 链接已登记在白名单 `zh-cn/contribute/allowed-link.md` 中 | 人工确认过的例外情况 |

> **注意：**
> 跳过条件 5 至 7 意味着：本项检查 **不会** 报出断链问题。若链接本身失效，会先由 [相对链接检查](./门禁检查规则说明文档.md#相对链接检查) 报错。请先修复断链，再处理名称准确性问题。

---

## 匹配规则总览

检查的核心是判断「链接名称」与「目标内容」是否匹配。匹配采用 **双向包含** 策略，且 **不区分大小写**：

- 链接名称是目标内容的子串，即通过；
- 目标内容是链接名称的子串，也通过。

目标内容按以下优先级依次尝试，任一命中即通过：

| 优先级 | 目标内容 | 适用场景 |
| --- | --- | --- |
| 1 | 目标锚点或目标文档的标题文本 | 全部场景 |
| 2 | 目标标题下方的说明文字与表格内容 | 链接带锚点 |
| 3 | 目录文件中该文档节点的父级模块名称 | 目标一级标题为「模块描述」或「组件描述」 |
| 4 | C 接口结构体别名（`typedef` 声明） | 目标文件名以 `capi-` 开头 |

---

## 链接名称的预处理

在比对之前，链接名称会先被规范化。理解这些规则有助于判断「为什么明明看起来不一样却通过了」以及「为什么看起来一样却报错了」。

| 编号 | 预处理动作 | 示例 |
| --- | --- | --- |
| 1 | 名称中含英文句点时，只保留最后一个句点之后的部分 | `button.ButtonComponent` 取 `ButtonComponent` |
| 2 | 去除名称中夹杂的 HTML 注释 | 名称「接口 + 注释标记 + 说明」取 `接口说明` |
| 3 | 去除 `sup` 上标标签 | `cm<sup>2</sup>` 取 `cm2` |
| 4 | 去除 `Del`、`RP数字`、`DelRow`、`DelCol数字` 标记 | `<!--RP1-->接口<!--RP1End-->` 取 `接口` |
| 5 | HTML 实体还原为原字符 | `&lt;` 还原为 `<`，`&nbsp;` 还原为空格 |
| 6 | 反斜杠转义还原为原字符 | `List\<String\>` 取 `List<String>` |
| 7 | 去除名称末尾的半角括号 | `createButton()` 取 `createButton` |
| 8 | 去除名称中的所有 `#` | `#接口说明` 取 `接口说明` |
| 9 | 去除名称开头的下划线 | `_AbilityState` 取 `AbilityState` |
| 10 | 去除名称末尾的分号 | `on('click');` 取 `on('click')` |
| 11 | 链接目标为目录文件时，去除名称末尾的「API参考」或「API Reference」 | `Ability API参考` 取 `Ability` |

### 标题一侧是否也做预处理

这一点极易出错，请务必区分：**目标标题是否经过上表预处理，取决于链接是否带锚点。**

| 场景 | 比对的目标标题 | 标题是否经过预处理 |
| --- | --- | --- |
| 链接到整个文档（无锚点） | 目标文档的一级标题 | **不经过**，仅去除首尾空格与反斜杠 |
| 链接到章节锚点（带 `#`） | 锚点对应的章节标题 | **经过**，与链接名称同样处理 |

因此在场景一中，链接名称被截断或还原后的文本，要与 **原样的一级标题** 比对；两侧处理力度不同，是「看起来一样却报错」的主要来源。

> **注意：**
> 预处理规则 1（句点截断）对 `@ohos.promptAction`、`@kit.ArkUI` 这类带模块前缀的名称影响很大：前缀会在比对前被丢弃。书写这类链接名称时，请勿额外附加目标标题中没有的说明文字，否则截断后的文本可能与原标题对不上。完整案例见 [实战案例](#实战案例)。

---

## 场景一：链接到整个 API 文档

链接地址以 `.md` 结尾且不含 `#`，例如：

```markdown
[Button组件](../reference/apis-arkui/arkui-ts/ts-basic-components-button.md)
```

### 判定流程

1. 读取目标文档的一级标题。
2. 将链接名称与一级标题做双向包含匹配（不区分大小写）。命中则通过。
3. 若一级标题为「模块描述」或「组件描述」，转入 [大文件拆分适配](#大文件拆分适配)。
4. 若目标文件名以 `capi-` 开头，转入 [C 接口结构体别名适配](#c-接口结构体别名适配)。
5. 以上均未命中，报错。

### 正例

目标文档 `ts-basic-components-button.md` 的一级标题为 `# Button`：

```markdown
[Button](../reference/apis-arkui/arkui-ts/ts-basic-components-button.md)
[Button组件](../reference/apis-arkui/arkui-ts/ts-basic-components-button.md)
[button](../reference/apis-arkui/arkui-ts/ts-basic-components-button.md)
```

三条均通过：第一条完全一致；第二条包含目标标题 `Button`；第三条忽略大小写后一致。

### 反例与报错样例

```markdown
[按钮组件](../reference/apis-arkui/arkui-ts/ts-basic-components-button.md)
[点击事件接口](../reference/apis-arkui/arkui-ts/ts-basic-components-button.md)
```

报错样例：

```text
error_type: 检测到链接名称与目标页面标题不一致
error_info: [按钮组件](../reference/apis-arkui/arkui-ts/ts-basic-components-button.md)
file: docs/zh-cn/application-dev/ui/button-overview.md
```

### 修改方法

按以下顺序尝试：

1. **首选：** 将链接名称改为目标文档的一级标题，或包含该标题的表述。
2. **次选：** 若希望链接名称表达更具体的含义，改为链接到文档内的具体章节，此时按 [场景二](#场景二链接到-api-文档中的章节锚点) 规则校验。
3. **兜底：** 确认链接名称确有特殊业务含义、无法与标题对齐时，申请加入 [白名单](#白名单申请)。

前两种方案的写法示例（目标文档一级标题为 `Button`，其下存在二级标题「创建按钮」）：

```markdown
[Button组件](../reference/apis-arkui/arkui-ts/ts-basic-components-button.md)
[创建按钮](../reference/apis-arkui/arkui-ts/ts-basic-components-button.md#创建按钮)
```

---

## 场景二：链接到 API 文档中的章节锚点

链接地址含 `#`，例如：

```markdown
[createButton](../reference/apis-arkui/arkui-ts/ts-basic-components-button.md#createbutton)
```

### 判定流程

1. 定位目标文档中该锚点对应的标题。
2. 将链接名称与标题文本做双向包含匹配（不区分大小写）。命中则通过。
3. 未命中时，提取该标题下方的内容做二次比对，详见 [标题下方内容的提取范围](#标题下方内容的提取范围)。
4. 若标题下方存在表格：
   - 名称在表格内容中命中，通过。
   - 均未命中，报 `链接名称在标题及标题下表格均不存在`。
5. 若标题下方不存在表格，报 `链接名称不准确`。

### 同名标题的锚点定位

目标文档中若存在多个文本相同的标题，锚点会自动追加序号：第一个为 `#接口说明`，第二个为 `#接口说明-1`，第三个为 `#接口说明-2`，依此类推。

检查时会依据锚点末尾的序号，定位到对应次序的标题，再提取该标题下方的内容进行比对。因此 **序号写错会导致比对到错误的章节**，进而产生看似莫名的名称不匹配报错。

### 标题下方内容的提取范围

从目标标题开始向下提取，遇到以下任一情况停止：

- 遇到下一个任意层级的标题。
- 遇到 `**Example**` 或 `**示例：**` 行（表示已进入示例代码部分）。

提取范围内的以下内容参与比对：

| 编号 | 参与比对的内容 |
| --- | --- |
| 1 | 范围内第一个非空行的文本（通常为章节说明文字） |
| 2 | 以 `ArkTS-Dyn`、`ArkTS-Sta` 开头的行 |
| 3 | 范围内第一个完整表格（含标题行、分隔符行、至少一行数据）中的指定列 |

表格列的选取规则：

- 表头中存在「名称」列时，取该列全部数据行内容。
- 表头中存在「typedef关键字」列时，取该列全部数据行内容。
- 表头中存在「枚举项」列时，取该列全部数据行内容。
- 上述列均不存在时，取表格每行的第一个有效列内容。

围栏代码块内的行不参与提取。

### 正例

目标章节内容如下：

```markdown
## Colors

配色相关的资源定义。

| 名称 | 类型 | 说明 |
| --- | --- | --- |
| brand | string | 品牌色 |
| fontPrimary | string | 主要字体色 |
| compBackgroundEmphasize | string | 强调背景色 |
```

以下链接均通过：

```markdown
[Colors](../reference/apis-arkui/js-apis-arkui-theme.md#colors)
[brand](../reference/apis-arkui/js-apis-arkui-theme.md#colors)
[fontPrimary](../reference/apis-arkui/js-apis-arkui-theme.md#colors)
[brand, fontPrimary, compBackgroundEmphasize](../reference/apis-arkui/js-apis-arkui-theme.md#colors)
[配色相关的资源定义。](../reference/apis-arkui/js-apis-arkui-theme.md#colors)
```

> **说明：**
> 第四条为「多名称组合链接」：链接名称以 `, ` 分隔为多个元素时，**每一个元素都必须** 在标题或表格内容中命中，只要有一个未命中即报错。

### 反例与报错样例

**反例一：标题下有表格但名称未命中**

```markdown
[按钮颜色](../reference/apis-arkui/js-apis-arkui-theme.md#colors)
```

报错样例：

```text
error_type: 链接名称在标题及标题下表格均不存在
error_info: [按钮颜色](../reference/apis-arkui/js-apis-arkui-theme.md#colors)
file: docs/zh-cn/application-dev/ui/theme-guide.md
```

修改方法：从目标章节表格的「名称」列中挑选真实存在的条目作为链接名称；若需同时指向多个条目，使用 `, ` 分隔且确保每个条目都存在。

**反例二：标题下无表格且名称未命中**

目标章节内容如下：

```markdown
## 创建按钮

调用如下接口创建一个按钮实例。
```

链接写法：

```markdown
[新建按钮](../reference/apis-arkui/arkui-ts/ts-basic-components-button.md#创建按钮)
```

报错样例：

```text
error_type: 链接名称不准确
error_info: [新建按钮](../reference/apis-arkui/arkui-ts/ts-basic-components-button.md#创建按钮)
```

修改方法：将链接名称改为与目标标题一致，或改为包含该标题文本的表述。以下两种写法均可通过，第二种的通过原因是目标标题「创建按钮」是链接名称「创建按钮的方法」的子串。

```markdown
[创建按钮](../reference/apis-arkui/arkui-ts/ts-basic-components-button.md#创建按钮)
[创建按钮的方法](../reference/apis-arkui/arkui-ts/ts-basic-components-button.md#创建按钮)
```

**反例三：多名称组合中部分名称不存在**

```markdown
[brand, fontPrimary, notExistColor](../reference/apis-arkui/js-apis-arkui-theme.md#colors)
```

报错样例：

```text
error_type: 链接名称在标题及标题下表格均不存在
error_info: [brand, fontPrimary, notExistColor](../reference/apis-arkui/js-apis-arkui-theme.md#colors)
```

修改方法：删除不存在的名称，或核对该名称在目标表格中的准确拼写。

---

## 场景三：API 参考文档内部的锚点链接

当前文档本身位于 `reference/` 路径下时，文档内部的锚点链接（`#锚点` 形式）同样参与检查，判定流程与 [场景二](#场景二链接到-api-文档中的章节锚点) 完全一致。

非 `reference/` 路径下的文档，其内部锚点链接 **不参与** 本项检查。

### 正例

在 `reference/apis-arkui/arkui-ts/ts-basic-components-button.md` 内部：

```markdown
详细参数说明请参见[接口说明](#接口说明)。
```

前提：当前文档中存在 `## 接口说明` 标题。

### 反例与报错样例

```markdown
详细参数说明请参见[参数说明](#接口说明)。
```

若 `## 接口说明` 章节下无表格，报错样例：

```text
error_type: 链接名称不准确
error_info: [参数说明](#接口说明)
file: docs/zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-button.md
```

---

## 特殊适配规则

### 大文件拆分适配

API 参考文档存在「大文件拆分」场景：一个模块被拆分为多个子文档，每个子文档的一级标题统一为「模块描述」或「组件描述」。此时用一级标题比对没有意义。

**判定流程：**

1. 检测到目标文档一级标题为「模块描述」或「组件描述」。
2. 从目标文档所在目录逐级向上查找 `Readme-CN.md`。
3. 在该目录文件的无序列表中，定位到指向目标文档的节点。
4. 向上查找缩进层级更小的最近一个节点，将其文本作为「模块名称」。
5. 去除模块名称中的 HTML 注释后，与链接名称做双向包含匹配。
6. 命中则通过，未命中则报 `检测到链接名称与目标页面标题不一致`。

**正例：**

目录文件 `Readme-CN.md` 内容如下：

```markdown
- [状态管理](./state-management/Readme-CN.md)
  - [组件状态管理](./state-management/arkts-new-state-management.md)
  - [应用状态管理](./state-management/arkts-new-app-state-management.md)
```

上述目录文件中，`arkts-new-state-management.md` 节点的直接父节点文本为「状态管理」。

链接到 `arkts-new-state-management.md`（其一级标题为「组件描述」）时，以下写法通过：

```markdown
[组件状态管理](../reference/apis-arkui/arkui-ts/state-management/arkts-new-state-management.md)
[状态管理](../reference/apis-arkui/arkui-ts/state-management/arkts-new-state-management.md)
[状态管理相关接口](../reference/apis-arkui/arkui-ts/state-management/arkts-new-state-management.md)
```

三条均通过的原因：一级标题「组件描述」与三个链接名称都不匹配，但模块名称「状态管理」分别是第一条、第二条链接名称的子串，也是第三条链接名称的子串，双向包含成立。

**反例与报错样例：**

```markdown
[组件级状态](../reference/apis-arkui/arkui-ts/state-management/arkts-new-state-management.md)
```

报错样例：

```text
error_type: 检测到链接名称与目标页面标题不一致
error_info: [组件级状态](../reference/apis-arkui/arkui-ts/state-management/arkts-new-state-management.md)
```

> **说明：**
> 「组件级状态」既不匹配一级标题「组件描述」，也不与模块名称「状态管理」构成包含关系，因此报错。

**修改方法：**

1. 打开目标文档所属目录的 `Readme-CN.md`，确认指向该文档的节点及其父节点文本。
2. 将链接名称改为与父节点文本一致，或与父节点文本构成包含关系的表述。
3. 若目录文件层级本身有误，先修正目录文件的缩进层级。

> **注意：**
> 父节点识别依赖目录文件中列表项的缩进层级。缩进错乱会导致取到错误的模块名称，进而产生看似莫名的不匹配报错。排查时请先确认目录文件层级正确。

### C 接口结构体别名适配

C API 文档（文件名以 `capi-` 开头）中，同一个结构体常有正式名称与 `typedef` 别名两种写法。

**判定流程：**

1. 目标文件名以 `capi-` 开头，且链接名称与一级标题不匹配。
2. 提取目标文档中 **一级标题到第一个二级标题之间** 的 C/C++ 代码块。
3. 收集其中以 `typedef` 开头的行，作为别名清单。
4. 链接名称在别名清单中命中则通过，否则报 `检测到链接名称与目标页面标题不一致`。

**正例：**

目标文档 `capi-struct.md` 的一级标题为 `OH_Drawing_Brush`，一级标题下紧跟一个语言标记为 `c` 的代码块，内容为：

```c
typedef struct OH_Drawing_Brush OH_Drawing_Brush;
typedef struct _OH_Drawing_Brush NativeBrush;
```

该代码块之后才是第一个二级标题（例如「概述」）。

以下链接均通过：

```markdown
[OH_Drawing_Brush](../reference/apis-arkui/arkui-c/capi-struct.md)
[NativeBrush](../reference/apis-arkui/arkui-c/capi-struct.md)
```

**反例与报错样例：**

```markdown
[画刷结构体](../reference/apis-arkui/arkui-c/capi-struct.md)
```

报错样例：

```text
error_type: 检测到链接名称与目标页面标题不一致
error_info: [画刷结构体](../reference/apis-arkui/arkui-c/capi-struct.md)
```

修改方法：改用结构体正式名称或 `typedef` 别名作为链接名称。

> **说明：**
> 别名只在一级标题与第一个二级标题之间的代码块中查找。若目标文档的 `typedef` 声明位于二级标题之下，则不参与别名匹配，此时需使用一级标题名称作为链接名称。

---

## 白名单申请

对于确实无法使命名对齐的历史文档或特殊表述，可登记到白名单中跳过检查。

**白名单文件：** `zh-cn/contribute/allowed-link.md`

**登记格式：** 该文件为一张表格，前三行为文档标题、表头、分隔符行，从第四行起为数据行。每行两列：

| 列 | 内容 | 说明 |
| --- | --- | --- |
| 第一列 | 出现该链接的文档路径 | 相对 `docs/` 的路径，例如 `zh-cn/application-dev/ui/button-overview.md` |
| 第二列 | 链接原文 | 完整的链接字符串，含方括号、圆括号及括号内的名称与地址 |

**示例：**

```markdown
| 文档路径 | 链接内容 |
| --- | --- |
| zh-cn/application-dev/ui/button-overview.md | [按钮组件](../reference/apis-arkui/arkui-ts/ts-basic-components-button.md) |
```

> **注意：**
> 匹配采用 **完全一致** 比对，第二列必须与文档中的链接原文逐字符相同，包含链接名称、链接地址、括号与空格。链接名称或地址发生任何改动后，白名单条目即失效，需同步更新。

---

## 排查流程

收到本项检查的报错后，建议按以下顺序排查：

1. **确认报错链接：** 从 error_info 中取出链接原文，在 file 字段所指的文档中搜索定位。
2. **确认链接是否指向 API 参考：** 查看链接地址中是否包含 `reference/`。若不包含却报错，说明当前文档位于 `reference/` 路径下且使用了文档内锚点。
3. **打开目标文档：** 按链接地址找到目标 API 文档。
4. **区分报错类型处理：**
   - 报 `检测到链接名称与目标页面标题不一致`：核对目标文档一级标题；若为「模块描述」或「组件描述」，核对Readme文件中的父节点名称；若文件名以 `capi-` 开头，核对 `typedef` 别名。
   - 报 `链接名称不准确`：核对锚点对应标题的文本，以及标题下方第一段说明文字。
   - 报 `链接名称在标题及标题下表格均不存在`：核对锚点对应标题下方表格的「名称」、「typedef关键字」、「枚举项」列或首列内容。
5. **核对锚点序号：** 若目标文档存在同名标题，确认锚点末尾的序号是否指向了预期章节。
6. **修改或申请白名单：** 优先修改链接名称；确无法对齐时登记白名单。

---

## 实战案例

以下两个案例取自同一次真实门禁日志，都指向 ArkUI 的 API 参考文档，但根因完全不同。

### 案例一：括号形态差异导致与一级标题不匹配

日志原文：

```text
{'error_type': '检测到链接名称与目标页面标题不一致', 'error_info': '[@ohos.promptAction（弹窗）](../reference/apis-arkui/js-apis-promptAction.md)', 'file': 'docs/zh-cn/application-dev/ui/arkts-immersive-light-sense-constraints.md'}
```

链接不带锚点，属于 [场景一](#场景一链接到整个-api-文档)，比对目标为 `js-apis-promptAction.md` 的一级标题：

```markdown
# @ohos.promptAction (弹窗)
```

标题使用 **半角括号，且左括号前有一个空格**；而链接名称使用 **全角括号、无空格**。

比对过程还原：

| 步骤 | 文本 |
| --- | --- |
| 链接名称原文 | `@ohos.promptAction（弹窗）` |
| 经预处理规则 1（句点截断） | `promptAction（弹窗）` |
| 经预处理规则 7（去末尾半角括号） | `promptAction（弹窗）`，全角括号不受影响 |
| 目标一级标题（场景一不做预处理） | `@ohos.promptAction (弹窗)` |
| 双向包含判定 | 两个方向均不成立 |

修改方法：按目标一级标题逐字符书写链接名称，包含括号形态与空格。

```markdown
[@ohos.promptAction (弹窗)](../reference/apis-arkui/js-apis-promptAction.md)
```

改后复核：名称经句点截断得到 `promptAction (弹窗)`，末尾半角右括号被去除后为 `promptAction (弹窗`，它是目标标题的子串，通过。

> **说明：**
> 若不希望名称携带括号说明，也可直接写 `@ohos.promptAction`：句点截断后为 `promptAction`，同样是目标标题的子串，通过。

### 案例二：带锚点时比对对象是章节而非一级标题

日志原文：

```text
{'error_type': '链接名称在标题及标题下表格均不存在', 'error_info': '[Select下拉菜单](../reference/apis-arkui/arkui-ts/ts-basic-components-select.md#menusystemmaterial)', 'file': 'docs/zh-cn/application-dev/ui/arkts-immersive-light-sense-faq.md'}
```

目标文档 `ts-basic-components-select.md` 的一级标题为 `Select`，链接名称 `Select下拉菜单` 恰好包含 `Select`。

也就是说，这条链接若 **不带锚点**，属于场景一，比对一级标题即可通过。但它带了锚点 `#menusystemmaterial`，于是转入 [场景二](#场景二链接到-api-文档中的章节锚点)：比对对象换成该锚点对应的章节标题与章节下方表格，链接名称在两者中均未命中，报错。

修改方法（二选一）：

1. **保留锚点：** 打开目标文档，找到锚点对应的章节标题，将链接名称改为该标题文本，或改为该章节表格「名称」列中真实存在的条目名。
2. **去掉锚点：** 改为链接到整个文档，此时按一级标题 `Select` 比对，原名称即可通过。

第二种写法：

```markdown
[Select下拉菜单](../reference/apis-arkui/arkui-ts/ts-basic-components-select.md)
```

> **注意：**
> 第一种写法中的链接名称必须以目标文档当前的章节标题为准，请先核对再填写，不要照抄其他文档中的写法。

### 两个案例的共性

| 共性 | 说明 |
| --- | --- |
| 同一链接写法散落在多篇文档 | 本次日志中，指向 promptAction 的链接出现在 5 篇文档，指向 Select 章节的链接出现在 4 篇文档，需在仓库内全文检索链接地址后一次改完 |
| 报错类型取决于相对路径解析结果 | 同一链接写法，在 `reference/` 目录下的文档中因路径多出一层而报断链，在 `ui/` 目录下的文档中路径正确、转为报名称不一致 |
| 根因都在「比对对象」判断失误 | 案例一忽略了标题一侧不做预处理，案例二忽略了锚点会改变比对层级 |

---

## 常见疑问

### 链接名称比标题多了几个字，为什么通过了？

匹配采用双向包含而非完全相等。链接名称 `Button组件` 包含目标标题 `Button`，判定通过。

### 链接名称与标题大小写不同，为什么通过了？

匹配不区分大小写，`button`、`BUTTON`、`Button` 三者等价。

### 链接名称是中文，目标标题是英文，能通过吗？

不能，除非中文名称恰好是标题下方表格或说明文字中出现过的内容。建议统一使用 API 的英文名称作为链接名称。

### 已经改对了名称，为什么还在报错？

依次确认：

- 改动是否已提交入库，门禁读取的是仓库中的最新内容。
- 目标文档是否也在本次改动中变更，导致标题文本已改变。
- 是否存在同名标题，锚点序号定位到了另一个章节。
- 目标文档一级标题是否被 HTML 注释包裹，规范化后与预期不同。

### 报错的链接明明指向的不是 API 文档？

检查链接地址中是否意外包含了 `reference/` 字样，例如目录名、文件名中带有该片段。此类情况会被判定为 API 参考链接。

### 英文文档为什么不检查？

英文 API 文档的命名与中文文档存在体系差异，当前版本对 `/en/` 路径下的文档跳过本项检查。英文文档的链接问题由 [相对链接检查](./门禁检查规则说明文档.md#相对链接检查) 与 [HTTP 链接检查](./门禁检查规则说明文档.md#http-链接检查) 覆盖。
