---
kits: ["ArkTS / 方舟编程语言"]
description: "将 ArkTS 原始堆快照转换为 heapsnapshot，用于 OOM 后的离线内存分析与故障排查。"
keywords: [rawheap_translator, ArkTS内存OOM, rawheap, heapsnapshot, 离线内存分析, 双文件混合模式, 环境变量配置, 堆快照裁剪级别, 工具版本匹配, 文件写入权限]
doctype: guide
status: active
---

# rawheap-translator 工具
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanghuan2022-->
<!--Designer: @wanghuan2022-->
<!--Tester: @m30041553; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

## 使用 rawheap-translator 工具解析 rawheap 文件

rawheap_translator 工具用于解析`.rawheap`原始堆快照，生成`.heapsnapshot`文件。开发者可将生成的文件导入 DevEco Studio 或 Chrome 开发者工具，检查对象和引用关系，辅助定位 ArkTS 内存不足（Out of Memory，OOM）问题。

rawheap_translator 工具提供以下解析能力：

- 支持在 Windows、Linux 和 macOS 主机上离线解析`.rawheap`文件。
- 生成`.heapsnapshot`文件，供开发者导入 DevEco Studio 或 Chrome 开发者工具进行分析。
- 支持单文件解析和双文件混合解析。双文件混合模式可将动态和静态运行时的配套快照解析并合并为一个`.heapsnapshot`文件。

应用发生 ArkTS 内存 OOM 时会自动进行 HeapDump。开发者也可调用[hidebug.dumpJsRawHeapData][dump-js-rawheap]接口，获取当前线程的 rawheap 文件，或使用[hidumper][hidumper]的`hidumper --mem-jsheap pid [-T tid] --raw`命令，主动获取指定进程或 JS 线程的快照。快照生成后，按下文选择模式并执行转换。

## 基本概念与模式选择

| 概念 | 含义与用途 |
| --- | --- |
| HeapDump | 将虚拟机堆中的对象和引用关系转储为快照的操作，用于后续内存分析。 |
| rawheap 文件 | 后缀为`.rawheap`的二进制原始堆快照，是工具的输入。 |
| heapsnapshot 文件 | 后缀为`.heapsnapshot`的转换结果，可导入内存分析工具。 |
| ArkTS-Dyn | ArkTS 动态运行时侧，Dyn 表示 Dynamic（动态）。在双文件示例中，使用`dynamic.rawheap`表示这一侧的快照。 |
| ArkTS-Sta | ArkTS 静态运行时侧，Sta 表示 Static（静态）。在双文件示例中，使用`static.rawheap`表示这一侧的快照。 |

