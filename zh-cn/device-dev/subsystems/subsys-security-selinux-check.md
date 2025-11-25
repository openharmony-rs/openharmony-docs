# OpenHarmony SELinux Check问题处理指导

## 概述

为规范OpenHarmony SELinux策略配置，针对neverallow检查无法覆盖到的场景和人工审核容易遗漏的问题，OpenHarmony提供了一套SELinux策略检查工具。


## file_contexts中data分区二级目录使用正则表达式检查

### 检查说明

data分区为可读写分区，大部分进程的数据文件和用户的文件存放在data分区，文件数量庞大，容易出现碎片化问题。为避免data分区打标签性能问题，需要限制data分区的二级目录不能存在正则表达式，该检查主要扫描`file_contexts`文件。

### 编译拦截

在`file_contexts`中，data分区二级目录使用正则表达式，会触发编译报错，关键报错信息`Regex is not allowed in the secondary directory under data`，报错如下：
```text
Regex is not allowed in the secondary directory under data, check '/data/log(/.*)?' failed in file out/rk3568/obj/base/security/selinux_adapter/file_contexts:214
 There are two solutions:
 1. Add '/data/log(/.*)?' to whitelist file 'data_regex_whitelist.txt' under 'base/security/selinux_adapter/sepolicy';
 2. Modify '/data/log(/.*)?' to remove the regular expression
```

### 拦截原因

说明以下`file_contexts`中的定义是非法的，因为`log(/.*)?`是正则表达式，且在data的第二级目录：
```text
/data/log(/.*)?                 u:object_r:data_log:s0
```

### 修复方法

主要有两种修复方式：

- 方式一：将不满足的路径`/data/log/(.*)?`添加到`//base/security/selinux_adapter/sepolicy/`下的白名单文件`data_regex_whitelist.txt`中，修改该白名单需要评估安全性和合理性，审慎修改。
- 方式二：修改data二级目录中不合理的正则表达式，以满足要求，例如，改成以下形式，则是合法的：
    ```text
    /data/log                       u:object_r:data_log:s0
    /data/log/(.*)?                 u:object_r:data_log:s0
    ```

## file_contexts中使用一级目录标签检查

### 检查说明

一级目录标签是指根路径下的子目录使用的标签，主要有：
```text
u:object_r:dev_file:s0
u:object_r:etc_file:s0
u:object_r:lib_file:s0
u:object_r:config_file:s0
u:object_r:updater_file:s0
u:object_r:system_file:s0
u:object_r:sys_prod_file:s0
u:object_r:chip_prod_file:s0
u:object_r:vendor_file:s0
u:object_r:data_file:s0
u:object_r:module_update_file:s0
```

`file_contexts`中禁止使用一级目录标签来定义路径标签，避免配置不合理的SELinux权限，对根路径的子目录产生影响，构成安全隐患。

### 编译拦截

在`file_contexts`配置中，不合理的使用一级目录标签，会触发编译报错，关键报错信息`partition label is not allow to use`，报错如下：

```
partition label is not allow to use, check '/data/log u:object_r:data_file:s0' failed in file out/rk3568/obj/base/security/selinux_adapter/file_contexts:213
 There are two solutions:
 1. Add '/data/log u:object_r:data_file:s0' to whitelist file 'partition_label_use_whitelist.txt' under 'base/security/selinux_adapter/sepolicy';
 2. Change '/data/log u:object_r:data_file:s0' to avoid using label in ['u:object_r:dev_file:s0', 'u:object_r:etc_file:s0', 'u:object_r:lib_file:s0', 'u:object_r:config_file:s0', 'u:object_r:updater_file:s0', 'u:object_r:system_file:s0', 'u:object_r:sys_prod_file:s0', 'u:object_r:chip_prod_file:s0', 'u:object_r:vendor_file:s0', 'u:object_r:data_file:s0', 'u:object_r:module_update_file:s0']
```

### 拦截原因

说明以下`file_contexts`中的定义是非法的，原因是为`/data/log`路径配置了标签`u:object_r:data_file:s0`，该标签属于一级目录标签：
```text
/data/log   u:object_r:data_file:s0
```

### 修复方法

主要有两种修复方式：

- 方式一：将不满足的路径及标签`'/data/log   u:object_r:data_file:s0'`添加到`//base/security/selinux_adapter/sepolicy/`下的白名单文件`partition_label_use_whitelist.txt`中，修改该白名单需要评估安全性和合理性，审慎修改。
- 方式二：更改`/data/log`的不合理标签，使用自定义标签，以满足要求，例如，改成以下形式，则是合法的：
    ```text
    /data/log    u:object_r:data_log:s0
    ```

## 使用高危组合权限检查

### 检查说明

当某一对主体和客体同时拥有几个不同的SELinux权限时，可能形成一种攻击路径。此检查项主要检查user版本策略和开发者模式策略。检查项的配置文件在`base/security/selinux_adapter/scripts/selinux_check/config/perm_group.json`，形式如下：
```json
{
    "check_rules": [
        {
            "name": "execute and execute_no_trans",
            "description": "process label should transform while execute a file",
            "perm_group": [
                {
                    "tclass": "*",
                    "perm": "execute execute_no_trans"
                }
            ]
        }
    ]
}
```

其中，`check_rules`表示所有权限组合检查项列表，每一个检查项中包括`name`、`description`、`perm_group`三个字段，`name`表示检查项的名称，`description`表示检查项描述，`perm_group`表示详细的可能存在攻击路径的权限列表，其中`tclass`表示操作类型，`perm`表示该操作类型下的权限，`tclass`可以填具体操作类型，也可以填`*`，填`*`表示会检查所有包括`perm`中权限的操作类型。

