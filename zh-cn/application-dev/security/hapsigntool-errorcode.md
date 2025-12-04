# 签名工具错误码

<!--Kit: Common-->
<!--Subsystem: Security-->
<!--Owner: @scuteehuangjun-->
<!--Designer: @scuteehuangjun; @liuchibin-->
<!--Tester: @wwrongs-->
<!--Adviser: @zengyawen-->

## 11106001 无效的文件格式

**错误信息**

Invalid File Format.

**错误描述**

输入文件格式错误。

**可能原因**

代码签名不支持输入的文件格式。

**处理步骤**

代码签名支持的文件格式为：hap、hsp、hqf。

## 11110001 文件流读取错误

**错误信息**

Input Stream Read Error.

**错误描述**

文件读取错误。

**可能原因**

文件读取错误。

**处理步骤**

请重试，或结合故障日志及应用包进一步分析。

## 11111002 证书错误

**错误信息**

Certificates Error.

**错误描述**

证书验证失败。

**可能原因**

1. 证书不正确。

2. 签名参数keyAlias的值不正确。

**处理步骤**

1. 检查证书格式内容是否正确。

2. 检查参数keyAlias的值是否正确。

## 11112001 Profile内容错误

**错误信息**

Profile Content Error.

**错误描述**

Profile内容错误。

**可能原因**

1. profile json内容格式不符合规范。

2. type缺失或值不合法。

3. bundle-info缺失。

4. app-identifier值类型错误或长度不合法。

**处理步骤**

1. 检查json内容结构是否符合格式规范。

2. 检查type值是否正确。

3. 补充bundle-info内容。

4. 确认app-identifier值类型为String，并且字符长度要求大于0、小于等于32。

## 11112002 module.json内容错误

**错误信息**

module.json Content Error.

**错误描述**

module.json文件内容错误。

**可能原因**

1. module.json内容格式不符合格式规范。

2. 应用包中hnp文件未在module.json中描述。

**处理步骤**

1. 检查json内容结构是否符合格式规范。

2. 在module.json中添加hnp文件描述，[开发指导](../quick-start/module-configuration-file.md#hnppackages标签)。

## 11112003 ELF文件错误

**错误信息**

ELF is incorrect.

**错误描述**

ELF文件解析错误。

**可能原因**

ELF文件的头信息错误。

**处理步骤**

检查ELF文件的头信息是否符合格式规范。

## 11112004 HNP文件错误

**错误信息**

Extract hnp file error.

**错误描述**

解压hnp文件错误。

**可能原因**

1. 提取hnp文件错误。

2. 解压hnp文件错误。

**处理步骤**

1. 再次执行签名。

2. 检查hnp文件打包是否正确。

## 11113001 算法错误

**错误信息**

Invalid algorithm.

**错误描述**

签名算法错误。

**可能原因**

安装的Java版本不支持此摘要算法。

**处理步骤**

代码签名需要SHA-256和SHA-512算法支持，请检查Java版本是否正确，当前支持Java8以上Java环境运行。

## 11114001 签名内部错误

**错误信息**

Code Sign Internal Error.

**错误描述**

代码签名内部错误。

**可能原因**

工具签名过程中发生了内部错误。

**处理步骤**

结合故障日志及应用包进一步分析。