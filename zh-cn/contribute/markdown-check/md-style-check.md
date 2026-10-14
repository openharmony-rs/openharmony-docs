# 门禁检查规则说明文档

本文档面向 **文档作者与提交者**，用于在门禁报错后，依据日志中的报错信息快速定位规则并完成修改。

使用方式：

1. 在门禁日志中找到 `docs_check` 步骤，复制其中 `error_info` 字段的内容。
2. 在下方 [报错信息速查表](#报错信息速查表) 中检索该内容的关键字，定位到对应检查项。
3. 跳转到对应章节，按「规则说明 → 正反例 → 修改方法」完成整改。
4. 首次处理时，建议先通读 [如何读懂门禁日志](#如何读懂门禁日志) 与 [实战：从日志到完成修改](#实战从日志到完成修改)。

> **说明：**
> API 链接准确性检查的规则较为独立，已拆分为单独文档，请参见 [API链接准确性检查规则说明](./API-reference-link-check.md)。

> **注意：**
> 为便于对照整改，本文档在反例代码块中刻意保留了大量真实的错误写法，包括错误的注释格式、错误的提示语写法、错误的链接标记等。这些内容本身会被门禁的格式检查识别为问题。若需将本文档纳入 docs 仓并接受门禁扫描，请在文档最后一行单独添加免检标记，写法参见[免检标记](#免检标记)。

---

## 如何读懂门禁日志

### 日志的整体结构

门禁按步骤依次执行。每个步骤先输出一行 `[step 序号] 步骤名`，随后输出该步骤的结果：通过时输出 `步骤名 result:success`，未通过时输出具体问题内容。

以下为一段真实日志的节选：

```text
2026-09-01 22:35:54: [step 1] gn_format_check
2026-09-01 22:35:54: gn_format_check result:success
2026-09-01 22:35:54: [step 2]docs_check
2026-09-01 22:35:58: {'API链接准确性检查，请查看指导': 'https://gitcode.com/openharmony/docs/blob/master/zh-cn/contribute/markdown-check/API-reference-link-check.md'}
{'error_type': 'link_error', 'error_info': '[PromptAction](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md)', 'file': 'docs/zh-cn/application-dev/reference/apis-arkui/arkts-apis-uimaterial.md'}
{'error_type': '检测到链接名称与目标页面标题不一致', 'error_info': '[@ohos.promptAction（弹窗）](../reference/apis-arkui/js-apis-promptAction.md)', 'file': 'docs/zh-cn/application-dev/ui/arkts-immersive-light-sense-constraints.md'}
2026-09-01 22:35:58: [step 3] api_check
2026-09-01 22:35:58: api_check result: success
```

> **说明：**
> 本文档只覆盖 `docs_check` 这一步骤输出的问题。日志中其他步骤（例如 `gn_format_check`、`api_check`、`DocCodeCheck`）的失败原因不在本文范围内。

### 判断 docs_check 是否通过

| 日志表现 | 含义 | 处理方式 |
| --- | --- | --- |
| 输出 `docs_check result:success` | 该步骤通过 | 无需处理 |
| 输出一行或多行以 `{'error_type':` 开头的内容 | 该步骤未通过 | 每一行是一个待修改的问题，需逐条处理 |

### 单条问题的字段含义

`docs_check` 输出的每一行是一个字典，固定包含三个字段。日志中为单行紧凑格式：

```text
{'error_type': 'link_error', 'error_info': '[PromptAction](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md)', 'file': 'docs/zh-cn/application-dev/reference/apis-arkui/arkts-apis-uimaterial.md'}
```

| 字段 | 含义 | 排查时的用法 |
| --- | --- | --- |
| `error_type` | 问题分类标识 | 在 [检查项总览](#检查项总览) 中据此定位所属检查项 |
| `error_info` | 具体问题描述 | 含「第 N 行」时直接跳到该行；不含行号时，其内容通常就是出问题的原始文本，需在文档中全文搜索 |
| `file` | 问题文档在仓库中的相对路径 | 确定需要打开并修改哪个文件 |

> **说明：**
> 本文档后续章节给出的报错样例，为便于阅读已按字段拆成多行展示，字段名与日志完全一致。多数样例只列出 `error_type` 与 `error_info`，省略了 `file` 字段；实际日志中每条记录都带有 `file`，其值即待修改文档的仓库相对路径。

> **注意：**
> 有两点容易混淆，请先明确。第一，部分 `error_info` 的内容本身以「错误类型：」开头（例如「错误类型：文档中使用制表符，请将制表符替换为空格」），这是描述文本的固定措辞，与字段 `error_type` 无关，不要把它当成字段名。第二，行首的时间戳（例如 `2026-09-01 22:35:58: `）由 CI 框架添加，通常只出现在该步骤输出块的第一行，与问题内容无关，排查时可忽略。

### 指导链接行

`docs_check` 未通过时，可能在输出开头插入一行官方指导链接。它 **不是一条问题记录**，没有 `error_type` 字段，不需要也无法修改，点开链接阅读即可。

| 指导链接行的内容 | 出现条件 |
| --- | --- |
| `{'API链接准确性检查，请查看指导': '...'}` | 存在 API 链接准确性问题 |
| `{'md_style_error类型问题处理，请查看指导': '...'}` | 存在 Markdown 格式问题 |

### 排查顺序建议

1. **先按 `file` 归组。** 同一篇文档往往会一次性报出多条问题，按文档归组后可一趟改完，避免反复提交。
2. **再看 `error_info` 是否含行号。** 含「第 N 行」「第 N - M 行」的，直接定位到该行或该区间。
3. **`error_info` 不含行号时，全文搜索该内容。** `link_error`（链接原文）、`figure_lost`（图片路径）、`尖括号未转义`（尖括号片段）等类型均属于这种情况。
4. **最后对照 `error_type` 阅读规则。** 理解规则本意后再改，避免改完换个形式再次触发。

---


---

## 检查项总览

| 检查项 | 报错中的 error_type | 适用文档范围 |
| --- | --- | --- |
| [责任田标签检查](#责任田标签检查) | `owner_lost` | `zh-cn/application-dev/` 下文档（master 分支） |
| [图片引用检查](#图片引用检查) | `figure_lost`、`figure_check` | 全部 Markdown 文档 |
| [相对链接检查](#相对链接检查) | `link_error`、`链接不规范`、`链接标题中存在br标签`、`不可链接到一级标题`、`面向第三方应用的文档，链接到了系统应用的文档`、`相对链接不可链接到readme/website` | 全部 Markdown 文档 |
| [API 链接准确性检查](./API-reference-link-check.md) | `链接名称不准确`、`链接名称在标题及标题下表格均不存在`、`检测到链接名称与目标页面标题不一致` | `application-dev/` 下中文文档 |
| [文件名检查](#文件名检查) | `file_name`、`en_file_check` | 全部文件 |
| [Markdown 格式检查](#markdown-格式检查) | `md_style_error`、`code_style_error`、`table_scan`、`notice_explanation`、`text_link_error`、`scan_html_error`、`scan_title`、`tag_error`、`mdLinkStyleError`、`md_LinkStyle_Error`、`Urlpath_Error` | 除 `en/` 路径外的全部 Markdown 文档 |
| [HTTP 链接检查](#http-链接检查) | `http_link_error`、`http_error` | 全部 Markdown 文档 |
| [英文文档中文字符检查](#英文文档中文字符检查) | `Chinese_in_English` | `en/` 下文档 |
| [文档标题检查](#文档标题检查) | `文档为空`、`文档一级标题错误`、`文档标题层级大于3`、`title_error` | 空文档检查覆盖全部文档；标题细则仅 `application-dev/` 下文档 |
| [尖括号与合并冲突检查](#尖括号与合并冲突检查) | `尖括号未转义` | 全部 Markdown 文档 |

---

## 通用跳过规则

在逐项排查前，请先确认文档是否命中以下跳过条件，避免无效修改。

### 空文档跳过

文档内容去除首尾空白后为空时，[文档标题检查](#文档标题检查) 会直接报「不可提交空文档」，其余检查项均跳过该文档。

### 免检标记

在文档 **最后一行** 单独写入下列标记，可跳过大部分检查项：

```text
<!--no_check-->
```

生效条件（必须同时满足）：

- 标记位于文档最后一个非空行。
- 该行除标记本身外不含任何其他字符（首尾空格允许）。

> **注意：**
> 1. 该标记仅用于处理少数确实不符合规则、但必须按此形态交付的文档。**添加时必须经资料接口人同意！！！添加后文档后续问题由领域自己手动检查，保证质量！！！**
> 2. 免检标记 **不对** [责任田标签检查](#责任田标签检查)、[文件名检查](#文件名检查)、[尖括号与合并冲突检查](#尖括号与合并冲突检查) 生效，这三项始终执行。

### 代码块内容排除

围栏代码块（由三个反引号包裹的内容）中的文本，在绝大多数检查项中会被排除，不会触发链接、标题、尖括号等规则。

代码块内部另有独立的 [示例代码检查](#示例代码检查) 规则。

### 英文文档差异

路径中包含 `/en/` 的文档：

- **跳过** 责任田标签检查、Markdown 格式检查、API 链接准确性检查。
- **执行** 英文文档中文字符检查、HTTP 链接检查（中文链接判定）、文件名检查、图片引用检查、相对链接检查、文档标题检查、尖括号检查。

### 删除与替换标记

`<!--Del-->` 与 `<!--DelEnd-->`、`<!--RP数字-->` 与 `<!--RP数字End-->` 标记对中的内容，在不同检查项中处理方式不同：

- 相对链接检查：标记对内的链接 **仍会检查**，但会放宽「不可链接到系统应用文档」的限制。
- 链接风格检查、表格检查：标记本身会被剔除后再检查内容。
- 标记对必须成对出现，否则触发 [标签配对检查](#标签配对检查)。

---

## 责任田标签检查

### 适用范围

同时满足以下条件的文档：

- 路径包含 `/zh-cn/application-dev/`。
- 提交目标分支为 master。

### 规则说明

文档需在一级标题下方，按顺序连续书写六个责任田标签：`Kit`、`Subsystem`、`Owner`、`Designer`、`Tester`、`Adviser`。

| 编号 | 规则 |
| --- | --- |
| 1 | 六个标签必须全部存在，缺失任一即报错 |
| 2 | 标签值不可为空或纯空格 |
| 3 | 每个标签必须独占一行，该行不可有其他内容 |
| 4 | 六个标签之间必须连续，不可夹杂其他内容 |
| 5 | 一级标题与第一个标签之间必须紧邻，不可夹杂其他内容 |
| 6 | `Kit`、`Subsystem` 的值不可包含中文 |
| 7 | `Kit`、`Subsystem` 的值必须在 `zh-cn/contribute/docs-owners.md` 清单中存在 |
| 8 | `Owner`、`Designer`、`Tester`、`Adviser` 的账号必须以 `@` 开头 |
| 9 | 账号只允许字母、数字、下划线、中划线，长度 3 至 50 个字符，且必须以字母开头 |
| 10 | 多个账号之间必须使用英文分号 `;` 分隔 |
| 11 | 每个标签的责任人数量不可超过 3 个 |

### 正例

```markdown
# Button组件

<!--Kit:ArkUI-->
<!--Subsystem:ArkUI-->
<!--Owner:@zhangsan;@lisi-->
<!--Designer:@wangwu-->
<!--Tester:@zhaoliu-->
<!--Adviser:@qianqi-->

## 简介

正文内容。
```

### 反例与报错样例

**反例一：缺失标签**

```markdown
# Button组件

<!--Kit:ArkUI-->
<!--Owner:@zhangsan-->
<!--Designer:@wangwu-->
```

报错样例：

```text
error_type: owner_lost
error_info: 该文档缺失Subsystem，请补充！
error_info: 该文档缺失Tester，请补充！
error_info: 该文档缺失Adviser，请补充！
```

**反例二：标签之间夹杂内容**

```markdown
<!--Kit:ArkUI-->

这里是多余的一段说明文字。

<!--Subsystem:ArkUI-->
```

报错样例：

```text
error_type: owner_lost
error_info: 该文档责任田标签之间存在其他内容，请处理！
```

**反例三：一级标题与标签之间夹杂内容**

```markdown
# Button组件

本文介绍 Button 组件的用法。

<!--Kit:ArkUI-->
```

报错样例：

```text
error_type: owner_lost
error_info: 该文档一级标题和责任田标签之间存在其他内容，请处理！
```

**反例四：标签值为空**

```markdown
<!--Owner:-->
```

报错样例：

```text
error_type: owner_lost
error_info: 该文档标记Owner为空，请添加!
```

**反例五：标签与其他内容同行**

```markdown
<!--Kit:ArkUI--> 这是 ArkUI 的文档
```

报错样例：

```text
error_type: owner_lost
error_info: 该文档标记Kit所在行还存在其他内容，请处理！
```

**反例六：Kit 或 Subsystem 含中文**

```markdown
<!--Kit:方舟UI框架-->
```

报错样例：

```text
error_type: owner_lost
error_info: 该文档标记Kit对应值存在中文，请处理！
```

**反例七：Kit 或 Subsystem 不在清单中**

```markdown
<!--Kit:MyOwnKit-->
```

报错样例：

```text
error_type: owner_lost
error_info: 该文档标记Kit对应值：[MyOwnKit]不在Kit清单中，请在zh-cn\contribute\docs-owners.md中添加!
```

修改方法：先在 `zh-cn/contribute/docs-owners.md` 中登记该 Kit 或 Subsystem，再回填到文档标签中；若为拼写错误，直接改为清单中已有的值。

**反例八：账号格式错误**

```markdown
<!--Owner:zhangsan-->
<!--Designer:@zhang san-->
<!--Tester:@123abc-->
```

报错样例：

```text
error_type: owner_lost
error_info: 该文档标记Owner，[zhangsan]账号前未添加@，或格式不符合gitCode账号要求，或多个账号之间未使用分号进行分隔等其他格式问题，请修改!
```

常见诱因：漏写 `@`、账号中含空格或非法字符、账号以数字开头、多个账号使用逗号或顿号分隔。

**反例九：责任人超过 3 个**

```markdown
<!--Owner:@user1;@user2;@user3;@user4-->
```

报错样例：

```text
error_type: owner_lost
error_info: 该文档标记Owner中责任人数量超过3个，请去除!
```

**反例十：文档编码非 UTF-8**

报错样例：

```text
error_type: owner_lost
error_info: 该文档编码有问题，请使用utf-8进行编码
```

修改方法：使用编辑器将文档另存为 UTF-8 编码后重新提交。该报错在多个检查项中均可能出现，含义一致。

---

## 图片引用检查

### 规则说明

| 编号 | 规则 |
| --- | --- |
| 1 | Markdown 图片语法与 HTML `img` 标签引用的本地图片，文件必须真实存在 |
| 2 | 图片文件大小必须小于 20MB |
| 3 | 不可出现 !\[]\() 这类完全为空的图片引用 |
| 4 | 以 `http://`、`https://` 开头的网络图片不检查文件是否存在，但会被 [链接风格检查](#链接风格检查) 判定为格式错误 |

### 正例

```markdown
![按钮示意图](./figures/button-example.png)
```

前提：`figures/button-example.png` 与当前文档处于正确的相对位置，且文件已一并提交。

### 反例与报错样例

**反例一：图片文件不存在**

```markdown
![按钮示意图](./figures/button-not-exist.png)
```

报错样例：

```text
error_type: figure_lost
error_info: ./figures/button-not-exist.png
file: docs/zh-cn/application-dev/ui/ts-basic-components-button.md
```

> **说明：**
> 该报错的 error_info 直接就是无法定位到的图片路径，请依据当前文档所在目录核算相对路径，并确认图片已提交入库。

常见诱因：

- 图片未随文档一起提交。
- 相对路径层级错误，`../` 数量不对。
- 图片文件名大小写与实际不一致。
- 图片被移动或重命名后未同步更新引用。

**反例二：图片超过 20MB**

```markdown
![演示动图](./figures/big-demo.gif)
```

报错样例：

```text
error_type: figure_check
error_info: 链接./figures/big-demo.gif对应图片大小，超过20MB
```

修改方法：压缩图片或拆分为多张图片，也可改用外部视频链接承载大体积演示内容。

**反例三：空图片引用**

```markdown
![]()
```

报错样例：

```text
error_type: figure_lost
error_info: ![]()
```

修改方法：补全图片描述与路径，或直接删除该残留内容。此类问题常见于从其他编辑器粘贴内容后的残留。

**反例四：HTML 图片标签引用失效**

```html
<img src="./figures/old-name.png" width="300">
```

报错样例：

```text
error_type: figure_lost
error_info: ./figures/old-name.png
```

---

## 相对链接检查

### 规则说明

检查 Markdown 链接语法（即 `[链接名称]` 紧跟 `(链接地址)` 的组合写法）中，链接地址为相对路径或锚点的情况。

| 编号 | 规则 |
| --- | --- |
| 1 | 链接名称中不可包含 `br` 换行标签 |
| 2 | 链接地址非纯锚点时，必须带文件后缀 |
| 3 | 链接地址中 `#` 最多只能出现 1 次 |
| 4 | 纯锚点链接（`#锚点`）指向的标题必须在当前文档中存在 |
| 5 | 不可链接到任意文档的一级标题 |
| 6 | 链接指向的目标文档必须真实存在 |
| 7 | 带锚点的跨文档链接，目标文档中该锚点必须存在 |
| 8 | 面向第三方应用的文档（文件名不以 `-sys.md` 结尾）不可链接到系统应用文档（文件名以 `-sys.md` 结尾） |
| 9 | 除 `Readme-CN.md`、`Readme-EN.md`、`website.md` 自身外，其他文档不可链接到这三类目录文件 |

### 锚点生成规则

判断锚点是否存在时，标题会按如下方式转换为锚点，修改锚点前请先理解该规则：

1. 去除标题中的 HTML 注释、HTML 标签。
2. 将空格替换为中划线 `-`。
3. 去除中文、字母、数字、中划线、下划线以外的所有字符。
4. 全部转为小写。
5. 同名标题重复出现时，第二个及之后会自动追加序号后缀。

例如标题 `## 设置 Button 参数` 对应锚点为 `#设置-button-参数`。

### 正例

```markdown
[接口说明](./arkui-ets-interface.md)
[创建按钮](./arkui-ets-interface.md#创建按钮)
[设置 Button 参数](#设置-button-参数)
[组件规范](../contribute/style-guidelines.md)
```

### 反例与报错样例

**反例一：目标文档不存在**

```markdown
[接口说明](./arkui-ets-interface-not-exist.md)
```

报错样例：

```text
error_type: link_error
error_info: [接口说明](./arkui-ets-interface-not-exist.md)
```

> **说明：**
> 该报错的 error_info 为链接原文，可直接在文档中搜索定位。

**反例二：锚点不存在**

```markdown
[创建按钮](./arkui-ets-interface.md#创建按钮的方法)
```

报错样例：

```text
error_type: link_error
error_info: [创建按钮](./arkui-ets-interface.md#创建按钮的方法)
```

修改方法：打开目标文档，核对标题实际文本，按 [锚点生成规则](#锚点生成规则) 重新书写锚点。

**反例三：链接地址缺少文件后缀**

```markdown
[接口说明](./arkui-ets-interface)
```

报错样例：

```text
error_type: 链接不规范
error_info: [接口说明](./arkui-ets-interface)
```

**反例四：链接地址中出现多个井号**

```markdown
[接口说明](./arkui-ets-interface.md#章节#小节)
```

报错样例：

```text
error_type: 链接不规范
error_info: [接口说明](./arkui-ets-interface.md#章节#小节)
```

**反例五：链接名称中含换行标签**

```markdown
[接口<br>说明](./arkui-ets-interface.md)
```

报错样例：

```text
error_type: 链接标题中存在br标签
error_info: [接口<br>说明](./arkui-ets-interface.md)
```

修改方法：删除链接名称中的 `br` 标签。若为表格中排版需要，请调整列宽或精简链接名称。

**反例六：链接到一级标题**

```markdown
[Button组件](./ts-basic-components-button.md#button组件)
```

假设 `Button组件` 是目标文档的一级标题，报错样例：

```text
error_type: 不可链接到一级标题
error_info: [Button组件](./ts-basic-components-button.md#button组件)
```

修改方法：去掉锚点，直接链接到文档本身。链接到文档即等价于定位到其一级标题。

```markdown
[Button组件](./ts-basic-components-button.md)
```

**反例七：第三方应用文档链接到系统应用文档**

```markdown
[系统能力说明](./arkui-ets-interface-sys.md)
```

当前文档文件名不以 `-sys.md` 结尾时，报错样例：

```text
error_type: 面向第三方应用的文档，链接到了系统应用的文档
error_info: [系统能力说明](./arkui-ets-interface-sys.md)
```

修改方法：改为链接面向第三方应用的对应文档；若该内容确实仅系统应用可见，则应将其放入 `-sys.md` 文档，或使用 Del 标记对、RP 标记对包裹（标记写法参见[标签配对检查](#标签配对检查)）。

**反例八：链接到目录文件**

```markdown
[返回目录](./Readme-CN.md)
[站点首页](../website.md)
```

报错样例：

```text
error_type: 相对链接不可链接到readme/website
error_info: [返回目录](./Readme-CN.md)
```

修改方法：删除该链接。目录文件由站点框架自动生成导航，无需在正文中手工链接。

---

## 文件名检查

### 规则说明

| 编号 | 规则 |
| --- | --- |
| 1 | 文件名（不含扩展名）只允许字母、数字、中划线 `-` |
| 2 | 文件名不可携带语言标记：不以 `zh-`、`cn-`、`en-` 开头，不以 `-zh`、`-cn`、`-en` 结尾，不包含 `-zh-`、`-cn-`、`-en-` |
| 3 | Markdown 文件扩展名必须为全小写 `.md` |
| 4 | `en/` 目录下的文档，在 `zh-cn/` 对应目录下必须存在同名文档 |

> **说明：**
> 规则 2 的判定不区分大小写，`Readme-CN.md` 与 `Readme-EN.md` 属于白名单，不受该规则约束。规则 4 同样豁免 `Readme-CN.md`、`Readme-EN.md`、`website.md`。

### 正例

```text
ts-basic-components-button.md
arkui-ets-interface.md
Readme-CN.md
```

### 反例与报错样例

**反例一：文件名含下划线或其他字符**

```text
ts_basic_components_button.md
Button组件说明.md
button (1).md
```

报错样例：

```text
error_type: file_name
error_info: 文件名仅可以由字母、数字、中划线 - 组成。
```

修改方法：将下划线、空格、括号、中文等全部替换为中划线或直接删除，保持全小写字母加数字加中划线的组合。

**反例二：文件名携带语言标记**

```text
zh-cn-button-guide.md
button-guide-en.md
arkui-en-interface.md
```

报错样例：

```text
error_type: file_name
error_info: 文件名不符合要求，请勿以zh-/cn-/en-开头、-zh/-cn/-en结尾、或包含-zh-/-cn-/-en-
```

修改方法：语言归属由文档所在目录（`zh-cn/` 或 `en/`）表达，文件名中不应再出现语言标记。

**反例三：扩展名大写**

```text
button-guide.MD
button-guide.Md
```

报错样例：

```text
error_type: file_name
error_info: Markdown文件后缀必须为md
```

**反例四：英文文档缺少对应中文文档**

```text
docs/en/application-dev/ui/ts-basic-components-button.md
```

若 `docs/zh-cn/application-dev/ui/ts-basic-components-button.md` 不存在，报错样例：

```text
error_type: en_file_check
error_info: 该英文文档，在zh-cn文件夹下，没有对应的文档！
```

修改方法：英文文档必须基于已有中文文档翻译产生。请确认中文文档路径与文件名与英文文档完全一致；若中文文档已重命名或移动，需同步调整英文文档位置。

---

## Markdown 格式检查

该项为综合性检查，包含多个子规则。仅对非 `/en/` 路径下的文档执行。

### 有序列表序号检查

**规则：**

- 不可使用中文顿号序号，例如 `1、`。
- 有序列表的点号后必须有一个空格，例如 `1. `，不可写作 `1.`。

**正例：**

```markdown
1. 第一项内容。
2. 第二项内容。
```

**反例与报错样例：**

```markdown
1、第一项内容。
2.第二项内容。
```

报错样例：

```text
error_type: md_style_error
error_info: 错误类型：使用了中文顿号序号"1、第一项内容。"，请改用Markdown有序列表格式"1. "；异常所在行号：第 8 行。请处理！
error_info: 错误类型：有序列表点号后缺少空格"2.第二项内容。"，请改用"1. "格式（点后加一个空格）；异常所在行号：第 9 行。请处理！
```

> **说明：**
> 引用块内的列表同样受该规则约束，例如 `> 1、说明内容` 也会被检出。

### 段落空行检查

**规则：** 普通文本行之间必须存在空行。连续两行及以上的普通文本（中间无空行）会被判定为一个多行段落并报错。

以下行不参与该规则判定：标题行、引用行、无序列表行、有序列表行、代码块围栏行、以 `+`、`_`、`__`、`**`、`~~` 开头的行、HTML 注释行、以 `br` 标签结尾的行。

**正例：**

```markdown
这是第一段内容。

这是第二段内容。
```

**反例与报错样例：**

```markdown
这是第一段的第一行。
这是第一段的第二行。
```

报错样例：

```text
error_type: md_style_error
error_info: 错误类型：段落之间需要存在空行；错误段落格式行号 12 - 13：请处理！错误内容：这是第一段的第一行。
这是第一段的第二行。
```

修改方法：在两行之间插入空行；若两行确实属于同一段落且需要换行显示，请在上一行末尾添加 `br` 换行标签。

### 示例代码检查

针对围栏代码块内部的检查，报错会给出代码块在文档中的起止行号。

#### 日志打印方式

**规则：** 代码块中不可使用 `console.log`，需统一使用 `console.info`。

**正例：**

```typescript
console.info('当前取值为：' + value);
```

**反例与报错样例：**

```typescript
console.log('当前取值为：' + value);
```

报错样例：

```text
error_type: code_style_error
error_info: 错误类型：日志打印方式错误；不可使用console.log进行日志打印。代码块位置第30行 - 第58行，请处理！
```

#### 注释格式

**规则：** 适用于 `ts`、`typescript`、`js`、`javascript`、`c`、`cpp`、`c++`、`json5` 代码块。

- 不允许空注释。
- 单行注释符 `//` 与注释内容之间必须恰好一个空格。
- 多行注释首行 `/*` 后必须一个空格。
- 多行注释各行 `*` 必须纵向对齐。
- 多行注释各行缩进不可小于首行缩进。

**正例：**

```typescript
// 这是一条单行注释
/* 这是一条单行块注释 */
/**
 * 这是多行注释
 * 星号已对齐
 */
```

**反例与报错样例：**

```typescript
//这是一条单行注释
/*这是一条单行块注释*/
/**
 * 这是多行注释
   * 星号未对齐
 */
//
```

报错样例：

```text
error_type: code_style_error
error_info: 错误类型：代码格式异常，不允许空注释，且注释符与注释内容之间需要留有一个空格；异常代码起始位置：第 42行。请处理！
error_info: 错误类型：代码格式异常，多行注释中*(星号)未对齐；异常代码起始位置：第 45行。请处理！
```

#### JSON 代码块注释

**规则：** `json` 代码块中不可出现注释。若需要注释，请将代码块语言标记改为 `json5`。

**反例：** 在语言标记为 `json` 的围栏代码块中书写注释，代码块内容如下（首尾各有三个反引号围栏行）：

```text
{
  // 这是不允许的注释
  "name": "test"
}
```

报错样例：

```text
error_type: code_style_error
error_info: 错误类型：代码格式异常，json代码块中不可使用注释，请使用json5格式；异常代码起始位置：第 20行。请处理！
```

修改方法：将该代码块的语言标记由 `json` 改为 `json5`，或删除其中的注释行。

#### JSON 与 JSON5 内容合法性

**规则：** `json` 与 `json5` 代码块内容必须能被正确解析，例如不可缺失引号、逗号、括号不配对等。

**反例与报错样例：**

```json5
{
  "name": "test"
  "value": 1,
}
```

报错样例：

```text
error_type: code_style_error
error_info: 错误类型：代码格式异常，json5代码块中格式存在异常，请将代码块放置在IDE中进行确认处理。；异常代码起始位置：第 66行。请处理！
```

修改方法：将代码块内容复制到 IDE 中格式化，依据 IDE 报错修正后回填。

#### 代码块缩进

**规则：** 代码块内各行的缩进不可小于代码块首行的缩进。

**反例：** 整个代码块（含围栏行）缩进 2 个空格书写，但其中一行代码顶格书写，结构如下表：

| 代码块内的行 | 内容 | 行首缩进 |
| --- | --- | --- |
| 围栏起始行 | 三个反引号加语言标记 typescript | 2 个空格 |
| 第 1 行代码 | let a: number = 1; | 2 个空格 |
| 第 2 行代码 | let b: number = 2; | 顶格无缩进，异常 |
| 围栏结束行 | 三个反引号 | 2 个空格 |

报错样例：

```text
error_type: md_style_error
error_info: 错误类型：代码块缩进异常；异常代码块所在位置行号：第 88 行 至 第 92。请处理！
```

### markdownlint 工具检查

由 markdownlint 工具执行的规则，报错中会给出精确行号。

| 规则编号 | 规则内容 |
| --- | --- |
| MD010 | 不可使用制表符（Tab），代码块内部同样检查 |
| MD029 | 有序列表序号格式必须规范 |
| MD034 | 不可直接使用裸 URL |
| MD040 | 围栏代码块必须指定语言 |
| MD046 | 代码块必须使用围栏风格（三个反引号），不可使用缩进风格 |

**制表符报错样例：**

```text
error_type: md_style_error
error_info: 错误类型：文档中使用制表符，请将制表符替换为空格；异常所在行号：第 15 行。请处理！
```

修改方法：在编辑器中开启「显示空白字符」，定位 Tab 并替换为空格。

**序号格式报错样例：**

```text
error_type: md_style_error
error_info: 错误类型：序列号格式异常；异常所在行号：第 22 行。请处理！
```

修改方法：有序列表请使用 `1. `、`2. `、`3. ` 递增书写，或统一使用 `1. ` 由渲染器自动编号，不可混用 `1)`、`01.` 等写法。

**裸 URL 报错样例：**

```text
error_type: md_style_error
error_info: 错误类型：文档中不可直接使用URL，请使用标准Markdown链接格式[]()或行内代码``将URL包裹；异常所在行号：第 33 行；被识别为裸链接的内容：https://example.com/guide。请处理！
```

修改方法（二选一）：

```markdown
[使用指南](https://example.com/guide)
```

或使用行内代码包裹，使其不参与链接渲染：

```markdown
下载地址为 `https://example.com/guide` 。
```

**代码块未指定语言：**

反例特征：代码块的起始围栏行只有三个反引号，其后未跟随任何语言标记，报错样例如下。

```text
error_type: md_style_error
error_info: 错误类型：代码块未指定语言；异常所在行号：第 41 行。请处理！
```

修改方法：在起始围栏后补全语言标记，例如 `typescript`、`json5`、`shell`；纯文本示例请使用 `text`。

**代码块风格报错样例：**

```text
error_type: md_style_error
error_info: 错误类型：代码块格式错误；异常所在行号：第 57 行。请处理！
```

修改方法：将四空格缩进式代码块改写为三个反引号包裹的围栏式代码块。

### 链接风格检查

**规则：**

| 编号 | 规则 |
| --- | --- |
| 1 | 链接地址中不可包含空格，左小括号后、右小括号前、地址内部均不可有空格 |
| 2 | 链接名称不可为空，方括号内必须有内容 |
| 3 | 链接地址不可为空，小括号内必须有内容 |
| 4 | 链接必须完整闭合，以右小括号结尾 |
| 5 | 相对链接地址必须以 `.md)` 结尾，或包含 `.md#`，或为纯锚点 `(#锚点)` |
| 6 | 图片必须使用仓库内相对路径，路径中需包含 `figures/`，且以 `png`、`jpg`、`jpeg`、`gif`、`svg` 结尾（大小写均可） |
| 7 | 图片不可使用网络地址 |
| 8 | 链接与图片语法不可出现在行内代码块中 |
| 9 | 不可残留以 ERROR 开头、标注 Invalid link 的回流转换失败标记，具体形态见下方报错样例 |

**正例：**

```markdown
[接口说明](./arkui-ets-interface.md)
[创建按钮](./arkui-ets-interface.md#创建按钮)
[本文简介](#简介)
[开发指南](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/arkts-create-custom-components)
![按钮示意图](./figures/button-example.png)
```

**反例与报错样例：**

```markdown
[接口说明]( ./arkui-ets-interface.md )
[](./arkui-ets-interface.md)
[接口说明]()
[接口说明](./arkui-ets-interface)
![示意图](https://example.com/pic.png)
![示意图](./images/pic.png)
```

报错样例：

```text
error_type: md_LinkStyle_Error
error_info: 链接格式错误：[接口说明]( ./arkui-ets-interface.md )
error_type: md_LinkStyle_Error
error_info: 链接格式错误：[](./arkui-ets-interface.md)
error_type: md_LinkStyle_Error
error_info: 链接格式错误：[接口说明]()
error_type: md_LinkStyle_Error
error_info: 图片链接格式错误：![示意图](https://example.com/pic.png)
error_type: md_LinkStyle_Error
error_info: 图片链接格式错误：![示意图](./images/pic.png)
```

> **注意：**
> 图片必须放在文档同级的 `figures` 目录下。使用 `images`、`pic` 等其他目录名，即使文件存在也会报「图片链接格式错误」。

**行内代码块中的链接报错样例：**

```markdown
请参考 `[接口说明](./arkui-ets-interface.md)` 完成配置。
```

```text
error_type: md_LinkStyle_Error
error_info: 链接 [接口说明](./arkui-ets-interface.md) 在行内代码块中，可能导致此处链接显示异常，请处理！
```

修改方法：去掉包裹链接的反引号，使链接正常渲染。

**回流失败标记报错样例：**

```text
error_type: mdLinkStyleError
error_info: 链接格式错误：[ERROR:Invalid link:
```

修改方法：该标记来自旧格式转换失败，需人工核对原意后改写为标准 Markdown 链接。

### 目录文件 urlpath 检查

**适用范围：** `application-dev/` 路径下的 `Readme-CN.md`、`Readme-EN.md`、`website.md`。

**规则：**

| 编号 | 规则 |
| --- | --- |
| 1 | 无序列表节点需通过 HTML 注释声明 urlpath，注释内容不可为空 |
| 2 | urlpath 只允许小写字母、数字、中划线 `-`、下划线 `_` |
| 3 | 同一文档内 urlpath 不可重复 |
| 4 | 节点未声明 urlpath 注释但存在链接时，取链接文件名（去掉 `.md`）作为 urlpath 参与重复性校验 |

**正例：**

```markdown
- [Button组件](./ts-basic-components-button.md)<!--button-component-->
- [Text组件](./ts-basic-components-text.md)<!--text-component-->
```

**反例与报错样例：**

```markdown
- [Button组件](./ts-basic-components-button.md)<!--Button Component-->
- [Text组件](./ts-basic-components-text.md)<!--button-component-->
- 分组节点
```

报错样例：

```text
error_type: Urlpath_Error
error_info: 第5行，内容- [Button组件](./ts-basic-components-button.md)<!--Button Component-->，该行urlpath格式错误，urlpath不可为空，且仅支持小写字母，数字，中划线，下划线。
error_type: Urlpath_Error
error_info: 第6行，内容- [Text组件](./ts-basic-components-text.md)<!--button-component-->，该行urlpath重复，请重新设置。
error_type: Urlpath_Error
error_info: 第7行，内容- 分组节点，该行urlpath格式错误，urlpath不可为空，且仅支持小写字母，数字，中划线，下划线。
```

### 提示语格式检查

**规则：** 关键词包含 `说明`、`注意`、`警告`、`Note`、`Caution`、`Warning`（英文不区分大小写）。

- 表格内：提示语前必须紧跟 `br` 换行标签，具体写法见下方表格内正例。
- 表格外：提示语必须以 `>` 开头独立成行，其后可紧跟 `br` 换行标签接续正文，具体写法见下方表格外正例。
- 表格标题行（下一行为分隔符行）不参与检查。
- 正文中出现「注意事项」这一词组时不参与检查。
- 提示语关键词需使用两个星号包裹加粗，冒号可为中文或英文，冒号可在加粗标记内或外。

**正例（表格外）：**

```markdown
> **说明：**
> 该接口仅在当前版本生效。
```

**正例（表格内）：**

```markdown
| 参数名 | 说明 |
| --- | --- |
| size | 尺寸取值。<br>**说明：**<br>默认值为 30。 |
```

**反例与报错样例：**

```markdown
**说明：** 该接口仅在当前版本生效。
```

```text
error_type: notice_explanation
error_info: 第18行提示语错误；错误信息：提示语应为独立一行、结尾紧跟换行标签，以“>”开头，错误行**说明：** 该接口仅在当前版本生效。
```

```markdown
| size | 尺寸取值。**说明：** 默认值为 30。 |
```

```text
error_type: notice_explanation
error_info: 第25行表格总说明或注意格式不符合写作规范，建议使用<br>**说明：**；错误信息：提示语前后紧跟换行标签，错误行| size | 尺寸取值。**说明：** 默认值为 30。 |
```

### 表格格式检查

**规则：**

| 编号 | 规则                           |
| --- |------------------------------|
| 1 | 表格内不可存在制表符                   |
| 2 | 表格至少三行：标题行、分隔符行、数据行          |
| 3 | 标题行不可为空列，不可缺列，如果无内容需要用`-`进行占位 |
| 4 | 必须存在分隔符行，且格式为竖线包裹的中划线与冒号组合   |
| 5 | 标题行与分隔符行列数必须一致               |
| 6 | 数据行不可为空列，列数必须与标题行一致          |
| 7 | 表格各行缩进必须一致                   |

**正例：**

```markdown
| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| size | number | 尺寸取值 |
| color | string | 颜色取值 |
```

**反例与报错样例：**

```markdown
| 参数名 | 类型 | 说明 |
| --- | --- |
| size | number | 尺寸取值 |
```

报错样例：

```text
error_type: table_scan
error_info: 表格范围：第30行 - 第33行，错误信息：标题行和分隔符行的列数不一致
```

**其他常见报错样例：**

```text
error_type: table_scan
error_info: 第41行表格错误，错误信息：存在制表符
error_type: table_scan
error_info: 表格范围：第52行 - 第54行，错误信息：表格至少需要三行（标题行、分隔符行和数据行）
error_type: table_scan
error_info: 第60行表格错误，错误信息：标题行格式不正确，存在空列: | 参数名 || 说明 |
error_type: table_scan
error_info: 表格范围：第71行 - 第75行，错误信息：缺少分隔符行、或分隔符行格式不正确，分隔符行为: | --- | --- |
error_type: table_scan
error_info: 第83行表格错误，错误信息：数据行格式不正确，存在空列: | size || 尺寸取值 |
error_type: table_scan
error_info: 表格范围：第90行 - 第94行，错误信息：数据行的列数与标题行不一致: | size | number |
error_type: table_scan
error_info: 第101行表格错误，错误信息：表格各行缩进不一致，请对齐！
error_type: table_scan
error_info: 表格范围：第110行 - 第112行，错误信息：缺少标题行
```

> **说明：**
> 报错中「表格范围」表示问题属于整个表格（如列数不一致、缺少分隔符行）；「第 N 行表格错误」表示问题精确定位到某一行。单元格内需要书写竖线时，请使用反斜杠转义为 `\|`。

### @link 链接检查

**规则：** `{@link}` 语法只允许两种形式，其余写法一律报错。

```text
形式一（完整链接）：{@link [链接名称](#锚点)}
形式二（空标记）：  {@link}
```

**正例：**

```markdown
详情参考{@link [创建按钮](#创建按钮)}。
```

**反例与报错样例：**

```markdown
详情参考{@link 创建按钮}。
详情参考{@link [创建按钮](button.md)}。
```

报错样例：

```text
error_type: text_link_error
error_info: 第12行链接错误；错误信息：{@link 创建按钮}
```

### HTML 标签检查

**规则：** 仅检查 `br` 与 `sup` 两类标签的书写是否规范。

- `br` 合法形式：`<br>`、`<br/>`、`</br>`，标签名与尖括号之间不可夹杂其他字符。
- `sup` 合法形式：`<sup>内容</sup>`，成对闭合。

**正例：**

```markdown
第一行内容<br>第二行内容
面积单位为 cm<sup>2</sup>
```

**反例与报错样例：**

```markdown
第一行内容<br  />第二行内容
面积单位为 cm<sup>2</sup  >
```

报错样例：

```text
error_type: scan_html_error
error_info: 第9行br错误；错误信息：<br  /
error_type: scan_html_error
error_info: 第10行sup错误；错误信息：<sup>2</sup  >
```

### 标题序号检查

**规则：** 任意层级标题中不可携带序号，包括阿拉伯数字序号、多级数字序号、中文顿号序号、中文数字序号、`No.` 序号。

**正例：**

```markdown
# Button组件

## 简介

## 接口说明

### 创建按钮
```

**反例与报错样例：**

```markdown
## 1. 简介
## 1.1 接口说明
## 二、注意事项
## No.1 创建按钮
```

报错样例：

```text
error_type: scan_title
error_info: 标题中不可出现序号：## 1. 简介
error_type: scan_title
error_info: 标题中不可出现序号：## 1.1 接口说明
error_type: scan_title
error_info: 标题中不可出现序号：## 二、注意事项
error_type: scan_title
error_info: 标题中不可出现序号：## No.1 创建按钮
```

修改方法：删除标题中的序号。文档层级顺序由标题级别与排列顺序自然表达，站点渲染时不会因缺少序号而错乱。

### 目录文件标题一致性检查

**适用范围：** `Readme-CN.md`、`Readme-EN.md`、`website.md`。

**规则：** 目录文件中链接的显示名称，必须与被链接文档的一级标题完全一致。

**反例与报错样例：**

目录文件中书写：

```markdown
- [按钮组件](./ts-basic-components-button.md)
```

而被链接文档的一级标题为 `# Button组件`，报错样例：

```text
error_type: scan_title
error_info: [按钮组件](./ts-basic-components-button.md) 中的文档标题与对应文档一级标题不一致！
```

修改方法：二者取其一统一。通常以文档一级标题为准，修改目录文件中的链接显示名称。

### 标签配对检查

**规则：** `<!--Del-->` 与 `<!--DelEnd-->`、`<!--RP数字-->` 与 `<!--RP数字End-->` 必须成对出现，且顺序正确（先开始后结束）。代码块内的标记不参与检查。

**正例：**

```markdown
<!--Del-->

这段内容将在发布时删除。

<!--DelEnd-->
```

**反例与报错样例：**

```markdown
<!--Del-->

这段内容缺少结束标签。
```

报错样例：

```text
error_type: tag_error
error_info: 第15行，开始标签<!--Del--> ，缺少对应结束标签<!--DelEnd-->
```

```markdown
这段内容缺少开始标签。

<!--DelEnd-->
```

报错样例：

```text
error_type: tag_error
error_info: 第22行,结束标签<!--DelEnd--> ，缺少对应开始标签<!--Del-->
```

> **说明：**
> RP 标记的数字需前后一致：数字为 1 的开始标记必须与数字为 1 的结束标记配对，不可与数字为 2 的结束标记交叉配对。

---

## HTTP 链接检查

### 规则说明

> **说明：**
> HTTP 链接的在线可访问性探测已下线，当前仅保留以下两项静态规则检查。

| 编号 | 规则 |
| --- | --- |
| 1 | 指向 docs 仓库的绝对链接必须改写为相对链接 |
| 2 | `en/` 目录下的英文文档中，HTTP 链接不可指向中文站点 |

规则 1 的判定前缀为 `gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/`（`http` 与 `https` 均适用），其中 `application-dev/device` 目录下的链接予以豁免。

规则 2 命中以下任一条件即判定为中文链接：

- 链接路径中包含 `/cn/` 或 `/zh-cn/`。
- 域名以 `cn.`、`zh-cn.`、`zh` 开头。
- URL 查询参数 `lang` 的值为 `cn`、`zh-CN` 或 `zh-cn`。

### 正例

```markdown
[接口说明](../reference/apis-arkui/arkui-ts/ts-basic-components-button.md)
[开发者官网](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/arkts-create-custom-components)
```

### 反例与报错样例

**反例一：使用 docs 仓绝对链接**

```markdown
[接口说明](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/ui/ts-basic-components-button.md)
```

报错样例：

```text
error_type: http_link_error
error_info: 链接- https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/ui/ts-basic-components-button.md 为docs仓中链接，请使用相对链接
```

修改方法：换算当前文档与目标文档的相对位置，改写为相对链接。同仓文档使用相对链接可保证在站点、GitCode 页面、本地预览三种环境下均可正常跳转，且不受分支切换影响。

**反例二：英文文档中存在中文链接**

```markdown
[开发指南](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/arkts-create-custom-components)
```

该链接出现在 `en/` 路径下的文档中时，报错样例：

```text
error_type: http_link_error
error_info: 英文文档存在中文链接:  https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/arkts-create-custom-components
```

修改方法：将链接中的 `cn` 语言段替换为 `en`，并确认目标英文页面真实存在。

**反例三：文档编码非 UTF-8**

```text
error_type: http_error
error_info: 该文档编码有问题，请使用utf-8进行编码
```

---

## 英文文档中文字符检查

### 适用范围

路径包含 `/en/` 的文档。路径包含 `/zh-cn/` 的文档不参与该检查。

### 规则说明

| 编号 | 规则 |
| --- | --- |
| 1 | 不可包含中文文字 |
| 2 | 不可包含中文标点符号，含全角空格、全角括号、全角冒号、中文引号、省略号等 |
| 3 | 相邻的问题行（中间仅隔空行）会合并为一条报错，并给出行号区间 |

### 正例

```markdown
This document describes how to use the Button component.

> **Note:**
> The default value is 30.
```

### 反例与报错样例

**反例一：残留中文文字**

```markdown
This document describes 如何使用 the Button component.
```

报错样例：

```text
error_type: Chinese_in_English
error_info: 第7行存在中文文字4个
```

**反例二：使用中文标点**

```markdown
This is an English sentence。
The value is “default”。
```

报错样例：

```text
error_type: Chinese_in_English
error_info: 第12行存在中文符号：。“”
```

**反例三：连续多行问题合并报错**

```markdown
这是第一行未翻译的内容。
这是第二行未翻译的内容。
```

报错样例：

```text
error_type: Chinese_in_English
error_info: 第20-21行存在中文文字18个，中文符号：。
```

**反例四：全角空格**

```markdown
The　value is 30.
```

报错样例：

```text
error_type: Chinese_in_English
error_info: 第30行存在中文符号：全角空格
```

修改方法：将全角空格替换为半角空格。此类问题常出现在从中文文档复制粘贴后未清理干净的场景。

---

## 文档标题检查

### 规则说明

| 编号 | 规则 | 适用范围 |
| --- | --- | --- |
| 1 | 不可提交空文档 | 全部 Markdown 文档 |
| 2 | 必须存在一级标题，且标题内容不可为空 | `application-dev/` 下文档 |
| 3 | 一级标题有且只能有一个 | `application-dev/` 下文档 |
| 4 | 一级标题必须位于文档第一行 | `application-dev/` 下文档 |
| 5 | 标题层级不可大于 3 | `zh-cn/application-dev/` 下文档 |
| 6 | 一级标题需与所属目录文件中该文档的链接名称一致 | `application-dev/` 下文档 |

> **说明：**
> 规则 6 中，中文文档比对 `Readme-CN.md`，英文文档比对 `Readme-EN.md`。若文档未被任何目录文件引用，则跳过该项比对。责任田标签、HTML 注释位于一级标题之前时，会使规则 4 判定失败。

### 正例

```markdown
# Button组件

## 简介

Button 组件用于响应点击事件。

### 接口说明

具体内容。
```

### 反例与报错样例

**反例一：空文档**

```text
error_type: 文档为空
error_info: 不可提交空文档
```

修改方法：补充文档内容；若该文档已废弃，请从仓库中删除文件并同步清理目录文件中的引用，而不是保留空文件。

**反例二：缺少一级标题**

```markdown
## 简介

正文内容。
```

报错样例：

```text
error_type: 文档一级标题错误
error_info: 文档缺少一级标题或一级标题内容为空
```

**反例三：一级标题内容为空**

```markdown
#

## 简介
```

报错样例同上。

**反例四：一级标题不在第一行**

```markdown
<!--Kit:ArkUI-->

# Button组件
```

报错样例：

```text
error_type: 文档一级标题错误
error_info: 一级标题没有在文档第一行
```

修改方法：将一级标题移动到文档第一行，责任田标签紧随一级标题之后书写。

**反例五：存在多个一级标题**

```markdown
# Button组件

## 简介

# Text组件

## 简介
```

报错样例：

```text
error_type: 文档一级标题错误
error_info: 文档存在多个一级标题，一个文档只能有且只有一个一级标题
```

修改方法：一个文档只承载一个主题。若确需介绍多个组件，请拆分为多个文档；若为层级误用，请将多余的 `#` 改为 `##`。

**反例六：标题层级大于 3**

```markdown
#### 参数说明
```

报错样例：

```text
error_type: 文档标题层级大于3
error_info: #### 参数说明
```

修改方法：将四级及更深标题提升为三级标题，或通过有序列表、表格重组内容结构。

**反例七：一级标题与目录文件不一致**

文档一级标题与目录文件中的链接名称不一致，例如文档首行为一级标题 `Button组件`，而 `Readme-CN.md` 中书写为：

```markdown
- [按钮组件](./ts-basic-components-button.md)
```

报错样例：

```text
error_type: title_error
error_info: 文档一级标题与Readme中的对应标题不一致
```

修改方法：统一二者文本。注意需完全一致，包含大小写、空格、标点。

---

## 尖括号与合并冲突检查

### 规则说明

| 编号 | 规则 |
| --- | --- |
| 1 | 文档中不可残留 Git 合并冲突标记 `<<<<<<< HEAD` |
| 2 | 文档中不可残留 Git 合并冲突标记 `>>>>>>>` |
| 3 | 形如 `<字母>` 的尖括号内容必须转义，否则会被渲染器识别为 HTML 标签并丢失 |

规则 3 的豁免范围：

- 已知 HTML 标签：`br`、`a`、`sub`、`sup`、`b`、`li`、`option`、`hr`、`ul`、`strong`、`p`、`text`。
- HTML 注释内容。
- 围栏代码块与行内代码块内容。
- 英文单引号包裹的内容。

### 正例

```markdown
泛型数组使用 `List<String>` 表示。

也可写作 List\<String\> 形式。

数组下标从 0 开始，最大值为 length - 1。
```

### 反例与报错样例

**反例一：尖括号未转义**

```markdown
泛型数组使用 List<String> 表示。
```

报错样例：

```text
error_type: 尖括号未转义
error_info: <String>
```

修改方法（二选一）：

- 使用行内代码包裹：`` `List<String>` ``（推荐，可同时保留代码样式）。
- 使用反斜杠转义：`List\<String\>`。

> **说明：**
> 该报错的 error_info 仅给出被识别出的尖括号片段，不含行号。若同一文档中多处出现相同片段，请全文搜索该片段逐一处理。

**反例二：合并冲突标记残留**

```text
<\<<<<<< HEAD
当前分支的内容
=======
其他分支的内容
>>>>>>> feature-branch
```

报错样例：

```text
error_type: 尖括号未转义
error_info: 文档中存在 <<<<<<< HEAD ，请处理！
error_type: 尖括号未转义
error_info: 文档中存在 >>>>>>> ，请处理！
```

修改方法：手工解决冲突，删除全部冲突标记行，保留最终需要的内容后重新提交。

**反例三：文档编码非 UTF-8**

```text
error_type: 尖括号未转义
error_info: 该文档编码有问题，请使用utf-8进行编码
```

---

## 报错信息速查表

下表按 error_info 中的关键字索引。使用浏览器或编辑器在本文档内搜索关键字，即可跳转到对应规则。

| 报错关键字 | 所属检查项 | 跳转 |
| --- | --- | --- |
| 该文档缺失 XXX，请补充 | 责任田标签检查 | [查看](#责任田标签检查) |
| 该文档标记 XXX 为空，请添加 | 责任田标签检查 | [查看](#责任田标签检查) |
| 该文档标记 XXX 所在行还存在其他内容 | 责任田标签检查 | [查看](#责任田标签检查) |
| 该文档标记 XXX 对应值存在中文 | 责任田标签检查 | [查看](#责任田标签检查) |
| 不在 XXX 清单中，请在 docs-owners.md 中添加 | 责任田标签检查 | [查看](#责任田标签检查) |
| 账号前未添加@，或格式不符合gitCode账号要求 | 责任田标签检查 | [查看](#责任田标签检查) |
| 责任人数量超过3个 | 责任田标签检查 | [查看](#责任田标签检查) |
| 责任田标签之间存在其他内容 | 责任田标签检查 | [查看](#责任田标签检查) |
| 一级标题和责任田标签之间存在其他内容 | 责任田标签检查 | [查看](#责任田标签检查) |
| 对应图片大小，超过20MB | 图片引用检查 | [查看](#图片引用检查) |
| error_info 为图片路径 | 图片引用检查 | [查看](#图片引用检查) |
| 链接标题中存在br标签 | 相对链接检查 | [查看](#相对链接检查) |
| 链接不规范 | 相对链接检查 | [查看](#相对链接检查) |
| 不可链接到一级标题 | 相对链接检查 | [查看](#相对链接检查) |
| 面向第三方应用的文档，链接到了系统应用的文档 | 相对链接检查 | [查看](#相对链接检查) |
| 相对链接不可链接到readme/website | 相对链接检查 | [查看](#相对链接检查) |
| 链接名称不准确 | API 链接准确性检查 | [查看](./API-reference-link-check.md) |
| 链接名称在标题及标题下表格均不存在 | API 链接准确性检查 | [查看](./API-reference-link-check.md) |
| 检测到链接名称与目标页面标题不一致 | API 链接准确性检查 | [查看](./API-reference-link-check.md) |
| 文件名仅可以由字母、数字、中划线 | 文件名检查 | [查看](#文件名检查) |
| 请勿以zh-/cn-/en-开头 | 文件名检查 | [查看](#文件名检查) |
| Markdown文件后缀必须为md | 文件名检查 | [查看](#文件名检查) |
| 该英文文档，在zh-cn文件夹下，没有对应的文档 | 文件名检查 | [查看](#文件名检查) |
| 使用了中文顿号序号 | 有序列表序号检查 | [查看](#有序列表序号检查) |
| 有序列表点号后缺少空格 | 有序列表序号检查 | [查看](#有序列表序号检查) |
| 段落之间需要存在空行 | 段落空行检查 | [查看](#段落空行检查) |
| 不可使用console.log进行日志打印 | 示例代码检查 | [查看](#示例代码检查) |
| 不允许空注释，且注释符与注释内容之间需要留有一个空格 | 示例代码检查 | [查看](#示例代码检查) |
| 多行注释中*(星号)未对齐 | 示例代码检查 | [查看](#示例代码检查) |
| 多行注释中，注释缩进异常 | 示例代码检查 | [查看](#示例代码检查) |
| json代码块中不可使用注释，请使用json5格式 | 示例代码检查 | [查看](#示例代码检查) |
| 代码块中格式存在异常 | 示例代码检查 | [查看](#示例代码检查) |
| 代码块缩进异常 | 示例代码检查 | [查看](#示例代码检查) |
| 文档中使用制表符 | markdownlint 工具检查 | [查看](#markdownlint-工具检查) |
| 序列号格式异常 | markdownlint 工具检查 | [查看](#markdownlint-工具检查) |
| 文档中不可直接使用URL | markdownlint 工具检查 | [查看](#markdownlint-工具检查) |
| 代码块未指定语言 | markdownlint 工具检查 | [查看](#markdownlint-工具检查) |
| 代码块格式错误 | markdownlint 工具检查 | [查看](#markdownlint-工具检查) |
| 链接格式错误 | 链接风格检查 | [查看](#链接风格检查) |
| 图片链接格式错误 | 链接风格检查 | [查看](#链接风格检查) |
| 在行内代码块中，可能导致此处链接显示异常 | 链接风格检查 | [查看](#链接风格检查) |
| urlpath重复 | 目录文件 urlpath 检查 | [查看](#目录文件-urlpath-检查) |
| urlpath格式错误 | 目录文件 urlpath 检查 | [查看](#目录文件-urlpath-检查) |
| 表格总说明或注意格式不符合写作规范 | 提示语格式检查 | [查看](#提示语格式检查) |
| 提示语错误 | 提示语格式检查 | [查看](#提示语格式检查) |
| 表格至少需要三行 | 表格格式检查 | [查看](#表格格式检查) |
| 存在制表符 | 表格格式检查 | [查看](#表格格式检查) |
| 标题行格式不正确 | 表格格式检查 | [查看](#表格格式检查) |
| 缺少标题行 | 表格格式检查 | [查看](#表格格式检查) |
| 缺少分隔符行、或分隔符行格式不正确 | 表格格式检查 | [查看](#表格格式检查) |
| 标题行和分隔符行的列数不一致 | 表格格式检查 | [查看](#表格格式检查) |
| 数据行格式不正确 | 表格格式检查 | [查看](#表格格式检查) |
| 数据行的列数与标题行不一致 | 表格格式检查 | [查看](#表格格式检查) |
| 表格各行缩进不一致 | 表格格式检查 | [查看](#表格格式检查) |
| 行链接错误 | @link 链接检查 | [查看](#link-链接检查) |
| 行br错误 | HTML 标签检查 | [查看](#html-标签检查) |
| 行sup错误 | HTML 标签检查 | [查看](#html-标签检查) |
| 标题中不可出现序号 | 标题序号检查 | [查看](#标题序号检查) |
| 中的文档标题与对应文档一级标题不一致 | 目录文件标题一致性检查 | [查看](#目录文件标题一致性检查) |
| 缺少对应结束标签 | 标签配对检查 | [查看](#标签配对检查) |
| 缺少对应开始标签 | 标签配对检查 | [查看](#标签配对检查) |
| 为docs仓中链接，请使用相对链接 | HTTP 链接检查 | [查看](#http-链接检查) |
| 英文文档存在中文链接 | HTTP 链接检查 | [查看](#http-链接检查) |
| 存在中文文字 N 个 | 英文文档中文字符检查 | [查看](#英文文档中文字符检查) |
| 存在中文符号 | 英文文档中文字符检查 | [查看](#英文文档中文字符检查) |
| 全角空格 | 英文文档中文字符检查 | [查看](#英文文档中文字符检查) |
| 不可提交空文档 | 文档标题检查 | [查看](#文档标题检查) |
| 文档缺少一级标题或一级标题内容为空 | 文档标题检查 | [查看](#文档标题检查) |
| 一级标题没有在文档第一行 | 文档标题检查 | [查看](#文档标题检查) |
| 文档存在多个一级标题 | 文档标题检查 | [查看](#文档标题检查) |
| 文档标题层级大于3 | 文档标题检查 | [查看](#文档标题检查) |
| 文档一级标题与Readme中的对应标题不一致 | 文档标题检查 | [查看](#文档标题检查) |
| `文档中存在 <<<<<<< HEAD ，请处理！` | 尖括号与合并冲突检查 | [查看](#尖括号与合并冲突检查) |
| `文档中存在 >>>>>>> ，请处理！` | 尖括号与合并冲突检查 | [查看](#尖括号与合并冲突检查) |
| error_info 为尖括号片段 | 尖括号与合并冲突检查 | [查看](#尖括号与合并冲突检查) |
| 该文档编码有问题，请使用utf-8进行编码 | 通用编码问题 | [查看](#文档编码问题) |

---

## 文档编码问题

多个检查项在读取文档失败时，都会返回同一条报错：

```text
error_info: 该文档编码有问题，请使用utf-8进行编码
```

### 常见诱因

- 文档由 Windows 记事本等工具保存为 GBK、ANSI 编码。
- 文档带有 UTF-8 BOM 头。
- 文档中混入了无法解码的二进制字符。

### 修改方法

1. 使用 VS Code 打开文档。
2. 单击右下角编码标识，选择「通过编码保存」。
3. 选择 `UTF-8`（不是 `UTF-8 with BOM`）。
4. 保存后重新提交。

---

## 修改后的自检建议

提交前建议按以下顺序自查，可拦截绝大多数门禁问题：

1. **确认文件本身合规：** 文件名全小写、仅含字母数字中划线、扩展名为 `.md`、编码为 UTF-8。
2. **确认文档骨架合规：** 一级标题在第一行且唯一、标题不超过三级、标题不带序号、非空文档。
3. **确认责任田完整：** 六个标签齐全、连续、独占一行、取值合法。
4. **确认链接与图片可用：** 本地目标文件存在、锚点存在、图片位于 `figures` 目录、无裸 URL。
5. **确认格式细节：** 表格三行齐全且列数一致、代码块已指定语言、提示语以 `>` 独立成行、有序列表使用 `1. ` 形式。
6. **英文文档额外确认：** 无中文文字与中文标点、无中文站点链接、`zh-cn` 下存在对应文档。



## 实战：从日志到完成修改

本节以一段真实日志为例，演示完整的排查过程。

### 原始日志

```text
2026-09-01 22:35:54: [step 2]docs_check
2026-09-01 22:35:58: {'API链接准确性检查，请查看指导': 'https://gitcode.com/openharmony/docs/blob/master/zh-cn/contribute/markdown-check/API-reference-link-check.md'}
{'error_type': 'link_error', 'error_info': '[@ohos.promptAction（弹窗）](../reference/apis-arkui/js-apis-promptAction.md)', 'file': 'docs/zh-cn/application-dev/reference/apis-arkui/arkts-apis-uimaterial.md'}
{'error_type': '检测到链接名称与目标页面标题不一致', 'error_info': '[@ohos.promptAction（弹窗）](../reference/apis-arkui/js-apis-promptAction.md)', 'file': 'docs/zh-cn/application-dev/ui/arkts-immersive-light-sense-constraints.md'}
{'error_type': '链接名称在标题及标题下表格均不存在', 'error_info': '[Select下拉菜单](../reference/apis-arkui/arkui-ts/ts-basic-components-select.md#menusystemmaterial)', 'file': 'docs/zh-cn/application-dev/ui/arkts-immersive-light-sense-faq.md'}
```

### 第一步：按 file 归组

| 待修改文档 | 问题条数 | 涉及的 error_type |
| --- | --- | --- |
| `docs/zh-cn/application-dev/reference/apis-arkui/arkts-apis-uimaterial.md` | 1 | `link_error` |
| `docs/zh-cn/application-dev/ui/arkts-immersive-light-sense-constraints.md` | 1 | `检测到链接名称与目标页面标题不一致` |
| `docs/zh-cn/application-dev/ui/arkts-immersive-light-sense-faq.md` | 1 | `链接名称在标题及标题下表格均不存在` |

### 第二步：处理 link_error

`error_type` 为 `link_error` 且 `error_info` 是一个链接原文，说明是 **断链**，参见 [相对链接检查](#相对链接检查)。

`error_info` 不含行号，因此在 `arkts-apis-uimaterial.md` 中全文搜索 `js-apis-promptAction.md`，找到该链接：

```markdown
[@ohos.promptAction（弹窗）](../reference/apis-arkui/js-apis-promptAction.md)
```

关键在于核算相对路径。该文档自身位于 `application-dev/reference/apis-arkui/` 目录下，`../reference/apis-arkui/js-apis-promptAction.md` 会先回退一层到 `application-dev/reference/`，再向下拼接 `reference/apis-arkui/`，最终解析为：

```text
application-dev/reference/reference/apis-arkui/js-apis-promptAction.md
```

路径中多出一层 `reference/`，文件不存在，因此报断链。

修改方法：该文档与目标文档同在 `reference/apis-arkui/` 目录下，直接使用同级相对路径即可。

```markdown
[@ohos.promptAction（弹窗）](./js-apis-promptAction.md)
```

> **注意：**
> 这是 `reference/` 目录下文档的高频错误。从 `application-dev/` 下的指南文档复制链接粘贴到 `reference/` 下的 API 文档时，`../reference/...` 这一层前缀必须去掉，否则会稳定报 `link_error`。

### 第三步：处理名称不一致

`error_type` 为 `检测到链接名称与目标页面标题不一致`，属于 API 链接准确性检查，参见 [API链接准确性检查规则说明](./API-reference-link-check.md)。

**先看清一个关键现象：** 本条与第二步那条的 `error_info` 完全相同，`file` 与 `error_type` 却不同。

| 对比项 | 第二步那条 | 本条 |
| --- | --- | --- |
| `file` 所在目录 | `application-dev/reference/apis-arkui/` | `application-dev/ui/` |
| 链接地址解析结果 | `application-dev/reference/reference/apis-arkui/` 下，文件不存在 | `application-dev/reference/apis-arkui/` 下，文件存在 |
| 报出的问题 | `link_error`，即断链 | 名称与目标页面标题不一致 |

同一个链接写法，因所在文档的目录层级不同，相对路径解析结果不同，报出的问题也就不同。**这正是排查必须先看 `file` 字段的原因。**

**再定位根因。** 打开目标文档 `js-apis-promptAction.md`，其一级标题为：

```markdown
# @ohos.promptAction (弹窗)
```

标题中使用的是 **半角括号，且左括号前有一个空格**。而报错链接的名称使用的是 **全角括号、无空格**：

```markdown
[@ohos.promptAction（弹窗）](../reference/apis-arkui/js-apis-promptAction.md)
```

比对时还会叠加一条预处理规则：链接名称中含英文句点时，只保留最后一个句点之后的部分。因此名称实际参与比对的文本是 `promptAction（弹窗）`，而目标标题保持原样为 `@ohos.promptAction (弹窗)`。两者括号形态不同，双向包含均不成立，于是报错。

**修改方法：** 链接名称按目标文档一级标题逐字符书写，包含括号的半角形态与左括号前的空格。

```markdown
[@ohos.promptAction (弹窗)](../reference/apis-arkui/js-apis-promptAction.md)
```

改后再走一遍预处理即可验证：名称经句点截断得到 `promptAction (弹窗)`，末尾的半角右括号被去除后为 `promptAction (弹窗`，它是目标标题 `@ohos.promptAction (弹窗)` 的子串，匹配通过。

> **注意：**
> 中英文括号形态、括号前后有无空格，都属于必须与目标标题一致的细节。从其他文档复制链接时，这类差异是「检测到链接名称与目标页面标题不一致」最常见的诱因。名称预处理规则详见 [链接名称的预处理](./API-reference-link-check.md#链接名称的预处理)。

### 第四步：处理表格中名称不存在

`error_type` 为 `链接名称在标题及标题下表格均不存在`，说明链接带锚点，锚点对应的标题及其下方表格都已找到，但链接名称在两者中均未命中。

```markdown
[Select下拉菜单](../reference/apis-arkui/arkui-ts/ts-basic-components-select.md#menusystemmaterial)
```

**关键点：带锚点的链接，比对对象是锚点对应的章节标题以及该章节下的表格，而不是文档的一级标题。**

本例中目标文档 `ts-basic-components-select.md` 的一级标题为 `Select`，链接名称 `Select下拉菜单` 恰好包含 `Select`。也就是说，这条链接如果 **不带锚点**，比对一级标题即可通过；正因为它带了锚点 `#menusystemmaterial`，比对对象换成了该章节，名称在章节标题与表格中均找不到，于是报错。

排查步骤：

1. 打开目标文档，搜索锚点 `menusystemmaterial` 对应的标题。锚点由标题文本转换而来，转换方式见 [锚点生成规则](#锚点生成规则)。
2. 查看该标题下方的表格，确认「名称」列（无该列时为首列）中列出的条目。
3. 二选一修改：
   - 保留锚点：将链接名称改为该章节标题，或表格中真实存在的条目名。
   - 去掉锚点：改为链接到整个文档，此时按一级标题比对，原名称 `Select下拉菜单` 即可通过。

去掉锚点的写法：

```markdown
[Select下拉菜单](../reference/apis-arkui/arkui-ts/ts-basic-components-select.md)
```

### 第五步：复扫确认

修改完成后重新触发门禁，确认日志中出现 `docs_check result:success`。

> **说明：**
> 同一种链接写法常在多篇文档中重复出现。本例日志中，指向 promptAction 的那条链接出现在 5 篇文档里，指向 Select 下拉菜单章节的那条出现在 4 篇文档里。修改时请在仓库内全文检索该链接地址，一次改完，否则下次扫描仍会在其他文档中报出。

> **注意：**
> 上例中 5 篇文档报出的问题并不完全相同：位于 `reference/` 目录下的那篇报断链，位于 `ui/` 目录下的 4 篇报名称不一致。根因不同，修改方式也不同，不可用同一种改法套用。

<!--no_check-->