### 编译拦截

不合理的权限配置，会触发编译报错，关键报错信息`check rule 'xxx' in user mode failed`，这里的`xxx`表示被拦截的检查项`name`，报错如下：
```text
        check rule 'execute and execute_no_trans' in user mode failed, process label should transform while execute a file
        violation list (scontext tcontext):
                appspawn appspawn_exec
        There are two solutions:
        1. Add the above list to whitelist file 'perm_group_whitelist.json' under 'base/security/selinux_adapter/sepolicy' in 'user' part of 'execute and execute_no_trans'
        2. Change the policy to avoid violating rule 'execute and execute_no_trans'

        check rule 'execute and execute_no_trans' in developer mode failed, process label should transform while execute a file
        violation list (scontext tcontext):
                appspawn appspawn_exec
        There are two solutions:
        3. Add the above list to whitelist file 'perm_group_whitelist.json' under 'base/security/selinux_adapter/sepolicy' in 'developer' part of 'execute and execute_no_trans'
        4. Change the policy to avoid violating rule 'execute and execute_no_trans'
```

### 拦截原因

上述报错是因为在user策略和开发者策略中，主体`appspawn`和客体`appspawn_exec`，都同时拥有`execute`和`execute_no_trans`权限：
```text
allow appspawn appspawn_exec:file { execute execute_no_trans };
```

### 修复方法

主要有两种修复方式：

- 方式一：将不合理的主体和客体组合添加到`//base/security/selinux_adapter/sepolicy/`下的白名单文件`perm_group_whitelist.json`中，修改该白名单需要评估合理性，审慎添加，该文件如下：
    ```text
    {
        "whitelist": [
            {
                "name": "execute and execute_no_trans",
                "user": [
                    "appspawn appspawn_exec"
                ],
                "developer": [
                ]
            }
        ]
    }
    ```
    其中，`whitelist`表示所有权限组合检查项白名单列表，每一个检查项白名单中包括`name`、`user`、`developer`三个字段，`name`表示检查项白名单的名称，与检查项`name`对应，`user`表示检查项白名单中的`user`策略白名单，`developer`表示检查项白名单中的开发者策略白名单。白名单的填写位置参考下表（下文中涉及违反`user`策略和`developer`策略的报错的修改方式均相同）：

    **表1** 策略检查与白名单字段与报错对应关系

    | 违反user策略 | 违反developer策略 | 写入字段位置 |
    | -------- | -------- | -------- |
    | 是 | 是 | user |
    | 否 | 是 | developer |
    | 是 | 否 | user，且需删除当前主客体在developer字段中的白名单 |

- 方式二：修改不合理的策略，以满足要求，例如，更改方案，避免同时申请这两个权限。

### 删除冗余的白名单

当整改了不合理的权限组合配置后，删除了不合理的策略，但是未同时删除白名单时，也会触发编译报错，关键报错信息`remove the following unnecessary whitelists in rule 'xxx' part 'user'`，这里的`xxx`表示被拦截的检查项`name`，报错如下：
```text
        check rule 'execute and execute_no_trans' failed in whitelist file 'perm_group_whitelist.json'
        remove the following unnecessary whitelists in rule 'execute and execute_no_trans' part 'user':
                appspawn appspawn_exec
        check rule 'execute and execute_no_trans' failed in whitelist file 'perm_group_whitelist.json'
        remove the following unnecessary whitelists in rule 'execute and execute_no_trans' part 'developer':
                appspawn appspawn_exec
```

需要同时删除白名单，将`//base/security/selinux_adapter/sepolicy/`下的白名单文件`perm_group_whitelist.json`中的相关白名单删除，该文件如下：
```text
{
    "whitelist": [
        {
            "name": "execute and execute_no_trans",
            "user": [
                "appspawn appspawn_exec"
            ],
            "developer": [
            ]
        }
    ]
}
```
这里根据报错，要删除检查项`"execute and execute_no_trans"`下的`user`字段的白名单`"appspawn appspawn_exec"`，另外，其他冗余白名单报错的删除位置参考下表：

**表2** 主客体组合权限检查项冗余白名单字段与报错对应关系
| user白名单冗余 | developer白名单冗余 | 删除白名单字段位置 |
| -------- | -------- | -------- |
| 是 | 是 | user |
| 否 | 是 | developer |
| 是 | 否 | user |


## 篡改高危进程基线检查

### 检查说明

OpenHarmony中存在一些高危进程，例如shell、console，这些进程的SELinux策略需要有管控，避免随意删除和新增，造成系统不可用或引入安全隐患。对于这些高危进程xx，其基线策略在`//base/security/selinux_adapter/sepolicy/`下的`xx.baseline`文件中。以sh基线为例，形式如下：
```text
(allow sh vendor_file (dir (search)))

developer_only(`
(allow sh system_lib_file (dir (search)))
')
```

其中被developer_only括起来的策略，表示该策略仅作为开发者模式下的基线；否则，表示该策略是user和开发者模式共用的基线。

### 编译拦截

新增和删除高危进程策略，都会触发编译报错，关键报错信息`check 'xxx' baseline in user mode failed`，xxx表示高危进程标签，报错如下：
```text
        check 'sh' baseline in user mode failed
                expect rule: (allow sh vendor_file (dir ())); actual rule: (allow sh vendor_file (dir (search)))
        There are two solutions:
        1. Add the above actual rule to baseline file 'sh.baseline' under 'base/security/selinux_adapter/sepolicy'
        2. Change the policy to satisfy expect rule

        check 'sh' baseline in developer mode failed
                expect rule: (allow sh vendor_file (dir ())); actual rule: (allow sh vendor_file (dir (search)))
        There are two solutions:
        1. Add the above actual rule to baseline file 'sh.baseline' under 'base/security/selinux_adapter/sepolicy' and add developer_only
        2. Change the policy to satisfy expect rule
