# CertificateDialogErrorCode

表示调用证书管理对话框相关API的错误码。

**起始版本：** 13

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## ERROR_GENERIC

```TypeScript
ERROR_GENERIC = 29700001
```

表示调用接口时发生内部错误。
例如IPC通信失败、内存操作失败、文件操作失败。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## ERROR_OPERATION_CANCELED

```TypeScript
ERROR_OPERATION_CANCELED = 29700002
```

表示用户在证书管理对话框中取消操作。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## ERROR_OPERATION_FAILED

```TypeScript
ERROR_OPERATION_FAILED = 29700003
```

表示用户在证书管理对话框中操作失败。
例如安装证书失败。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## ERROR_DEVICE_NOT_SUPPORTED

```TypeScript
ERROR_DEVICE_NOT_SUPPORTED = 29700004
```

表示接口不支持该设备

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## ERROR_NOT_COMPLY_SECURITY_POLICY

```TypeScript
ERROR_NOT_COMPLY_SECURITY_POLICY = 29700005
```

表示该操作不符合设备安全策略。
例如设备不允许用户管理GLOBAL_USER的CA证书。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## ERROR_PARAMETER_VALIDATION_FAILED

```TypeScript
ERROR_PARAMETER_VALIDATION_FAILED = 29700006
```

表示输入参数校验失败。

例如：参数格式不正确、取值范围无效

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## ERROR_NO_AVAILABLE_CERTIFICATE

```TypeScript
ERROR_NO_AVAILABLE_CERTIFICATE = 29700007
```

表示没有可用证书。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.CertificateManagerDialog

