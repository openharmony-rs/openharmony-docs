# musl 26.1.0 新增接口

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @da_wei_li11-->
<!--Designer: @liyiming13-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

## 概述

OpenHarmony采用musl作为C标准库。musl是一个轻量、快速、简单、免费的开源libc库，详细介绍参考[musl官方参考手册](https://musl.libc.org/manual.html)。

本文档描述musl在API版本26.1.0新增的接口。除特别说明外，本文接口的公共信息如下。

**库：** libc.so

**系统能力：** SystemCapability.Base

**起始版本：** 26.1.0

**相关模块：** [libc标准库](musl.md)

## group_sem_open

`group_sem_open`是OpenHarmony扩展接口，用于创建或打开指定`gid`下的命名信号量。详细介绍参考[group_ipc.h](capi-group-ipc-h.md)。

## group_sem_unlink

`group_sem_unlink`是OpenHarmony扩展接口，用于删除指定`gid`下的命名信号量名称。详细介绍参考[group_ipc.h](capi-group-ipc-h.md)。

## group_shm_open

`group_shm_open`是OpenHarmony扩展接口，用于创建或打开指定`gid`下的共享内存对象。详细介绍参考[group_ipc.h](capi-group-ipc-h.md)。

## group_shm_unlink

`group_shm_unlink`是OpenHarmony扩展接口，用于删除指定`gid`下的共享内存对象名称。详细介绍参考[group_ipc.h](capi-group-ipc-h.md)。

## close_range

`close_range`用于关闭指定区间内的所有已打开文件描述符，可能会受seccomp策略拦截。

**引用文件：** `<unistd.h>`（需定义`_GNU_SOURCE`）

**函数原型：**

```c
int close_range(unsigned int first, unsigned int last, int flags);
```

接口关闭区间`[first, last]`内的所有已打开文件描述符。

若内核支持`close_range`系统调用，接口直接委托该系统调用执行。仅当内核不支持`close_range`（返回`ENOSYS`）时，才回退为通过`close`系统调用逐个关闭文件描述符的循环；其他内核错误直接返回并设置`errno`。在回退路径中，`flags`必须为0，非零值将被拒绝并返回`EINVAL`。回退路径的循环上界由`getdtablesize()`获取的进程文件描述符表大小决定。

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `first` | 待关闭文件描述符范围的起始值（含）。 |
| `last` | 待关闭文件描述符范围的结束值（含）。 |
| `flags` | 控制关闭行为的标志位。内核支持`close_range`系统调用时，可为0或内核支持的标志位组合，例如`CLOSE_RANGE_CLOEXEC`（为文件描述符设置close-on-exec标志而非关闭），`CLOSE_RANGE_UNSHARE`（鸿蒙内核暂不支持）。这些常量不由musl头文件提供，可使用目标内核的`<linux/close_range.h>`或由调用方自行定义。回退路径下必须为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 成功时返回0；失败时返回-1，并设置`errno`指示错误。 |

**错误码：**

| 错误码 | 原因 | 处理措施 |
| --- | --- | --- |
| EINVAL | `flags`非法，或`first`大于`last`；回退路径下`flags`必须为0。 | 检查范围参数和`flags`；需要兼容不支持`close_range`的内核时，将`flags`设为0。 |
| EMFILE | 使用`CLOSE_RANGE_UNSHARE`时，打开的文件描述符数超过`/proc/sys/fs/nr_open`限制。 | 调整限制，或避免使用`CLOSE_RANGE_UNSHARE`（鸿蒙内核暂不支持）。 |
| ENOMEM | 使用`CLOSE_RANGE_UNSHARE`时内核内存不足。 | 稍后重试，或避免使用`CLOSE_RANGE_UNSHARE`（鸿蒙内核暂不支持）。 |

`EMFILE`和`ENOMEM`仅在传入`CLOSE_RANGE_UNSHARE`时可能出现。内核支持`close_range`时，其他错误会通过`errno`原样返回，具体取决于目标内核实现。

**安全属性：**

| 线程安全 | 异步信号安全 |
| --- | --- |
| MT-Safe | AS-Safe |

**示例：**

```c
#define _GNU_SOURCE
#include <unistd.h>
#include <stdio.h>

int main(void)
{
    /* 参数需谨慎设置，避免关闭系统重要文件导致异常 */
    if (close_range(100, ~0U, 0) < 0) {
        perror("close_range");
        return 1;
    }
    return 0;
}
```

## closefrom

`closefrom`用于关闭大于或等于指定值的所有已打开文件描述符，可能会受seccomp策略拦截。

**引用文件：** `<unistd.h>`（需定义`_GNU_SOURCE`）

**函数原型：**

```c
void closefrom(int lowfd);
```

接口关闭所有大于或等于`lowfd`的已打开文件描述符。若`lowfd`为负数，按0处理。

接口首先尝试调用内核`close_range`系统调用，范围为`[max(lowfd, 0), UINT_MAX]`且不带标志位。调用成功时立即返回；仅当内核不支持`close_range`（返回`ENOSYS`）时，才回退为通过`close`系统调用逐个关闭文件描述符的循环。其他内核错误直接返回并设置`errno`，不进入回退路径。回退路径的循环上界由`getdtablesize()`获取的进程文件描述符表大小决定。

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `lowfd` | 起始文件描述符值，关闭所有大于或等于该值的已打开文件描述符。为负数时按0处理。 |

**错误码：**

| 错误码 | 原因 | 处理措施 |
| --- | --- | --- |
| EINVAL | `flags`非法，或`first`大于`last`。 | 检查参数；`closefrom`正常调用不会触发。 |
| EMFILE | 使用`CLOSE_RANGE_UNSHARE`时，打开的文件描述符数超过`/proc/sys/fs/nr_open`限制。 | `closefrom`不使用该标志；直接调用`close_range`时需调整限制。 |
| ENOMEM | 使用`CLOSE_RANGE_UNSHARE`时内核内存不足。 | `closefrom`不使用该标志；直接调用`close_range`时稍后重试。 |

上述错误码继承自内核`close_range`系统调用的`errno`。`closefrom`以`flags=0`和有效区间调用，通常不会触发这些参数类错误；回退路径会忽略逐个`close`的错误。具体错误码取决于目标内核实现。

**安全属性：**

| 线程安全 | 异步信号安全 |
| --- | --- |
| MT-Safe | AS-Safe |

**示例：**

```c
#define _GNU_SOURCE
#include <unistd.h>
#include <stdio.h>

int main(void)
{
    /* 参数需谨慎设置，避免关闭系统重要文件导致异常 */
    closefrom(100);
    return 0;
}
```

## group_member

`group_member`用于检查调用进程是否属于指定组。

**引用文件：** `<unistd.h>`（需定义`_GNU_SOURCE`）

**函数原型：**

```c
int group_member(gid_t gid);
```

接口检查`gid`是否与调用进程的任一附加组ID（由`getgroups()`返回）匹配。匹配过程使用栈上分配的数组保存附加组列表，避免多次`alloca`导致的栈累积

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `gid` | 待检查的组ID，用于与调用进程的附加组ID列表进行匹配。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 若调用进程属于`gid`标识的组，返回1；否则返回0。 |

**错误码：**

| 错误码 | 原因 | 处理措施 |
| --- | --- | --- |
| EFAULT | `getgroups()`的`list`地址无效。 | `group_member`使用栈上有效缓冲区，通常不会触发；若发生，接口返回0，`errno`可能被设置。 |
| EINVAL | `getgroups()`的`size`小于附加组数量且不为0。 | `group_member`先查询数量再分配缓冲区，通常不会触发；若发生，接口返回0，`errno`可能被设置。 |

上述错误码继承自内核`getgroups`系统调用的`errno`，具体取决于目标内核实现。

**安全属性：**

| 线程安全 | 异步信号安全 |
| --- | --- |
| MT-Safe | AS-Unsafe（使用变长数组，请勿在信号处理函数中调用） |

**示例：**

```c
#define _GNU_SOURCE
#include <unistd.h>
#include <stdio.h>

int main(void)
{
    gid_t gid = 1000;

    if (group_member(gid)) {
        printf("Process is a member of group %u\n", gid);
    } else {
        printf("Process is NOT a member of group %u\n", gid);
    }
    return 0;
}
```

## __getpagesize

`__getpagesize`用于获取系统内存页大小，单位为字节。

**引用文件：** `<unistd.h>`

**函数原型：**

```c
int __getpagesize(void);
```

页大小通过`PAGE_SIZE`宏获取。在架构头文件预定义了`PAGE_SIZE`的架构上，它是编译时常量；否则`PAGE_SIZE`定义为`libc.page_size`，是C库初始化期间设置的运行时值。应用应优先调用`getpagesize()`；对可移植性有要求时可使用`sysconf(_SC_PAGESIZE)`。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回系统页大小，单位为字节。 |

**安全属性：**

| 线程安全 | 异步信号安全 |
| --- | --- |
| MT-Safe | AS-Safe |

**示例：**

```c
#include <unistd.h>
#include <stdio.h>

int main(void)
{
    int ps = __getpagesize();
    printf("Page size: %d bytes\n", ps);
    return 0;
}
```

## __openat64_2

`__openat64_2`是`openat64()`三参数形式的FORTIFY运行时入口，用于在编译时缺少`mode`参数的情况下提供运行时检查。

**引用文件：** `<fcntl.h>`

**函数原型：**

```c
#define _GNU_SOURCE
#include <fcntl.h>

int __openat64_2(int fd, const char *pathname, int flags);
```

当`openat64()`以`fd`、`pathname`、`flags`三个参数调用且未提供`mode`参数时，编译器生成的FORTIFY内联代码会调用此接口。该接口检查`flags`是否包含`O_CREAT`或`O_TMPFILE`：

- 若包含其中任一标志，底层`openat64()`要求提供`mode`参数。此时接口通过`__fortify_error()`输出诊断信息（指示参数过少），并调用`abort()`终止进程。
- 若两个标志均未设置，接口以`mode`为0调用真正的`openat64()`并返回其结果。在32位架构上，调用前会强制置位`O_LARGEFILE`标志。

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `fd` | 目录文件描述符，若为`AT_FDCWD`则相对于当前工作目录。 |
| `pathname` | 待打开文件的路径。 |
| `flags` | 文件打开标志。若包含`O_CREAT`或`O_TMPFILE`，则要求提供`mode`参数，否则触发`__fortify_error()`终止进程。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 成功时返回新的文件描述符。若`flags`要求`mode`参数（设置了`O_CREAT`或`O_TMPFILE`），接口不返回，进程被终止。底层`openat64()`调用失败时返回-1，并设置`errno`指示错误。 |

**错误码：**

当`flags`中包含`O_CREAT`或`O_TMPFILE`但未提供`mode`参数时，接口通过`__fortify_error()`终止进程。底层`openat64()`系统调用的错误会通过`errno`原样传递，具体错误码取决于目标内核实现。

**安全属性：**

| 线程安全 | 异步信号安全 |
| --- | --- |
| MT-Safe | AS-Safe（触发`__fortify_error()`时除外） |

> **说明：**
>
> 该接口属于FORTIFY源码加固机制，应用请勿直接调用。启用FORTIFY并包含`<fcntl.h>`时，编译器会自动插入对此接口的调用。开发者应使用标准的`openat()`或`openat64()`，因此本文不提供直接调用`__openat64_2()`的示例。

## getprotoent_r

`getprotoent_r`是`getprotoent`的可重入版本，用于顺序枚举协议数据库条目。

**引用文件：** `<netdb.h>`

**函数原型：**

```c
#include <netdb.h>

int getprotoent_r(struct protoent *res, char *buf, size_t buflen,
                  struct protoent **result);
```

接口每次调用返回一个协议条目，并将结果填入调用者提供的`res`指向的`struct protoent`结构体。协议数据库是编译时硬编码在C库中的常量数组，运行时不读取任何文件，包含`ip`、`icmp`、`tcp`、`udp`等知名协议条目。

调用者须提供长度为`buflen`字节的缓冲区`buf`。接口将协议名和别名指针数组拷贝到该缓冲区，`res`的各字段被设置为指向`buf`内部；成功时`*result`被设置为`res`。

枚举使用共享的内部游标跟踪当前位置。`_r`变体之间的并发调用由内部锁串行化；非可重入的`getprotoent()`、`setprotoent()`和`endprotoent()`不获取该锁，不具备线程安全性。调用`setprotoent()`或`endprotoent()`会将游标重置为0，同时重置`getprotoent_r()`的枚举位置。

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `res` | 调用者提供的`struct protoent`结构体指针，用于存储结果。 |
| `buf` | 调用者提供的缓冲区，用于存放协议名和别名指针数组。 |
| `buflen` | 缓冲区`buf`的字节长度。 |
| `result` | 输出参数，成功时指向`res`；失败或枚举完毕时为`NULL`。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 成功时返回0，并将`*result`设置为`res`；所有条目枚举完毕后返回`ENOENT`，并将`*result`设置为`NULL`；缓冲区过小时返回`ERANGE`，并将`*result`设置为`NULL`，此时游标不前进，调用者应使用更大的缓冲区重试。 |

**错误码：**

| 错误码 | 原因 | 处理措施 |
| --- | --- | --- |
| ENOENT | 所有协议条目已枚举完毕，或数据库为空。 | 根据需要调用`setprotoent()`重置枚举位置，或结束遍历。 |
| ERANGE | 提供的缓冲区`buf`过小，无法容纳结果。 | 增大`buflen`后重试；游标不前进，可读取同一条目。 |

接口通过返回值返回上述错误码，不设置`errno`。

**安全属性：**

| 线程安全 | 异步信号安全 |
| --- | --- |
| MT-Safe（仅`_r`变体之间串行化） | AS-Unsafe（请勿在信号处理函数中调用） |

> **说明：**
>
> 严禁将`getprotoent()`、`setprotoent()`、`endprotoent()`与`getprotoent_r()`混用，否则会因共享状态未同步访问而导致不可预测的结果。

**示例：**

```c
#include <netdb.h>
#include <stdio.h>

int main(void)
{
    struct protoent pe;
    struct protoent *result;
    char buf[1024];
    int rv;

    while ((rv = getprotoent_r(&pe, buf, sizeof(buf), &result)) == 0) {
        if (result)
            printf("protocol: %s, number: %d\n",
                   result->p_name, result->p_proto);
    }
    return 0;
}
```

## getprotobyname_r

`getprotobyname_r`是`getprotobyname`的可重入版本，用于按协议名称查询协议数据库条目。

**引用文件：** `<netdb.h>`

**函数原型：**

```c
#include <netdb.h>

int getprotobyname_r(const char *name, struct protoent *res,
                     char *buf, size_t buflen, struct protoent **result);
```

接口查找协议名与`name`匹配的条目，并将结果存入调用者提供的`res`指向的`struct protoent`结构体。匹配区分大小写，仅匹配协议官方名称，不支持别名。

协议数据库是编译时硬编码在C库中的常量数组，运行时不读取任何文件。调用者须提供长度为`buflen`字节的缓冲区`buf`，接口将协议名和别名指针数组拷贝到该缓冲区，`res`的各字段被设置为指向`buf`内部；成功时`*result`被设置为`res`。

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `name` | 待查找的协议名称。不能为`NULL`。 |
| `res` | 调用者提供的`struct protoent`结构体指针，用于存储结果。 |
| `buf` | 调用者提供的缓冲区，用于存放协议名和别名指针数组。 |
| `buflen` | 缓冲区`buf`的字节长度。 |
| `result` | 输出参数，成功时指向`res`；失败时为`NULL`。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 成功时返回0，并将`*result`设置为`res`；未找到协议名时返回`ENOENT`，并将`*result`设置为`NULL`；`name`为`NULL`时返回`EINVAL`，并将`*result`设置为`NULL`；缓冲区过小时返回`ERANGE`，并将`*result`设置为`NULL`。 |

**错误码：**

| 错误码 | 原因 | 处理措施 |
| --- | --- | --- |
| ENOENT | 协议数据库中未找到指定的协议名称。 | 检查协议名称是否为官方名称，且大小写匹配。 |
| EINVAL | `name`为`NULL`。 | 传入有效的协议名称。 |
| ERANGE | 提供的缓冲区`buf`过小，无法容纳结果。 | 增大`buflen`后重试。 |

接口通过返回值返回上述错误码，不设置`errno`。

**安全属性：**

| 线程安全 | 异步信号安全 |
| --- | --- |
| MT-Safe | AS-Unsafe（请勿在信号处理函数中调用） |

**示例：**

```c
#include <netdb.h>
#include <stdio.h>
#include <errno.h>

int main(void)
{
    struct protoent pe;
    struct protoent *result;
    char buf[1024];

    int rv = getprotobyname_r("tcp", &pe, buf, sizeof(buf), &result);
    if (rv == 0 && result) {
        printf("protocol: %s, number: %d\n",
               result->p_name, result->p_proto);
    } else if (rv == ENOENT) {
        printf("protocol not found\n");
    } else {
        printf("error: %d\n", rv);
    }
    return 0;
}
```

## getprotobynumber_r

`getprotobynumber_r`是`getprotobynumber`的可重入版本，用于按协议编号查询协议数据库条目。

**引用文件：** `<netdb.h>`

**函数原型：**

```c
#include <netdb.h>

int getprotobynumber_r(int proto, struct protoent *res,
                       char *buf, size_t buflen, struct protoent **result);
```

接口查找协议编号与`proto`匹配的条目，并将结果存入调用者提供的`res`指向的`struct protoent`结构体。协议数据库是编译时硬编码在C库中的常量数组，运行时不读取任何文件。

调用者须提供长度为`buflen`字节的缓冲区`buf`，接口将协议名和别名指针数组拷贝到该缓冲区，`res`的各字段被设置为指向`buf`内部；成功时`*result`被设置为`res`。

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `proto` | 待查找的协议编号。 |
| `res` | 调用者提供的`struct protoent`结构体指针，用于存储结果。 |
| `buf` | 调用者提供的缓冲区，用于存放协议名和别名指针数组。 |
| `buflen` | 缓冲区`buf`的字节长度。 |
| `result` | 输出参数，成功时指向`res`；失败时为`NULL`。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 成功时返回0，并将`*result`设置为`res`；未找到协议编号时返回`ENOENT`，并将`*result`设置为`NULL`；缓冲区过小时返回`ERANGE`，并将`*result`设置为`NULL`。 |

**错误码：**

| 错误码 | 原因 | 处理措施 |
| --- | --- | --- |
| ENOENT | 协议数据库中未找到指定的协议编号。 | 检查协议编号是否正确。 |
| ERANGE | 提供的缓冲区`buf`过小，无法容纳结果。 | 增大`buflen`后重试。 |

接口通过返回值返回上述错误码，不设置`errno`。

**安全属性：**

| 线程安全 | 异步信号安全 |
| --- | --- |
| MT-Safe | AS-Unsafe（请勿在信号处理函数中调用） |

**示例：**

```c
#include <netdb.h>
#include <stdio.h>
#include <errno.h>

int main(void)
{
    struct protoent pe;
    struct protoent *result;
    char buf[1024];

    int rv = getprotobynumber_r(6, &pe, buf, sizeof(buf), &result);
    if (rv == 0 && result) {
        printf("protocol: %s, number: %d\n",
               result->p_name, result->p_proto);
    } else if (rv == ENOENT) {
        printf("protocol not found\n");
    } else {
        printf("error: %d\n", rv);
    }
    return 0;
}
```

## getservent_r

`getservent_r`是`getservent`的可重入版本，用于顺序枚举服务数据库条目。

**引用文件：** `<netdb.h>`

**函数原型：**

```c
#define _GNU_SOURCE
#include <netdb.h>

int getservent_r(struct servent *se, char *buf, size_t buflen,
                 struct servent **result);
```

接口每次调用返回一个服务条目，并将结果填入调用者提供的`se`指向的`struct servent`结构体。服务数据库在运行时从文件`/etc/services`读取：首次调用或内部文件指针尚未打开时，接口打开该文件进行读取。

调用者须提供长度为`buflen`字节的缓冲区`buf`。接口将服务名、协议和别名指针数组拷贝到该缓冲区，`se`的各字段被设置为指向`buf`内部；成功时`*result`被设置为`se`。

枚举过程中跳过以`#`开头的行、空行、无法解析的行、协议非`tcp`/`udp`的行，以及端口号超出1～65535范围的行。`_r`变体之间的并发调用由内部锁串行化；非可重入的`getservent()`、`setservent()`和`endservent()`不获取该锁。`setservent()`可回卷或重新打开文件，并重置`getservent_r()`的枚举位置。

> **说明：**
>
> 实际读取能力仅在编译libc时定义了`__LITEOS_A__`的平台提供。其他平台上该接口为桩函数，返回0并将`*result`设置为`NULL`。

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `se` | 调用者提供的`struct servent`结构体指针，用于存储结果。 |
| `buf` | 调用者提供的缓冲区，用于存放服务名、协议和别名指针数组。 |
| `buflen` | 缓冲区`buf`的字节长度。 |
| `result` | 输出参数，成功时指向`se`；失败或枚举完毕时为`NULL`。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 成功时返回0，并将`*result`设置为`se`；未定义`__LITEOS_A__`的平台上返回0并将`*result`设置为`NULL`；所有条目枚举完毕或无法打开服务文件时返回`ENOENT`，并将`*result`设置为`NULL`；缓冲区过小时返回`ERANGE`，并将`*result`设置为`NULL`；内部数据结构内存分配失败时返回`ENOMEM`；流读取错误时返回底层`errno`（如`EIO`、`EBADF`）。以上失败情况均将`*result`设置为`NULL`。 |

**错误码：**

| 错误码 | 原因 | 处理措施 |
| --- | --- | --- |
| ENOENT | 所有服务条目已枚举完毕，或设备上不存在`/etc/services`。 | 确认服务数据库文件是否存在，或结束遍历。 |
| ERANGE | 提供的缓冲区`buf`过小，无法容纳结果。 | 增大`buflen`后重试。 |
| ESPIPE | `ERANGE`重试期间文件位置无法保存或恢复，无法重新读取当前条目。 | 重新调用`setservent()`后从头遍历，或增大缓冲区避免重试。 |
| ENOMEM | 内部数据结构内存分配失败。 | 释放不再使用的资源后重试。 |
| 底层`errno`（如`EIO`、`EBADF`） | 读取`/etc/services`时发生流错误，`ferror`为真。 | 检查流状态和底层文件；必要时通过`clearerr()`清理状态后重试。 |

**安全属性：**

| 线程安全 | 异步信号安全 |
| --- | --- |
| MT-Safe（仅`_r`变体之间串行化） | AS-Unsafe（请勿在信号处理函数中调用） |

> **说明：**
>
> 严禁将`getservent()`、`setservent()`、`endservent()`与`getservent_r()`混用，否则会因共享状态未同步访问而导致不可预测的结果。

**示例：**

```c
#define _GNU_SOURCE
#include <netdb.h>
#include <stdio.h>
#include <arpa/inet.h>

int main(void)
{
    struct servent se;
    struct servent *result;
    char buf[1024];
    int rv;

    while ((rv = getservent_r(&se, buf, sizeof(buf), &result)) == 0 && result != NULL) {
        printf("service: %s, port: %d, proto: %s\n",
               result->s_name, ntohs(result->s_port),
               result->s_proto);
    }
    return 0;
}
```

## getgrent_r

`getgrent_r`是`getgrent`的可重入版本，用于顺序枚举组数据库条目。

**引用文件：** `<grp.h>`

**函数原型：**

```c
#include <grp.h>

int getgrent_r(struct group *gr, char *buf, size_t size, struct group **res);
```

接口每次调用返回一个组条目，并将结果填入调用者提供的`gr`指向的`struct group`结构体。组数据库在运行时从文件`/etc/group`读取：首次调用或内部文件指针尚未打开时，接口打开该文件进行读取。

调用者须提供长度为`size`字节的缓冲区`buf`，且缓冲区须同时容纳行数据和成员指针数组。接口将解析的行内容和成员指针数组拷贝到该缓冲区，`gr`的字符串字段（`gr_name`、`gr_passwd`）和成员数组（`gr_mem`）被调整为指向`buf`内部；成功时`*res`被设置为`gr`。

该接口与非可重入的`getgrent()`共享内部文件游标，`_r`变体之间的并发调用由内部锁串行化。`setgrent()`关闭共享文件指针，使后续`getgrent_r()`调用从头重新打开文件；`endgrent()`是`setgrent()`的弱别名，效果相同。

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `gr` | 调用者提供的`struct group`结构体指针，用于存储结果。 |
| `buf` | 调用者提供的缓冲区，用于存放行数据和成员指针数组。 |
| `size` | 缓冲区`buf`的字节长度。 |
| `res` | 输出参数，成功时指向`gr`；失败时为`NULL`。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 成功时返回0，并将`*res`设置为`gr`；到达组文件末尾或无法打开`/etc/group`时返回`ENOENT`，并将`*res`设置为`NULL`；缓冲区过小时返回`ERANGE`，并将`*res`设置为`NULL`；成员指针数组或读取流所需内存分配失败时返回`ENOMEM`；流读取错误时返回底层`errno`（如`EIO`、`EBADF`）。以上失败情况均将`*res`设置为`NULL`。 |

**错误码：**

| 错误码 | 原因 | 处理措施 |
| --- | --- | --- |
| ENOENT | 已到达`/etc/group`末尾，或无法打开`/etc/group`。 | 确认组数据库文件存在，或结束遍历。 |
| ERANGE | 提供的缓冲区`buf`过小，无法容纳行数据和成员指针数组。 | 增大`size`后重试。 |
| ESPIPE | `ERANGE`重试期间文件位置无法保存或恢复，无法重新读取当前条目。 | 重新调用`setgrent()`后从头遍历，或增大缓冲区避免重试。 |
| ENOMEM | 成员指针数组或读取流所需内存分配失败。 | 释放不再使用的资源后重试。 |
| 底层`errno`（如`EIO`、`EBADF`） | 读取`/etc/group`时发生流错误，`ferror`为真。 | 检查流状态和底层文件；必要时通过`clearerr()`清理状态后重试。 |

**安全属性：**

| 线程安全 | 异步信号安全 |
| --- | --- |
| MT-Safe（仅`_r`变体之间串行化） | AS-Unsafe（请勿在信号处理函数中调用） |

> **说明：**
>
> 严禁将`getgrent()`、`getgrgid()`、`getgrnam()`、`setgrent()`与`getgrent_r()`混用，否则会因共享状态未同步访问而导致不可预测的结果。

**示例：**

```c
#include <grp.h>
#include <stdio.h>

int main(void)
{
    struct group gr;
    struct group *res;
    char buf[1024];
    int rv;

    while ((rv = getgrent_r(&gr, buf, sizeof(buf), &res)) == 0) {
        if (res)
            printf("group: %s, gid: %d\n",
                   res->gr_name, res->gr_gid);
    }
    return 0;
}
```

## getpwent_r

`getpwent_r`是`getpwent`的可重入版本，用于顺序枚举密码数据库（passwd）条目。

**引用文件：** `<pwd.h>`

**函数原型：**

```c
#include <pwd.h>

int getpwent_r(struct passwd *pw, char *buf, size_t size, struct passwd **res);
```

接口每次调用返回一个密码数据库条目，并将结果填入调用者提供的`pw`指向的`struct passwd`结构体。密码数据库在运行时从文件`/etc/passwd`读取：首次调用或内部文件指针尚未打开时，接口打开该文件进行读取。

调用者须提供长度为`size`字节的缓冲区`buf`。接口将解析的行内容拷贝到该缓冲区，`pw`的字符串字段（`pw_name`、`pw_passwd`、`pw_gecos`、`pw_dir`、`pw_shell`）被调整为指向`buf`内部；成功时`*res`被设置为`pw`。

该接口与非可重入的`getpwent()`共享内部文件游标，`_r`变体之间的并发调用由内部锁串行化。`setpwent()`关闭共享文件指针，使后续`getpwent_r()`调用从头重新打开文件；`endpwent()`是`setpwent()`的弱别名，效果相同。

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `pw` | 调用者提供的`struct passwd`结构体指针，用于存储结果。 |
| `buf` | 调用者提供的缓冲区，用于存放解析的行内容。 |
| `size` | 缓冲区`buf`的字节长度。 |
| `res` | 输出参数，成功时指向`pw`；失败时为`NULL`。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 成功时返回0，并将`*res`设置为`pw`；到达`/etc/passwd`末尾或无法打开`/etc/passwd`时返回`ENOENT`，并将`*res`设置为`NULL`；缓冲区过小时返回`ERANGE`，并将`*res`设置为`NULL`；读取流所需内存分配失败时返回`ENOMEM`；流读取错误时返回底层`errno`（如`EIO`、`EBADF`）。以上失败情况均将`*res`设置为`NULL`。 |

**错误码：**

| 错误码 | 原因 | 处理措施 |
| --- | --- | --- |
| ENOENT | 已到达`/etc/passwd`末尾，或无法打开`/etc/passwd`。 | 确认`/etc/passwd`文件存在，或结束遍历。 |
| ERANGE | 提供的缓冲区`buf`过小，无法容纳结果。 | 增大`size`后重试。 |
| ESPIPE | `ERANGE`重试期间文件位置无法保存或恢复，无法重新读取当前条目。 | 重新调用`setpwent()`后从头遍历，或增大缓冲区避免重试。 |
| ENOMEM | 读取流所需内存分配失败。 | 释放不再使用的资源后重试。 |
| 底层`errno`（如`EIO`、`EBADF`） | 读取`/etc/passwd`时发生流错误，`ferror`为真。 | 检查流状态和底层文件；必要时通过`clearerr()`清理状态后重试。 |

**安全属性：**

| 线程安全 | 异步信号安全 |
| --- | --- |
| MT-Safe（仅`_r`变体之间串行化） | AS-Unsafe（请勿在信号处理函数中调用） |

> **说明：**
>
> 严禁将`getpwent()`、`getpwuid()`、`getpwnam()`、`setpwent()`与`getpwent_r()`混用，否则会因共享状态未同步访问而导致不可预测的结果。

**示例：**

```c
#include <pwd.h>
#include <stdio.h>

int main(void)
{
    struct passwd pw;
    struct passwd *res;
    char buf[1024];
    int rv;

    while ((rv = getpwent_r(&pw, buf, sizeof(buf), &res)) == 0) {
        if (res)
            printf("user: %s, uid: %d, home: %s\n",
                   res->pw_name, res->pw_uid, res->pw_dir);
    }
    return 0;
}
```

## fgetpwent_r

`fgetpwent_r`是`fgetpwent`的可重入版本，用于从指定文件流读取密码数据库条目。

**引用文件：** `<pwd.h>`、`<stdio.h>`（需定义`_GNU_SOURCE`）

**函数原型：**

```c
#define _GNU_SOURCE
#include <pwd.h>
#include <stdio.h>

int fgetpwent_r(FILE *f, struct passwd *pw, char *buf, size_t size,
                struct passwd **res);
```

接口从调用者提供的流`f`中读取下一个密码数据库条目，并将结果存入调用者提供的`pw`指向的`struct passwd`结构体。

与`getpwent_r()`不同，该接口不使用共享的系统密码数据库游标，而是直接从调用者提供的`FILE`流中读取，调用者可控制读取的文件及读取位置，因此适合从任意来源读取`/etc/passwd`格式数据。流中每行应遵循`/etc/passwd`文件格式，包含用户名、密码占位符、UID、GID、GECOS字段、主目录和登录shell，字段之间以冒号分隔。

调用者须提供长度为`size`字节的缓冲区`buf`。接口将解析的行内容拷贝到该缓冲区，`pw`的字符串字段被调整为指向`buf`内部；成功时`*res`被设置为`pw`。该接口不使用内部锁或共享游标，调用者负责确保同一`FILE`流不被多个线程并发访问。

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `f` | 调用者提供的`FILE`流指针，从中读取密码数据库条目。 |
| `pw` | 调用者提供的`struct passwd`结构体指针，用于存储结果。 |
| `buf` | 调用者提供的缓冲区，用于存放解析的行内容。 |
| `size` | 缓冲区`buf`的字节长度。 |
| `res` | 输出参数，成功时指向`pw`；到达流末尾时为`NULL`。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 成功时返回0，并将`*res`设置为`pw`；到达流末尾时返回`ENOENT`，并将`*res`设置为`NULL`；缓冲区过小时返回`ERANGE`，并将`*res`设置为`NULL`；读取流所需内存分配失败时返回`ENOMEM`；流读取错误时返回底层`errno`（如`EIO`、`EBADF`）。以上失败情况均将`*res`设置为`NULL`。 |

**错误码：**

| 错误码 | 原因 | 处理措施 |
| --- | --- | --- |
| ENOENT | 已到达流末尾。 | 结束遍历，或确认流中是否还有数据。 |
| ERANGE | 提供的缓冲区`buf`过小，无法容纳结果。该条目已被消费。 | 增大`size`后从下一条目继续读取；无法重试当前条目。 |
| ENOMEM | 读取流所需内存分配失败。 | 释放不再使用的资源后重试。 |
| 底层`errno`（如`EIO`、`EBADF`） | 读取流时发生流错误，`ferror(f)`为真。 | 检查流状态和底层文件；必要时通过`clearerr()`清理状态后重试。 |

**安全属性：**

| 线程安全 | 异步信号安全 |
| --- | --- |
| MT-Safe（不得并发访问同一`FILE`流） | AS-Unsafe（请勿在信号处理函数中调用） |

**示例：**

```c
#define _GNU_SOURCE
#include <pwd.h>
#include <stdio.h>

int main(void)
{
    FILE *f = fopen("/etc/passwd", "r");
    if (!f) return 1;

    struct passwd pw;
    struct passwd *res;
    char buf[1024];
    int rv;

    while ((rv = fgetpwent_r(f, &pw, buf, sizeof(buf), &res)) == 0) {
        if (res)
            printf("user: %s, uid: %d, shell: %s\n",
                   res->pw_name, res->pw_uid, res->pw_shell);
    }
    fclose(f);
    return 0;
}
```

## pthread_sigqueue

`pthread_sigqueue`用于向指定线程发送携带附加数据的排队信号。

**引用文件：** `<signal.h>`

**函数原型：**

```c
#include <signal.h>

int pthread_sigqueue(pthread_t t, int sig, const union sigval value);
```

接口向线程`t`发送信号`sig`，并携带`value`中的数据。接口构造`siginfo_t`结构体：`si_code`设为`SI_QUEUE`，`si_pid`设为调用者的进程ID，`si_uid`设为调用者的用户ID，`si_value`设为提供的`value`。随后通过`rt_tgsigqueueinfo`系统调用将信号投递到指定线程。

以下信号保留供C库内部使用，不得通过此接口发送，否则返回`EINVAL`：

- `SIGCANCEL`：用于线程取消。
- `SIGTIMER`：用于定时器投递。
- `SIGSYNCCALL`：用于同步跨线程调用。

若目标线程已退出或从未完全初始化（内部线程ID为0），接口不进行系统调用，直接返回`ESRCH`。目标架构不提供`SYS_rt_tgsigqueueinfo`系统调用时，接口返回`ENOSYS`。

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `t` | 目标线程标识符。 |
| `sig` | 待发送的信号编号。不能为内部保留信号（`SIGCANCEL`、`SIGTIMER`、`SIGSYNCCALL`）。 |
| `value` | 随信号携带的数据，类型为`union sigval`。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 成功时返回0；失败时返回正的`errno`值指示错误，不设置`errno`。 |

**错误码：**

| 错误码 | 原因 | 处理措施 |
| --- | --- | --- |
| EINVAL | `sig`是内部保留信号（`SIGCANCEL`、`SIGTIMER`或`SIGSYNCCALL`），或不是有效的信号编号。 | 使用应用可发送的信号编号。 |
| ESRCH | 目标线程`t`已退出或未初始化。 | 确认目标线程仍然存活。 |
| EPERM | 调用者无权向目标线程发送信号。 | 检查调用进程的权限。 |
| ENOSYS | 目标架构不支持`SYS_rt_tgsigqueueinfo`系统调用。 | 改用其他线程间通知机制。 |

内核`rt_tgsigqueueinfo`系统调用返回的错误会以正值原样返回，具体错误码取决于目标内核实现。

**安全属性：**

| 线程安全 | 异步信号安全 |
| --- | --- |
| MT-Safe | AS-Unsafe（请勿在信号处理函数中调用） |

**示例：**

```c
#include <signal.h>
#include <stdio.h>
#include <pthread.h>
#include <unistd.h>

#define SIG_TEST (SIGRTMIN + 12) 

static volatile sig_atomic_t received_value;

static void handler(int sig, siginfo_t *si, void *ctx)
{
    (void)sig;
    (void)ctx;
    if (si->si_code == SI_QUEUE) {
        received_value = si->si_value.sival_int;
    }
}

static void *worker(void *arg)
{
    sleep(2);
    return NULL;
}

int main(void)
{
    struct sigaction sa = {0};
    sa.sa_sigaction = handler;
    sa.sa_flags = SA_SIGINFO;
    sigaction(SIG_TEST, &sa, NULL);

    pthread_t t;
    pthread_create(&t, NULL, worker, NULL);

    union sigval val;
    val.sival_int = 42;
    int rv = pthread_sigqueue(t, SIG_TEST, val);
    if (rv != 0) {
        printf("pthread_sigqueue failed: %d\n", rv);
    }

    pthread_join(t, NULL);
    if (rv == 0) {
        printf("received queued signal, value: %d\n", received_value);
    }
    return 0;
}
```

## __libc_single_threaded

`__libc_single_threaded`是全局标志变量，用于指示进程当前是否以单线程模式运行。

**引用文件：** `<sys/single_threaded.h>`

**变量声明：**

```c
#include <sys/single_threaded.h>

extern char __libc_single_threaded;
```

该变量在进程启动时初始化为1，表示进程为单线程。当通过`pthread_create()`创建第一个线程时，C库将其设置为0，表示进程已转为多线程。该赋值是普通的`char`赋值，不使用原子指令或内存屏障；一旦翻转为0，在进程剩余生命周期内不再恢复为1。

应用可在运行时读取该变量以执行单线程优化：进程保持单线程期间，可跳过对仅从单线程访问的数据结构的加锁。任意时刻读到1即可保证没有额外线程已被或正在创建；读到0后，进程在剩余生命周期内必须按多线程处理。

**示例：**

```c
#include <pthread.h>
#include <sys/single_threaded.h>
#include <stdio.h>

static pthread_mutex_t lock = PTHREAD_MUTEX_INITIALIZER;
static int counter = 0;

void increment(void)
{
    if (!__libc_single_threaded) {
        pthread_mutex_lock(&lock);
    }
    counter++;
    if (!__libc_single_threaded) {
        pthread_mutex_unlock(&lock);
    }
}

int main(void)
{
    printf("Single-threaded at start: %d\n", __libc_single_threaded);
    increment();
    return 0;
}
```

## __libc_stack_end

`__libc_stack_end`是全局指针变量，用于近似指向进程栈顶（最高地址）。

**引用文件：** 无公共头文件声明，需由使用者自行以`extern`声明

**变量声明：**

```c
extern void *__libc_stack_end;
```

变量近似指向进程栈的最高地址。动态链接程序由动态链接器根据初始栈指针设置，静态链接程序由`__libc_start_main()`根据启动时的栈帧设置。该值并非精确栈顶，在进程启动期间设置后，在整个进程生命周期内保持常量。

该变量用于与glibc ABI兼容。第三方库和工具（如性能分析器、回溯工具）可引用该变量以近似主线程栈的范围；C库本身不读取此变量。

**安全属性：**

| 线程安全 | 异步信号安全 |
| --- | --- |
| MT-Safe（初始化后只读） | AS-Safe（读取） |

**示例：**

```c
#include <stdio.h>

extern void *__libc_stack_end;

int main(void)
{
    int local;
    printf("Stack end: %p\n", __libc_stack_end);
    printf("Stack frame: %p\n", (void *)&local);
    return 0;
}
```

## C23整数转换接口通用说明

本节适用于`__isoc23_strtol`、`__isoc23_strtoul`、`__isoc23_strtoll`、`__isoc23_strtoull`、`__isoc23_strtoimax`、`__isoc23_strtoumax`、`__isoc23_wcstol`、`__isoc23_wcstoul`、`__isoc23_wcstoll`、`__isoc23_wcstoull`，以及带区域设置参数的`__isoc23_strtoll_l`、`__isoc23_strtoull_l`。

### 解析规则

各接口先跳过前导空白字符（宽字符接口跳过前导空白宽字符），再读取可选的正号或负号，并按`base`指定的进制转换数字。遇到第一个不属于该进制的字符时停止转换。

| 进制 | 解析规则 |
| --- | --- |
| 0 | `0x`或`0X`后紧跟十六进制数字时按十六进制解析；`0b`或`0B`后紧跟二进制数字时按二进制解析；其他以0开头的输入按八进制解析；其余按十进制解析。 |
| 2 | 按二进制解析；带`0b`或`0B`前缀且前缀后紧跟二进制数字时，按该前缀解析。 |
| 16 | 按十六进制解析，允许带`0x`或`0X`前缀，但前缀后必须紧跟十六进制数字。 |
| 其余2～36范围内的值 | 按指定进制解析，字母`a`～`z`和`A`～`Z`表示数值10～35。 |

不完整的前缀不等同于“未转换任何数字”。例如，`base`为0或2时转换`"0b"`，开头的0会被转换并返回0，结束位置指向`'b'`；`base`为0或16时转换`"0x"`，开头的0会被转换，结束位置指向`'x'`。这些情况不会因此设置`EINVAL`。

若业务要求整个输入都是整数，应在检查`errno`的同时，确认`*endptr`不等于`nptr`，且已指向字符串终止符。

### 无符号转换的负号

无符号转换也接受负号。数字部分未超出类型范围时，结果按无符号算术规则取负。例如，转换`"-1"`可得到对应无符号类型的最大值，不会仅因负号而报告溢出。需要拒绝负数时，应额外校验输入。

### 特性宏与名称重定向

包含对应头文件后即可直接调用`__isoc23_*`接口，不需要定义`_OHOS_ISOC23_CONVERSION_SOURCE`。

若希望通过普通函数名（如`strtol()`）使用C23行为，应在包含任何头文件之前定义`_OHOS_ISOC23_CONVERSION_SOURCE`，或在编译时传入`-D_OHOS_ISOC23_CONVERSION_SOURCE=1`。只要定义该宏（即使值为0），就会启用重定向；如需保留普通函数名的原有行为，请不要定义该宏。

单独定义`_GNU_SOURCE`、`_ALL_SOURCE`、`_ISOC23_SOURCE`或`_ISOC2X_SOURCE`，或者仅选择C2x/C23编译模式，都不会自动启用上述重定向。该特性宏仅选择对应的转换接口，不表示已支持全部C23标准库能力。`__isoc23_*`是本实现提供的ABI入口，ISO C标准规定的是对应的不带前缀的接口。

### 带区域设置参数的转换接口

`__isoc23_strtoll_l`和`__isoc23_strtoull_l`的声明需要`_GNU_SOURCE`。当前实现忽略区域设置参数`loc`，转换结果、结束位置和`errno`均与对应的不带`_l`接口相同。传入`newlocale()`创建的对象、`LC_GLOBAL_LOCALE`或`NULL`均可；对`NULL`和`LC_GLOBAL_LOCALE`的接受是本实现的行为，不能推广为其他C库中`_l`接口的通用规则。

在C代码中同时定义`_GNU_SOURCE`和`_OHOS_ISOC23_CONVERSION_SOURCE`，可使`strtoll_l()`、`strtoull_l()`调用重定向到对应的`__isoc23_*`接口；C++不启用该普通名称的重定向，应直接使用`__isoc23_*`接口。

### 安全属性

| 线程安全 | 异步信号安全 |
| --- | --- |
| MT-Safe | AS-Unsafe（请勿在信号处理函数中调用） |

并发调用使用独立的解析状态和线程局部`errno`；调用者应避免并发修改共享的输入字符串或`endptr`存储空间。

成功转换不清除已有的`errno`，调用前应将其设为0，调用后及时检查；返回0或边界值本身不能单独证明发生了错误。

## __isoc23_strtol

`__isoc23_strtol`用于将字符串开头的数字部分转换为`long`类型整数，支持C23规定的`0b`和`0B`二进制前缀。

**引用文件：** `<stdlib.h>`

**函数原型：**

```c
#include <stdlib.h>

long __isoc23_strtol(const char *restrict nptr,
    char **restrict endptr, int base);
```

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `nptr` | 指向有效、以`'\0'`结尾的输入字符串。不能传入空指针或未正确终止的字符数组。 |
| `endptr` | 用于接收第一个未转换字符的位置；若未转换任何数字，则接收原始输入`nptr`。可传入`NULL`，表示不保存位置。 |
| `base` | 进制，为0或2～36。0表示按前缀自动判断，具体见[解析规则](#解析规则)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 成功时返回转换得到的`long`值。数学结果超出`long`范围时，根据结果的符号返回`LONG_MIN`或`LONG_MAX`，并设置`errno`为`ERANGE`。没有可转换的数字时返回0并设置`errno`为`EINVAL`；若`endptr`有效，则`*endptr`为`nptr`。 |

**错误码：**

| 错误码 | 原因 | 处理措施 |
| --- | --- | --- |
| EINVAL | `base`既不是0，也不在2～36范围内；或跳过前导空白和可选符号后，没有可转换的数字。 | 检查进制和输入，并通过`endptr`确认是否完成转换。 |
| ERANGE | 带符号的数学结果超出`long`可表示范围。 | 按返回的边界值处理范围错误，必要时选择可表示更大范围的整数类型。 |

**示例：**

```c
#include <errno.h>
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
    char *end = NULL;
    errno = 0;
    long value = __isoc23_strtol("-0b101tail", &end, 0);
    int ok = errno == 0 && value == -5 && *end == 't';
    if (!ok) {
        return 1;
    }
    printf("value=%ld rest=%s\n", value, end);
    return 0;
}
```

预期输出：

```text
value=-5 rest=tail
```

## __isoc23_strtoul

`__isoc23_strtoul`用于将字符串开头的数字部分转换为`unsigned long`类型整数，支持C23规定的`0b`和`0B`二进制前缀。

**引用文件：** `<stdlib.h>`

**函数原型：**

```c
#include <stdlib.h>

unsigned long __isoc23_strtoul(const char *restrict nptr,
    char **restrict endptr, int base);
```

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `nptr` | 指向有效、以`'\0'`结尾的输入字符串。不能传入空指针或未正确终止的字符数组。 |
| `endptr` | 用于接收第一个未转换字符的位置；若未转换任何数字，则接收原始输入`nptr`。可传入`NULL`，表示不保存位置。 |
| `base` | 进制，为0或2～36。0表示按前缀自动判断，具体见[解析规则](#解析规则)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| unsigned long | 成功时返回转换得到的`unsigned long`值。数字部分的大小超过`ULONG_MAX`时返回`ULONG_MAX`，并设置`errno`为`ERANGE`。没有可转换的数字时返回0并设置`errno`为`EINVAL`；若`endptr`有效，则`*endptr`为`nptr`。 |

**错误码：**

| 错误码 | 原因 | 处理措施 |
| --- | --- | --- |
| EINVAL | `base`既不是0，也不在2～36范围内；或跳过前导空白和可选符号后，没有可转换的数字。 | 检查进制和输入，并通过`endptr`确认是否完成转换。 |
| ERANGE | 数字部分的大小超过`ULONG_MAX`。 | 按返回的边界值处理范围错误，必要时选择可表示更大范围的整数类型。 |

**示例：**

```c
#include <errno.h>
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
    char *end = NULL;
    errno = 0;
    unsigned long value = __isoc23_strtoul("0B101tail", &end, 0);
    int ok = errno == 0 && value == 5 && *end == 't';
    if (!ok) {
        return 1;
    }
    printf("value=%lu rest=%s\n", value, end);
    return 0;
}
```

预期输出：

```text
value=5 rest=tail
```

## __isoc23_strtoll

`__isoc23_strtoll`用于将字符串开头的数字部分转换为`long long`类型整数，支持C23规定的`0b`和`0B`二进制前缀。

**引用文件：** `<stdlib.h>`

**函数原型：**

```c
#include <stdlib.h>

long long __isoc23_strtoll(const char *restrict nptr,
    char **restrict endptr, int base);
```

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `nptr` | 指向有效、以`'\0'`结尾的输入字符串。不能传入空指针或未正确终止的字符数组。 |
| `endptr` | 用于接收第一个未转换字符的位置；若未转换任何数字，则接收原始输入`nptr`。可传入`NULL`，表示不保存位置。 |
| `base` | 进制，为0或2～36。0表示按前缀自动判断，具体见[解析规则](#解析规则)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long long | 成功时返回转换得到的`long long`值。数学结果超出`long long`范围时，根据结果的符号返回`LLONG_MIN`或`LLONG_MAX`，并设置`errno`为`ERANGE`。没有可转换的数字时返回0并设置`errno`为`EINVAL`；若`endptr`有效，则`*endptr`为`nptr`。 |

**错误码：**

| 错误码 | 原因 | 处理措施 |
| --- | --- | --- |
| EINVAL | `base`既不是0，也不在2～36范围内；或跳过前导空白和可选符号后，没有可转换的数字。 | 检查进制和输入，并通过`endptr`确认是否完成转换。 |
| ERANGE | 带符号的数学结果超出`long long`可表示范围。 | 按返回的边界值处理范围错误，必要时选择可表示更大范围的整数类型。 |

**示例：**

```c
#include <errno.h>
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
    char *end = NULL;
    errno = 0;
    long long value = __isoc23_strtoll("-0b101tail", &end, 0);
    int ok = errno == 0 && value == -5 && *end == 't';
    if (!ok) {
        return 1;
    }
    printf("value=%lld rest=%s\n", value, end);
    return 0;
}
```

预期输出：

```text
value=-5 rest=tail
```

## __isoc23_strtoull

`__isoc23_strtoull`用于将字符串开头的数字部分转换为`unsigned long long`类型整数，支持C23规定的`0b`和`0B`二进制前缀。

**引用文件：** `<stdlib.h>`

**函数原型：**

```c
#include <stdlib.h>

unsigned long long __isoc23_strtoull(const char *restrict nptr,
    char **restrict endptr, int base);
```

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `nptr` | 指向有效、以`'\0'`结尾的输入字符串。不能传入空指针或未正确终止的字符数组。 |
| `endptr` | 用于接收第一个未转换字符的位置；若未转换任何数字，则接收原始输入`nptr`。可传入`NULL`，表示不保存位置。 |
| `base` | 进制，为0或2～36。0表示按前缀自动判断，具体见[解析规则](#解析规则)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| unsigned long long | 成功时返回转换得到的`unsigned long long`值。数字部分的大小超过`ULLONG_MAX`时返回`ULLONG_MAX`，并设置`errno`为`ERANGE`。没有可转换的数字时返回0并设置`errno`为`EINVAL`；若`endptr`有效，则`*endptr`为`nptr`。 |

**错误码：**

| 错误码 | 原因 | 处理措施 |
| --- | --- | --- |
| EINVAL | `base`既不是0，也不在2～36范围内；或跳过前导空白和可选符号后，没有可转换的数字。 | 检查进制和输入，并通过`endptr`确认是否完成转换。 |
| ERANGE | 数字部分的大小超过`ULLONG_MAX`。 | 按返回的边界值处理范围错误，必要时选择可表示更大范围的整数类型。 |

**示例：**

```c
#include <errno.h>
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
    char *end = NULL;
    errno = 0;
    unsigned long long value = __isoc23_strtoull("0B101tail", &end, 0);
    int ok = errno == 0 && value == 5 && *end == 't';
    if (!ok) {
        return 1;
    }
    printf("value=%llu rest=%s\n", value, end);
    return 0;
}
```

预期输出：

```text
value=5 rest=tail
```

## __isoc23_strtoimax

`__isoc23_strtoimax`用于将字符串开头的数字部分转换为`intmax_t`类型整数，支持C23规定的`0b`和`0B`二进制前缀。

**引用文件：** `<inttypes.h>`

**函数原型：**

```c
#include <inttypes.h>

intmax_t __isoc23_strtoimax(const char *restrict nptr,
    char **restrict endptr, int base);
```

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `nptr` | 指向有效、以`'\0'`结尾的输入字符串。不能传入空指针或未正确终止的字符数组。 |
| `endptr` | 用于接收第一个未转换字符的位置；若未转换任何数字，则接收原始输入`nptr`。可传入`NULL`，表示不保存位置。 |
| `base` | 进制，为0或2～36。0表示按前缀自动判断，具体见[解析规则](#解析规则)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| intmax_t | 成功时返回转换得到的`intmax_t`值。数学结果超出`intmax_t`范围时，根据结果的符号返回`INTMAX_MIN`或`INTMAX_MAX`，并设置`errno`为`ERANGE`。没有可转换的数字时返回0并设置`errno`为`EINVAL`；若`endptr`有效，则`*endptr`为`nptr`。 |

**错误码：**

| 错误码 | 原因 | 处理措施 |
| --- | --- | --- |
| EINVAL | `base`既不是0，也不在2～36范围内；或跳过前导空白和可选符号后，没有可转换的数字。 | 检查进制和输入，并通过`endptr`确认是否完成转换。 |
| ERANGE | 带符号的数学结果超出`intmax_t`可表示范围。 | 按返回的边界值处理范围错误，必要时选择可表示更大范围的整数类型。 |

**示例：**

```c
#include <errno.h>
#include <stdio.h>
#include <inttypes.h>

int main(void)
{
    char *end = NULL;
    errno = 0;
    intmax_t value = __isoc23_strtoimax("-0b101tail", &end, 0);
    int ok = errno == 0 && value == -5 && *end == 't';
    if (!ok) {
        return 1;
    }
    printf("value=%" PRIdMAX " rest=%s\n", value, end);
    return 0;
}
```

预期输出：

```text
value=-5 rest=tail
```

## __isoc23_strtoumax

`__isoc23_strtoumax`用于将字符串开头的数字部分转换为`uintmax_t`类型整数，支持C23规定的`0b`和`0B`二进制前缀。

**引用文件：** `<inttypes.h>`

**函数原型：**

```c
#include <inttypes.h>

uintmax_t __isoc23_strtoumax(const char *restrict nptr,
    char **restrict endptr, int base);
```

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `nptr` | 指向有效、以`'\0'`结尾的输入字符串。不能传入空指针或未正确终止的字符数组。 |
| `endptr` | 用于接收第一个未转换字符的位置；若未转换任何数字，则接收原始输入`nptr`。可传入`NULL`，表示不保存位置。 |
| `base` | 进制，为0或2～36。0表示按前缀自动判断，具体见[解析规则](#解析规则)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| uintmax_t | 成功时返回转换得到的`uintmax_t`值。数字部分的大小超过`UINTMAX_MAX`时返回`UINTMAX_MAX`，并设置`errno`为`ERANGE`。没有可转换的数字时返回0并设置`errno`为`EINVAL`；若`endptr`有效，则`*endptr`为`nptr`。 |

**错误码：**

| 错误码 | 原因 | 处理措施 |
| --- | --- | --- |
| EINVAL | `base`既不是0，也不在2～36范围内；或跳过前导空白和可选符号后，没有可转换的数字。 | 检查进制和输入，并通过`endptr`确认是否完成转换。 |
| ERANGE | 数字部分的大小超过`UINTMAX_MAX`。 | 按返回的边界值处理范围错误，必要时选择可表示更大范围的整数类型。 |

**示例：**

```c
#include <errno.h>
#include <stdio.h>
#include <inttypes.h>

int main(void)
{
    char *end = NULL;
    errno = 0;
    uintmax_t value = __isoc23_strtoumax("0B101tail", &end, 0);
    int ok = errno == 0 && value == 5 && *end == 't';
    if (!ok) {
        return 1;
    }
    printf("value=%" PRIuMAX " rest=%s\n", value, end);
    return 0;
}
```

预期输出：

```text
value=5 rest=tail
```

## __isoc23_wcstol

`__isoc23_wcstol`用于将宽字符串开头的数字部分转换为`long`类型整数，支持C23规定的`0b`和`0B`二进制前缀。

**引用文件：** `<wchar.h>`

**函数原型：**

```c
#include <wchar.h>

long __isoc23_wcstol(const wchar_t *restrict nptr,
    wchar_t **restrict endptr, int base);
```

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `nptr` | 指向有效、以`L'\0'`结尾的输入宽字符串。不能传入空指针或未正确终止的字符数组。 |
| `endptr` | 用于接收第一个未转换宽字符的位置；若未转换任何数字，则接收原始输入`nptr`。可传入`NULL`，表示不保存位置。 |
| `base` | 进制，为0或2～36。0表示按前缀自动判断，具体见[解析规则](#解析规则)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 成功时返回转换得到的`long`值。数学结果超出`long`范围时，根据结果的符号返回`LONG_MIN`或`LONG_MAX`，并设置`errno`为`ERANGE`。没有可转换的数字时返回0并设置`errno`为`EINVAL`；若`endptr`有效，则`*endptr`为`nptr`。 |

**错误码：**

| 错误码 | 原因 | 处理措施 |
| --- | --- | --- |
| EINVAL | `base`既不是0，也不在2～36范围内；或跳过前导空白和可选符号后，没有可转换的数字。 | 检查进制和输入，并通过`endptr`确认是否完成转换。 |
| ERANGE | 带符号的数学结果超出`long`可表示范围。 | 按返回的边界值处理范围错误，必要时选择可表示更大范围的整数类型。 |

**示例：**

```c
#include <errno.h>
#include <stdio.h>
#include <wchar.h>

int main(void)
{
    wchar_t *end = NULL;
    errno = 0;
    long value = __isoc23_wcstol(L"-0b101tail", &end, 0);
    int ok = errno == 0 && value == -5 && *end == L't';
    if (!ok) {
        return 1;
    }
    printf("value=%ld rest=%ls\n", value, end);
    return 0;
}
```

预期输出：

```text
value=-5 rest=tail
```

## __isoc23_wcstoul

`__isoc23_wcstoul`用于将宽字符串开头的数字部分转换为`unsigned long`类型整数，支持C23规定的`0b`和`0B`二进制前缀。

**引用文件：** `<wchar.h>`

**函数原型：**

```c
#include <wchar.h>

unsigned long __isoc23_wcstoul(const wchar_t *restrict nptr,
    wchar_t **restrict endptr, int base);
```

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `nptr` | 指向有效、以`L'\0'`结尾的输入宽字符串。不能传入空指针或未正确终止的字符数组。 |
| `endptr` | 用于接收第一个未转换宽字符的位置；若未转换任何数字，则接收原始输入`nptr`。可传入`NULL`，表示不保存位置。 |
| `base` | 进制，为0或2～36。0表示按前缀自动判断，具体见[解析规则](#解析规则)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| unsigned long | 成功时返回转换得到的`unsigned long`值。数字部分的大小超过`ULONG_MAX`时返回`ULONG_MAX`，并设置`errno`为`ERANGE`。没有可转换的数字时返回0并设置`errno`为`EINVAL`；若`endptr`有效，则`*endptr`为`nptr`。 |

**错误码：**

| 错误码 | 原因 | 处理措施 |
| --- | --- | --- |
| EINVAL | `base`既不是0，也不在2～36范围内；或跳过前导空白和可选符号后，没有可转换的数字。 | 检查进制和输入，并通过`endptr`确认是否完成转换。 |
| ERANGE | 数字部分的大小超过`ULONG_MAX`。 | 按返回的边界值处理范围错误，必要时选择可表示更大范围的整数类型。 |

**示例：**

```c
#include <errno.h>
#include <stdio.h>
#include <wchar.h>

int main(void)
{
    wchar_t *end = NULL;
    errno = 0;
    unsigned long value = __isoc23_wcstoul(L"0B101tail", &end, 0);
    int ok = errno == 0 && value == 5 && *end == L't';
    if (!ok) {
        return 1;
    }
    printf("value=%lu rest=%ls\n", value, end);
    return 0;
}
```

预期输出：

```text
value=5 rest=tail
```

## __isoc23_wcstoll

`__isoc23_wcstoll`用于将宽字符串开头的数字部分转换为`long long`类型整数，支持C23规定的`0b`和`0B`二进制前缀。

**引用文件：** `<wchar.h>`

**函数原型：**

```c
#include <wchar.h>

long long __isoc23_wcstoll(const wchar_t *restrict nptr,
    wchar_t **restrict endptr, int base);
```

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `nptr` | 指向有效、以`L'\0'`结尾的输入宽字符串。不能传入空指针或未正确终止的字符数组。 |
| `endptr` | 用于接收第一个未转换宽字符的位置；若未转换任何数字，则接收原始输入`nptr`。可传入`NULL`，表示不保存位置。 |
| `base` | 进制，为0或2～36。0表示按前缀自动判断，具体见[解析规则](#解析规则)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long long | 成功时返回转换得到的`long long`值。数学结果超出`long long`范围时，根据结果的符号返回`LLONG_MIN`或`LLONG_MAX`，并设置`errno`为`ERANGE`。没有可转换的数字时返回0并设置`errno`为`EINVAL`；若`endptr`有效，则`*endptr`为`nptr`。 |

**错误码：**

| 错误码 | 原因 | 处理措施 |
| --- | --- | --- |
| EINVAL | `base`既不是0，也不在2～36范围内；或跳过前导空白和可选符号后，没有可转换的数字。 | 检查进制和输入，并通过`endptr`确认是否完成转换。 |
| ERANGE | 带符号的数学结果超出`long long`可表示范围。 | 按返回的边界值处理范围错误，必要时选择可表示更大范围的整数类型。 |

**示例：**

```c
#include <errno.h>
#include <stdio.h>
#include <wchar.h>

int main(void)
{
    wchar_t *end = NULL;
    errno = 0;
    long long value = __isoc23_wcstoll(L"-0b101tail", &end, 0);
    int ok = errno == 0 && value == -5 && *end == L't';
    if (!ok) {
        return 1;
    }
    printf("value=%lld rest=%ls\n", value, end);
    return 0;
}
```

预期输出：

```text
value=-5 rest=tail
```

## __isoc23_wcstoull

`__isoc23_wcstoull`用于将宽字符串开头的数字部分转换为`unsigned long long`类型整数，支持C23规定的`0b`和`0B`二进制前缀。

**引用文件：** `<wchar.h>`

**函数原型：**

```c
#include <wchar.h>

unsigned long long __isoc23_wcstoull(const wchar_t *restrict nptr,
    wchar_t **restrict endptr, int base);
```

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `nptr` | 指向有效、以`L'\0'`结尾的输入宽字符串。不能传入空指针或未正确终止的字符数组。 |
| `endptr` | 用于接收第一个未转换宽字符的位置；若未转换任何数字，则接收原始输入`nptr`。可传入`NULL`，表示不保存位置。 |
| `base` | 进制，为0或2～36。0表示按前缀自动判断，具体见[解析规则](#解析规则)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| unsigned long long | 成功时返回转换得到的`unsigned long long`值。数字部分的大小超过`ULLONG_MAX`时返回`ULLONG_MAX`，并设置`errno`为`ERANGE`。没有可转换的数字时返回0并设置`errno`为`EINVAL`；若`endptr`有效，则`*endptr`为`nptr`。 |

**错误码：**

| 错误码 | 原因 | 处理措施 |
| --- | --- | --- |
| EINVAL | `base`既不是0，也不在2～36范围内；或跳过前导空白和可选符号后，没有可转换的数字。 | 检查进制和输入，并通过`endptr`确认是否完成转换。 |
| ERANGE | 数字部分的大小超过`ULLONG_MAX`。 | 按返回的边界值处理范围错误，必要时选择可表示更大范围的整数类型。 |

**示例：**

```c
#include <errno.h>
#include <stdio.h>
#include <wchar.h>

int main(void)
{
    wchar_t *end = NULL;
    errno = 0;
    unsigned long long value = __isoc23_wcstoull(L"0B101tail", &end, 0);
    int ok = errno == 0 && value == 5 && *end == L't';
    if (!ok) {
        return 1;
    }
    printf("value=%llu rest=%ls\n", value, end);
    return 0;
}
```

预期输出：

```text
value=5 rest=tail
```

## __isoc23_strtoll_l

`__isoc23_strtoll_l`用于将字符串开头的数字部分转换为`long long`类型整数，支持C23规定的`0b`和`0B`二进制前缀。当前实现忽略区域设置参数`loc`。

**引用文件：** `<stdlib.h>`、`<locale.h>`

**函数原型：**

```c
#define _GNU_SOURCE
#include <stdlib.h>
#include <locale.h>

long long __isoc23_strtoll_l(const char *restrict nptr,
    char **restrict endptr, int base, locale_t loc);
```

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `nptr` | 指向有效、以`'\0'`结尾的输入字符串。不能传入空指针或未正确终止的字符数组。 |
| `endptr` | 用于接收第一个未转换字符的位置；若未转换任何数字，则接收原始输入`nptr`。可传入`NULL`，表示不保存位置。 |
| `base` | 进制，为0或2～36。0表示按前缀自动判断，具体见[解析规则](#解析规则)。 |
| `loc` | 区域设置对象，当前实现忽略此参数。对象的创建和释放由调用者负责，具体见[带区域设置参数的转换接口](#带区域设置参数的转换接口)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long long | 成功时返回转换得到的`long long`值。数学结果超出`long long`范围时，根据结果的符号返回`LLONG_MIN`或`LLONG_MAX`，并设置`errno`为`ERANGE`。没有可转换的数字时返回0并设置`errno`为`EINVAL`；若`endptr`有效，则`*endptr`为`nptr`。 |

**错误码：**

| 错误码 | 原因 | 处理措施 |
| --- | --- | --- |
| EINVAL | `base`既不是0，也不在2～36范围内；或跳过前导空白和可选符号后，没有可转换的数字。 | 检查进制和输入，并通过`endptr`确认是否完成转换。 |
| ERANGE | 带符号的数学结果超出`long long`可表示范围。 | 按返回的边界值处理范围错误，必要时选择可表示更大范围的整数类型。 |

**示例：**

```c
#define _GNU_SOURCE
#include <errno.h>
#include <stdio.h>
#include <stdlib.h>
#include <locale.h>

int main(void)
{
    locale_t loc = newlocale(LC_ALL_MASK, "C", NULL);
    if (loc == NULL) {
        perror("newlocale");
        return 1;
    }
    char *end = NULL;
    errno = 0;
    long long value = __isoc23_strtoll_l("-0b101tail", &end, 0, loc);
    int ok = errno == 0 && value == -5 && *end == 't';
    freelocale(loc);
    if (!ok) {
        return 1;
    }
    printf("value=%lld rest=%s\n", value, end);
    return 0;
}
```

预期输出：

```text
value=-5 rest=tail
```

## __isoc23_strtoull_l

`__isoc23_strtoull_l`用于将字符串开头的数字部分转换为`unsigned long long`类型整数，支持C23规定的`0b`和`0B`二进制前缀。当前实现忽略区域设置参数`loc`。

**引用文件：** `<stdlib.h>`、`<locale.h>`

**函数原型：**

```c
#define _GNU_SOURCE
#include <stdlib.h>
#include <locale.h>

unsigned long long __isoc23_strtoull_l(const char *restrict nptr,
    char **restrict endptr, int base, locale_t loc);
```

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `nptr` | 指向有效、以`'\0'`结尾的输入字符串。不能传入空指针或未正确终止的字符数组。 |
| `endptr` | 用于接收第一个未转换字符的位置；若未转换任何数字，则接收原始输入`nptr`。可传入`NULL`，表示不保存位置。 |
| `base` | 进制，为0或2～36。0表示按前缀自动判断，具体见[解析规则](#解析规则)。 |
| `loc` | 区域设置对象，当前实现忽略此参数。对象的创建和释放由调用者负责，具体见[带区域设置参数的转换接口](#带区域设置参数的转换接口)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| unsigned long long | 成功时返回转换得到的`unsigned long long`值。数字部分的大小超过`ULLONG_MAX`时返回`ULLONG_MAX`，并设置`errno`为`ERANGE`。没有可转换的数字时返回0并设置`errno`为`EINVAL`；若`endptr`有效，则`*endptr`为`nptr`。 |

**错误码：**

| 错误码 | 原因 | 处理措施 |
| --- | --- | --- |
| EINVAL | `base`既不是0，也不在2～36范围内；或跳过前导空白和可选符号后，没有可转换的数字。 | 检查进制和输入，并通过`endptr`确认是否完成转换。 |
| ERANGE | 数字部分的大小超过`ULLONG_MAX`。 | 按返回的边界值处理范围错误，必要时选择可表示更大范围的整数类型。 |

**示例：**

```c
#define _GNU_SOURCE
#include <errno.h>
#include <stdio.h>
#include <stdlib.h>
#include <locale.h>

int main(void)
{
    locale_t loc = newlocale(LC_ALL_MASK, "C", NULL);
    if (loc == NULL) {
        perror("newlocale");
        return 1;
    }
    char *end = NULL;
    errno = 0;
    unsigned long long value = __isoc23_strtoull_l("0B101tail", &end, 0, loc);
    int ok = errno == 0 && value == 5 && *end == 't';
    freelocale(loc);
    if (!ok) {
        return 1;
    }
    printf("value=%llu rest=%s\n", value, end);
    return 0;
}
```

预期输出：

```text
value=5 rest=tail
```

## strtol_l

`strtol_l`用于将字符串开头的数字部分转换为`long`类型整数。当前实现忽略区域设置参数`loc`，不识别`0b`或`0B`二进制前缀。

**引用文件：** `<stdlib.h>`、`<locale.h>`

**函数原型：**

```c
#define _GNU_SOURCE
#include <stdlib.h>
#include <locale.h>

long strtol_l(const char *restrict nptr, char **restrict endptr,
    int base, locale_t loc);
```

接口先跳过前导空白字符，再读取可选的正号或负号，并按`base`指定的进制转换数字。遇到第一个不属于该进制的字符时停止转换。

与`__isoc23_strtol()`不同，`strtol_l()`不识别二进制前缀。`base`为0时转换`"0b101"`只转换开头的0并返回0，结束位置指向`'b'`；`base`为2时同样不识别`0b`前缀。`base`为0和`base`为2时的解析规则如下：

| 进制 | 解析规则 |
| --- | --- |
| 0 | `0x`或`0X`后紧跟十六进制数字时按十六进制解析；其他以0开头的输入按八进制解析；其余按十进制解析。 |
| 2 | 按二进制解析，但不识别`0b`或`0B`前缀。 |
| 16 | 按十六进制解析，允许带`0x`或`0X`前缀，但前缀后必须紧跟十六进制数字。 |
| 其余3～36范围内的值 | 按指定进制解析，字母`a`～`z`和`A`～`Z`表示数值10～35。不识别二进制前缀。 |

`loc`不能改变本次调用的字符分类、数字形式或分组规则。例如，按十进制转换`"1,000"`时仅得到1，结束位置指向逗号，不会把逗号识别为千位分隔符。接口不会切换线程的区域设置或接管区域设置对象。

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `nptr` | 指向有效、以`'\0'`结尾的输入字符串。不能传入空指针或未正确终止的字符数组。 |
| `endptr` | 用于接收第一个未转换字符的位置；若未转换任何数字，则接收原始输入`nptr`。可传入`NULL`，表示不保存位置。 |
| `base` | 进制，为0或2～36。0表示按前缀自动判断，具体见上表。 |
| `loc` | 区域设置对象，当前实现忽略此参数。对象的创建和释放由调用者负责。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 成功时返回转换得到的`long`值。数学结果超出`long`范围时，根据结果的符号返回`LONG_MIN`或`LONG_MAX`，并设置`errno`为`ERANGE`。没有可转换的数字时返回0并设置`errno`为`EINVAL`；若`endptr`有效，则`*endptr`为`nptr`。 |

**错误码：**

| 错误码 | 原因 | 处理措施 |
| --- | --- | --- |
| EINVAL | `base`既不是0，也不在2～36范围内；或跳过前导空白和可选符号后，没有可转换的数字。 | 检查进制和输入，并通过`endptr`确认是否完成转换。 |
| ERANGE | 带符号的数学结果超出`long`可表示范围。 | 按返回的边界值处理范围错误，必要时选择可表示更大范围的整数类型。 |

在包含任何头文件之前定义`_GNU_SOURCE`以启用接口声明。当前实现调用原有的`strtol()`入口；即使应用定义了`_OHOS_ISOC23_CONVERSION_SOURCE`，也不会改变`strtol_l()`的解析行为。`strtol_l()`是带区域设置参数的扩展接口，不属于ISO C标准接口。

**安全属性：**

| 线程安全 | 异步信号安全 |
| --- | --- |
| MT-Safe | AS-Unsafe（请勿在信号处理函数中调用） |

**示例：**

```c
#define _GNU_SOURCE
#include <errno.h>
#include <locale.h>
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
    locale_t loc = newlocale(LC_ALL_MASK, "C", NULL);
    if (loc == NULL) {
        perror("newlocale");
        return 1;
    }
    char *hex_end = NULL;
    char *binary_end = NULL;
    errno = 0;
    long hex_value = strtol_l("0x2atail", &hex_end, 0, loc);
    int ok = errno == 0 && hex_value == 42 && *hex_end == 't';

    errno = 0;
    long binary_value = strtol_l("0b101", &binary_end, 0, loc);
    ok = ok && errno == 0 && binary_value == 0 && *binary_end == 'b';
    freelocale(loc);
    if (!ok) {
        return 1;
    }
    printf("hex: value=%ld rest=%s\n", hex_value, hex_end);
    printf("binary: value=%ld rest=%s\n", binary_value, binary_end);
    return 0;
}
```

预期输出：

```text
hex: value=42 rest=tail
binary: value=0 rest=b101
```

## C23格式化输入接口通用说明

本节适用于`__isoc23_scanf`、`__isoc23_fscanf`、`__isoc23_sscanf`、`__isoc23_vfscanf`、`__isoc23_vsscanf`和`__isoc23_swscanf`。

### 调用与名称重定向

包含对应头文件后即可直接调用`__isoc23_*`接口，不需要定义`_OHOS_ISOC23_CONVERSION_SOURCE`。

若希望通过普通函数名（如`scanf()`）使用C23行为，应在包含任何头文件之前定义`_OHOS_ISOC23_CONVERSION_SOURCE`，或在编译时传入`-D_OHOS_ISOC23_CONVERSION_SOURCE=1`。只要定义该宏（即使值为0），就会启用重定向；如需保留普通函数名的原有行为，请不要定义该宏。

单独定义`_GNU_SOURCE`、`_ALL_SOURCE`、`_ISOC23_SOURCE`或`_ISOC2X_SOURCE`，或者仅选择C2x/C23编译模式，都不会自动启用上述重定向。该特性宏仅选择对应的格式化输入接口，不表示已支持全部C23标准库能力。

格式化输入扩展仅覆盖`scanf`、`fscanf`、`sscanf`、`vfscanf`、`vsscanf`和`swscanf`的对应C23入口。其他成员（包括`vscanf`、`fwscanf`、`wscanf`、`vfwscanf`、`vwscanf`和`vswscanf`）仍使用原有实现。未启用重定向的普通函数仍保留原有的解析、输入消耗、错误报告和内存分配行为。

### 整数输入格式

| 格式 | 含义 | 对应输出参数类型 |
| --- | --- | --- |
| `%i` | 自动识别十进制、前导0八进制、`0x`或`0X`十六进制，以及`0b`或`0B`二进制输入，允许带正负号。 | 未指定长度修饰符时为`int *`。 |
| `%b` | 读取二进制整数，允许带正负号及`0b`或`0B`前缀。 | 未指定长度修饰符时为`unsigned int *`。 |
| `%wNd`、`%wNi` | 读取指定宽度的有符号整数。 | 对应的`intN_t *`。 |
| `%wNb`、`%wNo`、`%wNu`、`%wNx`、`%wNX` | 读取指定宽度的无符号整数。 | 对应的`uintN_t *`。 |
| `%wfNd`、`%wfNi`及对应的无符号格式 | 使用指定最小宽度的快速整数类型。 | 对应的`int_fastN_t *`或`uint_fastN_t *`。 |

`N`只能为8、16、32或64。例如，`%w32d`需要传入`int32_t *`。`wN`和`wfN`也可用于`%n`，此时需要传入对应的有符号整数指针；它们不能用于浮点、指针、字符或字符串转换。

快速整数类型的实际宽度可能大于`N`位，应使用目标平台`<stdint.h>`声明的对应类型，不能仅根据`N`推测输出对象的类型。

字段宽度用于限制本次转换读取的输入量，写在长度修饰符之前。例如，`%3w16d`中的3表示字段宽度，16表示结果使用`int16_t`。字段宽度不能超过`INT_MAX`，否则设置`errno`为`EINVAL`。

`<inttypes.h>`中的`SCNb*`宏可用于构造对应无符号整数类型的二进制输入格式，例如`"%" SCNb32`。这些宏只提供格式字符串，不会自动使旧的输入接口支持`%b`。

### 输出对象与字符编码

各输出参数必须按格式字符串中的顺序传入，并指向类型正确、容量足够的对象。

- `*`表示抑制赋值，只消耗输入，不写入输出对象。
- `%n`记录当前调用已消耗的输入字节数，包括跳过的空白；它不消耗输入，也不增加返回的赋值项数。
- `%s`和`%[`成功时追加字符串终止符，缓冲区应预留相应空间；`%c`不追加终止符。
- `%lc`、`%ls`和`%l[`的字段宽度按生成的宽字符数计数，但`%n`仍按输入字节计数。多字节解码受`LC_CTYPE`影响。
- POSIX风格的`m`修饰符可用于`c`、`s`或`[`，由接口分配输出缓冲区。调用者应传入相应的二级指针，并对每个成功接收的缓冲区调用`free()`。

数值解析使用ASCII数字和小数点`.`，不识别区域设置特有的数字形式或分组分隔符。在内置`C`区域设置下，大于`0x7f`的字节采用musl保留原始字节的映射方式；需要按UTF-8解码时，应选择UTF-8区域设置。

进行多字节到宽字符转换时，无效或不完整的字节序列会导致`EILSEQ`。此时可能已经消耗部分输入并写入部分输出，不能把失败的转换结果当作完整字符串使用。

### 输入边界行为

| 输入情况 | 行为 |
| --- | --- |
| 识别相应前缀的整数格式遇到不完整的`0b`或`0x` | 匹配失败，目标数值不变；已读取的前缀不回退，后续转换（包括`%n`）不执行。 |
| 浮点输入为不完整的`1e+`或`0x1p+` | 匹配失败，目标数值不变；已经读取的指数部分不回退。 |
| `%f`读取`"0x."` | 匹配失败，目标对象不变。 |
| `%f`读取`"nX!"` | 匹配失败。对于流输入，`n`已消耗，`X`尚未读取。 |
| `%p`读取`(nil)` | 不区分字母大小写，写入空指针。 |
| `%c`尚未达到字段宽度就遇到输入末尾 | 若已读到至少一个字符，仍可能成功。需要确定读取量时可配合`%n`。 |
| 数值或字符串转换开始前已无输入 | 保留原有`errno`，应通过返回值判断输入结束。 |

有效的`nan`、`nan()`和`nan(payload)`可生成带相应符号的NaN。括号内只允许ASCII字母、数字和下划线，并会读取到右括号。无效字符会被消耗并导致匹配失败；缺少右括号或字段宽度使括号内容被截断时也会失败。字段宽度为3时可只匹配`nan(...)`中的`nan`部分。NaN的具体负载位表示由实现决定。

使用`%m`进行字符转换时，接口可能先按字段宽度预留空间。因此，即使实际输入很短，过大的字段宽度也可能导致`ENOMEM`。

### 流状态与安全属性

对`stdin`或指定文件流进行读取时，应结合返回值、`feof()`和`ferror()`区分输入结束、格式不匹配和读取错误。下表假定流原先没有结束或错误标志。

| 输入与格式 | 返回值及输出 | 流状态 |
| --- | --- | --- |
| 空输入，格式为`"%d"` | 返回`EOF`，输出对象不变。 | `feof()`非零，`ferror()`为0。 |
| 输入`"abc"`，格式为`"%d"` | 返回0，输出对象不变。 | 两个状态均为0。 |
| 输入`"42"`后结束，格式为`"%d %d"` | 返回1，第一个输出对象为42，第二个不变。 | `feof()`非零，`ferror()`为0。 |

上述情况不改写原有`errno`。流的结束和错误标志会保留；需要重新使用流时，应按实际场景通过`clearerr()`清除已有状态。底层读取还可能报告`EBADF`、`EIO`、`EINTR`或`EAGAIN`等错误，不能将其与普通格式不匹配混为一谈。

流锁仅保护单次库内操作；调用者应避免并发修改共享的输入字符串、格式字符串或输出对象，并协调区域设置修改。

**安全属性：**

| 线程安全 | 异步信号安全 |
| --- | --- |
| MT-Safe locale | AS-Unsafe（请勿在信号处理函数中调用） |

## __isoc23_scanf

`__isoc23_scanf`用于从标准输入读取格式化数据，支持C23二进制输入和整数宽度修饰符。

**引用文件：** `<stdio.h>`

**函数原型：**

```c
#include <stdio.h>

int __isoc23_scanf(const char *restrict format, ...);
```

接口按`format`从标准输入`stdin`读取数据，将转换结果写入后续参数指向的对象。调用可能阻塞等待输入，格式末尾的空白可能使读取持续到出现非空白字符或输入结束。

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `format` | 有效、以空字符结尾的格式字符串。 |
| `...` | 按格式顺序传入的输出对象指针。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回成功赋值且计入统计的输入项数。 |

**错误码：**

| 错误码 | 原因 | 处理措施 |
| --- | --- | --- |
| EINVAL | `wN`或`wfN`格式错误、不受支持或与转换类型不兼容，或者字段宽度超过`INT_MAX`。 | 检查格式字符串、整数宽度及输出对象类型。 |
| EILSEQ | 字符编码转换遇到无效、不完整的多字节序列，或无法表示的宽字符。 | 检查输入编码与`LC_CTYPE`，不要使用未完成的字符串结果。 |
| ENOMEM | 内存分配失败，或`%m`所需的分配或扩容大小超出`size_t`可表示范围。 | 检查字段宽度和内存使用情况，释放已成功分配的输出缓冲区。 |
| ERANGE | 内部数值解析检测到上溢或下溢。 | 检查输入范围。需要严格校验整数范围时，优先使用带结束位置和范围检查的字符串整数转换接口。 |

未发生错误时，接口保留调用前的`errno`。普通数值匹配失败不作为`EINVAL`报告；正的返回值也不保证后续没有错误，应结合赋值项数、`errno`和流状态判断。

`ERANGE`不能完整覆盖输出类型的范围检查，输入值应能由目标类型表示。

**示例：**

运行后输入`0b101 110`并换行，程序将读取两个整数。

```c
#include <stdio.h>

int main(void)
{
    int value = 0;
    unsigned int binary = 0;
    int ret = __isoc23_scanf("%i %b", &value, &binary);
    if (ret != 2) {
        if (ferror(stdin)) {
            fputs("input read error\n", stderr);
        } else {
            fputs("expected two integers\n", stderr);
        }
        return 1;
    }
    printf("value=%d binary=%u\n", value, binary);
    return 0;
}
```

预期输出：

```text
value=5 binary=6
```

## __isoc23_fscanf

`__isoc23_fscanf`用于从指定文件流读取格式化数据，支持C23二进制输入和整数宽度修饰符。

**引用文件：** `<stdio.h>`

**函数原型：**

```c
#include <stdio.h>

int __isoc23_fscanf(FILE *restrict stream, const char *restrict format, ...);
```

接口按`format`从`stream`读取数据。文件流应允许输入，且不能是宽字符定向流。读取会推进流位置，即使转换失败，也可能已消耗部分输入。`%n`记录本次调用消耗的字节数，不是文件中的绝对位置。

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `stream` | 有效、已打开且可读的文件流。 |
| `format` | 有效、以空字符结尾的格式字符串。 |
| `...` | 按格式顺序传入的输出对象指针。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回成功赋值且计入统计的输入项数。 |

**错误码：**

| 错误码 | 原因 | 处理措施 |
| --- | --- | --- |
| EINVAL | `wN`或`wfN`格式错误、不受支持或与转换类型不兼容，或者字段宽度超过`INT_MAX`。 | 检查格式字符串、整数宽度及输出对象类型。 |
| EILSEQ | 字符编码转换遇到无效、不完整的多字节序列，或无法表示的宽字符。 | 检查输入编码与`LC_CTYPE`，不要使用未完成的字符串结果。 |
| ENOMEM | 内存分配失败，或`%m`所需的分配或扩容大小超出`size_t`可表示范围。 | 检查字段宽度和内存使用情况，释放已成功分配的输出缓冲区。 |
| ERANGE | 内部数值解析检测到上溢或下溢。 | 检查输入范围。需要严格校验整数范围时，优先使用带结束位置和范围检查的字符串整数转换接口。 |

> **说明：**
>
> 非LiteOS实现会在`stream`为`NULL`时记录致命错误并调用`abort()`，这不是可恢复的`EINVAL`错误。LiteOS省略该项检查，但调用者仍必须传入有效流。

**示例：**

示例先向临时文件写入数据，再定位到文件开头读取。运行环境需要允许创建临时文件。

```c
#include <stdio.h>

int main(void)
{
    FILE *stream = tmpfile();
    if (stream == NULL) {
        perror("tmpfile");
        return 1;
    }
    if (fputs("0b101 110", stream) == EOF || fseek(stream, 0, SEEK_SET) != 0) {
        perror("prepare input");
        fclose(stream);
        return 1;
    }

    int value = 0;
    unsigned int binary = 0;
    int ret = __isoc23_fscanf(stream, "%i %b", &value, &binary);
    int failed = ret != 2 || value != 5 || binary != 6;
    if (fclose(stream) == EOF) {
        perror("fclose");
        return 1;
    }
    if (failed) {
        return 1;
    }
    printf("value=%d binary=%u\n", value, binary);
    return 0;
}
```

预期输出：

```text
value=5 binary=6
```

## __isoc23_sscanf

`__isoc23_sscanf`用于从字符串读取格式化数据，支持C23二进制输入和整数宽度修饰符。

**引用文件：** `<stdio.h>`

**函数原型：**

```c
#include <stdio.h>

int __isoc23_sscanf(const char *restrict s, const char *restrict format, ...);
```

接口按`format`解析字符串`s`，不修改输入字符串。输入在空字符处结束。`%n`记录已消耗的字节数，包括跳过的空白，不包括字符串终止符。

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `s` | 有效、以空字符结尾的输入字符串。 |
| `format` | 有效、以空字符结尾的格式字符串。 |
| `...` | 按格式顺序传入的输出对象指针。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回成功赋值且计入统计的输入项数。 |

**错误码：**

| 错误码 | 原因 | 处理措施 |
| --- | --- | --- |
| EINVAL | `wN`或`wfN`格式错误、不受支持或与转换类型不兼容，或者字段宽度超过`INT_MAX`。 | 检查格式字符串、整数宽度及输出对象类型。 |
| EILSEQ | 字符编码转换遇到无效、不完整的多字节序列，或无法表示的宽字符。 | 检查输入编码与`LC_CTYPE`，不要使用未完成的字符串结果。 |
| ENOMEM | 内存分配失败，或`%m`所需的分配或扩容大小超出`size_t`可表示范围。 | 检查字段宽度和内存使用情况，释放已成功分配的输出缓冲区。 |
| ERANGE | 内部数值解析检测到上溢或下溢。 | 检查输入范围。需要严格校验整数范围时，优先使用带结束位置和范围检查的字符串整数转换接口。 |

**示例：**

示例使用`SCNb32`构造二进制格式，并通过`%n`获取已消耗的字节数。

```c
#include <inttypes.h>
#include <stdio.h>

int main(void)
{
    int value = 0;
    int count = -1;
    int32_t exact = 0;
    uint32_t binary = 0;
    int ret = __isoc23_sscanf("0b101 42 110", "%i %w32d %" SCNb32 "%n",
        &value, &exact, &binary, &count);
    if (ret != 3 || value != 5 || exact != 42 || binary != 6 || count != 12) {
        return 1;
    }
    printf("value=%d exact=%" PRId32 " binary=%" PRIu32 " count=%d\n",
        value, exact, binary, count);
    return 0;
}
```

预期输出：

```text
value=5 exact=42 binary=6 count=12
```

## __isoc23_vfscanf

`__isoc23_vfscanf`使用`va_list`从指定文件流读取格式化数据，支持C23二进制输入和整数宽度修饰符。

**引用文件：** `<stdio.h>`、`<stdarg.h>`

**函数原型：**

```c
#include <stdarg.h>
#include <stdio.h>

int __isoc23_vfscanf(FILE *restrict stream, const char *restrict format, va_list ap);
```

接口使用可变参数列表`ap`从指定文件流读取数据，其输入规则与[__isoc23_fscanf()](#__isoc23_fscanf)相同。

调用前应通过`va_start()`或`va_copy()`初始化`ap`，调用后由调用者执行对应的`va_end()`。调用后应将该参数列表视为已使用；需要再次遍历时，应预先使用独立的`va_copy()`副本。

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `stream` | 有效、已打开且可读的文件流，不能是宽字符定向流。 |
| `format` | 有效、以空字符结尾的格式字符串。 |
| `ap` | 已初始化的可变参数列表，按格式顺序包含输出对象指针。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回成功赋值且计入统计的输入项数。 |

**错误码：**

| 错误码 | 原因 | 处理措施 |
| --- | --- | --- |
| EINVAL | `wN`或`wfN`格式错误、不受支持或与转换类型不兼容，或者字段宽度超过`INT_MAX`。 | 检查格式字符串、整数宽度及输出对象类型。 |
| EILSEQ | 字符编码转换遇到无效、不完整的多字节序列，或无法表示的宽字符。 | 检查输入编码与`LC_CTYPE`，不要使用未完成的字符串结果。 |
| ENOMEM | 内存分配失败，或`%m`所需的分配或扩容大小超出`size_t`可表示范围。 | 检查字段宽度和内存使用情况，释放已成功分配的输出缓冲区。 |
| ERANGE | 内部数值解析检测到上溢或下溢。 | 检查输入范围。需要严格校验整数范围时，优先使用带结束位置和范围检查的字符串整数转换接口。 |

此接口不执行`__isoc23_fscanf()`在非LiteOS实现中的空流检查。传入`NULL`或无效的`stream`属于未定义行为，不能依赖特定返回值或`errno`。

**示例：**

示例通过包装函数传递`va_list`，由包装函数配对调用`va_start()`和`va_end()`。运行环境需要允许创建临时文件。

```c
#include <stdarg.h>
#include <stdint.h>
#include <stdio.h>

static int ReadValues(FILE *stream, const char *format, ...)
{
    va_list ap;
    va_start(ap, format);
    int ret = __isoc23_vfscanf(stream, format, ap);
    va_end(ap);
    return ret;
}

int main(void)
{
    FILE *stream = tmpfile();
    if (stream == NULL) {
        perror("tmpfile");
        return 1;
    }
    if (fputs("-0B11 23", stream) == EOF || fseek(stream, 0, SEEK_SET) != 0) {
        perror("prepare input");
        fclose(stream);
        return 1;
    }

    int value = 0;
    int16_t exact = 0;
    int ret = ReadValues(stream, "%i %w16d", &value, &exact);
    int failed = ret != 2 || value != -3 || exact != 23;
    if (fclose(stream) == EOF) {
        perror("fclose");
        return 1;
    }
    if (failed) {
        return 1;
    }
    printf("value=%d exact=%d\n", value, (int)exact);
    return 0;
}
```

预期输出：

```text
value=-3 exact=23
```

## __isoc23_vsscanf

`__isoc23_vsscanf`使用`va_list`从字符串读取格式化数据，支持C23二进制输入和整数宽度修饰符。

**引用文件：** `<stdio.h>`、`<stdarg.h>`

**函数原型：**

```c
#include <stdarg.h>
#include <stdio.h>

int __isoc23_vsscanf(const char *restrict s, const char *restrict format, va_list ap);
```

接口使用可变参数列表`ap`解析字符串`s`，不修改输入字符串，其输入规则与[__isoc23_sscanf()](#__isoc23_sscanf)相同。

调用前应通过`va_start()`或`va_copy()`初始化`ap`，调用后由调用者执行对应的`va_end()`。调用后不能直接复用该参数列表再次遍历；需要多次使用时，应预先创建独立副本。

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `s` | 有效、以空字符结尾的输入字符串。 |
| `format` | 有效、以空字符结尾的格式字符串。 |
| `ap` | 已初始化的可变参数列表，按格式顺序包含输出对象指针。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回成功赋值且计入统计的输入项数。 |

**错误码：**

| 错误码 | 原因 | 处理措施 |
| --- | --- | --- |
| EINVAL | `wN`或`wfN`格式错误、不受支持或与转换类型不兼容，或者字段宽度超过`INT_MAX`。 | 检查格式字符串、整数宽度及输出对象类型。 |
| EILSEQ | 字符编码转换遇到无效、不完整的多字节序列，或无法表示的宽字符。 | 检查输入编码与`LC_CTYPE`，不要使用未完成的字符串结果。 |
| ENOMEM | 内存分配失败，或`%m`所需的分配或扩容大小超出`size_t`可表示范围。 | 检查字段宽度和内存使用情况，释放已成功分配的输出缓冲区。 |
| ERANGE | 内部数值解析检测到上溢或下溢。 | 检查输入范围。需要严格校验整数范围时，优先使用带结束位置和范围检查的字符串整数转换接口。 |

**示例：**

示例读取整数和尾部字符。`%n`记录读取整数后的位置，不增加返回的赋值项数。

```c
#include <stdarg.h>
#include <stdio.h>

static int ReadValues(const char *s, const char *format, ...)
{
    va_list ap;
    va_start(ap, format);
    int ret = __isoc23_vsscanf(s, format, ap);
    va_end(ap);
    return ret;
}

int main(void)
{
    int value = 0;
    int count = -1;
    char tail = '?';
    int ret = ReadValues("0b101Z", "%i%n%c", &value, &count, &tail);
    if (ret != 2 || value != 5 || count != 5 || tail != 'Z') {
        return 1;
    }
    printf("value=%d count=%d tail=%c\n", value, count, tail);
    return 0;
}
```

预期输出：

```text
value=5 count=5 tail=Z
```

## __isoc23_swscanf

`__isoc23_swscanf`用于从宽字符串读取格式化数据，支持C23二进制输入和整数宽度修饰符。

**引用文件：** `<wchar.h>`

**函数原型：**

```c
#include <wchar.h>

int __isoc23_swscanf(const wchar_t *restrict s, const wchar_t *restrict format, ...);
```

接口按宽字符格式字符串`format`解析宽字符串`s`，将结果写入后续参数指向的对象。输入和格式均为`wchar_t`数组，不是多字节字符串。上述整数输入格式均应写在宽字符格式字符串中，例如`L"%w32d"`。

宽字符输入的行为与多字节输入存在以下差异：

- 输入在`L'\0'`处结束。字段宽度和`%n`按输入宽字符数计数，不按编码后的字节数计数，也不包含终止符。
- `%lc`、`%ls`和`%l[`直接写入`wchar_t`对象，不要求输入字符能在当前区域设置下编码为多字节序列。
- 不带`l`的`%c`、`%s`和`%[`按`LC_CTYPE`将宽字符转换为`char`缓冲区中的多字节序列。字段宽度限制输入宽字符数，不能作为输出字节容量的上限；`%s`和`%[`还需为终止空字节预留空间，`%c`不追加终止符。
- 无法编码为多字节输出时设置`EILSEQ`。尚无计入统计的赋值时返回`EOF`，否则返回已有赋值项数。失败时可能已写入部分输出，不能将其当作完整字符串使用。
- 宽字符空白使用musl内置分类。例如，即使在`C`区域设置下，`%ls`读取`L"X\u3000Y"`也会在U+3000处停止，U+0085同样作为分隔符。数值使用ASCII语法，小数点为`.`，不识别区域设置特有的数字形式或分组分隔符。

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `s` | 有效、以`L'\0'`结尾的输入宽字符串。 |
| `format` | 有效、以`L'\0'`结尾的宽字符格式字符串，例如`L"%i %w32d"`。 |
| `...` | 按格式顺序传入的输出对象指针，类型和容量须与格式匹配。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回成功赋值且计入统计的输入项数。 |

**错误码：**

| 错误码 | 原因 | 处理措施 |
| --- | --- | --- |
| EINVAL | `wN`或`wfN`格式错误、不受支持或与转换类型不兼容，或者字段宽度超过`INT_MAX`。 | 检查格式字符串、整数宽度及输出对象类型。 |
| EILSEQ | 字符编码转换遇到无效、不完整的多字节序列，或无法表示的宽字符。 | 检查输入编码与`LC_CTYPE`，不要使用未完成的字符串结果。 |
| ENOMEM | 内存分配失败，或`%m`所需的分配或扩容大小超出`size_t`可表示范围。 | 检查字段宽度和内存使用情况，释放已成功分配的输出缓冲区。 |
| ERANGE | 内部数值解析检测到上溢或下溢。 | 检查输入范围。需要严格校验整数范围时，优先使用带结束位置和范围检查的字符串整数转换接口。 |

**示例：**

示例同时读取二进制整数、指定宽度整数和一个宽字符。`%n`记录已读取的宽字符数，不计入返回的赋值项数。

```c
#include <stdint.h>
#include <stdio.h>
#include <wchar.h>

int main(void)
{
    int value = 0;
    int32_t exact = 0;
    wchar_t tail = L'?';
    int count = -1;
    int ret = __isoc23_swscanf(L"0b101 42 \u4e2d", L"%i %w32d %lc%n",
        &value, &exact, &tail, &count);
    if (ret != 3 || value != 5 || exact != 42 || tail != L'\u4e2d' || count != 10) {
        return 1;
    }
    printf("value=%d exact=%ld tail=U+%04lx count=%d\n",
        value, (long)exact, (unsigned long)tail, count);
    return 0;
}
```

预期输出：

```text
value=5 exact=42 tail=U+4e2d count=10
```