```

### 拦截原因

上述报错是因为新增了sh的策略`"allow sh vendor_file:dir search;"`，对应的cil形式为`"(allow sh vendor_file (dir (search)))"`，同时违反了user和developer下的进程基线，期望的cil形式基线是`"(allow sh vendor_file (dir ()))"`。

### 修复方法

主要有两种修复方式：

- 方式一：将报错中`"actual rule"`字段的cil策略，作为新基线添加到`//base/security/selinux_adapter/sepolicy/`下的基线文件`xx.baseline`中，`xx`为违反基线的进程标签。修改该基线文件需要评估安全性和合理性，审慎修改。其中，基线的填写位置参考下表：

    **表3** 篡改高危进程基线检查基线更新位置与报错对应关系
    | user基线报错 | developer基线报错 | 更新基线是否需要在developer_only内 |
    | -------- | -------- | -------- |
    | 是 | 是 | 否 |
    | 否 | 是 | 是 |
    | 是 | 否 | 将developer_only内的基线挪到外部 |

- 方式二：修改不合理的策略，以满足要求，例如，更改方案，避免违反基线。

### 删除冗余的基线

当整改了不合理的基线策略后，删除了不合理的策略，但是未同时删除基线时，也会触发编译报错，关键报错信息`check 'xxx' baseline in user mode failed`，xxx表示高危进程标签，报错如下：
```
        check 'sh' baseline in user mode failed
                expect rule: (allow sh rootfs (dir (search))); actual rule: (allow sh rootfs (dir ()))
        There are two solutions:
        1. Add the above actual rule to baseline file 'sh.baseline' under 'base/security/selinux_adapter/sepolicy'
        2. Change the policy to satisfy expect rule

        check 'sh' baseline in developer mode failed
                expect rule: (allow sh rootfs (dir (search))); actual rule: (allow sh rootfs (dir ()))
        There are two solutions:
        1. Add the above actual rule to baseline file 'sh.baseline' under 'base/security/selinux_adapter/sepolicy' and add developer_only
        2. Change the policy to satisfy expect rule
```

需要同时删除基线，将`//base/security/selinux_adapter/sepolicy/`下的基线文件`sh.baseline`中的相关基线删除。

这里根据报错，要删除基线`"(allow sh rootfs (dir (search)))"`，另外，以符合`"actual rule"`，其他冗余基线报错的删除位置参考下表：

**表4** 篡改高危进程基线检查冗余基线与报错对应关系
| user基线冗余 | developer基线冗余 | 删除基线字段位置 |
| -------- | -------- | -------- |
| 是 | 是 | developer_only外 |
| 否 | 是 | developer_only内 |
| 是 | 否 | developer_only外 |

## ioctl的权限策略检查

### 检查说明

涉及配置ioctl相关的SELinux策略时，除了配置allow规则以外，还需要根据avc日志对ioctl的ioctlcmd进行限制，否则会导致所有的ioctlcmd权限都被开放，不满足权限最小化原则。

### 编译拦截

配置的 allow 规则访问权限包含了 ioctl，但未限定 ioctl 权限参数时，会触发编译报错，关键报错信息`check ioctl rule in user mode failed`，报错如下：
```text
 check ioctl rule in user mode failed.
 violation list (allow scontext tcontext:tclass ioctl)
    allow wifi_host data_service_el1_file:file ioctl;
    allow wifi_host dev_hdfwifi:chr_file ioctl;
    allow write_updater updater_block_file:blk_file ioctl;
 please add "allowxperm" rule based on the above list.
```

### 拦截原因

仅添加`allow scontext tcontext:tclass ioctl`规则会导致主体有对tcontext:tclass所有ioctl的权限，权限过大被编译拦截，需添加具体的allowxperm对ioctl权限精细化管控，达到权限最小化。

### 修复方法

主要有两种修复方式：
- 方式一：根据avc日志对ioctl的ioctlcmd进行限制。例如，有下面的avc日志：
    ```text
    #avc:  denied  { ioctl } for  pid=1 comm="init" path="/data/app/el1/bundle/public" dev="mmcblk0p11" ino=652804 ioctlcmd=0x6613 scontext=u:r:init:s0 tcontext=u:object_r:data_app_el1_file:s0 tclass=dir permissive=0
    ```
    根据该avc日志配置了允许ioctl的SELinux策略：
    ```text
    allow init data_app_el1_file:dir { ioctl };
    ```
    同时，还需要根据avc日志中的`ioctlcmd=0x6613`字段，在相同user或开发者模式基线下添加allowxperm，进一步限制ioctl的开放范围：
    ```text
    allowxperm init data_app_el1_file:dir ioctl { 0x6613 };
    ```
    
- 方式二：将拦截日志中的 "scontext tcontext tclass" 字符添加到`//base/security/selinux_adapter/sepolicy/`下白名单 `ioctl_xperm_whitelist.json` 中，修改该白名单需要评估合理性。
    拦截日志中 `user mode` 表示该策略是user和开发者模式共用的基线，另外 `developer mode` 则表示该策略仅作为开发者模式下的基线，相应添加到白名单列表中。
    ```text
    {
        "whitelist": {
            "user": [
                "wifi_host data_service_el1_file file"
            ],
            "developer": [
            ]
        }
    }
    ```


## permissive 主体类型的权限检查

### 检查说明

增加 permissive 的主体类型，会放开其访问所有客体的权限，不满足权限最小化原则。

### 编译拦截

