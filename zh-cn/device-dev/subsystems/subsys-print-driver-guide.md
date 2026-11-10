# 打印驱动开发指南

本文档说明如何将 `testbackend` 打印驱动（backend + PPD）编译、部署到鸿蒙设备，完成从设备发现到打印的完整链路。

## 项目结构

```
entry/libs/arm64-v8a/
├── testbackend          # CUPS backend 二进制（需编译）
└── testbackend.ppd      # 打印机描述文件（直接使用）
```

```
entry/src/main/
├── ets/extensionAbility/DriverExtensionAbility.ets   # 驱动扩展入口
└── module.json5                                       # 驱动安装配置
```

## 驱动能力

`testbackend` 作为 CUPS backend，实现以下能力：

| 能力 | 说明 |
|------|------|
| 设备发现 | 被 CUPS 无参调用时，向 stdout 输出打印机设备列表，使打印机出现在鸿蒙的打印机添加界面 |
| 打印作业处理 | 接收 CUPS 管道传入的 PDF 数据，保存为本地文件（虚拟打印机场景） |
| 双输入模式 | 支持 stdin 管道输入和文件路径输入两种方式 |
| 可配置输出目录 | 优先读取 `TMPDIR` 环境变量，默认输出到 `/data/service/.../cups/spool/tmp/` |
| 日志输出 | stderr 输出 `DEBUG:` 前缀日志，便于定位问题 |

## 源码解析

### 完整源码：testbackend.cpp

```cpp
/*
 * Copyright (c) 2025 Huawei Device Co., Ltd.
 * Licensed under the Apache License, Version 2.0 (the "License");
 * you may not use this file except in compliance with the License.
 * You may obtain a copy of the License at
 *
 *     http://www.apache.org/licenses/LICENSE-2.0
 *
 * Unless required by applicable law or agreed to in writing, software
 * distributed under the License is distributed on an "AS IS" BASIS,
 * WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 * See the License for the specific language governing permissions and
 * limitations under the License.
 */

#include <cstdio>
#include <cstdlib>
#include <cstring>
#include <cerrno>
#include <string>
#include <unistd.h>
#include <fcntl.h>
#include <sys/stat.h>
#include <netdb.h>
#include <arpa/inet.h>

const size_t BUFFER_SIZE = 4096;
const std::string DEFAULT_TMP_DIR = "/data/service/el1/public/print_service/cups/spool/tmp";
const size_t OUTPUT_FILE_BUF_SIZE = 256;

// 设备发现模式 — 返回支持的打印机列表
static int list_devices() {
    printf("network com.example.backendtest_entry_testbackend:/ \"testbackend\" \"Save PDF to local file\"\n");
    fflush(stdout);
    return 0;
}

// 参数校验
static bool validate_args(const int argc, const char* const argv[]) {
    if (argc != 6 && argc != 7) {
        fprintf(stderr, "ERROR: invalid argc %d, only 6 or 7 allowed\n", argc);
        fprintf(stderr, "Usage: %s job-id user title copies options [file]\n", argv[0]);
        return false;
    }
    return true;
}

// 获取临时目录
static std::string get_temp_dir() {
    const char* tmp_dir_c = getenv("TMPDIR");
    std::string tmp_dir;
    if (tmp_dir_c == nullptr) {
        tmp_dir = DEFAULT_TMP_DIR;
    } else {
        tmp_dir = tmp_dir_c;
    }
    return tmp_dir;
}

// 构建输出文件路径
static int build_output_path(const std::string& tmp_dir, const std::string& job_id,
                             std::string& output_file) {
    output_file = tmp_dir + "/" + job_id + ".pdf";
    if (output_file.length() >= OUTPUT_FILE_BUF_SIZE) {
        fprintf(stderr, "ERROR: path too long (need %zu bytes, max %zu)\n",
                output_file.length(), OUTPUT_FILE_BUF_SIZE - 1);
        return 1;
    }
    return 0;
}

// 打开输入源
static int open_input_source(int argc, char* argv[]) {
    int input_fd = -1;
    if (argc == 7) {
        input_fd = open(argv[6], O_RDONLY);
        if (input_fd < 0) {
            fprintf(stderr, "ERROR: open file %s failed: %s\n", argv[6], strerror(errno));
            return -1;
        }
    } else {
        input_fd = 0;  // stdin
    }
    return input_fd;
}

// 写入输出文件
static int write_output_file(int input_fd, const std::string& output_file) {
    FILE* fp_dest = fopen(output_file.c_str(), "wb");
    if (fp_dest == nullptr) {
        fprintf(stderr, "ERROR: open output %s failed: %s\n", output_file.c_str(), strerror(errno));
        return 1;
    }
    char buffer[BUFFER_SIZE];
    ssize_t bytes_read;
    while ((bytes_read = read(input_fd, buffer, BUFFER_SIZE)) > 0) {
        size_t bytes_written = fwrite(buffer, 1, static_cast<size_t>(bytes_read), fp_dest);
        if (bytes_written != static_cast<size_t>(bytes_read)) {
            fprintf(stderr, "ERROR: write failed (wrote %zu of %zd bytes): %s\n",
                    bytes_written, bytes_read, strerror(errno));
            fclose(fp_dest);
            return 1;
        }
    }
    if (bytes_read < 0) {
        fprintf(stderr, "ERROR: read failed: %s\n", strerror(errno));
        fclose(fp_dest);
        return 1;
    }
    fclose(fp_dest);
    return 0;
}

int main(int argc, char* argv[]) {
    // 1. 设备发现模式：argc == 1 时 CUPS 要求输出设备列表
    if (argc == 1) {
        return list_devices();
    }

    // 2. 参数校验
    if (!validate_args(argc, argv)) {
        return 1;
    }

    // 3. 获取作业信息
    if (argc < 2 || !argv[1] || strlen(argv[1]) == 0) {
        fprintf(stderr, "ERROR: job id is missing\n");
        return 1;
    }
    std::string job_id = argv[1];

    // 4. 构建输出路径
    std::string tmp_dir = get_temp_dir();
    std::string output_file;
    if (build_output_path(tmp_dir, job_id, output_file) != 0) {
        return 1;
    }

    // 5. 打开输入源（文件 or stdin）
    int input_fd = open_input_source(argc, argv);
    if (input_fd < 0) {
        return 1;
    }

    // 6. 写入输出文件
    if (write_output_file(input_fd, output_file) != 0) {
        if (input_fd != 0) close(input_fd);
        return 1;
    }

    // 7. 清理
    if (input_fd != 0) close(input_fd);

    return 0;
}
```

