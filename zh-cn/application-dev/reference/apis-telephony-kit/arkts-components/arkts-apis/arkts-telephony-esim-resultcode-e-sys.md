# ResultCode（系统接口）

```TypeScript
export enum ResultCode
```

结果码。

**起始版本：** 18

<!--Device-eSIM-export enum ResultCode--><!--Device-eSIM-export enum ResultCode-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_SOLVABLE_ERRORS

```TypeScript
RESULT_SOLVABLE_ERRORS = -2
```

用户必须解决可解决的错误。

**起始版本：** 18

<!--Device-ResultCode-RESULT_SOLVABLE_ERRORS = -2--><!--Device-ResultCode-RESULT_SOLVABLE_ERRORS = -2-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_MUST_DISABLE_PROFILE

```TypeScript
RESULT_MUST_DISABLE_PROFILE = -1
```

必须禁用活动配置文件才能执行操作。

**起始版本：** 18

<!--Device-ResultCode-RESULT_MUST_DISABLE_PROFILE = -1--><!--Device-ResultCode-RESULT_MUST_DISABLE_PROFILE = -1-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_OK

```TypeScript
RESULT_OK = 0
```

成功。

**起始版本：** 18

<!--Device-ResultCode-RESULT_OK = 0--><!--Device-ResultCode-RESULT_OK = 0-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_GET_EID_FAILED

```TypeScript
RESULT_GET_EID_FAILED = 201
```

获取EID失败。

**起始版本：** 18

<!--Device-ResultCode-RESULT_GET_EID_FAILED = 201--><!--Device-ResultCode-RESULT_GET_EID_FAILED = 201-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_ACTIVATION_CODE_CHANGED

```TypeScript
RESULT_ACTIVATION_CODE_CHANGED = 203
```

最终用户确认后，激活码将被更改。

**起始版本：** 18

<!--Device-ResultCode-RESULT_ACTIVATION_CODE_CHANGED = 203--><!--Device-ResultCode-RESULT_ACTIVATION_CODE_CHANGED = 203-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_ACTIVATION_CODE_INVALID

```TypeScript
RESULT_ACTIVATION_CODE_INVALID = 204
```

激活码无效。

**起始版本：** 18

<!--Device-ResultCode-RESULT_ACTIVATION_CODE_INVALID = 204--><!--Device-ResultCode-RESULT_ACTIVATION_CODE_INVALID = 204-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_SMDP_ADDRESS_INVALID

```TypeScript
RESULT_SMDP_ADDRESS_INVALID = 205
```

SM-DP+服务器地址非法。

**起始版本：** 18

<!--Device-ResultCode-RESULT_SMDP_ADDRESS_INVALID = 205--><!--Device-ResultCode-RESULT_SMDP_ADDRESS_INVALID = 205-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_EUICC_INFO_INVALID

```TypeScript
RESULT_EUICC_INFO_INVALID = 206
```

无效的eUICC信息。

**起始版本：** 18

<!--Device-ResultCode-RESULT_EUICC_INFO_INVALID = 206--><!--Device-ResultCode-RESULT_EUICC_INFO_INVALID = 206-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_TLS_HANDSHAKE_FAILED

```TypeScript
RESULT_TLS_HANDSHAKE_FAILED = 207
```

TLS握手失败。

**起始版本：** 18

<!--Device-ResultCode-RESULT_TLS_HANDSHAKE_FAILED = 207--><!--Device-ResultCode-RESULT_TLS_HANDSHAKE_FAILED = 207-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_CERTIFICATE_IO_ERROR

```TypeScript
RESULT_CERTIFICATE_IO_ERROR = 208
```

证书网络连接错误。

**起始版本：** 18

<!--Device-ResultCode-RESULT_CERTIFICATE_IO_ERROR = 208--><!--Device-ResultCode-RESULT_CERTIFICATE_IO_ERROR = 208-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_CERTIFICATE_RESPONSE_TIMEOUT

```TypeScript
RESULT_CERTIFICATE_RESPONSE_TIMEOUT = 209
```

证书地址无效或响应超时。

**起始版本：** 18

<!--Device-ResultCode-RESULT_CERTIFICATE_RESPONSE_TIMEOUT = 209--><!--Device-ResultCode-RESULT_CERTIFICATE_RESPONSE_TIMEOUT = 209-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_AUTHENTICATION_FAILED

```TypeScript
RESULT_AUTHENTICATION_FAILED = 210
```

鉴权失败。

**起始版本：** 18

<!--Device-ResultCode-RESULT_AUTHENTICATION_FAILED = 210--><!--Device-ResultCode-RESULT_AUTHENTICATION_FAILED = 210-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_RESPONSE_HTTP_FAILED

```TypeScript
RESULT_RESPONSE_HTTP_FAILED = 211
```

HTTP响应失败。

**起始版本：** 18