在策略文件中增加 `permissive scontext;` 后，会触发编译报错，关键报错信息 `check permissive rule in user mode failed`，报错如下：
```text
 check permissive rule in user mode failed.
 violation list (scontext):
    sa_subsys_dfx_service
 There are two solutions:
    1. Add the above list to whitelist file 'permissive_whitelist.json' under 'base/security/selinux_adapter/sepolicy' in 'user' mode.
    2. Change the policy to avoid violating rule.
```

### 拦截原因

规则中存在新增的 permissive 主体类型。

### 修复方法

主要有两种修复方式：
- 方式一：删除不必要的 permissive 定义。
- 方式二：添加主体类型scontext到 `//base/security/selinux_adapter/sepolicy/` 下白名单 `permissive_whitelist.json` 中，修改该白名单需要评估合理性。
    拦截日志中 `user mode` 表示该策略是user和开发者模式共用的基线，另外 `developer mode` 则表示该策略仅作为开发者模式下的基线，相应添加到白名单文件。
    ```text
    {
        "whitelist": {
            "user": [
                "sa_subsys_dfx_service"
            ],
            "developer": [
            ]
        }
    }
    ```

## 进程类型及其关联的属性检查

### 检查说明

为了管理系统组件和芯片组件的进程访问范围，识别跨组件的资源和节点访问、进程间通信等行为，需要根据进程类型划分进程标签类型，并关联特定进程域的属性。表5展示了不同进程域包含的进程。

**表5** 进程域属性用途
|  进程域  |  进程范围  | 所属组件类型 |
| -------- | -------- | -------- |
| sadomain | 系统服务SA进程，例如foundation | 系统组件 |
| hap_domain | 应用进程，例如system_basic_hap | 系统组件 |
| native_system_domain | 系统组件Native进程，例如aa | 系统组件 |
| hdfdomain | HDF服务进程，例如location_host | 芯片组件 |
| native_chipset_domain | 芯片组件Native进程，例如chipset_init | 芯片组件 |

### 编译拦截

- 在定义进程标签类型时，未关联到一个正确的域，会导致编译报错拦截。关键报错信息`Check rule in user mode failed: a process should be associated with a domain`，报错如下：
    ```text
    Check rule in user mode failed: a process should be associated with a domain.
    Violation list (type):
            "distributed_isolate_hap",
    There are two solutions:
    1. Associate the types to one of domains:
            sadomain, hap_domain, native_system_domain, hdfdomain, native_chipset_domain
    2. Add the above list to "missing_domain" field under "user" field in domain_whitelist.json file.
    ```

- 在定义进程标签类型时，关联到多个域，会导致报错拦截。关键报错信息`Check rule in user mode failed: a process is restricted to a single domain`，报错如下：
    ```text
    Check rule in user mode failed: a process is restricted to a single domain.
    Violation list (type):
            "nwebspawn",
    There are two solutions:
    1. Change types to prevent association with multiple domains.
    2. Add the above list to "conflict_domain" field under "user" field in domain_whitelist.json file.
    ```

### 拦截原因

报错说明进程标签类型定义未正确地关联到进程域。类型`distributed_isolate_hap`和`nwebspawn`的定义关联到了属性`domain`说明其为进程标签类型。而`distributed_isolate_hap`仅关联了`domain`，未关联具体的进程域；`nwebspawn`关联了两个进程域`sadomain`和`native_system_domain`导致拦截报错。

```text
# distributed_isolate_hap的定义
type distributed_isolate_hap, domain;

# nwebspawn的定义
type nwebspawn, sadomain, native_system_domain, domain;
```

### 修复方法

- 进程标签类型未关联到一个正确的进程域报错，有两种修复方法：

    - 方式一：修改不合理的策略，以满足要求。

        例如，将不合理的进程类型`distributed_isolate_hap`关联到`hap_domain`，即定义修改为`type distributed_isolate_hap, hap_domain, domain;`。

    - 方式二：将不合理的类型添加到`//base/security/selinux_adapter/sepolicy/`下的白名单文件`domain_whitelist.json`。

        报错信息中`Add the above list to "missing_domain" field under "user" field in domain_whitelist.json file`中的`user`说明该类型定义在`user`模式和开发者模式均生效，需要增加到`user`字段下的`missing_domain`中。

        修改该白名单需要评估合理性，审慎添加。该文件如下：

        ```json
        {
            "whitelist": {
                "user": {
                    "missing_domain": [
                        "distributed_isolate_hap"
                    ],
                    "conflict_domain": []
                },
                "developer": {
                    "missing_domain": [],
                    "conflict_domain": []
                }
            }
        }
        ```

- 进程标签类型关联到多个进程域报错，有两种修复方案：

    - 方式一：修改不合理的策略，以满足要求。

        例如，将不合理的进程类型`nwebspawn`仅关联到`native_system_domain`，即定义修改为`type nwebspawn, native_system_domain, domain;`。

    - 方式二：将不合理的类型添加到`//base/security/selinux_adapter/sepolicy/`下的白名单文件`domain_whitelist.json`。

        报错信息中`Add the above list to "conflict_domain" field under "user" field in domain_whitelist.json file`中的`user`说明该类型定义在`user`和`developer`模式均生效，需要增加到`user`字段下的`conflict_domain`中。

        修改该白名单需要评估合理性，审慎添加，该文件如下：

        ```json
        {
            "whitelist": {
                "user": {
                    "missing_domain": [],
                    "conflict_domain": [
                        "nwebspawn"
                    ]
                },
                "developer": {
                    "missing_domain": [],
                    "conflict_domain": []
                }
            }
        }
        ```

### 删除冗余的白名单

