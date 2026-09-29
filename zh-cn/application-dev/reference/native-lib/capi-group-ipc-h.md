# group_ipc.h

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @da_wei_li11-->
<!--Designer: @liyiming13-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

## 概述

提供按组标识符组织共享内存和命名信号量的接口，支持多个进程访问同一共享对象及进行同步。这些接口是OpenHarmony扩展接口。

**引用文件：** `<sys/group_ipc.h>`

**库：** libc.so

**系统能力：** SystemCapability.Base

**起始版本：** 26.2.0

**相关模块：** [libc标准库](musl.md)

## 使用说明

四个接口使用相同的路径规则：将`gid`格式化为十进制目录名，去掉`name`的所有前导斜杠后，访问`/dev/group/shm/<gid>/<name>`。例如，`gid`为1001、`name`为`/shared-state`时，实际路径为`/dev/group/shm/1001/shared-state`。

- 调用前，`/dev/group/shm/<gid>`必须已经存在，且调用进程具有所需的目录和文件访问权限。接口不会创建父目录、修改目录的属主或权限，也不会回退到`/dev/shm`。父目录不存在时返回失败，`errno`为`ENOENT`。
- `gid`由业务方约定，用于选择目录。接口不要求它等于调用进程的实际或有效组ID，也不会切换进程身份。相同`gid`不会自动授予访问权限，不同UID也不意味着一定拒绝访问；访问结果由系统权限控制决定。
- 具有访问权限的多个进程使用相同`gid`和`name`，可打开同一个尚未被删除的对象。不同`gid`对应不同路径。共享内存和命名信号量共用该路径空间，应使用不同名称。
- `name`必须是有效的、以空字符结尾的字符串。去掉前导斜杠后的名称长度为1～`NAME_MAX`字节（当前为255），不能是`.`或`..`，也不能含有斜杠。空字符串、全斜杠及包含子路径的名称均不合法。
- 共享内存的数据同步需要配合`MAP_SHARED`映射。并发访问的先后顺序由业务方使用信号量等机制协调。

接口先去掉`name`的前导斜杠，再校验剩余名称的长度。剩余名称超过`NAME_MAX`，或组目录路径解析过程中符号链接展开后的路径超过系统长度限制时，返回失败并设置`errno`为`ENAMETOOLONG`。

## 函数汇总