### 代码与能力对应关系

#### 设备发现 — `list_devices()`

```cpp
static int list_devices() {
    printf("network com.example.backendtest_entry_testbackend:/ \"testbackend\" \"Save PDF to local file\"\n");
    fflush(stdout);
    return 0;
}
```

这是 backend 的核心能力入口。CUPS 在搜索打印机时会无参数调用所有 backend，backend 必须向 stdout 输出设备声明：

```
device-class device-uri "device-make-and-model" "device-info"
```

| 字段 | 示例值 | 说明 |
|------|--------|------|
| device-class | `network` | 设备类型：`network` / `direct` / `serial` / `file` |
| device-uri | `com.example.backendtest_entry_testbackend:/` | 设备 URI，`{包名}_{module名}_{backend名}:/` 格式，系统自动拼接保证唯一 |
| make-and-model | `"testbackend"` | 打印机型号，显示在添加界面 |
| device-info | `"Save PDF to local file"` | 打印机描述信息 |

这行输出决定了打印机能否出现在鸿蒙 **设置 → 打印机和扫描仪** 的添加界面中。开发者适配自己的打印机时，只需修改此函数中的设备声明即可。

#### 参数校验 — `validate_args()`

```cpp
static bool validate_args(const int argc, const char* const argv[]) {
    if (argc != 6 && argc != 7) {
        fprintf(stderr, "ERROR: invalid argc %d, only 6 or 7 allowed\n", argc);
        fprintf(stderr, "Usage: %s job-id user title copies options [file]\n", argv[0]);
        return false;
    }
    return true;
}
```

CUPS 调用 backend 执行打印时，传入标准参数：

```
testbackend job-id user title copies options [file]
```