当整改了不合理的进程类型，但未同时删除白名单时，会触发编译报错。关键报错信息`delete any unused data from "xxx" field under "user" field in domain_whitelist.json file`，表示需要从白名单文件 `domain_whitelist.json` 中删除 `user` 字段下 `xxx` 的数据。

报错信息中`under "user" field`说明该进程标签类型定义在`user`和`developer`模式均生效；`xxx`指明是`missing_domain`或`conflict_domain`，分别对应缺少进程域和关联了多个域的场景，报错如下：

```text
Check whitelist of "missing_domain" in user mode failed.
Violation list (type):
        "distributed_isolate_hap",
Solution: delete any unused data from "missing_domain" field under "user" field in domain_whitelist.json file.
```

### 修改进程域基线检查

不同进程域有不同的策略管控。为了避免进程所属的域随意更换，造成系统不可用或引入安全隐患，进程域包含的进程有基线管控。进程域的基线策略在`//base/security/selinux_adapter/sepolicy/`下的`domain_baseline.json`中。

**基线检查的编译拦截**

新增和删除进程域包含的进程、修改进程所属的进程域，都会触发编译报错。关键报错信息`Check "xxx" baseline in user mode failed`，`xxx`表示违反的进程域的基线，报错如下：

```text
Check "hap_domain" baseline in user mode failed.
violation list (type):
        "distributed_isolate_hap",
Solution: add the above list to "hap_domain" field under "user" field in baseline file domain_baseline.json.
```

**基线检查的拦截说明**

报错说明`distributed_isolate_hap`是属于`hap_domain`的进程域，其定义为`type distributed_isolate_hap, hap_domain, domain;`，但类型不在`hap_domain`的基线中，导致拦截报错。

**修复基线报错方法**

新增进程需要修改对应进程域的基线。关键报错信息`add the above list to "hap_domain" field under "user" field in baseline file domain_baseline.json`，说明该进程类型定义在`user`和`developer`模式均生效，需要将进程加入`user`字段下的`hap_domain`。基线文件形式如下：

```json
{
    "user": {
        ...
        "hap_domain": [
            "distributed_isolate_hap"
        ],
        ...
    },
    "developer": {
        ...
        "hap_domain": [],
        ...
    }
}

```

将进程从一个进程域修改到另一个域时，例如将进程标签类型属性从 `hap_domain` 修改到 `native_chipset_domain`，需要评估安全性和合理性，审慎进行修改。

**删除冗余基线**

当删除一个进程类型定义但未同时删除基线时，会触发编译报错。关键报错信息为：`delete any unused data from "xxx" field under "user" field in baseline file domain_baseline.json`。`xxx`代表需要删除的进程域的基线数据，`under "user" field`说明该进程类型在`user`和`developer`模式下均生效，需要从`user`字段中删除。报错如下：

```text
Check "native_system_domain" baseline in "user" mode failed.
Violation list (type):
        "hnp_native",
Solution: delete any unused data from "native_system_domain" field under "user" field in baseline file domain_baseline.json.
```

## 套接字文件的策略检查


### 检查说明

为了管理Unix域套接字文件`sock_file`的访问权限，识别系统组件和芯片组件之间通过套接字进行通信的行为，所有对`sock_file`操作涉及的客体必须关联到属性`system_sock_domain`或者`chipset_sock_domain`，拦截包含以下两种情况：
1. 既没有关联`system_sock_domain`，也没有关联`chipset_sock_domain`；
2. 同时关联了`system_sock_domain`和`chipset_sock_domain`。

### 编译拦截

在策略文件中，使用不合理的类型作为Unix域套接字文件的安全上下文，会触发编译报错。

- 类型未关联`system_sock_domain`和`chipset_sock_domain`中的一个属性。关键报错信息`Check sock_file with correct socket attribute in user mode failed`，报错如下：

    ```text
    Check sock_file with correct socket attribute in user mode failed.

    Violation list (type):
            "dev_unix_socket",
    The above types should be associated with exactly one of the two attributes: chipset_sock_domain and system_sock_domain.
    ```


- 类型同时关联了`system_sock_domain`和`chipset_sock_domain`两个属性报错。关键报错信息`Check sock_file with single socket attribute in user mode failed`，报错如下：
    ```text
    Check sock_file with single socket attribute in user mode failed.

    Violation list (types):
            "faultloggerd_socket",
    There are two solutions:
            1. Associate types with either chipset_sock_domain or system_sock_domain.
            2. Add the above list to "user" field in socket_whitelist.json file.
    ```

### 拦截原因

报错说明te文件中对Unix域套接字文件的类型定义是不合理的。对`sock_file`访问的策略说明`faultloggerd_socket`和`dev_unix_socket`用作Unix域套接字文件的标签类型，但`faultloggerd_socket`定义未关联`system_sock_domain`或者`chipset_sock_domain`, `dev_unix_socket`定义同时关联了`system_sock_domain`和`chipset_sock_domain`，导致拦截报错。

```text
# 对sock_file的allow策略
allow faultloggerd faultloggerd_socket:sock_file { setattr };
allow installs dev_unix_socket:sock_file { write };

# faultloggerd_socket定义：未关联socket所需属性
type faultloggerd_socket, dev_attr, file_attr;

# dev_unix_socket定义：关联多个属性导致冲突
type dev_unix_socket, dev_attr, file_attr, system_sock_domain, chipset_sock_domain;
```

### 修复方法