开发者需要解析一份`.rawheap`文件时，可使用单文件模式。如果应用使用[ArkTS-Dyn 和 ArkTS-Sta](#基本概念与模式选择)混合运行，且开发者已取得两者配套的快照，可使用双文件混合模式，将两份文件解析并合并为一个`.heapsnapshot`文件。

早期版本仅支持单文件解析，后续版本增加了双文件混合模式。开发者可执行`rawheap_translator --help`查看所用工具支持的模式。如果帮助信息未提供双文件用法，请更新工具后再使用双文件混合模式。

## 获取工具与准备输入

开发者可根据主机平台（Windows、Linux 或 macOS），从对应 SDK 的`sdk/default/openharmony/toolchains`目录获取 rawheap_translator 工具。Windows 下的可执行文件为`rawheap_translator.exe`。

开始转换前，请检查以下条件：

| 检查项 | 要求与不满足时的影响 |
| --- | --- |
| 格式与版本 | 工具必须支持输入快照的格式版本。版本不匹配可能导致解析失败，请使用与快照生成环境匹配的 SDK 工具。 |
| 文件配对 | 双文件模式使用 ArkTS-Dyn 和 ArkTS-Sta 的配套快照。使用 hidumper 获取时，应选择同一进程、同一次转储生成的动态和静态快照，并核对进程号和时间戳一致。不能仅凭`.rawheap`后缀判断类型。 |
| 输入顺序 | 双文件模式先传入动态快照，再传入静态快照。顺序错误会导致文件格式检查或解析失败。 |
| 文件权限 | 输入文件必须可读，输出文件所在目录必须存在且可写。路径或权限不满足要求时，可能无法打开输入或保存输出。 |
| 输出名称 | 建议显式指定以`.heapsnapshot`结尾的输出文件名。对于其他名称，自动补全后缀的工具会在原名称后追加`.heapsnapshot`，例如，`out.txt`会生成`out.txt.heapsnapshot`。不要把输出名写成`.rawheap`，以免被识别为双文件模式的第二个输入。 |

例如，在动静态混合场景下，一次转储生成动态快照`jsheap-64949-64950-1751075546050.rawheap`和静态快照`static_jsheap-64949-1751075546050.rawheap`，两份文件的进程号均为`64949`，时间戳均为`1751075546050`。快照命名和获取方式请参见[hidumper 查询虚拟机堆内存][hidumper]。

## 配置主机环境

建议将工具保存在固定目录，并将工具所在目录加入 PATH 环境变量。PATH 中应填写包含可执行文件的目录，例如`/path/to/toolchains`。也可直接使用工具的完整路径执行命令，此时无需配置 PATH。

### Windows 环境变量配置

配置路径概览：系统属性 → 高级系统设置 → 环境变量 → 用户变量 Path → 新建工具目录 → 重新打开命令提示符。

以下以 Windows 10 为例：

1. 右键单击“此电脑”，选择“属性”，打开系统属性相关设置页面。
2. 单击“高级系统设置”，进入高级系统配置。
3. 在“高级”页签中单击“环境变量”，打开变量设置窗口。
4. 在“用户变量”中选择“Path”并单击“编辑”，配置当前用户的命令查找路径。
5. 单击“新建”，增加一个目录项。
6. 填入`rawheap_translator.exe`所在目录，例如`C:\OpenHarmony\toolchains`。
7. 单击“确定”保存并关闭相关窗口。
8. 重新打开命令提示符，执行以下命令，确认系统能找到工具并查看其用法：

   ```bat
   where rawheap_translator
   rawheap_translator.exe --help
   ```

### Linux 环境变量配置

1. 打开终端，执行以下命令，查看用户默认登录 Shell，以选择对应的配置文件。如果已手动切换 Shell，请按实际使用的 Shell 选择下面的步骤。

   ```bash
   echo "$SHELL"
   ```

2. 将以下示例中的`/path/to/toolchains`替换为工具所在的实际目录。使用 Bash 交互式终端时，将目录加入`~/.bashrc`并立即加载：

   ```bash
   printf '%s\n' 'export PATH="/path/to/toolchains:$PATH"' >> ~/.bashrc
   source ~/.bashrc
   ```

   使用 Zsh 交互式终端时，改为更新`~/.zshrc`，并在 Zsh 中加载：

   ```bash
   printf '%s\n' 'export PATH="/path/to/toolchains:$PATH"' >> ~/.zshrc
   source ~/.zshrc
   ```

3. 执行以下命令，确认工具目录已生效，并查看当前版本支持的模式。重新打开同类交互式终端后，再检查一次命令是否可用。

   ```bash
   command -v rawheap_translator
   rawheap_translator --help
   ```

### macOS 环境变量配置

1. 打开终端，执行`echo "$SHELL"`查看用户默认登录 Shell，以选择配置文件。如果已手动切换 Shell，请按实际使用的 Shell 选择下面的步骤。
2. 将`/path/to/toolchains`替换为工具所在的实际目录。使用 Zsh 交互式终端时，更新`~/.zshrc`，并在 Zsh 中加载：

   ```bash
   printf '%s\n' 'export PATH="/path/to/toolchains:$PATH"' >> ~/.zshrc
   source ~/.zshrc
   ```

   使用 Bash 登录终端时，更新`~/.bash_profile`并立即加载：

   ```bash
   printf '%s\n' 'export PATH="/path/to/toolchains:$PATH"' >> ~/.bash_profile
   source ~/.bash_profile
   ```

3. 执行`command -v rawheap_translator`和`rawheap_translator --help`，确认工具可用。重新打开相同类型的终端后，再确认配置仍然生效。

## 执行解析

### 解析命令

单文件模式下，开发者传入一份`.rawheap`文件，工具将其转换为`.heapsnapshot`文件：

```text
rawheap_translator <rawheap_file> [heapsnapshot_file]
```

双文件混合模式下，开发者依次传入动态和静态运行时的配套文件，工具合并生成一个`.heapsnapshot`文件。使用前请确认帮助信息包含此模式，并检查前文的文件配对条件：

```text
rawheap_translator <dynamic_rawheap_file> <static_rawheap_file> [heapsnapshot_file]
```

尖括号表示必选参数，方括号表示可选参数，执行命令时不输入这些括号。Windows 命令提示符中使用`rawheap_translator.exe`。

### 参数说明

| 参数 | 适用模式 | 必选 | 说明 |
| --- | --- | --- | --- |
| rawheap_file | 单文件 | 是 | 需要单独解析的`.rawheap`文件路径，可为 ArkTS-Dyn 或 ArkTS-Sta 侧的快照。输入可使用 OOM 时生成的快照，也可使用主动转储得到的快照。 |
| dynamic_rawheap_file | 双文件混合 | 是 | ArkTS-Dyn 侧快照路径，必须放在静态快照参数之前。 |
| static_rawheap_file | 双文件混合 | 是 | 双文件混合解析时的 ArkTS-Sta 侧快照路径。静态快照可通过单文件模式独立解析，无需配套的动态快照。 |
| heapsnapshot_file | 两种模式 | 否 | 输出文件路径。省略时，在当前工作目录生成`hprof_<时间戳>.heapsnapshot`，例如`hprof_2026-9-18-10-20-30.heapsnapshot`。时间戳使用命令执行时的本地时间，各字段不补零。显式指定时，建议使用完整的`.heapsnapshot`后缀；支持自动补后缀的工具会在其他名称后追加该后缀。输出目录必须存在且可写。 |

路径中包含空格时，请用双引号包围整个路径。保存位置以本次转换日志显示的路径为准。

## 解析示例与结果验证

### Windows 解析示例

打开命令提示符，进入 rawheap 文件所在目录，执行以下命令，在当前目录生成指定文件：

```bat
rawheap_translator.exe memleak-js-com.example.myapplication-7979-7979-20241215191332.rawheap myapplication-7979-7979.heapsnapshot
```

单独解析静态快照时，执行：

```bat
rawheap_translator.exe static.rawheap static.heapsnapshot
```

合并动态和静态运行时的配套快照时，执行：

```bat
rawheap_translator.exe dynamic.rawheap static.rawheap merged.heapsnapshot
```

### Linux 和 macOS 解析示例

打开终端，进入 rawheap 文件所在目录，执行以下命令，在当前目录生成指定文件。两个平台使用相同的解析命令：

```bash
rawheap_translator memleak-js-com.example.myapplication-7979-7979-20241215191332.rawheap myapplication-7979-7979.heapsnapshot
```

单独解析静态快照时，执行：

```bash
rawheap_translator static.rawheap static.heapsnapshot
```

合并动态和静态运行时的配套快照时，执行：

```bash
rawheap_translator dynamic.rawheap static.rawheap merged.heapsnapshot
```

### 参考输出

以下是动态快照单文件转换的一组参考日志。实际日志内容、数量和保存路径会随工具版本、输入文件及运行目录变化：

```text
[INFO ] ParseVersion            current metadata version is 1.0.0
[INFO ] ParseTypeEnums          total JSType count 214
[INFO ] ParseTypeList           total metadata count 220
[INFO ] SetBitField             set BitField offset 8
[INFO ] SetBitField             set BindingSize offset 32
[INFO ] SetBitField             set Length offset 8
[INFO ] SetBitField             set Data offset 16
[INFO ] ReadVersion             current rawheap version is 1.0.0
[INFO ] RawHeap                 start to translate rawheap
[INFO ] ReadRootTable           root node count 6244
[INFO ] ReadStringTable         string table count 11208
[INFO ] ReadObjTable            section objects count 96432
[INFO ] Translate               success
[INFO ] Serialize               start to serialize
[INFO ] Translate               file save to /data/local/tmp/myapplication-7979-7979.heapsnapshot
```

### 验证并查看结果

1. 检查本次日志，确认没有解析或保存错误，并记录工具报告的输出路径。双文件模式还需检查是否存在引用未解析等合并提示。
2. 确认对应`.heapsnapshot`文件已由本次命令生成或更新，且文件非空。Windows 可执行`dir myapplication-7979-7979.heapsnapshot`；Linux 和 macOS 可执行`ls -l myapplication-7979-7979.heapsnapshot`。静态快照单独解析示例应检查`static.heapsnapshot`，双文件示例应检查`merged.heapsnapshot`。
3. 通过 DevEco Studio 的[Snapshot 模板基本操作][snapshot-operations]页面，参照“离线导入内存快照文件”小节导入文件，或使用 Chrome 开发者工具的内存面板导入文件。检查对象与引用关系。文件存在并不代表转换结果一定完整；若合并存在引用未解析提示，应重新核对文件配对和工具版本。

## 文件参考规格

rawheap 文件的大小和生成耗时与当前 ArkTS 堆内存大小及存活对象数量呈强正相关。当 ArkTS 堆内存占用较大、存活对象数量较多时，生成的文件会更大，耗时也会更长。开发者可以订阅[资源泄漏事件][resource-leak-events]，自定义事件处理逻辑。

从 API version 20 开始，虚拟机支持两种规格的 HeapDump。开发者可调用[hidebug.setJsRawHeapTrimLevel][set-rawheap-trim-level]接口，设置当前进程转储虚拟机原始堆快照的裁剪级别。设置`TRIM_LEVEL_2`时，需使用支持该格式的解析工具；旧版工具可能转换失败。

从 API version 22 开始，`TRIM_LEVEL_1`模式新增对象属性名解析能力。生成的 rawheap 文件相对于原先会变大，具体增长大小与对象属性名数量和字符串大小有关。

| 规格 | 特点 |
| --- | --- |
| `TRIM_LEVEL_1` | dump 速度快，生成的 rawheap 文件大。API version 20 之前版本，虚拟机默认为此规格。 |
| `TRIM_LEVEL_2` | dump 速度稍慢，生成的 rawheap 文件大小相比`TRIM_LEVEL_1`缩小 40% 左右。 |

下表给出不同堆大小下，rawheap 文件大小、生成耗时及解析耗时的示例，供评估文件上报的性能和流量开销时参考。实际数据会随应用、设备和工具版本变化。

| 规格 | 堆大小（MB） | rawheap 文件（MB） | 生成耗时（s） | 解析耗时（s） |
| --- | --- | --- | --- | --- |
| TRIM_LEVEL_1 | 690 | 629 | 2.64 | 14 |
| TRIM_LEVEL_2 | 690 | 376 | 3.47 | 14 |
| TRIM_LEVEL_1 | 653 | 618 | 2.63 | 13 |
| TRIM_LEVEL_2 | 653 | 347 | 3.36 | 13 |
| TRIM_LEVEL_1 | 576 | 563 | 3.63 | 15 |
| TRIM_LEVEL_2 | 576 | 294 | 4.53 | 15 |

## 常见问题

### 工具版本不匹配

**问题现象**：rawheap_translator 提示 rawheap 文件的格式版本与所用工具不匹配。例如，下面的日志表示此次运行的工具不能解析格式版本为`2.0.0`的 rawheap 文件：

```text
[INFO ] ParseVersion            current metadata version is 1.0.0
[INFO ] ParseTypeEnums          total JSType count 214
[INFO ] ParseTypeList           total metadata count 220
[INFO ] SetBitField             set BitField offset 8
[INFO ] SetBitField             set BindingSize offset 32
[INFO ] SetBitField             set Length offset 8
[INFO ] SetBitField             set Data offset 16
[INFO ] ReadVersion             current rawheap version is 2.0.0
[ERROR] ParseRawheap            The rawheap file's version 2.0.0 is not matched the current rawheap translator, please use the newest version of the translator!
```

**原因与处理**：所用工具不支持输入文件的格式版本。请更换支持该格式的工具，优先使用与快照生成环境匹配的 SDK 版本。日志中的 rawheap 格式版本不应直接当作工具发布版本号。

### 文件无法打开

**问题现象**：转换时提示`open file failed`。以下示例在解析完成后无法打开输出文件：

```text
[INFO ] ParseVersion            current metadata version is 1.0.0
[INFO ] ParseTypeEnums          total JSType count 214
[INFO ] ParseTypeList           total metadata count 220
[INFO ] SetBitField             set BitField offset 8
[INFO ] SetBitField             set BindingSize offset 32
[INFO ] SetBitField             set Length offset 8
[INFO ] SetBitField             set Data offset 16
[INFO ] ReadVersion             current rawheap version is 1.0.0
[INFO ] RawHeap                 start to translate rawheap
[INFO ] ReadRootTable           root node count 6244
[INFO ] ReadStringTable         string table count 11208
[INFO ] ReadObjTable            section objects count 96432
[INFO ] Translate               success
[ERROR] Initialize              open file failed
```

**原因与处理**：检查输出路径是否正确、输出目录是否存在且可写，修改路径或权限后重试。

### 文件解析失败

**问题现象**：工具未生成预期的`.heapsnapshot`文件。例如，日志停留在读取对象表阶段：

```text
[INFO ] ParseVersion            current metadata version is 1.0.0
[INFO ] ParseTypeEnums          total JSType count 214
[INFO ] ParseTypeList           total metadata count 220
[INFO ] SetBitField             set BitField offset 8
[INFO ] SetBitField             set BindingSize offset 32
[INFO ] SetBitField             set Length offset 8
[INFO ] SetBitField             set Data offset 16
[INFO ] ReadVersion             current rawheap version is 1.0.0
[INFO ] RawHeap                 start to translate rawheap
[INFO ] ReadRootTable           root node count 6244
[INFO ] ReadStringTable         string table count 11208
[INFO ] ReadObjTable            section objects count 96432
```

**原因与处理**：工具版本过低可能导致转换失败。可使用[DevEco Studio 6.1.1 Release][deveco-studio]及以上版本配套的工具重试，并核对输入快照的格式版本。若升级后仍失败，请检查输入文件是否完整。

### 双文件模式不可用或合并结果异常

**问题现象**：执行`rawheap_translator --help`后未显示双文件用法，或双文件转换时出现引用未解析提示、合并结果缺失。

**原因与处理**：先确认所用工具版本支持双文件混合模式，再检查动态文件在前、静态文件在后的参数顺序，以及两份文件是否为配套快照。若出现引用未解析提示，或发现合并结果缺失，请核对输入文件的来源和完整性，必要时重新获取配套快照后再解析。

[dump-js-rawheap]: ../reference/apis-performance-analysis-kit/js-apis-hidebug.md#hidebugdumpjsrawheapdata18

[hidumper]: ../dfx/hidumper.md#查询虚拟机堆内存

[snapshot-operations]: https://developer.huawei.com/consumer/cn/doc/doccenter-deveco-studio/ide-snapshot-basic-operations

[resource-leak-events]: ../dfx/hiappevent-watcher-resourceleak-events.md

[set-rawheap-trim-level]: ../reference/apis-performance-analysis-kit/js-apis-hidebug.md#hidebugsetjsrawheaptrimlevel20

[deveco-studio]: https://developer.huawei.com/consumer/cn/download/deveco-studio
