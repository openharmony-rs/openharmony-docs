# 面向Agent的CLI命令概述

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zhu-feimo-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

## 概述

CLI（Command-Line Interface，命令行界面）是一套自API版本26.0.0起支持的、面向Agent（智能体）的系统级命令调用能力。它以独立可执行程序的形式部署在设备上，遵循统一的命令规范，并以JSON格式输出执行结果，为Agent提供了除ArkTS API之外的另一种全新的系统交互方式。

## 核心价值

- **标准化调用入口**：提供统一的命令格式和参数规范，降低Agent接入系统能力的成本。
- **JSON结构化输出**：执行结果以JSON格式返回，包含错误码、错误原因和解决建议，便于Agent程序化解析和处理。
- **跨进程独立性**：CLI作为独立可执行程序运行，不依赖调用方的运行时环境，通过应用内Native代码调用。
- **权限管控**：通过系统权限机制控制CLI的访问范围，确保系统安全。

## 典型场景

- **Agent拉起应用**：Agent在应用内通过Native（C/C++）代码fork+execvp方式调用CLI的start命令，启动指定的应用组件（比如[UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md)），支持[显式启动](explicit-implicit-want-mappings.md#显式want匹配原理)和[隐式启动](explicit-implicit-want-mappings.md#隐式want匹配原理)。
- **Agent停止应用**：Agent在应用内通过Native（C/C++）代码fork+execvp方式调用CLI的force-stop命令，强制停止指定应用及其进程，用于资源清理或异常恢复。

> **说明：**
>
> CLI与[aa工具](../tools/aa-tool.md#aa工具命令列表)均提供Ability管理能力，但适用场景不同：CLI以独立可执行程序形式部署在设备上，使用长选项参数格式，以JSON格式输出结果；aa工具通过hdc shell远程执行，使用短选项参数格式，以文本格式输出结果。若在PC/2in1设备上进行应用内调用且需要JSON结构化结果，使用CLI；若需要通过hdc远程调试或在手机/平板上执行，使用aa工具。

## 约束与限制

- **设备要求**：CLI当前仅支持PC/2in1设备。
- **权限要求**：应用内调用CLI需申请`ohos.permission.CUSTOM_SANDBOX`权限，详见[申请CLI访问权限](cli-permission-guide.md)。
- **调用方式**：在PC/2in1设备上，Agent需通过应用内Native（C/C++）代码以fork+execvp方式执行并调用CLI，详情请参见[实现CLI调用](cli-invocation-guide.md)。