- 类型未关联`system_sock_domain`或者`chipset_sock_domain`报错，有以下两种修复方法：

    - 方式一：修改不合理的策略，以满足要求。

        例如，将不合理的Unix域套接字文件的类型`faultloggerd_socket`关联到`system_sock_domain`，即定义修改为`type faultloggerd_socket, dev_attr, file_attr, system_sock_domain;`。

    - 方式二：将不合理的类型添加到`//base/security/selinux_adapter/sepolicy/`下的白名单文件`socket_whitelist.json`。

        报错信息中`Add the above list to "user" field in socket_whitelist.json file`中的`user`说明该类型定义在`user`和`developer`模式均生效，需要增加到`user`字段下，修改该白名单需要评估合理性，审慎添加。白名单文件的形式如下：

        ```json
        {
            "whitelist": {
                "user": [
                    "faultloggerd_socket"
                ],
                "developer": []
            }
        }
        ```

- 类型同时关联了`system_sock_domain`和`chipset_sock_domain`报错，需要修改不合理的策略以满足要求。例如，将不合理的Unix域套接字文件的类型`dev_unix_socket`关联到`chipset_sock_domain`，即定义修改为`type dev_unix_socket, dev_attr, file_attr, chipset_sock_domain;`。

### 删除冗余的白名单

当修正了不合理的Unix域套接字文件相关策略，但未同时删除白名单时，也会触发编译错误。关键错误信息为：`delete any unused data from "user" field in socket_whitelist.json file`，表示需要把指定路径从白名单文件`socket_whitelist.json`中白名单的`user`字段中去除。报错如下：

```text
Check whitelist of socket rule in user mode failed.
Violation list (types):
        "faultloggerd_socket",
Solution: delete any unused data from "user" field in socket_whitelist.json file.
```

## 参数属性检查

### 检查说明

为了控制系统参数的权限访问范围，系统参数的安全上下文定义时，其标签类型需要关联正确的属性。参数的访问范围与其需要关联的属性对应关系如表6所示。

**表6** 参数的访问范围与其安全上下文中类型需要关联的属性对应关系
| 访问范围 | 需关联的属性  |
| -------- | -------- |
| 仅在系统组件内部可用 | system_parameter_attr, system_internal_parameter_attr |
| 系统组件外部可读不可写 | system_parameter_attr, system_restricted_parameter_attr |
| 系统组件外部可读写 | system_parameter_attr, system_public_parameter_attr |
| 仅芯片组件内部可用 | vendor_parameter_attr, vendor_internal_parameter_attr |
| 芯片组件外部可读不可写 | vendor_parameter_attr, vendor_restricted_parameter_attr |
| 芯片组件外部可读写 | vendor_parameter_attr, vendor_public_parameter_attr |

### 编译拦截

若定义了属性类型，但属性未关联合理的参数的访问属性，则会触发编译报错。关键报错信息`Check attributes of parameter "parameter_attr" in user mode failed`，报错如下：

```text
Check attributes of parameter "parameter_attr" in user mode failed.
Violation list (type):
        "accessibility_param",
Solution:
1. Associate types with one of attributes (system_parameter_attr, vendor_parameter_attr).
2. Add types to "parameter_attr" field under "user" field in parameter_whitelist.json file.
```


### 拦截原因

出现这个报错是因为`accessibility_param`是一个系统参数的标签类型，定义是`type accessibility_param, parameter_attr;`，未关联正确的参数属性。

### 修复方法

主要有两种修复方式：

- 方式1： 修改不合理的策略，以满足要求，例如修改`accessibility_param`定义为`type accessibility_param, parameter_attr, system_parameter_attr, system_internal_parameter_attr;`，标记其是仅在系统组件内部可用的属性。


- 方式二：将报错中的类型添加到`//base/security/selinux_adapter/sepolicy/`下的白名单文件`parameter_whitelist.json`中。关键报错信息为`Add types to "xxx" field under "user" field in parameter_whitelist.json file`，`xxx`说明需要加入的白名单字段，`under "user" field`说明该类型定义在`user`和`developer`模式均生效，需要添加将白名单添加到`user`字段下的`parameter_attr`，白名单形式如下：

    ```text
    {
        "whitelist": {
            "user": {
                "parameter_attr": [
                    "accessibility_param",
                ]
            },
            "developer": {
                "parameter_attr": []
            }
        }
    }
    ```


### 删除冗余的白名单

当整改了不合理的类型定义，但未同时删除白名单，会触发编译报错。关键报错信息为`delete any unused data from "user" field under "parameter_attr" field in parameter_whitelist.json file`，表示需要把指定类型从白名单文件`parameter_whitelist.json`中白名单的`user`字段下的中`parameter_attr`去除。报错如下：

```text
Check whitelist of attribute "parameter_attr" in user mode failed.
Violation list (type):
        "accessibility_param",
Solution: delete any unused data from "user" field under "parameter_attr" field in parameter_whitelist.json file.
```

### 修改参数基线检查

由于跨系统组件、芯片组件可访问的参数在升级时容易引入不兼容的问题，系统组件外部可读不可写、系统组件外部可读写、芯片组件外部可读不可写、芯片组件外部可读写这四类参数有基线管控，避免随意新增跨组件访问的参数。

**基线检查的编译拦截**

新增和删除有基线管控的参数类型，都会触发编译报错。关键报错信息`Check baseline of attribute "xxx" in user mode failed`，`xxx`表示违反的基线的参数类型。

```text
Check baseline of attribute "system_restricted_parameter_attr" in user mode failed.
Violation list (type):
        "accesstoken_perm_param",
Solution: add the above list to "system_restricted_parameter_attr" field under "user" field in parameter_baseline.json file.

Check baselise of attribute "system_public_parameter_attr" in user mode failed.
Violation list (type):
        "accessibility_param",
Solution: delete any unused data from "user" field under "system_public_parameter_attr" field in parameter_baseline.json file.
```

**基线检查的报错说明**

