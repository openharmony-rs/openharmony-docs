# 证书管理命令行工具使用指导

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @chaceli-->
<!--Designer: @chande-->
<!--Tester: @sunzibin001-->
<!--Adviser: @zengyawen-->

从API版本26.0.1开始，提供证书管理命令行工具（certmgr），主要用于在设备上通过命令行方式安装用户CA证书。支持安装当前用户级和所有用户级（GlobalUser）的CA证书，支持PEM/DER和PKCS#7（P7B）格式的证书文件，同时支持通过管道输入证书数据。

## 命令行工具获取

支持运行在OpenHarmony PC/2in1设备上的工具：该工具随系统预置，无需额外配置，可在终端窗口中直接执行certmgr命令。

## 命令行工具命令列表

| 命令          | 描述                                                         |
| ------------- | ------------------------------------------------------------ |
| -h            | 帮助命令，用于查询工具支持的命令信息。                         |
| installUserCA | 安装用户CA证书。  |

## 帮助命令（-h）

```bash
# 查询工具支持的全部命令信息
certmgr -h

# 查询installUserCA命令的参数信息
certmgr installUserCA -h
```

## 安装用户CA证书命令（installUserCA）

安装用户CA证书时，系统会拉起用户身份认证（PIN码认证）或管理员授权认证，认证通过后方可完成安装<!--RP1--><!--RP1End-->。当指定`-g`参数时，证书将安装到所有用户级（GlobalUser）目录，此时需要进行管理员授权认证；未指定`-g`参数时，证书安装到当前用户目录，需要进行用户身份认证。

**命令参数列表**

| 参数             | 参数说明               |
| ---------------- | ---------------------- |
| -h               | 显示帮助信息。    |
| -g               | 安装到所有用户级（GlobalUser）目录，默认安装到当前用户目录。可选项。 |
| -F certFileFormat | 证书文件格式，支持PEM_DER或P7B，默认为PEM_DER。可选项。 |
| certFile         | 待安装的CA证书文件路径，仅允许指定一个文件。<br>支持管道输入，未使用管道输入时为必填项。 |

**示例**：

```bash
# 1. 安装PEM/DER格式的CA证书到当前用户
certmgr installUserCA -F PEM_DER ca_cert.pem

# 2. 安装P7B格式的CA证书到当前用户
certmgr installUserCA -F P7B ca_cert.p7b

# 3. 安装CA证书到所有用户级（GlobalUser）目录
certmgr installUserCA -g -F PEM_DER ca_cert.pem

# 4. 通过管道输入安装CA证书
cat ca_cert.pem | certmgr installUserCA -F PEM_DER

# 5. 使用默认参数（PEM_DER格式）安装CA证书到当前用户
certmgr installUserCA ca_cert.pem

# 安装成功时，输出证书URI
```

> **说明：**
>
> - 使用`-g`参数安装到所有用户级（GlobalUser）目录时，受设备安全策略管控。设备安全策略可通过`installGlobalUserCA_defaultConfig`、`enableInstallGlobalUserCA_userList`和`disableInstallGlobalUserCA_userList`配置项控制是否允许当前用户安装所有用户级CA证书。
> - 安装证书时系统会拉起身份认证界面，认证界面标题会根据设备系统语言进行本地化显示。
> - P7B格式证书可能包含多张证书，安装成功后会输出每个证书的URI。

## 错误信息

### CM_CMD_ERR_PARAM_INVALID

命令行参数错误或参数无效，报错提示以下信息之一：
- `Missing value for -F parameter`
- `Invalid certFileFormat: <format>`
- `Unknown parameter: <param>`
- `Multiple certificate files specified. Only one certificate file is allowed.`
- `certFile is required when no pipe input`
- `Install failed: Invalid argument`
- `Invalid file size: <size>`
- `No data from pipe input`

**可能原因**

1. 使用`-F`参数时未指定值，或指定的值不是PEM_DER或P7B。
2. 输入了未知的参数（以`-`开头但工具不支持的参数）。
3. 指定了多个证书文件，工具仅允许指定一个证书文件。
4. 未通过文件路径或管道输入提供证书数据。
5. 证书文件大小为0或超过对应格式的最大限制（PEM_DER格式为8196字节，P7B格式为307200字节即300KB）。
6. 通过管道输入时未提供任何数据。

**处理步骤**

