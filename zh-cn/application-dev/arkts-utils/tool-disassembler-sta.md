# Disassembler反汇编工具（ArkTS-Sta）
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @oatuwwutao-->
<!--Designer: @oatuwwutao-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @jinqiuheng-->

## 简介

Disassembler是ArkTS反汇编工具，ArkTS-Sta版本的Disassembler用于将静态的方舟字节码文件（`.abc`）反汇编为可读的文本。

工具随DevEco Studio SDK发布。以Windows平台为例，ArkTS-Sta版本的Disassembler工具位于DevEco Studio/sdk/default/openharmony/toolchains/ark_disasm_static.exe。

## 命令行说明

命令格式如下：

```bash
ark_disasm_static.exe [options] input_file output_file
```

参数说明：

| 参数 | 必选 | 描述 |
| --- | --- | --- |
| [options] | 否 | 命令选项，详见下文options选项说明。 |
| input_file | 是 | 输入的方舟字节码文件路径。 |
| output_file | 是 | 反汇编内容的输出文件路径。 |

options选项说明：

| 选项 | 必填 | 存在入参 | 描述 |
| -------- | -------- | -------- | -------- |
| --debug | 否 | 否 | 启用调试日志（DEBUG级别），默认输出到标准输出。 |
| --debug-file | 否 | 是 | 指定调试日志输出文件。格式：--debug-file FILENAME。需配合--debug使用。 |
| --help | 否 | 否 | 打印帮助信息并退出。 |
| --quiet | 否 | 否 | 精简输出模式，等效于同时开启所有--skip-*系列选项。 |
| --skip-string-literals | 否 | 否 | 将指令中的字符串字面量替换为其在abc文件中的偏移量ID，缩减输出文件体积。 |
| --verbose | 否 | 否 | 开启详细信息输出模式，在方法体内输出调试信息表（行号表、局部变量表）。 |
| --version | 否 | 否 | 打印方舟版本号、字节码文件格式版本号及最低支持版本号。 |

## 输出格式与使用说明

本章介绍ArkTS-Sta版本的Disassembler的输出格式与使用方法。

### 输出文件结构

ArkTS-Sta版本的反汇编文件按顺序包含以下段落：

| 段落 | 说明 |
| --- | --- |
| 文件头注释 | `# source binary: <文件名>` |
| RECORDS段 | 类、接口、外部依赖等类型定义。 |
| FUNCTIONS段 | 函数和方法定义。 |

### 基础反汇编示例

假设已存在ArkTS-Sta方舟字节码文件`example.abc`，其源代码内容如下：

```typescript
let i: int = 99;
let str: String = "Hello World!";
function show(): int {
    console.info(str);
    return i;
}
show();
```

执行：

```bash
ark_disasm_static.exe example.abc output.pa
```

output.pa内容如下：

```text
# source binary: example.abc

.language eTS

.record arkruntime.annotation.Module <external>

.record std.core.Console <external>

.record std.core.ETSGLOBAL <external> {
    std.core.Console console <static, external, access.field=public>
}

.record std.core.Object <external>

.record std.core.String <external>

.record std.core.StringBuilder <external>

.record test.ETSGLOBAL <ets.abstract, ets.extends=std.core.Object, access.record=public, ets.annotation.type=class, ets.annotation.class=arkruntime.annotation.Module, ets.annotation.id=id_743, ets.annotation.element.name=exported, ets.annotation.element.type=array, ets.annotation.element.value=> {
    i32 i = 99 <static, access.field=public>
    std.core.String str = "Hello World!" <static, access.field=public>
}

.function void test.ETSGLOBAL._cctor_() <cctor, static> {
    ldai 0x63
    ststatic test.ETSGLOBAL.i
    lda.str "Hello World!"
    ststatic.obj test.ETSGLOBAL.str
    call.short <static> test.ETSGLOBAL.show:()
    return.void
}

.function void test.ETSGLOBAL.main() <static, access.function=public> {
    return.void
}

.function i32 test.ETSGLOBAL.show() <static, access.function=public> {
    ldstatic.obj std.core.ETSGLOBAL.console
    sta.obj v0
    ldstatic.obj test.ETSGLOBAL.str
    ets.nullcheck
    call.acc.short std.core.Console.info:(std.core.Console,std.core.String), v0, 0x1
    ldstatic test.ETSGLOBAL.i
    return
}

.function void std.core.Console.info(std.core.Console a0, std.core.String a1) <external, access.function=public>

```

### verbose模式

```bash
ark_disasm_static.exe --verbose example.abc output.pa
```

verbose模式在默认输出基础上增加调试信息，如方法/代码偏移量、指令字节码、行号表及局部变量表。以`_cctor_`方法为例：

```text
.function void test.ETSGLOBAL._cctor_() <cctor, static> { # offset: 0x0186, code offset: 0x01ec
#   CODE:
    ldai 0x63                                  # offset: 0x0000, [IMM8]..............[0x13 0x63]
    ststatic test.ETSGLOBAL.i                  # offset: 0x0002, [ID16]..............[0x8c 0x00 0x00]
    call.short <static> test.ETSGLOBAL.show:() # offset: 0x0005, [V4_V4_ID16]........[0x96 0x00 0x00 0x00]
    return.void                                # offset: 0x0009, [NONE]..............[0x92]

#   LINE_NUMBER_TABLE:
#    line 4294967295: 0
#    line 4294967301: 5
}
```

### skip-string-literals模式

```bash
ark_disasm_static.exe --skip-string-literals example.abc output.pa
```

`--skip-string-literals`模式会将指令中的字符串字面量替换为其在abc文件中的偏移量。以`_cctor_`方法为例：

```text
.function void test.ETSGLOBAL._cctor_() <cctor, static> {
    ldai 0x63
    ststatic test.ETSGLOBAL.i
    lda.str "0x175"
    ststatic.obj test.ETSGLOBAL.str
    call.short <static> test.ETSGLOBAL.show:()
    return.void
}
```

对比基础输出，`lda.str "Hello World!"`变为`lda.str "0x175"`，其中`0x175`是字符串`"Hello World!"`在abc文件中的偏移量。

> **说明**：
>
> skip-string-literals仅替换**指令中**的字符串字面量引用，不影响Record字段定义中的初始值（如`std.core.String str = "Hello World!"`保持不变）。