| 名称 | 描述 |
| --- | --- |
| [group_sem_open](#group_sem_open) | 创建或打开指定`gid`下的命名信号量。 |
| [group_sem_unlink](#group_sem_unlink) | 删除指定`gid`下的命名信号量名称。 |
| [group_shm_open](#group_shm_open) | 创建或打开指定`gid`下的共享内存对象。 |
| [group_shm_unlink](#group_shm_unlink) | 删除指定`gid`下的共享内存对象名称。 |

## 函数说明

### group_sem_open()

```c
sem_t *group_sem_open(const char *name, int flags, gid_t gid, ...);
```

创建或打开命名信号量。除增加`gid`参数及改变访问路径外，使用方式与`sem_open()`相同。返回的句柄可传给`sem_wait()`、`sem_trywait()`、`sem_post()`等接口，并使用`sem_close()`关闭。

**起始版本：** 26.2.0

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `name` | 信号量名称，遵循[使用说明](#使用说明)中的名称规则。 |
| `flags` | 打开标志。`0`表示仅打开已有对象；`O_CREAT`表示不存在时创建；`O_CREAT \| O_EXCL`表示排他创建，对象已存在时失败。`O_EXCL`应与`O_CREAT`配合使用。 |
| `gid` | 用于选择父目录的业务组标识符，取值范围为`gid_t`可表示的值，0合法。目录仍须预先存在。 |
| `...` | 指定`O_CREAT`时，依次传入`mode_t mode`（创建权限参数）和`unsigned int value`（信号量初值参数）。`mode`仅使用`0666`包含的读写权限位，并受进程`umask`影响。`value`范围为0～`SEM_VALUE_MAX`（当前为2147483647）。打开已有对象时不修改其权限或计数值；仅在实际创建对象时读取和校验这两个参数。 |

**返回值：**

成功返回信号量指针；失败返回`SEM_FAILED`并设置`errno`。

**错误码：**

| errno | 原因 | 处理措施 |
| --- | --- | --- |
| EACCES | 缺少访问父目录或信号量对象所需的权限。 | 核查调用进程身份和目录访问权限。创建对象需要父目录的写入和搜索权限；打开已有信号量需要对象的读写权限，必要时由环境管理方调整权限。 |
| EEXIST | 指定`O_CREAT \| O_EXCL`，但对象已存在。 | 确认已有对象是业务约定的信号量且已完成初始化；需要复用时将`flags`设为`0`，需要新建时由业务方协调原对象的清理时机。 |
| EINTR | 打开或创建过程中，底层操作被信号中断并报告此错误。 | 检查信号的处理要求；业务仍需继续时重新调用接口，若信号用于终止任务则结束操作。重试时仍须处理对象已存在的情况。 |
| EINVAL | 名称不合法，或创建时的初值超过`SEM_VALUE_MAX`。 | 按[使用说明](#使用说明)检查`name`；创建时将`value`设为0～`SEM_VALUE_MAX`范围内的值。 |
| EMFILE | 进程的文件描述符或命名信号量引用资源达到上限。 | 关闭不再使用的文件描述符，通过`sem_close()`释放不再使用的命名信号量引用，再重试。 |
| ENAMETOOLONG | 去掉前导斜杠后的名称超过`NAME_MAX`，或底层路径解析后的长度超过系统限制。 | 将去掉前导斜杠后的名称缩短到`NAME_MAX`字节以内；由环境管理方检查组目录及其父路径中的符号链接展开结果。 |
| ENFILE | 系统已打开过多的信号量或文件，无法再分配系统级打开资源。 | 由环境管理方排查系统资源占用，协调相关进程关闭不再使用的信号量引用或文件后重试。 |
| ENOENT | 父目录不存在，或未指定`O_CREAT`且对象不存在。 | 核查`gid`和组目录；目录不存在时由环境管理方准备。仅对象不存在且需要创建时，指定`O_CREAT`并传入`mode`和`value`。 |
| ENOSPC | 没有足够的空间或文件系统资源来创建信号量对象或写入其初始状态。 | 检查组目录所在文件系统的可用空间和索引节点（inode）资源，清理已确认不再使用的对象，或由环境管理方扩充资源后重试。 |

应用应在失败后及时读取并保存`errno`，避免后续调用改写错误信息。示例见[信号量示例](#信号量示例)。

处理`EEXIST`时，清理原对象前应由业务方确认其不再被使用，并协调所有参与进程的生命周期。直接删除其他进程仍在使用的对象名称后重新创建，会使已有句柄与新句柄指向不同对象。

### group_sem_unlink()

```c
int group_sem_unlink(const char *name, gid_t gid);
```

删除命名信号量的名称，不删除其父目录。名称删除后，其他进程不能再按该名称打开原对象；已经打开的信号量仍然有效，直至对应引用通过`sem_close()`关闭。使用同一名称重新创建的信号量是一个新对象。

**起始版本：** 26.2.0

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `name` | 要删除的信号量名称，遵循[使用说明](#使用说明)中的名称规则。 |
| `gid` | 对象所在目录的业务组标识符，与创建或打开时使用的`gid`一致。 |

**返回值：**

成功返回0；失败返回-1并设置`errno`。

**错误码：**

| errno | 原因 | 处理措施 |
| --- | --- | --- |
| EACCES | 没有删除指定对象名称所需的权限，例如缺少父目录的写入或搜索权限。 | 核查调用进程身份和父目录权限，由环境管理方处理权限问题；对象本身的读写权限不能单独决定是否允许删除。 |
| EINVAL | 名称不合法。 | 按[使用说明](#使用说明)检查`name`，使用与创建对象时对应的合法名称。 |
| ENAMETOOLONG | 去掉前导斜杠后的名称超过`NAME_MAX`，或底层路径解析后的长度超过系统限制。 | 核对创建时使用的名称，确保去掉前导斜杠后的长度不超过`NAME_MAX`字节；由环境管理方检查父路径中的符号链接展开结果。 |
| ENOENT | 父目录或指定名称的对象不存在。 | 核查`gid`、名称和父目录；若业务仅要求名称已不存在，可将该结果视为清理完成。 |

应用应在失败后及时读取并保存`errno`。示例见[信号量示例](#信号量示例)。

### group_shm_open()

```c
int group_shm_open(const char *name, int flag, mode_t mode, gid_t gid);
```

创建或打开共享内存对象，返回文件描述符。新建对象的初始长度为0，应先使用`ftruncate()`设置长度，再使用`mmap()`建立映射。文件描述符使用`close()`关闭，映射使用`munmap()`解除。

**起始版本：** 26.2.0

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `name` | 共享内存对象名称，遵循[使用说明](#使用说明)中的名称规则。 |
| `flag` | 访问模式为`O_RDONLY`或`O_RDWR`，可按需组合`O_CREAT`、`O_EXCL`和`O_TRUNC`。`O_CREAT`在对象不存在时创建；`O_CREAT \| O_EXCL`在对象已存在时失败；`O_TRUNC`将对象长度截断为0，建议与`O_RDWR`一起使用。 |
| `mode` | 创建权限参数，常用值为`0600`（仅属主读写）或`0660`（属主和属组读写），受进程`umask`影响。打开已有对象时不改变其权限。该参数必须传入，不创建对象时可传0。 |
| `gid` | 用于选择父目录的业务组标识符，取值范围为`gid_t`可表示的值，0合法。目录仍须预先存在。 |

接口在打开时附加`O_NOFOLLOW`、`O_CLOEXEC`和`O_NONBLOCK`标志，分别用于拒绝跟随最终路径分量的符号链接、在执行新程序时关闭文件描述符，以及以非阻塞方式打开。

**返回值：**

成功返回非负文件描述符；失败返回-1并设置`errno`。

**错误码：**

| errno | 原因 | 处理措施 |
| --- | --- | --- |
| EACCES | 缺少访问父目录、打开或创建对象所需的权限，或指定`O_TRUNC`但没有对象的写权限。 | 核查调用进程身份、目录权限和对象权限。创建对象需要父目录的写入和搜索权限；打开已有对象需要与`O_RDONLY`或`O_RDWR`对应的访问权限，截断对象还需要写权限。 |
| EEXIST | 指定`O_CREAT \| O_EXCL`，但对象已存在。 | 确认已有对象的类型、数据格式和初始化状态；需要复用时按访问需求使用`O_RDONLY`或`O_RDWR`打开，保留数据时不要指定`O_TRUNC`。需要新建时按[group_sem_open()](#group_sem_open)中的清理原则协调原对象的生命周期。 |
| EINTR | 打开或创建过程中，底层操作被信号中断并报告此错误。 | 检查信号的处理要求；业务仍需继续时重新调用接口，若信号用于终止任务则结束操作。重试时仍须处理对象已存在的情况。 |
| EINVAL | 名称不合法。 | 按[使用说明](#使用说明)检查`name`，修正空名称、`.`、`..`或包含子路径的名称。 |
| EMFILE | 进程的文件描述符数量达到上限。 | 关闭进程不再使用的文件描述符，检查文件描述符泄漏及进程资源限制后重试。 |
| ENAMETOOLONG | 去掉前导斜杠后的名称超过`NAME_MAX`，或底层路径解析后的长度超过系统限制。 | 将去掉前导斜杠后的名称缩短到`NAME_MAX`字节以内；由环境管理方检查组目录及其父路径中的符号链接展开结果。 |
| ENFILE | 系统已打开过多的共享内存对象或文件，无法再分配系统级打开资源。 | 由环境管理方排查系统文件资源占用，协调相关进程关闭不再使用的文件描述符后重试。 |
| ENOENT | 父目录不存在，或未指定`O_CREAT`且对象不存在。 | 核查`gid`和组目录；目录不存在时由环境管理方准备。仅对象不存在且需要创建时，指定`O_CREAT`并设置创建权限。 |
| ENOSPC | 没有足够的空间或文件系统资源来创建共享内存对象。 | 检查组目录所在文件系统的可用空间和索引节点（inode）资源，清理已确认不再使用的对象，或由环境管理方扩充资源后重试。 |

应用应在失败后及时读取并保存`errno`。后续`ftruncate()`和`mmap()`调用失败时，应分别按相应接口的错误码处理。示例见[共享内存示例](#共享内存示例)。

### group_shm_unlink()

```c
int group_shm_unlink(const char *name, gid_t gid);
```

删除共享内存对象的名称，不删除其父目录。已经打开的文件描述符和映射仍然有效；名称被删除且所有引用释放后，对象资源被回收。以同一名称重新创建的对象与旧对象相互独立。

**起始版本：** 26.2.0

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `name` | 要删除的共享内存对象名称，遵循[使用说明](#使用说明)中的名称规则。 |
| `gid` | 对象所在目录的业务组标识符，与创建或打开时使用的`gid`一致。 |

**返回值：**

成功返回0；失败返回-1并设置`errno`。

**错误码：**

| errno | 原因 | 处理措施 |
| --- | --- | --- |
| EACCES | 没有删除指定对象名称所需的权限，例如缺少父目录的写入或搜索权限。 | 核查调用进程身份和父目录权限，由环境管理方处理权限问题；对象本身的读写权限不能单独决定是否允许删除。 |
| EINVAL | 名称不合法。 | 按[使用说明](#使用说明)检查`name`，使用与创建对象时对应的合法名称。 |
| ENAMETOOLONG | 去掉前导斜杠后的名称超过`NAME_MAX`，或底层路径解析后的长度超过系统限制。 | 核对创建时使用的名称，确保去掉前导斜杠后的长度不超过`NAME_MAX`字节；由环境管理方检查父路径中的符号链接展开结果。 |
| ENOENT | 父目录或指定名称的对象不存在。 | 核查`gid`、名称和父目录；若业务仅要求名称已不存在，可将该结果视为清理完成。 |

应用应在失败后及时读取并保存`errno`。示例见[共享内存示例](#共享内存示例)。

## 示例

以下两个示例分别展示创建或打开、操作、关闭和删除名称的完整生命周期。运行前，由具备相应权限的环境管理方准备`/dev/group/shm/1001`，并授予调用进程所需的访问权限；接口不会代建目录。示例中的`gid`仅为业务约定值。

示例使用排他创建，若同名对象已存在则报告错误，不覆盖已有对象。跨进程使用时，各进程应约定相同的`gid`、名称和共享数据格式，并由业务方协调初始化完成时机及最终删除对象名称的时机。

### 信号量示例

```c
#include <fcntl.h>
#include <stdio.h>
#include <sys/group_ipc.h>

int main(void)
{
    const gid_t gid = 1001;
    const char *name = "/example-ready";
    int result = 0;
    sem_t *sem = group_sem_open(name, O_CREAT | O_EXCL, gid, (mode_t)0660, 0U);
    if (sem == SEM_FAILED) {
        perror("group_sem_open");
        return 1;
    }
    if (sem_post(sem) == -1 || sem_wait(sem) == -1) {
        perror("sem_post/sem_wait");
        result = 1;
    }
    if (sem_close(sem) == -1) {
        perror("sem_close");
        result = 1;
    }
    if (group_sem_unlink(name, gid) == -1) {
        perror("group_sem_unlink");
        result = 1;
    }
    return result;
}
```

### 共享内存示例

```c
#include <fcntl.h>
#include <stdio.h>
#include <sys/group_ipc.h>
#include <unistd.h>

int main(void)
{
    const gid_t gid = 1001;
    const char *name = "/example-state";
    int result = 1;
    int *state;
    int fd = group_shm_open(name, O_CREAT | O_EXCL | O_RDWR, 0660, gid);
    if (fd == -1) {
        perror("group_shm_open");
        return 1;
    }
    if (ftruncate(fd, sizeof(*state)) == -1) {
        perror("ftruncate");
        goto cleanup;
    }
    state = mmap(NULL, sizeof(*state), PROT_READ | PROT_WRITE, MAP_SHARED, fd, 0);
    if (state == MAP_FAILED) {
        perror("mmap");
        goto cleanup;
    }
    *state = 42;
    result = 0;
    if (munmap(state, sizeof(*state)) == -1) {
        perror("munmap");
        result = 1;
    }
cleanup:
    if (close(fd) == -1) {
        perror("close");
        result = 1;
    }
    if (group_shm_unlink(name, gid) == -1) {
        perror("group_shm_unlink");
        result = 1;
    }
    return result;
}
```