该报错是由于`accesstoken_perm_param`定义为系统组件外部可读不可写，而参数类型不在对应参数属性的基线内；`accessibility_param`定义为系统组件内部可读写，该参数类型无需放在系统组件外部可读写的基线内。

```text
# accesstoken_perm_param的参数类型定义
type accesstoken_perm_param, parameter_attr, system_parameter_attr, system_restricted_parameter_attr;

# accessibility_param的参数类型定义
type accessibility_param, parameter_attr, system_parameter_attr, system_internal_parameter_attr;
```

#### 修复基线报错

新增和删除参数需要修改对应的属性的基线，基线在`//base/security/selinux_adapter/sepolicy/`下的`parameter_baseline.json`文件中。

新增基线的关键报错信息`add the above list to "system_restricted_parameter_attr" field under "user" field in parameter_baseline.json file`, 其中`under "user" field`说明该参数类型在`user`模式和`developer`模式中均生效，需将参数类型添加到`user`字段下的`system_restricted_parameter_attr`。

删除基线的关键报错信息`delete any unused data from "user" field under "system_public_parameter_attr" field in parameter_baseline.json file`, 其中`under "user" field`说明该参数类型在`user`模式和`developer`模式中均生效，需将参数类型从`user`字段下的`system_public_parameter_attr`删除。

基线文件形式如下：

```json
{
    "baseline": {
        "user": {
            "system_restricted_parameter_attr": [
                "accesstoken_perm_param"
            ],
            "system_public_parameter_attr": [],
            "vendor_restricted_parameter_attr": [],
            "vendor_public_parameter_attr": []
        },
        "developer": {
            "system_restricted_parameter_attr": [],
            "system_public_parameter_attr": [],
            "vendor_restricted_parameter_attr": [],
            "vendor_public_parameter_attr": []
        }
    }
}
```

## 文件路径和关联属性检查

### 检查说明

不同的目录用于存放特定的文件资源，例如，`/system/lib`路径下用于存放系统组件的共享库，需要尽量避免芯片组件进程加载执行。为了对这些文件权限进行访问范围的管理，要求特定目录下的文件配置的安全上下文关联对应的属性，具体的对应关系如表7所示。

**表7** 路径与其安全上下文中类型需要关联的属性对应关系
| 路径 | 关联的属性  |
| -------- | -------- |
| /vendor | vendor_file_attr |
| /vendor/bin | vendor_bin_file_attr |
| /eng_chipset/bin | vendor_bin_file_attr |
| /vendor/lib | vendor_lib_file_attr |
| /vendor/lib64 | vendor_lib_file_attr |
| /eng_chipset/lib | vendor_lib_file_attr |
| /eng_chipset/lib64 | vendor_lib_file_attr |
| /vendor/etc | vendor_etc_file_attr |
| /sys_prod | sys_prod_file_attr |
| /sys_prod/bin | sys_prod_bin_file_attr |
| /sys_prod/lib | sys_prod_lib_file_attr |
| /sys_prod/lib64/ | system_lib_file_attr |
| /sys_prod/etc | sys_prod_etc_file_attr |
| /system/lib | system_lib_file_attr |
| /system/lib64 | system_lib_file_attr |
| /eng_system/lib/ | system_lib_file_attr |
| /eng_system/lib64/ | system_lib_file_attr |
| /system/etc | system_etc_file_attr |
| /eng_system/etc/ | system_etc_file_attr |
| /chip_prod | chip_prod_file_attr |
| /chip_prod/bin | chip_prod_bin_file_attr |
| /chip_prod/etc | chip_prod_etc_file_attr |
| /chip_prod/lib | chip_prod_lib_file_attr |
| /chip_prod/lib64 | chip_prod_lib_file_attr |
| /chip_prod/lib64/passthrough | chip_prod_passthrough_file_attr |
| /cust | system_file_attr |
| /preload | system_file_attr |
| /data/vendor | data_vendor_file_attr |
| /data/service/ | data_service_file_attr |
| /data/data_chipset | data_chipset_file_attr |
| /dev | dev_attr |

### 编译拦截

配置 `file_contexts` 时，如果文件未关联所需属性，将会触发编译错误。关键报错信息`Check security context of file and its associated attributes in user mode failed`，报错如下：

```text        
Check security context of file and its associated attributes in user mode failed.


Check security context of file failed. There are two solutions:
        1: Associate following types with the attribute: type, attribute (file)
                hdf_devmgr_exec, vendor_file_attr       (/vendor/bin/hdf_devmgr)
                hdf_devmgr_exec, vendor_bin_file_attr   (/vendor/bin/hdf_devmgr)

        2: Add following file path to "user" field in file_contexts_typeattr_whitelist.json file.
                Change "permissive_list" of "path": /vendor
                        "/vendor/bin/hdf_devmgr"


                Change "permissive_list" of "path": /vendor/bin
                        "/vendor/bin/hdf_devmgr"
```

### 拦截原因

上述报错是因为`/vendor/bin/hdf_devmgr`文件的安全上下文及其相关的类型定义在不符合要求。
由于文件在`/vendor`、`/vendor/bin`下，`hdf_devmgr_exec`需要同时关联`vendor_file_attr`和`vendor_bin_file_attr`的属性。
而`hdf_devmgr_exec`的定义不符合该路径下文件类型属性的要求。相关策略定义如下：

```text
# file_contexts中安全上下文的定义
/vendor/bin/hdf_devmgr        u:object_r:hdf_devmgr_exec:s0

# 类型在te里的定义
type hdf_devmgr_exec, exec_attr, file_attr, system_file_attr;
```


### 修复方法

主要有两种修复方式：