| 参数 | 说明 |
|------|------|
| job-id | 作业 ID，用于标识本次打印任务 |
| user | 发起打印的用户 |
| title | 打印任务标题 |
| copies | 打印份数 |
| options | 打印选项（如纸张方向等） |
| file | 可选，输入文件路径；不传则从 stdin 读取 |

argc 必须为 6（stdin 输入）或 7（文件输入），否则说明调用方式有误。

#### 输出目录 — `get_temp_dir()` + `build_output_path()`

```cpp
static std::string get_temp_dir() {
    const char* tmp_dir_c = getenv("TMPDIR");
    if (tmp_dir_c == nullptr) {
        tmp_dir = DEFAULT_TMP_DIR;  // /data/service/el1/public/print_service/cups/spool/tmp
    } else {
        tmp_dir = tmp_dir_c;
    }
    return tmp_dir;
}

static int build_output_path(const std::string& tmp_dir, const std::string& job_id,
                             std::string& output_file) {
    output_file = tmp_dir + "/" + job_id + ".pdf";
    // ... 路径长度校验
}
```

- 优先使用 `TMPDIR` 环境变量指定的目录
- 默认输出到 `/data/service/el1/public/print_service/cups/spool/tmp/{job-id}.pdf`
- 对路径长度做了 256 字节上限校验

#### 双输入模式 — `open_input_source()`

```cpp
static int open_input_source(int argc, char* argv[]) {
    if (argc == 7) {
        input_fd = open(argv[6], O_RDONLY);  // 从文件读取
    } else {
        input_fd = 0;  // 从 stdin 读取（CUPS 管道）
    }
    return input_fd;
}
```

CUPS 有两种方式把数据传给 backend：
- **管道方式**（argc=6）：数据从 stdin 流入，最常见的方式
- **文件方式**（argc=7）：数据已落盘，通过 argv[6] 传入文件路径

#### 数据写入 — `write_output_file()`

```cpp
static int write_output_file(int input_fd, const std::string& output_file) {
    FILE* fp_dest = fopen(output_file.c_str(), "wb");
    char buffer[BUFFER_SIZE];
    while ((bytes_read = read(input_fd, buffer, BUFFER_SIZE)) > 0) {
        fwrite(buffer, 1, bytes_read, fp_dest);  // 4KB 循环读写
    }
    fclose(fp_dest);
    return 0;
}
```

- 以 4KB 缓冲区循环读写，将输入原样输出到 PDF 文件
- 写入失败时通过 stderr 输出 `ERROR:` 日志

### PPD 文件：testbackend.ppd

```ppd
*PPD-Adobe: "4.3"
*Manufacturer:    "Generic"
*ModelName:       "testbackend"
*ShortNickName:   "testbackend"
*NickName:        "testbackend"
*cupsFilter:      "application/pdf 0 -"
*ColorDevice:     True

*OpenUI *PageSize/Page Size: PickOne
*DefaultPageSize: A4
*PageSize A3/A3:  "<</PageSize[842 1191]/ImagingBBox null>>setpagedevice"
*PageSize A4/A4:  "<</PageSize[595 842]/ImagingBBox null>>setpagedevice"
*PageSize A5/A5:  "<</PageSize[421 595]/ImagingBBox null>>setpagedevice"
*PageSize A6/A6:  "<</PageSize[298 421]/ImagingBBox null>>setpagedevice"
*PageSize B4/B4:  "<</PageSize[729 1032]/ImagingBBox null>>setpagedevice"
*PageSize B5/B5:  "<</PageSize[516 729]/ImagingBBox null>>setpagedevice"
*PageSize 16K/16K: "<</PageSize[496 701]/ImagingBBox null>>setpagedevice"
*PageSize 32K/32K: "<</PageSize[350 496]/ImagingBBox null>>setpagedevice"
*CloseUI: *PageSize
```

关键配置：

| 字段 | 值 | 含义 |
|------|----|------|
| `cupsFilter` | `"application/pdf 0 -"` | PDF 直透传到 backend，无 filter 转换 |
| `Manufacturer` | `"Generic"` | 厂商标识 |
| `ModelName` | `"testbackend"` | 型号名，需与 backend 发现的设备名匹配 |
| `PageSize` | A3/A4/A5/A6/B4/B5/16K/32K | 支持的纸张尺寸 |
| `ColorDevice` | `True` | 声明为彩色设备 |

