# 文件管理变更说明
## cl.filemanagement.1 沙箱路径`/storage/Users/currentUser/appdata`下无权限目录的stat和access行为变更

**访问级别**

公共能力

**变更原因**

为强化沙箱路径下的安全机制，应用对`/storage/Users/currentUser/appdata`下的目录进行stat和access时，需严格遵循权限管控设计，确保仅可访问有权限的目录及文件。

**变更影响**

此变更不涉及应用适配。

- 变更前：应用对沙箱路径`/storage/Users/currentUser/appdata`下没有权限的目录执行stat和access时，可以成功。

- 变更后：应用对沙箱路径`/storage/Users/currentUser/appdata`下没有权限的目录执行stat和access时，无法成功。

**起始 API Level**

9

**变更发生版本**

从OpenHarmony SDK 7.0.0.32开始。

**变更的接口/组件**

musl/sys/stat.h中stat、fstat、fstat64、fstatat等接口。

musl/unistd.h中access、faccessat等接口。

**适配指导**

排查及适配步骤如下：

1. 检查是否有硬编码访问：`/storage/Users/currentUser/appdata/el2/{本应用包名}/files/`路径。

   适配建议：删除硬编码逻辑，访问本应用路径可以转化为沙箱路径`/data/storage/el2/base/files/`。

2. 检查是否有硬编码访问：`/storage/Users/currentUser/appdata/el2/{其他应用包名}/files/`路径。

   适配建议：
    - 如果其他应用未对本应用授权，先获取授权再进行访问。

    - 如果其他应用已对本应用授权，无需整改。