- 方式一：修改不合理的file_contexts或类型定义，以满足要求。

    例如，修改`hdf_devmgr_exec`的定义为`type hdf_devmgr_exec, exec_attr, file_attr, vendor_file_attr, vendor_bin_file_attr;`

- 方式二：将路径添加到`//base/security/selinux_adapter/sepolicy/`下的白名单文件`file_contexts_typeattr_whitelist.json`中。

    `Change "permissive_list" of "path": xxx`中说明该路径违反了的`xxx`路径下需要关联的属性，须添加到对应`xxx`的白名单内。报错中的`to "user" field`提示说明需要加入`user`字段的白名单。

    修改白名单文件需要评估安全性和合理性，审慎修改。白名单形式如下：

    ```json
    {
        "whitelist": [
            {
                "path": "/vendor",
                "permissive_list": {
                    "user": [
                        "/vendor/bin/hdf_devmgr",
                    ],
                    "developer": []
                }
            },
            {
                "path": "/vendor/bin",
                "permissive_list": {
                    "user": [
                        "/vendor/bin/hdf_devmgr"
                    ],
                    "developer": []
                }
            },
            ...
        ]
    }
    ```

### 删除冗余的白名单

当整改路径的 `file_contexts` 后，未同时删除白名单时，会触发编译报错。关键报错信息`Add following file path to "user" field in file_contexts_typeattr_whitelist.json file`。后续提示 `Change "permissive_list" of "path": xxx` 表示需要将指定路径从 `xxx` 的白名单 `permissive_list` 中移除。拦截提示中的 `to "user" field` 说明该路径需要从 `user` 项中移除。报错如下：

```
Check security context of file and its associated attributes in user mode failed.


Check security context of file failed. There are two solutions:
    1: Associate following types with the attribute: type, attribute (file)
            hdf_devhost_exec, vendor_file_attr      (/vendor/bin/hdf_devhost)
            hdf_devhost_exec, vendor_bin_file_attr  (/vendor/bin/hdf_devhost)

    2: Add following file path to "user" field in file_contexts_typeattr_whitelist.json file.
            Change "permissive_list" of "path": /vendor
                    "/vendor/bin/hdf_devhost"


            Change "permissive_list" of "path": /vendor/bin
                    "/vendor/bin/hdf_devhost"
```

## 虚拟文件系统的标签类型关联属性检查

### 检查说明

为了对不同文件系统挂载的节点访问权限进行管理，要求挂载到不同文件系统的文件标签类型关联对应的属性如表8所示。

**表8** 文件系统与其安全上下文中类型需要关联的属性对应关系
| 文件系统 | 关联的属性  |
| -------- | -------- |
| proc | proc_attr |
| sysfs | sysfs_attr |
| debugfs | debugfs_attr |
| tracefs | debugfs_attr |

### 编译拦截

配置virtfs_contexts没有关联要求的属性会触发编译报错。关键报错信息`Check security context of filesystem in user mode failed`，报错如下：

```text
Check security context of filesystem in user mode failed.

The node mounted to "tracefs" should be associated with the attribute "debugfs_attr"
            tracefs_trace_marker_file
There are two solutions:
1. Associate types with the attribute "debugfs_attr".
2. Add types to "user" field under "permissive_list" field of "tracefs" in virtfs_whitelist.json file.
```

### 拦截原因

报错原因是节点`/trace_marker`挂载到`tracefs`文件系统，其安全上下文`u:object_r:tracefs_trace_marker_file:s0`的类型`tracefs_trace_marker_file`需要关联属性`debugfs_attr`，而实际的类型定义中未关联指定的属性，不符合该文件系统对安全上下文类型的定义要求，导致拦截报错。相关策略如下：

```text
# 节点的安全上下文定义
genfscon tracefs /trace_marker u:object_r:tracefs_trace_marker_file:s0

# 类型的属性定义
type tracefs_trace_marker_file, fs_attr;
```


### 修复方法

主要有两种修复方式：

- 方式一：修改不合理的`virtfs_contexts`或类型定义，以满足要求。

    例如，修改`tracefs_trace_marker_file`定义为`type tracefs_trace_marker_file, fs_attr, debugfs_attr;`

- 方式二：将节点添加到`//base/security/selinux_adapter/sepolicy/`下的白名单文件`virtfs_whitelist.json`中。

    提示信息中`Add types to "user" field under "permissive_list" field of "xxx" in virtfs_whitelist.json file`中说明该节点违反了的`xxx`文件系统下类型需要关联的属性，`to "user" field`说明该类型在`user`和`developer`模式均生效，需添加文件的`virtfs`为`xxx`的项的白名单`permissive_list`下`user`字段内。白名单的文件形式如下：

    ```json
    {
        ...
            {
                "virtfs": "tracefs",
                "permissive_list": {
                    "user": [
                        "tracefs_trace_marker_file"
                    ],
                    "developer": []
                }
            }
    }
    ```


### 删除冗余的白名单

整改路径中的不合理的 `virtfs_contexts` 后，若未删除白名单，会触发编译报错。关键报错信息为`Delete any unused data from "user" field under "permissive_list" of "xxx" in virtfs_whitelist.json file`，表示需要将指定路径从白名单文件 `virtfs_whitelist.json` 中移除。具体来说，需要在 `virtfs` 为 `xxx` 的项中，去掉 `permissive_list` 中的冗余路径；`from "user" field`则说明该类型在`user`和`developer`模式下均生效，需要从`user`字段中去除。报错如下：


```text
Check security context of filesystem in user mode failed.

Delete any unused data from "user" field under "permissive_list" field of "tracefs" in virtfs_whitelist.json file:
            tracefs_trace_marker_file
```