`cupsFilter: "application/pdf 0 -"` 中 `-` 表示不经过任何 filter，CUPS 将 PDF 原样交给 backend。这是虚拟打印机/PDF 输出场景的标准配置。

## 编译

编译环境搭建详见 **OpenHarmony打印扫描驱动开发指南1.9** 第三章。这里重点说明 BUILD.gn 的配置逻辑和 testbackend 的编译方式。

### BUILD.gn 配置解析

BUILD.gn 位于 OpenHarmony 源码 `/third_party/cups/BUILD.gn`，是 CUPS 组件的编译入口。testbackend 的编译配置需要在此文件中完成三件事：**声明源码变量**、**注册到 cups_action**、**添加编译目标**。

#### 声明源码变量

在 BUILD.gn 顶部的变量声明区域，定义 testbackend 的源码路径：

```gn
testbackend_generated_sources = [ "$backend_code_dir/testbackend.cpp" ]
```

其中 `backend_code_dir` 在文件头部已定义：

```gn
cups_code_dir = "${target_gen_dir}/cups-2.4.14"
backend_code_dir = "$cups_code_dir/backend"
```

这意味着 testbackend.cpp 需要放在源码的 `third_party/cups/backend/` 目录下，编译时会由 `cups_action` 将其拷贝到生成目录。

#### 注册到 cups_action

`cups_action` 是一个 action 目标，负责将源码从仓库目录拷贝到编译生成目录，并应用 OpenHarmony 补丁。testbackend 的源码变量必须加入其 `outputs` 列表：

```gn
action("cups_action") {
  # ... 其他 outputs
  outputs += testbackend_generated_sources
  # ...
}
```

#### 注册到编译 group

`third_party_cups` 是顶层编译入口，testbackend 需要加入其 `deps`：

```gn
group("third_party_cups") {
  public_deps = [ ":cups" ]
  deps = [
    ":cups-deviced",
    ":cups-driverd",
    ":cups-exec",
    ":cupsd",
    ":cupsfilter",
    ":cupsimage",
    ":ipp",
    ":mime.convs",
    ":mime.types",
    ":rastertopwg",
    ":commandtops",
    ":usb",
    ":testbackend",       # ← 添加此行
  ]
  # ...
}
```

#### 添加编译目标

参照同文件中 usb、ipp 等 backend 的写法，添加 testbackend 的 `ohos_executable`：

```gn
ohos_executable("testbackend") {
  sources = testbackend_generated_sources
  deps = [
    ":backend",
    ":cups",
    ":cups_action",
  ]
  external_deps = []
  install_enable = true
  module_install_dir = "$cups_serverbin_dir/backend"
  public_configs = [ ":cups_config" ]
  subsystem_name = "$SUBSYSTEM_NAME"
  part_name = "$PART_NAME"
}
```

各字段说明：

| 字段 | 值 | 说明 |
|------|----|------|
| `sources` | `testbackend_generated_sources` | 引用前面声明的源码变量 |
| `deps` | `:backend`, `:cups`, `:cups_action` | 依赖 backend 共享库（网络/USB 通用代码）、libcups、源码拷贝 action |
| `external_deps` | 空 | testbackend 不依赖外部部件；如需 hilog、libusb 等，参照 usb backend 添加 |
| `install_enable` | `true` | 随系统安装 |
| `module_install_dir` | `$cups_serverbin_dir/backend` | 安装到 CUPS backend 目录，CUPS 通过此路径发现和调用 backend |
| `public_configs` | `:cups_config` | 继承 CUPS 头文件路径和编译选项 |
| `subsystem_name` / `part_name` | `thirdparty` / `cups` | 所属子系统和部件 |

> **新增 backend 时的模式**：声明源码变量 → 加入 cups_action.outputs → 在 group deps 和 ohos_executable 中添加。参照 testbackend 的写法即可扩展新的 backend。

### 编译 & 导出

```bash
# 容器内编译（arm64）
./build.sh --product-name rk3568 --build-target third_party/cups:third_party_cups --target-cpu arm64

# 宿主机导出产物
docker cp oh_builder:/home/openharmony/out/rk3568/thirdparty/cups/testbackend D:\dist
```

