# PrintErrorCode

```TypeScript
enum PrintErrorCode
```

打印错误代码的枚举。

**起始版本：** 14

<!--Device-print-enum PrintErrorCode--><!--Device-print-enum PrintErrorCode-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## E_PRINT_EDM_POLICY_RESTRICTED

```TypeScript
E_PRINT_EDM_POLICY_RESTRICTED = 13100015
```

打印操作被EDM策略限制。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PrintErrorCode-E_PRINT_EDM_POLICY_RESTRICTED = 13100015--><!--Device-PrintErrorCode-E_PRINT_EDM_POLICY_RESTRICTED = 13100015-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## E_PRINT_FILE_IO

```TypeScript
E_PRINT_FILE_IO = 13100007
```

表示文件输入/输出错误，请检查文件路径、文件状态和操作是否正确。

**起始版本：** 14

<!--Device-PrintErrorCode-E_PRINT_FILE_IO = 13100007--><!--Device-PrintErrorCode-E_PRINT_FILE_IO = 13100007-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## E_PRINT_GENERIC_FAILURE

```TypeScript
E_PRINT_GENERIC_FAILURE = 13100001
```

表示一般打印失败，请检查打印服务运行状态并重试。

**起始版本：** 14

<!--Device-PrintErrorCode-E_PRINT_GENERIC_FAILURE = 13100001--><!--Device-PrintErrorCode-E_PRINT_GENERIC_FAILURE = 13100001-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## E_PRINT_INVALID_EXTENSION

```TypeScript
E_PRINT_INVALID_EXTENSION = 13100004
```

表示打印扩展无效，请检查扩展能力实现是否正确。

**起始版本：** 14

<!--Device-PrintErrorCode-E_PRINT_INVALID_EXTENSION = 13100004--><!--Device-PrintErrorCode-E_PRINT_INVALID_EXTENSION = 13100004-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## E_PRINT_INVALID_PARAMETER

```TypeScript
E_PRINT_INVALID_PARAMETER = 401
```

表示无效的参数，请检查参数类型和取值范围。

**起始版本：** 14

<!--Device-PrintErrorCode-E_PRINT_INVALID_PARAMETER = 401--><!--Device-PrintErrorCode-E_PRINT_INVALID_PARAMETER = 401-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## E_PRINT_INVALID_PRINT_JOB

```TypeScript
E_PRINT_INVALID_PRINT_JOB = 13100006
```

表示打印任务无效，请检查任务ID和状态是否正确。

**起始版本：** 14

<!--Device-PrintErrorCode-E_PRINT_INVALID_PRINT_JOB = 13100006--><!--Device-PrintErrorCode-E_PRINT_INVALID_PRINT_JOB = 13100006-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## E_PRINT_INVALID_PRINTER

```TypeScript
E_PRINT_INVALID_PRINTER = 13100005
```

表示打印机无效，请确认打印机ID及打印机信息是否正确后重试。

**起始版本：** 14

<!--Device-PrintErrorCode-E_PRINT_INVALID_PRINTER = 13100005--><!--Device-PrintErrorCode-E_PRINT_INVALID_PRINTER = 13100005-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## E_PRINT_NO_PERMISSION

```TypeScript
E_PRINT_NO_PERMISSION = 201
```

表示无权限，请根据对应接口的权限要求申请所需权限，并在配置文件中声明。

**起始版本：** 14

<!--Device-PrintErrorCode-E_PRINT_NO_PERMISSION = 201--><!--Device-PrintErrorCode-E_PRINT_NO_PERMISSION = 201-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## E_PRINT_NONE

```TypeScript
E_PRINT_NONE = 0
```

表示没有错误。

**起始版本：** 14

<!--Device-PrintErrorCode-E_PRINT_NONE = 0--><!--Device-PrintErrorCode-E_PRINT_NONE = 0-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## E_PRINT_RPC_FAILURE

```TypeScript
E_PRINT_RPC_FAILURE = 13100002
```

表示RPC失败，请检查RPC通信状态并重试。

**起始版本：** 14

<!--Device-PrintErrorCode-E_PRINT_RPC_FAILURE = 13100002--><!--Device-PrintErrorCode-E_PRINT_RPC_FAILURE = 13100002-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## E_PRINT_SERVER_FAILURE

```TypeScript
E_PRINT_SERVER_FAILURE = 13100003
```

表示打印服务失败，请检查打印服务是否正常运行并重试。

**起始版本：** 14

<!--Device-PrintErrorCode-E_PRINT_SERVER_FAILURE = 13100003--><!--Device-PrintErrorCode-E_PRINT_SERVER_FAILURE = 13100003-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## E_PRINT_SMB_CONNECTION_FAILURE

```TypeScript
E_PRINT_SMB_CONNECTION_FAILURE = 13100013
```

表示SMB协议共享打印机连接失败（发生网络错误、主机不可达或端口被阻止）。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PrintErrorCode-E_PRINT_SMB_CONNECTION_FAILURE = 13100013--><!--Device-PrintErrorCode-E_PRINT_SMB_CONNECTION_FAILURE = 13100013-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## E_PRINT_SMB_INVALID_CREDENTIALS

```TypeScript
E_PRINT_SMB_INVALID_CREDENTIALS = 13100014
```

表示SMB协议共享打印机账号/密码错误。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PrintErrorCode-E_PRINT_SMB_INVALID_CREDENTIALS = 13100014--><!--Device-PrintErrorCode-E_PRINT_SMB_INVALID_CREDENTIALS = 13100014-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## E_PRINT_SMB_LOGIN_LOCKOUT

```TypeScript
E_PRINT_SMB_LOGIN_LOCKOUT = 13100012
```

表示当前SMB协议共享打印机账号因多次登录失败而被锁定。请等待账号解锁后重试，或联系管理员处理。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PrintErrorCode-E_PRINT_SMB_LOGIN_LOCKOUT = 13100012--><!--Device-PrintErrorCode-E_PRINT_SMB_LOGIN_LOCKOUT = 13100012-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## E_PRINT_TOO_MANY_FILES

```TypeScript
E_PRINT_TOO_MANY_FILES = 13100010
```

表示文件数量超过上限，当前上限99个。

**起始版本：** 18

<!--Device-PrintErrorCode-E_PRINT_TOO_MANY_FILES = 13100010--><!--Device-PrintErrorCode-E_PRINT_TOO_MANY_FILES = 13100010-End-->

**系统能力：** SystemCapability.Print.PrintFramework