<!--Device-ResultCode-RESULT_RESPONSE_HTTP_FAILED = 211--><!--Device-ResultCode-RESULT_RESPONSE_HTTP_FAILED = 211-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_CONFIRMATION_CODE_INCORRECT

```TypeScript
RESULT_CONFIRMATION_CODE_INCORRECT = 212
```

确认码不正确。

**起始版本：** 18

<!--Device-ResultCode-RESULT_CONFIRMATION_CODE_INCORRECT = 212--><!--Device-ResultCode-RESULT_CONFIRMATION_CODE_INCORRECT = 212-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_EXCEEDED_CONFIRMATION_CODE_TRY_LIMIT

```TypeScript
RESULT_EXCEEDED_CONFIRMATION_CODE_TRY_LIMIT = 213
```

已达到最大确认码尝试次数。

**起始版本：** 18

<!--Device-ResultCode-RESULT_EXCEEDED_CONFIRMATION_CODE_TRY_LIMIT = 213--><!--Device-ResultCode-RESULT_EXCEEDED_CONFIRMATION_CODE_TRY_LIMIT = 213-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_NO_PROFILE_ON_SERVER

```TypeScript
RESULT_NO_PROFILE_ON_SERVER = 214
```

服务器上没有可供下载的配置文件。

**起始版本：** 18

<!--Device-ResultCode-RESULT_NO_PROFILE_ON_SERVER = 214--><!--Device-ResultCode-RESULT_NO_PROFILE_ON_SERVER = 214-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_TRANSACTION_ID_INVALID

```TypeScript
RESULT_TRANSACTION_ID_INVALID = 215
```

事务ID无效。

**起始版本：** 18

<!--Device-ResultCode-RESULT_TRANSACTION_ID_INVALID = 215--><!--Device-ResultCode-RESULT_TRANSACTION_ID_INVALID = 215-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_SERVER_ADDRESS_INVALID

```TypeScript
RESULT_SERVER_ADDRESS_INVALID = 216
```

服务器地址无效。

**起始版本：** 18

<!--Device-ResultCode-RESULT_SERVER_ADDRESS_INVALID = 216--><!--Device-ResultCode-RESULT_SERVER_ADDRESS_INVALID = 216-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_GET_BOUND_PROFILE_PACKAGE_FAILED

```TypeScript
RESULT_GET_BOUND_PROFILE_PACKAGE_FAILED = 217
```

获取BPP失败。

**起始版本：** 18

<!--Device-ResultCode-RESULT_GET_BOUND_PROFILE_PACKAGE_FAILED = 217--><!--Device-ResultCode-RESULT_GET_BOUND_PROFILE_PACKAGE_FAILED = 217-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_USER_CANCEL_DOWNLOAD

```TypeScript
RESULT_USER_CANCEL_DOWNLOAD = 218
```

最终用户取消下载。

**起始版本：** 18

<!--Device-ResultCode-RESULT_USER_CANCEL_DOWNLOAD = 218--><!--Device-ResultCode-RESULT_USER_CANCEL_DOWNLOAD = 218-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_SERVER_UNAVAILABLE

```TypeScript
RESULT_SERVER_UNAVAILABLE = 220
```

运营商服务器不可用。

**起始版本：** 18

<!--Device-ResultCode-RESULT_SERVER_UNAVAILABLE = 220--><!--Device-ResultCode-RESULT_SERVER_UNAVAILABLE = 220-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_PROFILE_NON_DELETE

```TypeScript
RESULT_PROFILE_NON_DELETE = 223
```

PPR禁止删除文件。

**起始版本：** 18

<!--Device-ResultCode-RESULT_PROFILE_NON_DELETE = 223--><!--Device-ResultCode-RESULT_PROFILE_NON_DELETE = 223-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_SMDP_ADDRESS_INCORRECT

```TypeScript
RESULT_SMDP_ADDRESS_INCORRECT = 226
```

认证响应服务器地址不匹配。

**起始版本：** 18

<!--Device-ResultCode-RESULT_SMDP_ADDRESS_INCORRECT = 226--><!--Device-ResultCode-RESULT_SMDP_ADDRESS_INCORRECT = 226-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_ANALYZE_AUTHENTICATION_SERVER_RESPONSE_FAILED

```TypeScript
RESULT_ANALYZE_AUTHENTICATION_SERVER_RESPONSE_FAILED = 228
```

解析服务器身份验证响应错误。

**起始版本：** 18

<!--Device-ResultCode-RESULT_ANALYZE_AUTHENTICATION_SERVER_RESPONSE_FAILED = 228--><!--Device-ResultCode-RESULT_ANALYZE_AUTHENTICATION_SERVER_RESPONSE_FAILED = 228-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_ANALYZE_AUTHENTICATION_CLIENT_RESPONSE_FAILED

```TypeScript
RESULT_ANALYZE_AUTHENTICATION_CLIENT_RESPONSE_FAILED = 229
```

解析客户端身份验证响应错误。

**起始版本：** 18