1. 检查`-F`参数的值是否为PEM_DER或P7B。
2. 检查命令中是否包含工具不支持的参数，移除多余或错误的参数。
3. 确保只指定一个证书文件路径。
4. 如未指定证书文件路径，请通过管道输入证书数据。
5. 检查证书文件是否有有效内容，且文件大小不超过对应格式的限制（PEM_DER格式不超过8196字节，P7B格式不超过307200字节即300KB）。
6. 使用管道输入时，确保管道中包含有效的证书数据。例如通过`cat ca_cert.pem | certmgr installUserCA`方式传入证书文件内容，避免管道为空或未传入任何数据导致读取失败。

### CM_CMD_ERR_OPEN_FILE_FAIL

文件打开失败，报错提示：`Failed to open file: <filePath>`

**可能原因**

输入的证书文件路径不存在或无法打开。

**处理步骤**

检查证书文件路径是否正确，确保文件存在且可读。

### CM_CMD_ERR_INVALID_CERT_FORMAT

证书格式无效，报错提示：`Install failed: Invalid certificate format`

**可能原因**

输入的证书文件格式无效或不符合要求。例如PEM_DER格式下输入的文件不是有效的PEM格式（Base64编码，包含`-----BEGIN CERTIFICATE-----`和`-----END CERTIFICATE-----`头尾标记）或DER格式（二进制编码）的X.509 CA证书，或P7B格式下输入的文件不是有效的PKCS#7格式证书文件。

**处理步骤**

1. 确认证书文件为有效的X.509 CA证书，PEM_DER格式支持PEM编码（文本格式）或DER编码（二进制格式）的证书文件，P7B格式支持PKCS#7格式证书文件。
2. 确认`-F`参数指定的格式与证书文件实际格式一致，例如PEM格式证书使用`-F PEM_DER`，PKCS#7格式证书使用`-F P7B`。
3. 使用证书工具（如openssl）校验证书文件是否合法，使用合法的证书文件重新安装。

### CM_CMD_ERR_MAX_CERT_COUNT_REACHED

证书数量达到最大限制，报错提示：`Install failed: Maximum certificate count reached`

**可能原因**

系统中用户CA证书数量已达到上限，无法继续安装。

**处理步骤**

通过系统设置的"证书与凭据"页面卸载不再使用的用户CA证书，释放证书数量配额后重新安装。

### CM_CMD_ERR_DEVICE_ENTER_ADVSECMODE

设备进入高级安全模式，报错提示：`Install failed: Device is in advanced security mode`

**可能原因**

设备已进入高级安全模式，该模式下不允许安装用户CA证书。

**处理步骤**

退出设备的高级安全模式后重新执行安装命令。

### CM_CMD_ERR_PERMISSION_DENIED

设备安全策略限制，报错提示：`The operation does not comply with the device security policy, the device does not allow users to manage the CA certificate of the global user`

**可能原因**

使用`-g`参数安装所有用户级CA证书时，当前用户被设备安全策略禁止管理全局用户CA证书。

**处理步骤**

确认设备安全策略配置是否允许当前用户安装所有用户级CA证书。判定逻辑如下：
- `disableInstallGlobalUserCA_userList`：用户ID列表，以`|`分隔（如`100|101`）。当前用户ID在该列表中则禁止安装。
- `installGlobalUserCA_defaultConfig`：默认策略，取值为`enable`或`disable`。当取值为`disable`时，默认禁止所有用户安装，除非当前用户ID在`enableInstallGlobalUserCA_userList`中。
- `enableInstallGlobalUserCA_userList`：允许安装的用户ID列表，以`|`分隔。仅在`installGlobalUserCA_defaultConfig`为`disable`时生效。

即：当前用户不在`disableInstallGlobalUserCA_userList`中，且当`installGlobalUserCA_defaultConfig`为`disable`时当前用户在`enableInstallGlobalUserCA_userList`中，才允许安装。

### CM_CMD_ERR_INTERNAL_ERROR

Internal error，报错提示：`Install failed: Permission denied`

**可能原因**

当前用户没有调用安装用户CA证书接口的权限，可能由其他模块异常导致。

**处理步骤**

重新执行命令尝试，若多次失败请联系系统管理员排查。

### CM_CMD_ERR_USER_CANCELLED

用户取消认证，报错提示：`User cancelled authentication`或`User cancelled admin authorization`

**可能原因**

在身份认证或管理员授权界面，用户取消了认证操作。

**处理步骤**

重新执行命令，并在认证界面完成身份认证或管理员授权。
