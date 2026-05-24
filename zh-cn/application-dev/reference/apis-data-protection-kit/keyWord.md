# 术语表

本术语表按英文首字母排序。

## A

**AccountType; 账号类型**

授权账号类型枚举，包括云账号（CLOUD_ACCOUNT）、域账号（DOMAIN_ACCOUNT）和企业账号（ENTERPRISE_ACCOUNT），用于标识DLP文件授权用户的账号类型。

**ActionFlagType; 操作标志类型**

对DLP文件可执行的操作类型枚举，包括查看、保存、另存为、编辑、截屏、屏幕共享、录屏、复制、打印、导出和权限修改等操作权限标志，DLP沙箱应用可根据权限状态对相应按钮进行置灰处理。

**AuthUser; 授权用户**

被授权访问DLP文件的用户数据结构，包含授权账号、账号类型、授予的权限以及授权到期时间等信息，用于定义哪些用户可以访问特定的DLP文件及其权限范围。

## C

**CustomProperty; 自定义属性**

企业定制策略配置结构，包含企业策略JSON字符串和可选的查询选项，用于企业账号生成和管理企业DLP文件时配置定制化的防护策略。

## D

**Data Loss Prevention (DLP); 数据防泄漏**

系统提供的系统级数据防泄漏解决方案，提供跨设备的文件权限管理、加密存储、授权访问等能力。通过DLP技术，可以保护敏感文件的安全性，防止数据泄漏。

**DLP File; DLP文件**

经过数据防泄漏加密保护的权限受控文件，扩展名为.dlp。仅授权列表内的用户可以打开，授权分为完全控制权限和只读权限，系统会根据授权策略限制用户对文件的操作权限。

**DLP File Access; DLP文件访问权限**

DLP文件授权类型枚举，包括无权限（NO_PERMISSION）、只读权限（READ_ONLY）、编辑权限（CONTENT_EDIT）和完全控制权限（FULL_CONTROL），用于定义用户对DLP文件的基础访问级别。

**DLP Manager; DLP管理器**

DLP权限管理应用，用于管理DLP文件的权限设置、授权用户配置等。可通过startDLPManagerForResult接口以无边框形式打开，完成权限管理后返回结果码和返回数据。

**DLP Manager Result; DLP管理器返回结果**

打开DLP权限管理应用并退出后返回的结果数据结构，包含结果码和Want数据，用于向调用方返回权限管理操作的结果。

**DLP Permission Info; DLP权限信息**

DLP文件的权限信息数据结构，包含DLP文件访问权限（dlpFileAccess）和详细操作权限标志（flags），用于描述用户对DLP文件的具体权限配置。

**DLP Property; DLP属性**

DLP文件的授权相关信息数据结构，包含权限设置者账号信息、授权用户列表、联系人账号、是否允许离线打开、授予所有人的权限、文件权限到期时间戳等配置信息，用于定义DLP文件的完整授权策略。

**DLP Sandbox; DLP沙箱**

用于打开DLP文件的隔离运行环境。当打开DLP文件时自动安装沙箱，关闭DLP文件时自动卸载沙箱。沙箱环境提供应用隔离和数据保护，防止DLP文件中的敏感数据泄漏到非受控环境。

**DLP Sandbox Info; DLP沙箱信息**

DLP沙箱的信息数据结构，包含沙箱应用索引、沙箱应用的tokenID以及可选的被绑定的沙箱应用索引，用于描述沙箱环境的配置状态。

**DLP Sandbox State; DLP沙箱状态**

DLP沙箱身份数据结构，包含应用包名和沙箱应用索引，用于标识沙箱应用的身份状态，在沙箱卸载事件监听中使用。

## E

**Enterprise Policy; 企业策略**

企业定制防护策略数据结构，包含企业策略JSON字符串，用于企业账号设置和管理应用防护策略，实现企业级的DLP防护能力。

## F

**Filesystem in Userspace (FUSE); 用户空间文件系统**

用于管理DLP文件的虚拟文件系统。通过FUSE技术创建link文件，实现对DLP文件的透明访问和管理。对link文件的读写操作会同步到DLP文件，提供便捷的文件操作接口。

## G

**Gathering Policy Type; 聚合策略类型**

DLP沙箱聚合策略类型枚举，包括聚合（GATHERING）和非聚合（NON_GATHERING）。聚合表示同一权限类型的DLP文件在同一沙箱内打开，非聚合表示不同DLP文件在不同沙箱打开。

## R

**Retention Sandbox; 保留沙箱**

保持沙箱状态的沙箱环境。设置沙箱保留状态后，DLP文件关闭时自动卸载沙箱策略暂时失效，沙箱环境将保持运行状态，避免频繁安装卸载沙箱，提升用户体验。

**Retention Sandbox Info; 保留沙箱信息**

保留沙箱的信息数据结构，包含沙箱应用索引、应用包名和文件URI列表，用于描述哪些文件保持在沙箱环境中打开。

## S

**Sandbox App Config; 沙箱应用配置**

沙箱应用的配置信息，可通过setSandboxAppConfig设置、getSandboxAppConfig获取、cleanSandboxAppConfig清理。用于配置沙箱应用的自定义行为和参数。

## A (接口/类型)

**Accessed DLP File Info; 已访问DLP文件信息**

被打开的DLP文件信息数据结构，包含DLP文件的URI和最近打开时间，用于记录和查询DLP文件的访问历史。

**Action Type; 动作类型**

文件权限到期后执行的动作枚举，包括不允许打开（NOT_OPEN）和允许编辑权限打开（OPEN），用于定义DLP文件权限到期后的访问策略。

**AuthUser; 授权用户**

见授权用户。

**Dlp Conn Manager; DLP连接管理器**

用于管理DLP连接插件注册和注销的类，提供registerPlugin和unregisterPlugin接口，将回调能力在系统服务中注册或注销，实现DLP连云能力的扩展。

**Dlp Conn Plugin; DLP连接插件**

DLP连接插件接口，提供connectServer方法，用于系统服务侧调用前端通信能力，处理连云请求并通过回调返回结果，实现企业账号服务器的连接能力。

**Dlp File Query Options; DLP文件查询选项**

企业DLP文件的查询选项数据结构，包含用户定义分类标签，用于查询和关闭符合指定条件的已打开企业DLP文件。