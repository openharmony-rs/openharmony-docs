# ArkTS Migration Visualizer使用指南
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @cy917474985-->
<!--Designer: @cy917474985-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @zhang_yixin13-->

## 工具简介

`ArkTS Migration Visualizer`是一款面向工程静态化重构分析的性能敏感识别工具。它通过整合 **Homecheck**生成的依赖图与 **Hapray**生成的性能数据，帮助开发者识别应用中的性能瓶颈点，并进一步定位这些瓶颈所关联的文件、HAR模块依赖关系，从而更准确地圈定可优先开展工程静态化重构的代码范围。

> **说明：**
>
> - [`Homecheck`](https://gitcode.com/openharmony-sig/homecheck)：静态依赖分析工具，用于扫描工程源码并生成HAR级、文件级依赖关系数据。
> - [`Hapray`](https://gitcode.com/SMAT/ArkAnalyzer-HapRay)：性能采集工具，用于采集应用运行过程中的性能耗时与时间线数据。

## 获取代码

从GitCode下载`arkcompiler_runtime_core`仓：

```text
https://gitcode.com/openharmony/arkcompiler_runtime_core
```

进入目录：

```text
static_core/plugins/ets/tools/migration_visualizer
```

本文命令示例默认以Windows环境为主，并假设在仓库根目录下执行命令。

## 环境要求

- Python版本需要3.10到3.12。
- Node.js / npm，推荐node20及以上版本。
- Git工具。
- 可用的OpenHarmony / DevEco SDK。
- Windows环境下可正常访问依赖仓和镜像源。

## 配置文件

先复制配置模板：

```text
configs/config.example.json -> configs/config.json
```

配置文件`configs/config.json`中的常用配置项、数据类型、是否必填及说明见下表。

| 配置项 | 类型 | 是否必填 | 说明 |
| --- | --- | --- | --- |
| `project_path` | `string` | 是 | 待分析的OpenHarmony工程路径。 |
| `sdk_hms_path` | `string` | 是 | DevEco SDK中`hms`目录路径，例如`C:\\Program Files\\DevEco Studio\\sdk\\default\\hms`。 |
| `sdk_openharmony_path` | `string` | 是 | DevEco SDK中`openharmony`或`base`目录路径，例如`C:\\Program Files\\DevEco Studio\\sdk\\default\\openharmony`。 |
| `deps_root` | `string` | 否 | 依赖下载与运行目录，默认是`.deps`。 |
| `c_sdk_paths` | `string[]` | 否 | 额外C/C++ SDK目录列表，会传给Homecheck。 |
| `analysis_dir` | `string` | 否 | 自定义Homecheck分析输出目录。 |
| `homecheck_path` | `string` | 否 | 使用已有Homecheck目录，覆盖bootstrap下载结果。 |
| `hapray_path` | `string` | 否 | 使用已有Hapray目录，覆盖bootstrap下载结果。 |
| `windows_short_alias_root` | `string` | 否 | Windows下Hapray短路径别名目录，可留空。 |
| `hdc_path` | `string` | 条件必填 | 当脚本无法自动发现`hdc`时填写，Windows环境建议显式配置。 |
| `hapray_python` | `string` | 条件必填 | 当Hapray无法自动找到可用Python 3.10到3.12解释器时填写。 |
| `npm_registry` | `string` | 否 | npm镜像地址。 |
| `npm_strict_ssl` | `string` | 否 | npm严格证书校验开关，通常写`true`、`false`或留空。 |
| `npm_fetch_timeout` | `int` | 否 | npm下载超时时间，单位为毫秒。 |
| `npm_fetch_retries` | `int` | 否 | npm下载重试次数。 |
| `pip_index_url` | `string` | 否 | pip镜像地址。 |
| `pip_timeout` | `int` | 否 | pip下载超时时间，单位为秒。 |
| `pip_retries` | `int` | 否 | pip下载重试次数。 |
| `hapray_round` | `int` | 否 | 采集轮数。 |
| `hapray_devices` | `string[]` | 否 | 指定Hapray采集设备列表。 |
| `hapray_so_dir` | `string` | 否 | native `.so`符号目录。 |
| `node_max_old_space_size` | `int` | 否 | Homecheck使用的Node.js堆内存大小，单位为MB。 |

补充说明：

- Windows路径可直接写为`C:\\...`。
- `sdk_hms_path`和`sdk_openharmony_path`应直接指向组件目录本身，而不是它们的父SDK根目录。
- 如果仓库路径较长，建议将`deps_root`改为较短的绝对路径，例如`C:\\OH\\.amv-deps\\migration_visualizer`。
- 当`windows_short_alias_root`为空时，脚本会优先根据`deps_root`自动推导短路径别名目录。
- 使用手动监听模式时，请确保`project_path`指向实际要操作的应用工程，并且`AppScope/app.json5`中的`bundleName`与`--manual-package`一致。

## 准备依赖

在仓库根目录执行：

```bat
.\src\scripts\bootstrap.cmd --tool all --verify
```

如需临时指定镜像源和依赖目录，可以这样执行：

```bat
.\src\scripts\bootstrap.cmd --tool all --verify ^
  --npm-registry https://<your-npm-mirror>/ ^
  --pip-index-url https://<your-pypi-mirror>/simple/ ^
  --deps-root C:\OH\.amv-deps\migration_visualizer
```

说明：

- `bootstrap.cmd`默认读取`configs/config.json`中的`deps_root`。
- 也可以通过`--deps-root`临时覆盖，并且命令行参数优先级高于配置文件。
- `bootstrap.cmd`和`run_all.py`都支持`--deps-root`。
- 如果希望整个流程都使用同一套临时依赖目录，需要在后续命令中继续传入相同的`--deps-root`。

## 一键运行

### 手动监听模式

文档中的运行流程统一按照手动监听模式说明。执行以下命令后，可在设备上手动操作目标应用：

```bat
python src\run_all.py --manual-package com.example.xxx --manual-duration 60
```

手动监听模式的特点如下：

- 仍然走`Homecheck + Hapray`的完整采集链路。
- 当应用启动且控制台出现`Starting manual workload collection`日志后，即可在设备上手动操作目标应用。
- 采集结束后同样会生成相同的四份输入文件。
- 自动选择最新的`artifacts/test_run_*`。
- 生成`src/web/hierarchical_integrated_data.json`。
- 默认启动本地页面`http://localhost:8000/`。

如果`8000`端口已被占用，脚本会自动尝试后续可用端口。

**页面示意**
![ArkTS Migration Visualizer页面示意](figures/dependency-graph.png)

## `run_all.py`常用参数

- `--manual-package`：手动监听模式下的目标应用包名。
- `--manual-duration`：手动监听时长，单位为秒。
- `--deps-root`：临时覆盖依赖目录。
- `--skip-collect`：跳过采集，直接使用已有产物构建页面。
- `--run-dir`：指定已有的`artifacts/test_run_*`目录。
- `--serve` / `--no-serve`：是否在构建完成后启动本地服务器，默认启动。
- `--port`：本地页面端口，默认`8000`。
- `--no-open`：不自动打开浏览器。
- `--quiet`：减少控制台输出。

示例：

```bat
python src\run_all.py --skip-collect
python src\run_all.py --skip-collect --run-dir artifacts\test_run_YYYYMMDD_HHMMSS
python src\run_all.py --manual-package com.example.xxx --manual-duration 60 --port 8010
```

## 依赖关系可视化页面说明

依赖关系可视化页面为纯静态页面，不依赖后端服务。

当前支持的交互包括：

- 首层展示HAR依赖图。
- 点击HAR节点可进入文件依赖图。
- 点击空白处或按`Esc`可清除当前固定详情。
- 详情面板会显示节点名称、完整路径和耗时。
- `Non-zero`会隐藏零耗时节点，并在隐藏后自动重连路径。
- 排行榜支持点击跳转并高亮对应节点。

## 常见问题

### 端口占用处理

如果启动页面时发现`8000`端口已被占用，可以按以下方式处理：

- 直接重新执行命令，脚本会自动尝试后续可用端口。
- 如果希望固定端口，可显式传入`--port`，例如：

```bat
python src\run_all.py --skip-collect --port 8010
```

- 如果需要确认占用情况，可在Windows命令行执行：

```bat
netstat -ano | findstr :8000
```

### 依赖下载失败处理

如果执行`bootstrap.cmd`时出现依赖下载失败、超时或镜像访问异常，可按以下顺序排查：

- 确认当前环境可访问GitCode、npm镜像源和PyPI镜像源。
- 优先显式指定可用镜像源并重新执行：

```bat
.\src\scripts\bootstrap.cmd --tool all --verify ^
  --npm-registry https://<your-npm-mirror>/ ^
  --pip-index-url https://<your-pypi-mirror>/simple/
```

- 如果Windows路径过长，建议同时指定较短的`--deps-root`，例如`C:\\OH\\.amv-deps\\migration_visualizer`。
- 如果之前下载过程中断，建议删除`deps_root`目录下未完成的依赖目录后重新执行，例如`deps_root\\sources\\homecheck`、`deps_root\\sources\\ArkAnalyzer-HapRay`。
- 如果后续执行`run_all.py`，请继续传入与bootstrap阶段一致的`--deps-root`，避免混用不同依赖目录。
