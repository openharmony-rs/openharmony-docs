# CertificateDialogErrorCode

```TypeScript
export enum CertificateDialogErrorCode
```

Enumerates the error codes reported when the certificate management dialog box APIs are called.

**Since:** 13

<!--Device-certificateManagerDialog-export enum CertificateDialogErrorCode--><!--Device-certificateManagerDialog-export enum CertificateDialogErrorCode-End-->

**System capability:** SystemCapability.Security.CertificateManagerDialog

## ERROR_GENERIC

```TypeScript
ERROR_GENERIC = 29700001
```

Internal error. For example, IPC communication failure, memory operation failure, and file operation failure.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

<!--Device-CertificateDialogErrorCode-ERROR_GENERIC = 29700001--><!--Device-CertificateDialogErrorCode-ERROR_GENERIC = 29700001-End-->

**System capability:** SystemCapability.Security.CertificateManagerDialog

## ERROR_OPERATION_CANCELED

```TypeScript
ERROR_OPERATION_CANCELED = 29700002
```

The user canceled the operation in the certificate management dialog box.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

<!--Device-CertificateDialogErrorCode-ERROR_OPERATION_CANCELED = 29700002--><!--Device-CertificateDialogErrorCode-ERROR_OPERATION_CANCELED = 29700002-End-->

**System capability:** SystemCapability.Security.CertificateManagerDialog

## ERROR_OPERATION_FAILED

```TypeScript
ERROR_OPERATION_FAILED = 29700003
```

The operation fails in the certificate management dialog box. For example, the certificate fails to be installed.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

<!--Device-CertificateDialogErrorCode-ERROR_OPERATION_FAILED = 29700003--><!--Device-CertificateDialogErrorCode-ERROR_OPERATION_FAILED = 29700003-End-->

**System capability:** SystemCapability.Security.CertificateManagerDialog

## ERROR_DEVICE_NOT_SUPPORTED

```TypeScript
ERROR_DEVICE_NOT_SUPPORTED = 29700004
```

The device does not support the API called.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

<!--Device-CertificateDialogErrorCode-ERROR_DEVICE_NOT_SUPPORTED = 29700004--><!--Device-CertificateDialogErrorCode-ERROR_DEVICE_NOT_SUPPORTED = 29700004-End-->

**System capability:** SystemCapability.Security.CertificateManagerDialog

## ERROR_NOT_COMPLY_SECURITY_POLICY

```TypeScript
ERROR_NOT_COMPLY_SECURITY_POLICY = 29700005
```

The device security policy is not met when the API is called. For example, the device does not allow users to manage the CA certificate of GLOBAL_USER.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

<!--Device-CertificateDialogErrorCode-ERROR_NOT_COMPLY_SECURITY_POLICY = 29700005--><!--Device-CertificateDialogErrorCode-ERROR_NOT_COMPLY_SECURITY_POLICY = 29700005-End-->

**System capability:** SystemCapability.Security.CertificateManagerDialog

## ERROR_PARAMETER_VALIDATION_FAILED

```TypeScript
ERROR_PARAMETER_VALIDATION_FAILED = 29700006
```

The input parameter verification fails.

For example, the parameter format is incorrect or the parameter range is invalid.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

<!--Device-CertificateDialogErrorCode-ERROR_PARAMETER_VALIDATION_FAILED = 29700006--><!--Device-CertificateDialogErrorCode-ERROR_PARAMETER_VALIDATION_FAILED = 29700006-End-->

**System capability:** SystemCapability.Security.CertificateManagerDialog

## ERROR_NO_AVAILABLE_CERTIFICATE

```TypeScript
ERROR_NO_AVAILABLE_CERTIFICATE = 29700007
```

No certificate is available.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

<!--Device-CertificateDialogErrorCode-ERROR_NO_AVAILABLE_CERTIFICATE = 29700007--><!--Device-CertificateDialogErrorCode-ERROR_NO_AVAILABLE_CERTIFICATE = 29700007-End-->

**System capability:** SystemCapability.Security.CertificateManagerDialog

## ERROR_OPERATION_TIMEOUT

```TypeScript
ERROR_OPERATION_TIMEOUT = 29700009
```

The operation in the certificate management dialog box timed out.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-CertificateDialogErrorCode-ERROR_OPERATION_TIMEOUT = 29700009--><!--Device-CertificateDialogErrorCode-ERROR_OPERATION_TIMEOUT = 29700009-End-->

**System capability:** SystemCapability.Security.CertificateManagerDialog

## ERROR_NOT_CONCURRENT_SUPPORT

```TypeScript
ERROR_NOT_CONCURRENT_SUPPORT = 29700010
```

The API does not support concurrent calls.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-CertificateDialogErrorCode-ERROR_NOT_CONCURRENT_SUPPORT = 29700010--><!--Device-CertificateDialogErrorCode-ERROR_NOT_CONCURRENT_SUPPORT = 29700010-End-->

**System capability:** SystemCapability.Security.CertificateManagerDialog