<!--Device-ResultCode-RESULT_ANALYZE_AUTHENTICATION_CLIENT_RESPONSE_FAILED = 229--><!--Device-ResultCode-RESULT_ANALYZE_AUTHENTICATION_CLIENT_RESPONSE_FAILED = 229-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_ANALYZE_AUTHENTICATION_CLIENT_MATCHING_ID_REFUSED

```TypeScript
RESULT_ANALYZE_AUTHENTICATION_CLIENT_MATCHING_ID_REFUSED = 231
```

由于匹配ID被拒绝，解析客户端身份验证响应错误。

**起始版本：** 18

<!--Device-ResultCode-RESULT_ANALYZE_AUTHENTICATION_CLIENT_MATCHING_ID_REFUSED = 231--><!--Device-ResultCode-RESULT_ANALYZE_AUTHENTICATION_CLIENT_MATCHING_ID_REFUSED = 231-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_PROFILE_TYPE_ERROR_AUTHENTICATION_STOPPED

```TypeScript
RESULT_PROFILE_TYPE_ERROR_AUTHENTICATION_STOPPED = 233
```

由于配置文件类型中的错误，身份验证已停止。

**起始版本：** 18

<!--Device-ResultCode-RESULT_PROFILE_TYPE_ERROR_AUTHENTICATION_STOPPED = 233--><!--Device-ResultCode-RESULT_PROFILE_TYPE_ERROR_AUTHENTICATION_STOPPED = 233-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_CARRIER_SERVER_REFUSED_ERRORS

```TypeScript
RESULT_CARRIER_SERVER_REFUSED_ERRORS = 249
```

运营商服务器拒绝原因码为3.8的错误。

**起始版本：** 18

<!--Device-ResultCode-RESULT_CARRIER_SERVER_REFUSED_ERRORS = 249--><!--Device-ResultCode-RESULT_CARRIER_SERVER_REFUSED_ERRORS = 249-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_CERTIFICATE_INVALID

```TypeScript
RESULT_CERTIFICATE_INVALID = 251
```

证书无效。

**起始版本：** 18

<!--Device-ResultCode-RESULT_CERTIFICATE_INVALID = 251--><!--Device-ResultCode-RESULT_CERTIFICATE_INVALID = 251-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_OUT_OF_MEMORY

```TypeScript
RESULT_OUT_OF_MEMORY = 263
```

由于内存不足，配置文件安装失败。

**起始版本：** 18

<!--Device-ResultCode-RESULT_OUT_OF_MEMORY = 263--><!--Device-ResultCode-RESULT_OUT_OF_MEMORY = 263-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_PPR_FORBIDDEN

```TypeScript
RESULT_PPR_FORBIDDEN = 268
```

PPR规则禁止此操作。

**起始版本：** 18

<!--Device-ResultCode-RESULT_PPR_FORBIDDEN = 268--><!--Device-ResultCode-RESULT_PPR_FORBIDDEN = 268-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_NOTHING_TO_DELETE

```TypeScript
RESULT_NOTHING_TO_DELETE = 270
```

没有可删除的配置文件。

**起始版本：** 18

<!--Device-ResultCode-RESULT_NOTHING_TO_DELETE = 270--><!--Device-ResultCode-RESULT_NOTHING_TO_DELETE = 270-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_PPR_NOT_MATCH

```TypeScript
RESULT_PPR_NOT_MATCH = 276
```

与PPR约束不匹配。

**起始版本：** 18

<!--Device-ResultCode-RESULT_PPR_NOT_MATCH = 276--><!--Device-ResultCode-RESULT_PPR_NOT_MATCH = 276-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_CAT_BUSY

```TypeScript
RESULT_CAT_BUSY = 283
```

会话正在进行。

**起始版本：** 18

<!--Device-ResultCode-RESULT_CAT_BUSY = 283--><!--Device-ResultCode-RESULT_CAT_BUSY = 283-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_PROFILE_EID_INVALID

```TypeScript
RESULT_PROFILE_EID_INVALID = 284
```

此eSIM配置文件已被使用或无效。

**起始版本：** 18

<!--Device-ResultCode-RESULT_PROFILE_EID_INVALID = 284--><!--Device-ResultCode-RESULT_PROFILE_EID_INVALID = 284-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_DOWNLOAD_TIMEOUT

```TypeScript
RESULT_DOWNLOAD_TIMEOUT = 287
```

下载超时。

**起始版本：** 18

<!--Device-ResultCode-RESULT_DOWNLOAD_TIMEOUT = 287--><!--Device-ResultCode-RESULT_DOWNLOAD_TIMEOUT = 287-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## RESULT_SGP_22_OTHER

```TypeScript
RESULT_SGP_22_OTHER = 400
```

SGP.22中定义的其他错误。

**起始版本：** 18

<!--Device-ResultCode-RESULT_SGP_22_OTHER = 400--><!--Device-ResultCode-RESULT_SGP_22_OTHER = 400-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。