产物 `testbackend` 放入工程 `entry/libs/arm64-v8a/` 即可。PPD 无需编译。

## 驱动安装配置

### module.json5

`extensionAbilities` 中声明驱动类型和文件映射，系统安装 HAP 时会自动将文件推送到设备对应路径：

```json5
"extensionAbilities": [
  {
    "name": "DriverExtensionAbility",
    "srcEntry": "./ets/extensionAbility/DriverExtensionAbility.ets",
    "type": "driver",
    "exported": false,
    "metadata": [
      {
        "name": "desc",
        "value": "testbackend printer driver"
      },
      {
        "name": "vendor",
        "value": "test company"
      },
      {
        "name": "cupsBackend",
        "value": "/print_service/cups/serverbin/backend",
        "resource": "/libs/arm64-v8a/testbackend"
      },
      {
        "name": "cupsPpd",
        "value": "/print_service/cups/datadir/model",
        "resource": "/libs/arm64-v8a/testbackend.ppd"
      }
    ]
  }
]
```

metadata 字段含义：

| name | value（设备目标路径） | resource（工程内源路径） |
|------|----------------------|------------------------|
| `cupsBackend` | `/print_service/cups/serverbin/backend` | backend 二进制 |
| `cupsPpd` | `/print_service/cups/datadir/model` | PPD 文件 |

### build-profile.json5

`entry/build-profile.json5` 的 `buildOption` 中加入（防止驱动安装失败）：

```json5
"nativeLib": {
  "collectAllLibs": true,
  "debugSymbol": {
    "strip": true,
    "exclude": []
  }
}
```

### SDK 补丁

DevEco 默认 SDK 不识别 `type: "driver"`，需手动修改两处后重启：

1. **module.json** — `extensionAbilities.type` 的枚举值中 `preview` 下面添加 `"driver"`
2. **resource pattern** — 正则改为 `(^[$]profile:[0-9a-zA-Z_.]+|(?=.*[{])(?=.*[}])[0-9a-zA-Z_.{}]+)|(^(/[\w-]+)+(.[a-z]+)?)$|.*`

> 具体操作见 OpenHarmony打印扫描驱动开发指南1.9 第 6.3 节（5.1 ~ 5.3）。

## 部署 & 验证

```bash
# 签名后构建 HAP（DevEco: Build → Build Hap(s)）
# 安装到设备
hdc install entry-default-signed.hap
```

HAP 安装后驱动文件自动部署到设备：

```
/print_service/cups/serverbin/backend/testbackend     ← backend
/print_service/cups/datadir/model/testbackend.ppd     ← PPD
```

### 数据流全链路

```
设备发现              添加打印机             发起打印
   │                    │                    │
   ▼                    ▼                    ▼
backend 无参调用     CUPS 读取设备声明     CUPS 管道传 PDF
   │                + PPD 创建队列            │
   ▼                    │                    ▼
stdout 输出设备声明       ▼              testbackend 接收
（device line）    打印机出现在           stdin/fd，保存到
                  添加界面               spool/tmp/{job-id}.pdf
```

## 验证清单

| 阶段 | 操作 | 预期 |
|------|------|------|
| 发现 | 设备 **设置 → 打印机和扫描仪** -> 添加打印机和扫描仪 | 列表中出现 "**Save PDF to local file**" |
| 添加 | 点击添加 | 打印机状态显示"已连接" |
| 打印 | 选择 "**Save PDF to local file**" 发起打印，然后执行 `hdc shell ls /data/service/el1/public/print_service/cups/spool/tmp/` | 目录下出现新生成的 PDF 文件 |

## 参考

- [OpenHarmony打印扫描驱动开发指南1.9](https://gitcode.com/openharmony/applications_print_spooler/blob/master/OpenHarmony%E6%89%93%E5%8D%B0%E6%89%AB%E6%8F%8F%E9%A9%B1%E5%8A%A8%E5%BC%80%E5%8F%91%E6%8C%87%E5%8D%971.9.md)
- [CUPS Backend 规范](https://www.cups.org/doc/man-backend.html)
- [OpenHarmony 打印框架](https://gitee.com/openharmony/print_print_fwk)
