# PrintErrorCode

```TypeScript
enum PrintErrorCode
```

Enumerates the print error codes.

**Since:** 14

<!--Device-print-enum PrintErrorCode--><!--Device-print-enum PrintErrorCode-End-->

**System capability:** SystemCapability.Print.PrintFramework

## E_PRINT_EDM_POLICY_RESTRICTED

```TypeScript
E_PRINT_EDM_POLICY_RESTRICTED = 13100015
```

The print operation is restricted by the EDM policy.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintErrorCode-E_PRINT_EDM_POLICY_RESTRICTED = 13100015--><!--Device-PrintErrorCode-E_PRINT_EDM_POLICY_RESTRICTED = 13100015-End-->

**System capability:** SystemCapability.Print.PrintFramework

## E_PRINT_FILE_IO

```TypeScript
E_PRINT_FILE_IO = 13100007
```

File input/output error. Check whether the file path, file status, and operation are correct.

**Since:** 14

<!--Device-PrintErrorCode-E_PRINT_FILE_IO = 13100007--><!--Device-PrintErrorCode-E_PRINT_FILE_IO = 13100007-End-->

**System capability:** SystemCapability.Print.PrintFramework

## E_PRINT_GENERIC_FAILURE

```TypeScript
E_PRINT_GENERIC_FAILURE = 13100001
```

Generic printing failure. Check the running status of the print service and try again.

**Since:** 14

<!--Device-PrintErrorCode-E_PRINT_GENERIC_FAILURE = 13100001--><!--Device-PrintErrorCode-E_PRINT_GENERIC_FAILURE = 13100001-End-->

**System capability:** SystemCapability.Print.PrintFramework

## E_PRINT_INVALID_EXTENSION

```TypeScript
E_PRINT_INVALID_EXTENSION = 13100004
```

Invalid print extension. Check whether the extension capability is correctly implemented.

**Since:** 14

<!--Device-PrintErrorCode-E_PRINT_INVALID_EXTENSION = 13100004--><!--Device-PrintErrorCode-E_PRINT_INVALID_EXTENSION = 13100004-End-->

**System capability:** SystemCapability.Print.PrintFramework

## E_PRINT_INVALID_PARAMETER

```TypeScript
E_PRINT_INVALID_PARAMETER = 401
```

Invalid parameter. Check the parameter type and value range.

**Since:** 14

<!--Device-PrintErrorCode-E_PRINT_INVALID_PARAMETER = 401--><!--Device-PrintErrorCode-E_PRINT_INVALID_PARAMETER = 401-End-->

**System capability:** SystemCapability.Print.PrintFramework

## E_PRINT_INVALID_PRINT_JOB

```TypeScript
E_PRINT_INVALID_PRINT_JOB = 13100006
```

Invalid print job. Check whether the job ID and status are correct.

**Since:** 14

<!--Device-PrintErrorCode-E_PRINT_INVALID_PRINT_JOB = 13100006--><!--Device-PrintErrorCode-E_PRINT_INVALID_PRINT_JOB = 13100006-End-->

**System capability:** SystemCapability.Print.PrintFramework

## E_PRINT_INVALID_PRINTER

```TypeScript
E_PRINT_INVALID_PRINTER = 13100005
```

Invalid printer. Check whether the printer ID and printer information are correct and try again.

**Since:** 14

<!--Device-PrintErrorCode-E_PRINT_INVALID_PRINTER = 13100005--><!--Device-PrintErrorCode-E_PRINT_INVALID_PRINTER = 13100005-End-->

**System capability:** SystemCapability.Print.PrintFramework

## E_PRINT_NO_PERMISSION

```TypeScript
E_PRINT_NO_PERMISSION = 201
```

No permission. Request the required permission based on the permission requirements of the corresponding API and declare the permission in the configuration file.

**Since:** 14

<!--Device-PrintErrorCode-E_PRINT_NO_PERMISSION = 201--><!--Device-PrintErrorCode-E_PRINT_NO_PERMISSION = 201-End-->

**System capability:** SystemCapability.Print.PrintFramework

## E_PRINT_NONE

```TypeScript
E_PRINT_NONE = 0
```

No error.

**Since:** 14

<!--Device-PrintErrorCode-E_PRINT_NONE = 0--><!--Device-PrintErrorCode-E_PRINT_NONE = 0-End-->

**System capability:** SystemCapability.Print.PrintFramework

## E_PRINT_RPC_FAILURE

```TypeScript
E_PRINT_RPC_FAILURE = 13100002
```

RPC failure. Check the RPC communication status and try again.

**Since:** 14

<!--Device-PrintErrorCode-E_PRINT_RPC_FAILURE = 13100002--><!--Device-PrintErrorCode-E_PRINT_RPC_FAILURE = 13100002-End-->

**System capability:** SystemCapability.Print.PrintFramework

## E_PRINT_SERVER_FAILURE

```TypeScript
E_PRINT_SERVER_FAILURE = 13100003
```

Print service failure. Check whether the print service is running properly and try again.

**Since:** 14

<!--Device-PrintErrorCode-E_PRINT_SERVER_FAILURE = 13100003--><!--Device-PrintErrorCode-E_PRINT_SERVER_FAILURE = 13100003-End-->

**System capability:** SystemCapability.Print.PrintFramework

## E_PRINT_SMB_CONNECTION_FAILURE

```TypeScript
E_PRINT_SMB_CONNECTION_FAILURE = 13100013
```

The SMB-based shared printer fails to be connected (due to a network error, unreachable host, or blocked port).

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintErrorCode-E_PRINT_SMB_CONNECTION_FAILURE = 13100013--><!--Device-PrintErrorCode-E_PRINT_SMB_CONNECTION_FAILURE = 13100013-End-->

**System capability:** SystemCapability.Print.PrintFramework

## E_PRINT_SMB_INVALID_CREDENTIALS

```TypeScript
E_PRINT_SMB_INVALID_CREDENTIALS = 13100014
```

The SMB-based shared printer account or password is incorrect.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintErrorCode-E_PRINT_SMB_INVALID_CREDENTIALS = 13100014--><!--Device-PrintErrorCode-E_PRINT_SMB_INVALID_CREDENTIALS = 13100014-End-->

**System capability:** SystemCapability.Print.PrintFramework

## E_PRINT_SMB_LOGIN_LOCKOUT

```TypeScript
E_PRINT_SMB_LOGIN_LOCKOUT = 13100012
```

The SMB-based shared printer account is locked due to multiple failed login attempts. Try again after the account is unlocked, or contact the administrator.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintErrorCode-E_PRINT_SMB_LOGIN_LOCKOUT = 13100012--><!--Device-PrintErrorCode-E_PRINT_SMB_LOGIN_LOCKOUT = 13100012-End-->

**System capability:** SystemCapability.Print.PrintFramework

## E_PRINT_TOO_MANY_FILES

```TypeScript
E_PRINT_TOO_MANY_FILES = 13100010
```

Excessive files. Maximum number: 99.

**Since:** 18

<!--Device-PrintErrorCode-E_PRINT_TOO_MANY_FILES = 13100010--><!--Device-PrintErrorCode-E_PRINT_TOO_MANY_FILES = 13100010-End-->

**System capability:** SystemCapability.Print.PrintFramework
