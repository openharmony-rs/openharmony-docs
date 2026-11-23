# 查询应用信息命令（public-dump）
 
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @wang19954-->
<!--Tester: @lixueqing513-->
<!--Adviser: @HelloCrease-->

## 场景介绍

public-dump命令用于查询已安装应用的包信息，可查询全部包名列表、Debug包列表、指定包详情、快捷方式信息以及应用名称信息。

## 命令格式

```bash
ohos-bm public-dump [--all] [--debugBundle] [--bundleName <bundleName>] [--shortcutInfo] [--label] [--help]
```

命令执行后返回查询结果。查询操作由系统完成，应用侧无需额外处理。

## 约束限制

- **设备与权限要求**：执行本命令需具备`ohos.permission.GET_ALL_BUNDLE_INFO`。
- **参数约束**：至少指定一个查询选项；`--shortcutInfo`必须与`--bundleName`同时使用；`--bundleName`必须携带包名参数值。
- **用户限制**：不支持指定userId，查询用户由调用方UID推导。

## 参数说明

| 参数 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| --all | flag | 否 | 列出系统中已安装的全部应用包名。可与`--label`组合，输出全部应用的名称信息。 |
| --debugBundle | flag | 否 | 列出系统中Debug类型应用包名。 |
| --bundleName | string | 条件必填 | 指定要查询的应用包名。单独使用时输出应用详细信息；与`--shortcutInfo`或`--label`组合时必填。 |
| --shortcutInfo | flag | 否 | 查询指定应用的快捷方式信息。必须与`--bundleName`同时使用。 |
| --label | flag | 否 | 查询应用名称信息。与`--all`组合输出全部应用名称，与`--bundleName`组合输出指定包的应用名称信息。 |
| --help | flag | 否 | 显示public-dump子命令的帮助信息。 |

## 错误码

命令执行失败时，JSON输出中的`errCode`字段返回以下错误码：

| 错误码 | 说明 | 处理建议 |
| ------- | -------- | -------- |
| ERR_DUMP_PARAM_ERROR | 参数错误。未携带选项、`--bundleName`未带参数值、使用了未支持选项，或`--shortcutInfo`未配合`--bundleName`。 | 检查命令参数是否完整、拼写是否正确；使用`--help`查看支持的参数列表。 |
| ERR_APPEXECFWK_SERVICE_INTERNAL_ERROR | 查询失败或结果为空。 | 确认已申请并获得`ohos.permission.GET_ALL_BUNDLE_INFO`权限；检查包名是否正确、目标应用是否已安装。 |

## 示例代码

- 查询已安装应用列表：

    ```bash
    ohos-bm public-dump --all
    ```

- 查询已安装的debug应用列表：

    ```bash
    ohos-bm public-dump --debugBundle
    ```

- 查询指定应用详细信息：

    ```bash
    ohos-bm public-dump --bundleName com.example.myapplication
    ```

- 查询指定应用的快捷方式信息：

    ```bash
    ohos-bm public-dump --shortcutInfo --bundleName com.example.myapplication
    ```

- 查询已安装应用的名称：

    ```bash
    ohos-bm public-dump --all --label
    ```

- 查询指定应用的名称：

    ```bash
    ohos-bm public-dump --bundleName com.example.myapplication --label
    ```