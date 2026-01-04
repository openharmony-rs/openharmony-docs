# Taihe基本使用文档

本文档介绍Taihe的安装、环境配置以及命令行工具的使用方法。

## 环境配置

- 源码用户

  Ubuntu用户可在拉取的Taihe项目根目录下运行`scripts/install-ubuntu-deps`一键配置环境。

  对于非Ubuntu用户，需要手动安装以下依赖项：

  - **运行时**
    - Clang 15（GCC不保证完整支持）
    - CMake 3.14
  - **编译器**
    - Python 3.10
    - uv（安装可参考[官方文档](https://github.com/astral-sh/uv)）

  安装完成后，在项目根目录下以此运行`uv sync`和`uv build`命令以同步依赖并构建项目，完成环境配置。

  在配置好环境后，每次使用时都需要先在项目根目录下运行`source .venv/bin/activate`来激活虚拟环境，或者在使用命令行工具时运行`uv run taihec`命令而不是直接运行`taihec`。

- 二进制包用户

  二进制包内已经包含了所有的依赖，用户无需手动配置环境。

## Taihe命令行使用方法

`taihec`是Taihe的核心编译器工具，用于解析Taihe IDL文件并编译为目标语言的代码。并支持选择任意多种代码生成后端，生成适用于不同场景的代码。以下是`taihec`的基本用法：

```sh
taihec [taihe_files ...] [options ...]
```

- `taihe_files`可以是一个或多个Taihe IDL文件，也可以使用通配符（例如`path/to/idl/*.ohidl`）来指定多个文件。
- `options`用于指定代码生成的各种选项，详见下表。

### 命令行选项

|参数|简写|说明|
| ---- | ---- | ---- |
| `--output <path>` | `-O<path>` | 指定生成的目标文件存放目录（如缺省则默认生成在`taihe-generated`目录下）|
| `--generate <backend>` | `-G<backend>` | 指定要启用的代码生成后端，如`abi-header`、`abi-source`、`c-author`等 |
| `--build <build-system>` | `-B<build-system>` | 指定构建系统类型，目前支持`cmake`（生成`CMakeLists.txt`）|
| `--codegen <namespace>:<config>[=<value>]` | `-C<namespace>:<config>[=<value>]` | 额外的代码生成配置项，例如`sts:keep-name`、`arkts:module-prefix=prefix`等 |
| `--version` | | 打印版本信息 |
| `--help` | `-h` | 帮助信息 |

### 代码生成后端

代码生成后端决定了`taihec`会生成哪些代码文件。后端之间存在依赖关系，命令行工具会自动根据配置的后端来递归地启用所需的其他后端，生成完整的代码。

| Backend | 说明 | 依赖 |
| ------- | ---- | ---- |
| `abi-header` | 生成Taihe C ABI头文件，包括类型声明，函数声明等 | 无 |
| `abi-source` | 生成Taihe C ABI源文件，包含必要的符号定义 | `abi-header` |
| `c-author` | 生成C语言提供者侧的接口导出宏以及模板代码 | `abi-source` |
| `cpp-common` | 生成C++接口提供者和消费者侧的公共代码 | `abi-header` |
| `cpp-author` | 生成C++接口提供者侧的接口导出宏以及模板代码 | `cpp-common`, `abi-source` |
| `cpp-user` | 生成C++接口消费者侧所需的所有代码 | `cpp-common` |
| `ani-bridge` | 生成ANI用户侧的桥接代码 | `cpp-user` |
| `napi-bridge` | 生成NAPI用户侧的桥接代码 | `cpp-user` |
| `pretty-print` | 将Taihe IDL文件格式化输出 | 无 |

### 代码生成配置

使用`ani-bridge`后端时支持以下代码生成配置：

| Codegen Config | 说明 |
| -------------- | ---- |
| `sts:keep-name` |保持生成的代码中的函数和方法名称与Taihe IDL文件中的名称一致，若不使用此选择则会默认将Taihe IDL文件中的名称首字母小写|
| `arkts:module-prefix=<prefix>` | 指定生成的ArkTS对应的模块名，该配置会影响生成符号的ANI签名 |
| `arkts:path-prefix=<prefix>` | 指定生成的ArkTS对应的路径前缀，该配置会影响生成符号的ANI签名 |

*注：DevEco用户必须指定`arkts:module-prefix`和`arkts:path-prefix`*

使用`napi-bridge`后端时不支持任何代码生成配置。

## 使用示例

以下是两个`taihec`的基本使用示例：
```sh
taihec test/ani_test/idl/*.ohidl -Otest/ani_test/generated -Gani-bridge -Gcpp-author -Carkts:module-prefix=<module_name> -Carkts:path-prefix=<pkg_name> -Bcmake  # 生成用户自己在IDL中定义的接口的ANI桥接代码，以及C++实现模板等

taihec test/napi_string/idl/*.ohidl -Otest/napi_string/generated -Gnapi-bridge -Gcpp-author  # 生成用户自己在IDL中定义的接口的NAPI桥接代码，以及C++实现模板等
```
